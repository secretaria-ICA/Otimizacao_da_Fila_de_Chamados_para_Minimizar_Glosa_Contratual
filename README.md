# Otimização da Fila de Chamados para Minimizar Glosa Contratual

#### Aluno: [Gabriel Nogueira Ferreira](https://github.com/gnf1).
#### Orientadora: [Ana Carolina Alves Abreu](https://github.com/acarolina1612).
#### Co-orientador: [Allan Gurwicz](https://github.com/agurwicz).

---

Trabalho apresentado ao curso [BI MASTER](https://ica.puc-rio.ai/bi-master) como pré-requisito para conclusão de curso e obtenção de crédito na disciplina "Projetos de Sistemas Inteligentes de Apoio à Decisão".

---

### Resumo

Uma empresa prestadora de serviços de TI está tendo dificuldade em atender as demandas em um de seus contratos, dado que o volume de chamados abertos todos os meses é muito grande, além de ter poucos analistas para atender todas as demandas, implicando em uma alta glosa em seu contrato e gerando prejuízos em alguns meses.
  
No contrato da empresa existem dois indicadores primários para atender os chamados no mês. O primeiro é o mínimo de entrega no mês de cada tipo de chamado, que são:
  
- Orientações;
- Correções (*bugs* impeditivos e *bugs* não impeditivos);
- Melhorias pequenas,
- Melhorias médias. 

O segundo é o tempo de resolução de cada chamado, com os seguintes prazos de atendimento:

- Orientações: 2 dias;
- *Bugs* impeditivos: 2 dias;
- *Bugs* não impeditivos: 5 dias;
- Melhorias pequenas : 5 dias;
- Melhorias médias: 20 dias.

De modo a evitar glosas, a líder técnica da equipe realiza um planejamento mensal de chamados de modo a organizar a fila destes. Este é um processo custoso em termos de tempo, além do fato de existirem casos em que chamados potencialmente minimizadores da glosa não são atendidos.

O presente trabalho procurou estudar e utilizar algoritmos genéticos para otimizar a quantidade e alocação de chamados a serem atendidos, respeitando as restrições de tempo disponível de analistas e dias de trabalho, visando minimizar a glosa total e o tempo gasto pela especialista nesta alocação manual. O algoritmo genético (GA) é uma boa escolha nesta demanda pelo fato do problema ser composto por diversas variáveis complexas, que em alguns casos não são levadas em conta pelo especialista.
  
Os dados para solução do problema foram retirados do sistema de chamados da empresa, com as seguintes informações: 

- Sequencial;
- Equipe;
- Tipo de demanda;
- Número de dias em aberto;
- Glosa prevista.

O cálculo da função objetivo foi feito com base no número de dias em aberto somado ao número de dias previstos para atendimento ao chamado, aplicando as regras de atraso de chamados informadas no edital do contrato. Para o escopo dessa prova de conceito, utilizou-se os dados da equipe "corporativo", com apenas 1 analista para atender as demandas.

De modo a priorizar a obtenção de soluções que procurem alocar o máximo de chamados, adicionou-se uma penalidade às soluções propostas pelo GA que mantiveram chamados não alocados.

Este trabalho utilizou o "*solver*" do Microsoft Excel, com o método "*evolutionary*". Diversas configurações foram testadas, e o melhor resultado foi obtido com os seguintes parâmetros:

| Parâmetro                        |  Valor |
| :------------------------------- | -----: |
| Convergência                     | 0,0002 |
| Taxa de mutação                  |   0,07 |
| Tamanho da população             |   1000 |
| Semente aleatória                |      0 |
| Tempo máximo sem aperfeiçoamento |     30 |


Como restrições ao algoritmo, o tempo total de atendimento aos chamados não pode ultrapassar o máximo de horas que uma equipe tem para disponível no dia. Além disso, o GA só pode alocar chamados em dias úteis. Por conta disso, alguns chamados poderão não ser alocados em um determinado mês.

#### Resultados:

Segue a comparação do melhor resultado obtido com o GA, e a alocação do especalista:

| Glosa - GA | Glosa - Especialista |           Observação          |
| :--------: | :------------------: | :---------------------------: |
|    74,55   |         92,35        | Levando em conta a penalidade |
|    55,80   |         56,10        |     Removendo a penalidade    |

No primeiro, a penalidade imposta ao GA é levada em conta no cálculo do resultado final, enquanto no segundo esta é subtraida.

Um ponto importante a destacar é de que mesmo que o resultado com a remoção na penalidade tenha um menor ganho, o fato de se utilizar o GA para identificar a melhor estratégia leva a uma economia significativa de tempo do especialista.

---

Matrícula: 191.671.011

Pontifícia Universidade Católica do Rio de Janeiro

Curso de Pós Graduação *Business Intelligence Master*
