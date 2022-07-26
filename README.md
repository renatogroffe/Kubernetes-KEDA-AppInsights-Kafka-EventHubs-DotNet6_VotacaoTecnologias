# Kubernetes-KEDA-AppInsights-Kafka-EventHubs-DotNet6_VotacaoTecnologias
Objetos para Deployment de um Worker Service (apuração de votos de tecnologias) no Kubernetes utilizando KEDA, Helm, monitoramento com Azure Application Insights, Apache Kafka (a partir de uma instância do Azure Event Hubs) e .NET 6.

Worker Service para consumo de **mensagens vinculadas a um tópico do Apache Kafka** (imagem **renatogroffe/workerquestao-kafka-appinsights-dotnet6:latest**) - é justamente esta aplicação que será escalada via **KEDA**:

**https://github.com/renatogroffe/DotNet6-WorkerService-AppInsights-Kafka-Partitions-SqlServer_VotacaoTecnologias**

Projeto que serviu de base para o **envio de mensagens a um tópico do Apache Kafka** (imagem **renatogroffe/sitequestao-kafka-appinsights-dotnet6:latest**):

**https://github.com/renatogroffe/ASPNETCore6-MVC-AzureEventHubs-Kafka-AppInsights_SiteQuestao**

No arquivo **keda-instalacao&sdot;sh** estão as instruções para instalação do KEDA **(Kubernetes Event-driven Autoscaling)** em um **cluster Kubernetes**.

Para os testes de carga que escalam a aplicação utilizei o pacote npm [**loadtest**](https://www.npmjs.com/package/loadtest). O exemplo a seguir procederá com o envio de **5 mil requisições**, simulando **70 usuários concorrentes**:

**loadtest -c 70 -n 5000 -k** ***ENDPOINT***