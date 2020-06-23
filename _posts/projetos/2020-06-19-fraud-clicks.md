---
layout: post
title: "Meu Primeiro Projeto de Data Science"
categories: update
permalink: /:categories/:year/:month/:day/:title.html
author: "Victor de Paula"
---

Meu primeiro "projetinho" de Data Science foi a *Detecção de Fraudes no Tráfego de Cliques em Propagandas de Aplicações Mobile*, que faz parte do curso *Big Data Analytics com R e Microsoft Azure Machine Learning* da [Data Science Academy (DSA)](https://www.datascienceacademy.com.br/), uma plataforma de cursos online de tecnologia, com uma didática muito voltada para a prática. O *Big Data Analytics com R e Microsoft Azure Machine Learning* é o primeiro curso da *Formação Cientista de Dados (FCD)* da DSA e engloba os conceitos básicos de Data Science, além de programação em R e criação de modelos de Machine Learning com o [Microsoft Azure Machine Learning](https://azure.microsoft.com/pt-br/services/machine-learning/).

# Contextualização: os cliques fraudulentos em anúncios online

Empresas que anunciam online estão muito suscetíveis a cliques fraudulentos (também chamadas de *click frauds*), isto é, quando um indivíduo ou algum programa de computador explora anunciantes online, clicando repetidamente em um anúncio PPC (*pay-per-click*) para gerar cobranças fraudulentas. A fraude aumenta os custos de publicidade, reduz as taxas de conversão de download e distorce os dados de usuário para negócios online. Só para se ter uma ideia, em uma previsão feita pela [Juniper Research](https://www.juniperresearch.com/home), os cliques fraudulentos em publicidade digital em 2019 estima um prejuízo de US$ 42bi aos anunciantes, 21% a mais do que em 2018, quando o prejuízo foi de US$ 35bi. Anualmente, até 2023, o prejuízo causado por cliques fraudulentos deve alcançar a marca dos US$ 100bi.

Devido à falta de adoção de soluções antifraude para anunciantes menores e às táticas cada vez mais complexas dos fraudadores, a [Juniper](https://www.juniperresearch.com/home) prevê que os anunciantes economizarão apenas US$ 16bi em possíveis gastos com anúncios perdidos em fraudes. Além disso, a pesquisa aponta que o crescimento do inventário de anúncios dos editores crescerá mais rápido do que a demanda dos anunciantes nos próximos quatro anos. Como resultado, fraudadores procurarão preencher essa lacuna crescente entre oferta e demanda preenchendo o inventário não utilizado com anúncios fraudulentos.

Segundo Michel Primo, executivo da [ClickCease](https://clickcease.com.br/?tap_a=54098-332c74&tap_s=573603-0d13ff), uma Martech israelense especializada na defesa contra ações desse tipo, os cliques fraudulentos envolvem ações que forçam o anunciante a gastar com cliques que não foram feitos por consumidores reais. Nesse caso, robôs clicam de maneira consecutiva e fazem o responsável pelo anúncio pagar por visualizações que não atingiram potenciais clientes verdadeiros, ou seja, não há ganho direto para o responsável pelo golpe, apenas prejuízo para o anunciante. Michel Primo também afirma que "o Brasil é um dos principais mercados mundiais na publicidade digital, então é natural que seja um alvo valioso para esse tipo de golpe".

Ainda segundo a [ClickCease](https://clickcease.com.br/?tap_a=54098-332c74&tap_s=573603-0d13ff), entre as melhores estratégias para evitar golpes na publicidade digital, estão softwares que monitoram o tráfego e identificam comportamentos anormais, assim como a escolha adequada dos parceiros que fazem parte do ecossistema de marketing da empresa.

# Meu projeto

O algoritmo foi desenvolvido em linguagem R e utiliza um dataset do [kaggle](https://www.kaggle.com/c/talkingdata-adtracking-fraud-detection/data), com as seguintes características dos cliques:

* ip: endereço IP do clique;
* app: ID do aplicativo para marketing;
* device: ID do tipo de dispositivo do celular do usuário (por exemplo, iphone 6 plus, iphone 7, huawei
mate 7 etc);
* os: ID da versão do telefone móvel do usuário;
* channel: ID do canal do editor de anúncios para celular
* click_time: registro de data e hora do clique (UTC);
* attributed_time: se o usuário baixar o aplicativo para depois de clicar em um anúncio, este é o horário
do download do aplicativo;
* is_attributed: a variável a ser prevista, indicando que o aplicativo foi baixado;

A análise exploratória dos dados permitiu os seguintes insights:

* Dados altamente desbalancedos, podendo acarretar em overfitting;
* Cada endereço de IP gera entre 2 e 3 cliques;
* 80% dos endereços de IP geram 3 cliques;
* 0,2% dos cliques são efetivamente convertidos em download;
* Cerca de 12% dos endereços de IP dão mais de 27 cliques, sendo suspeitos de fraude;
* Dos IPs com mais de 27 cliques, 2% realizam o download;
* Dos IPs com mais de 27 cliques, 25% dão mais que 200 cliques de um total de 100,000 cliques;
* Os IPs com mais que 200 cliques representam 3% dos total de cliques;
* Cerca de 10% dos cliques é realizado no período da madrugada;
* Dos cliques convertidos em download, 40% no período da manhã;
* A média entre clique e download do app é de 75 minutos, aproximadamente;
* A conversão de download está ligada ao enderço de IP, mais do que as outras características;

Utilizando o *K-Nearest Neighbor Classification* como modelo preditivo, o algoritmo foi capaz de conseguir **acurácia maior que 90% para previsão dos dados apresentados**. Todavia, para buscar uma performance melhor, um estudo mais detalhado sobre o dataset precisa ser feito, como subdividir ainda mais os as horas do dia nas quais um clique é realizado (ao invés de madrugada, manhã, tarde e noite). Uma outra sugestão de melhoria para generalização do modelo é realizar uma *feature selection* visando escolher as características mais representativas da conversão de cliques.

Para download dos arquivos, acesse minha página do [GitHub](https://github.com/victordp/projeto-dsa-01).

# Fontes

[What is click fraud? How to Identify and Prevent Fraudulent Clicks](https://www.bigcommerce.com/ecommerce-answers/what-is-click-fraud-identify-and-prevent-fraudulent-clicks/)

[Indústria de cliques fraudulentos em publicidade digital deve causar um prejuízo de US$ 42 bilhões em 2019](https://www.brasil61.com/noticias/industria-de-cliques-fraudulentos-em-publicidade-digital-deve-causar-um-prejuizo-de-us-42-bilhoes-em-2019-pran197702)

[ADVERTISING FRAUD LOSSES TO REACH $42 BILLION IN 2019, DRIVEN BY EVOLVING TACTICS BY FRAUDSTERS](https://www.juniperresearch.com/press/press-releases/advertising-fraud-losses-to-reach-42-bn-2019)

[FAKE CLIQUE: FRAUDES EM PUBLICIDADE DIGITAL GERAM PREJUÍZOS DE US$ 42 BILHÕES](https://blogdochicopereira.com/web/fake-clique-fraudes-em-publicidade-digital-geram-prejuizos-de-us-42-bilhoes/)

[Data Science Academy](https://www.datascienceacademy.com.br/)