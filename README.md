# AVA3 — Situação 1: Placa 2 (1 LED — Módulo Receptor)

Código-fonte referente à **Placa 2** na **Situação 1** (comunicação serial ponto a ponto unidirecional entre duas placas Arduino Uno simuladas no **Tinkercad Circuits**), atuando como nó receptor para acionamento remoto de um LED.

## Arquivo Principal
- `Placa 2_um_led_um_botao.txt`

## Visão Geral do Circuito e Funcionamento
- **Microcontrolador:** Arduino Uno (Placa 2 — receptora, à direita na simulação)[cite: 1].
- **Saída (`LED1`):** LED vermelho conectado ao pino `A0` (`OUTPUT`) em série com resistor limitador de corrente e referenciado ao terra comum (`GND`)[cite: 1].
- **Comunicação Serial (UART):** taxa de `9600` bps (`Serial.begin(9600)`), interligada de forma cruzada (`TX` $\rightarrow$ `RX` e `RX` $\rightarrow$ `TX`) com compartilhamento de `GND` junto à placa transmissora[cite: 1].
- **Lógica (`loop()`):** verifica a disponibilidade de dados com `Serial.available()`, lê o byte recebido via `Serial.read()` em uma variável `char` (`dados`) e atualiza o estado do LED com `digitalWrite(LED1, dados)`.

## Cenários Documentados no Tinkercad
- **Sistema inicial com um botão e um LED desligado:** `LED1` permanece apagado na condição inicial de repouso[cite: 1].
- **Sistema inicial com um botão e um LED ligado:** `LED1` acende ao receber o comando transmitido pela placa 1 quando `BOT1` é pressionado.
