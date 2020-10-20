# Escalonamento de CPU 📊

> Não Preempritivo: O processo __não__ pode ser interrompido <br/>
> Preempritivo: __Pode__ ser interrompido

## :arrow_right: Escalonamento FIFO (First In First Out) :arrow_lower_right:: <img src="https://img.shields.io/badge/-n%C3%A3o%20preemptivo-red" /> 
  - O escalonamento *FIFO*, significa o primeiro processo a “chegar” será o primeiro a “sair”, ou seja, ser executado, além de não poder ser interrompido até o final de sua execução (não preemptivo).
  
  __Exemplo:__ Em uma analogia simples com um estacionamento de um shopping, em que há uma fila para poder entrar e sair do mesmo, o 1º carro a chegar, será o 1º a sair também. <br/>

## :chart: Escalonamento HPF (Highest Priority First): <img src="https://img.shields.io/badge/-n%C3%A3o%20preemptivo-red" />
  - Nesse escalonamento, o que define a ordem de execução é a prioridade do processo, logo processos como o do sistema operacional, por exemplo, serão executados antes de outros mais secundários.
  
  __Exemplo:__ Utilizando ainda o exemplo do estacionamento, seria o caso de chegar um carro ao estacionamento de uma pessoa super importante do governo, sendo colocado como o 1º da fila para entrar no estacionamento. <br/>

## :pinching_hand: Escalonamento SJF (Shortest Job First): <img src="https://img.shields.io/badge/-n%C3%A3o%20preemptivo-red" />
  - É quase o contrário do *HPF*, definindo agora o processo a ser executado pelo seu tamanho, ou seja, quanto menor o processo mais rápido ele será executado, sendo posto assim para ser 1º que outros processos.
  
  __Exemplo:__ No caso do estacionamento, seria o caso de alguém com um meio de locomoção menor, como uma bicicleta, entrar antes de um carro por exemplo, visto que uma bicicleta é menor e mais rápida de entrar e “estacionar”. <br/>
 
## :balance_scale: Escalonamento HRN (Highest Response-Ratio Next): <img src="https://img.shields.io/badge/-n%C3%A3o%20preemptivo-red" />
  - Administra de forma dinâmica os processos que estão na fila, levando em consideração seu tempo de execução e prioridade, unindo assim os escalonamentos *SJF* e *HPF*, colocando o processo com maior prioridade para execução, mas depois de concluído, podendo trocá-lo por um processo com menor tempo de execução.
  
  __Exemplo:__ Em um estacionamento, seria o caso de ser a vez da bicicleta entrar, contudo acaba de chegar o carro do presidente do país para entrar no estacionamento, passando assim a entrada ao carro. <br/>

## :small_red_triangle_down: Escalonamento SRT (Shortest Remaining Time): <img src="https://img.shields.io/badge/-preemptivo-green" />
  - É a versão preemptiva do *SJF*, ou seja, pode ser interrompida durante sua execução. Possui a mesma ideia de processar primeiro processos menores, porém caso o processo que estiver sendo executado tiver um tempo para ser finalizado maior que o tempo de execução novo processo que chegou, ele será substituído, voltando para o final da fila. <br/>
 - Contudo, voltará somente com o tempo que faltava para terminar seu processamento, ou seja, se o Processo A levava 12s para ser concluído e foi interrompido com 5s de execução, pois chegou um processo B que levava só 2s para ser processado, o processo A voltará para o final da fila faltando 7s para terminar de ser processado pela CPU.
 
  __Exemplo:__ Fazendo uma analogia com um supermercado, podemos imaginar uma fila de um atendimento caracterizado como “Caixa Rápido”, a onde há alguém (Pessoa A) sendo atendido com 7 produtos, dos quais 2 já foram passados pela caixa, porém acaba de chegar mais uma pessoa (Pessoa B) a fila com apenas 2 produtos, logo essa pessoa passará imediatamente a frente da Pessoa A e a mesma voltará ao final da fila, agora com apenas 5 produtos restando. <br/>

