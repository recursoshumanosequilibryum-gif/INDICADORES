# Relatório Mensal de RH — Template Automatizável

Template em Markdown para gerar relatórios mensais de indicadores de RH (turnover, absenteísmo, admissões, desligamentos, horas extras etc.) de forma automatizada, seja por uma IA (Claude, ChatGPT) ou por uma planilha inteligente.

## O que este template faz

- Define **campos personalizáveis** entre chaves `{ }` (ex: `{turnover}`, `{absenteismo}`, `{admissoes}`) para você preencher com os dados do mês.
- Traz **regras de interpretação** (variações, comparação com metas, cruzamento entre indicadores, níveis de severidade) para padronizar a análise.
- Especifica o **formato de saída em texto corrido**, já estruturado com resumo executivo, análise por indicador e recomendações.
- Inclui um **exemplo de prompt pronto** para usar diretamente com uma IA.

## Como usar

### Com uma IA (Claude, ChatGPT, etc.)
1. Copie o template abaixo (seções 1 a 5).
2. Substitua os campos entre chaves pelos valores reais do mês (ou peça para a IA puxar de uma planilha/sistema conectado).
3. Use o prompt de exemplo da seção 4, ou peça diretamente: *"gere o relatório mensal de RH seguindo este template com estes dados: ..."*

### Em planilha (Excel / Google Sheets)
1. Transforme cada campo `{campo}` em uma referência de célula (ex: `{turnover}` → `=B2`).
2. Use fórmulas condicionais (`SE`/`IF`) para reproduzir as regras de severidade da seção 2.
3. Opcional: conecte a planilha a um add-on de IA para gerar o texto final automaticamente a partir dos números calculados.

---

# Template

> **Como usar:** preencha os campos entre chaves `{ }` com os valores do mês (manualmente, via planilha inteligente ou via IA conectada aos seus dados). O bloco "Instruções para geração automática" abaixo contém as regras de interpretação que devem ser seguidas para montar as análises e recomendações a partir dos números informados.

## 1. Dados de Entrada (preencher)

| Indicador | Valor do mês | Valor do mês anterior | Meta/Benchmark |
|---|---|---|---|
| Turnover (%) | {turnover} | {turnover_mes_anterior} | {meta_turnover} |
| Absenteísmo (%) | {absenteismo} | {absenteismo_mes_anterior} | {meta_absenteismo} |
| Admissões (nº) | {admissoes} | {admissoes_mes_anterior} | — |
| Desligamentos (nº) | {desligamentos} | {desligamentos_mes_anterior} | — |
| Horas extras (h ou %) | {horas_extras} | {horas_extras_mes_anterior} | {meta_horas_extras} |
| Headcount total | {headcount} | {headcount_mes_anterior} | — |
| Período de referência | {mes_referencia} | — | — |
| Área/Departamento | {area} | — | — |

*(Adicione ou remova linhas conforme os indicadores disponíveis na sua empresa — ex: `{engajamento}`, `{clima_organizacional}`, `{custo_por_contratacao}`, `{tempo_medio_contratacao}`.)*

## 2. Instruções para geração automática (regras de interpretação)

A IA ou planilha deve seguir esta lógica ao montar o relatório final:

1. **Calcular variações**: para cada indicador, calcular a variação percentual em relação ao mês anterior e classificar como ▲ alta, ▼ queda ou ► estável (variação entre -2% e +2%).
2. **Comparar com meta/benchmark**: quando houver meta informada, indicar se o resultado está **dentro**, **acima** ou **abaixo** do esperado.
3. **Cruzar indicadores relacionados**:
   - Turnover alto + absenteísmo alto → sinal de possível insatisfação ou problema de clima.
   - Desligamentos > admissões → headcount em contração; avaliar se é planejado.
   - Horas extras em alta + admissões baixas → possível sobrecarga da equipe atual.
4. **Classificar severidade** de cada alerta em: 🟢 Normal / 🟡 Atenção / 🔴 Crítico, com base em quanto o valor se distancia da meta (ex: até 10% acima = Atenção; mais de 25% acima = Crítico — ajustável por empresa).
5. **Gerar recomendações práticas**, ligadas a cada indicador fora da meta, priorizando as de maior severidade.
6. **Nunca inventar dados**: se um campo não for informado, a IA deve indicar "dado não informado" em vez de estimar.

## 3. Formato de Saída Esperado (texto corrido, gerado automaticamente)

```
RELATÓRIO MENSAL DE INDICADORES DE RH
Período: {mes_referencia} | Área: {area}

RESUMO EXECUTIVO
[2-3 frases sintetizando o mês: tendência geral de turnover, absenteísmo e força de trabalho]

1. TURNOVER
Resultado: {turnover}% (mês anterior: {turnover_mes_anterior}%) — variação [▲/▼/►]
Status frente à meta: [dentro/acima/abaixo] da meta de {meta_turnover}%
Análise: [interpretação da causa provável com base no cruzamento de indicadores]
Severidade: [🟢/🟡/🔴]

2. ABSENTEÍSMO
Resultado: {absenteismo}% (mês anterior: {absenteismo_mes_anterior}%) — variação [▲/▼/►]
Status frente à meta: [dentro/acima/abaixo] da meta de {meta_absenteismo}%
Análise: [interpretação]
Severidade: [🟢/🟡/🔴]

3. MOVIMENTAÇÃO DE PESSOAL
Admissões: {admissoes} | Desligamentos: {desligamentos}
Saldo do mês: [admissões - desligamentos]
Análise: [expansão, contração ou estabilidade da equipe]

4. HORAS EXTRAS
Resultado: {horas_extras} (mês anterior: {horas_extras_mes_anterior}) — variação [▲/▼/►]
Análise: [relação com headcount e volume de desligamentos/admissões]
Severidade: [🟢/🟡/🔴]

RECOMENDAÇÕES DO MÊS
1. [Recomendação prioritária ligada ao indicador mais crítico]
2. [Recomendação secundária]
3. [Recomendação preventiva/monitoramento]

PRÓXIMOS PASSOS SUGERIDOS
- [Ação de curto prazo]
- [Indicador a monitorar com atenção no próximo mês]
```

## 4. Exemplo de Prompt para usar com uma IA (ex: Claude, ChatGPT)

> "Você é um analista de RH. Usando o template de relatório mensal acima e os seguintes dados: turnover = 4,2%, absenteísmo = 3,8%, admissões = 12, desligamentos = 18, horas extras = 15% acima da meta, headcount = 340 (mês anterior 346), meta de turnover = 3%, meta de absenteísmo = 3%, meta de horas extras = 5% — gere o relatório completo em formato textual seguindo exatamente a estrutura da seção 3, com análises cruzadas e recomendações priorizadas por severidade."

## 5. Dicas de personalização

- Em planilhas (Excel/Google Sheets), os campos entre `{ }` podem virar referências de célula (ex: `=B2` no lugar de `{turnover}`).
- As metas podem ser fixas ou dinâmicas (ex: média dos últimos 6 meses).
- Para times de RH com múltiplas áreas, gere o relatório uma vez por `{area}` e depois consolide um resumo comparativo entre áreas.
- Adapte os limites de severidade (10%/25% no item 2.4) à realidade e ao histórico da sua empresa.

---

## Licença

Distribuído sob a licença **MIT** — uso livre, inclusive comercial, com atribuição.

```
MIT License

Copyright (c) 2026

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