## :arrows_clockwise: Escalonamento RR (Round Robin): <img src="https://img.shields.io/badge/-preemptivo-green" />
  - É quase igual ao *FIFO*, com a organização segundo a ordem de chegada, porém nele existe a presença de um intervalo chamado de *Quantum*, o qual define o tempo que cada processo terá para ser executado, terminando esse tempo e o processo não sendo terminado de ser executado, ele voltará ao final da fila, tendo seu contexto salvo, e aguardará ser processado novamente.
  
  __Exemplo:__ Utilizando as pessoas A e B do exemplo anterior, na mesma fila do supermercado, imaginemos que existe um tempo (*Quantum*) para a atendente do caixa conseguir passar as compras, por exemplo de 10s, todas as compras da Pessoa A levam cerca de 21s para serem passadas e da Pessoa B 8s. <br/>
Assim quando for a vez da Pessoa A ser atendida, ela terá que voltar ao final da fila novamente, com seu contexto de 11s restantes para terminar de ser atendida (visto que 21s da Pessoa A menos 10s da atendente é igual aos 11s restantes), porém a Pessoa B será atendida de uma vez, sem a necessidade de voltar novamente a fila. <br/>

## :fog: Escalonamento MQ (Multilevel Queues): <img src="https://img.shields.io/badge/-preemptivo-green" />
  - Cada tipo de processo é separado em uma fila específica para ele, havendo agora uma ordenação de quais filas são mais importantes e precisam ser executadas primeiro, ou seja, processos do sistema ficam em uma fila que tem a maior prioridade, processos secundários ficam em outra fila (podendo ter um outro tipo de processo como o *FIFO* por exemplo), processos *RR* ficam em outra fila e assim por diante, sendo assim, cada fila pode ter um tipo diferente de escalonamento.
  
  __Exemplo:__ Fazendo a analogia com o as filas de um supermercado, onde há caixas (filas) específicas para cada necessidade (processo), por exemplo, há uma fila para pessoas com necessidades especiais (idosos, gestantes, deficientes e etc), uma fila para compras rápidas, uma fila para compras mais extensas e etc, além de que, dependendo da ocasião, uma determinado fila pode ter uma atenção (prioridade) maior que as demais. <br/>

## :arrow_right: :arrows_clockwise: Escalonamento MFQ (Multilevel Feedback Queues): <img src="https://img.shields.io/badge/-preemptivo-green" />
  - É baseado em filas encadeadas, ou seja, uma após a outra, não sendo mais separadas pelo tipo de processo. Todos os novos processos são sempre colocados na 1ª fila que tem o escalonamento *FIFO*, assim como a 2ª, 3ª ..., menos a última fila, possuindo o escalonamento *RR*, visto que é necessário que todos os processos sejam finalizados de alguma maneira.
  
  __Exemplo:__ No caso de um supermercado, podemos imaginar uma fila que leva logo a outra, sendo que as pessoas que chegaram primeiro são também as primeiras a chegarem a última fila, que tem por objetivo de que terminem todas as compras, acontecendo nela o mesmo [exemplo do escalonamento RR](https://github.com/pferreirafabricio/cpu-scheduling/blob/main/README.md#arrows_clockwise-escalonamento-rr-round-robin-), entre a Pessoa A e a Pessoa B. <br/>
  
## :recycle: Contribua
  Acha que alguma explicação ficou confusa ou que poderia ser melhor? Quer adicionar algum vídeo ou imagem para complementar a explicação? É só mandar um Pull Request com a sua alteração 😃
 1. Clone esse repositório;
 2. Crie uma branch com a sua alteração: ```git checkout -b adiciona-video-fifo```
 3. Commit suas mudanças: ```git commit -m 'feat: Adiciona vídeo de explicação sobre FIFO'```
 4. Push sua branch: ```git push origin adiciona-video-fifo```
 
## :page_with_curl:	Licensa
Esse projeto está sob a licensa MIT. De uma olhada nela [LICENSE](LICENSE.md) para mais detalhes.

