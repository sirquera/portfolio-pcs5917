# PCS5917 – IA Adversarial

## Portfólio Individual

**Aluna:** Glaucia Santana  
**Disciplina:** PCS5917 – IA Adversarial  
**Período:** 3º período de 2026  
**Instituição:** Universidade de São Paulo – Escola Politécnica  
**Professor:** Victor Takashi Hayashi  

## 1. Objetivo do Portfólio

Este portfólio reúne as principais atividades, estudos, experimentos e reflexões desenvolvidos ao longo da disciplina **PCS5917 – IA Adversarial**.

O objetivo é documentar individualmente o processo de aprendizagem sobre:

- notícias e referências científicas sobre IA Adversarial (Aula 1);
- fundamentos de Inteligência Artificial e Segurança (Aula 2);
- aplicação de IA em cibersegurança (Aula 3);
- ataques adversariais contra sistemas de IA (Aulas 4 e 5);
- avaliação de ataques e uso de LLMs como juiz (Aula 6);
- defesas em Large Language Models (Aula 7).

Os experimentos realizados durante as aulas devem ser complementados por registros individuais, notebooks, respectivos resultados e referências bibliográficas (citações).

## 2. Organização do Repositório

**IMPORTANTE**: somente branch main (demais branches serão desconsideradas na correção).
Faça o desenvolvimento incremental com **commits semanais**, pois a evolução durante as semanas também é critério de avaliação.
Organize seu README focando em ser objetivo, com evidências de resultados e citações às referências utilizadas.

```text
.
├── README.md (com registros de resultados)
├── notebooks/ (colocar aqui os notebooks citados no README)
│   ├── aula-02-llm-jailbreaks.ipynb
│   ├── aula-03-asvspoof.ipynb
│   ├── aula-04-nanogcg.ipynb
│   ├── aula-05-pair.ipynb (e/ou cipherchat)
│   ├── aula-06-llm-judge.ipynb
│   └── aula-07-defesas-llm.ipynb
├── images/ (colocar aqui as imagens usadas no README)
│   └── ...
└── outros/
    └── ...
```

## 3. Registros de Aprendizagem

### Aula 1 — Notícias e referências científicas sobre IA Adversarial

**Recorte escolhido:** a superfície adversarial está se deslocando do *modelo* para o *agente*, enquanto o instrumento que usamos para medir ataques permanece frágil. As três fontes abaixo, lidas juntas, sustentam essa tese.

#### Notícia

A Agência Brasil noticiou que a Abin incluiu **"ataques cibernéticos autônomos com agentes de inteligência artificial"** entre os cinco principais desafios de segurança projetados para 2026. Segundo o documento da agência, a IA pode operar como **agente ofensivo autônomo, capaz de planejar, executar e adaptar ataques** — com risco de escalada de um incidente cibernético para conflito militar [1].

O ponto relevante para a disciplina não é a projeção em si, mas o **deslocamento do objeto de ataque**: a preocupação declarada por um órgão de Estado já não é o modelo que responde algo indevido, e sim o agente que planeja e executa.

#### Referências científicas

**[2] SoK sobre jailbreaking em IA agêntica (set/2026).** Mia et al. reposicionam a segurança de jailbreak em torno do *pipeline completo de execução agêntica*, propondo taxonomias unificadas de ataque e defesa que cobrem interação com o usuário, planejamento, memória, uso de ferramentas e comunicação entre agentes. Dois achados interessam diretamente ao recorte: alinhamento nativo forte **não** garante robustez a jailbreak adversarial; e *"low final-response attack success can mask severe intermediate compromise"* — ou seja, medir apenas a resposta final subestima o comprometimento de componentes internos do agente.

**[3] Confiabilidade de LLMs como juízes (fev/2026).** Schwinn et al. mostram que o desempenho de juízes automáticos **degrada para perto do acaso** sob a mudança de distribuição própria dos testes adversariais. Os protocolos atuais de validação não consideram a variação entre modelos-vítima, a distorção dos padrões de saída nem a ambiguidade semântica. A consequência é direta: muitos ataques relatam **taxas de sucesso infladas** por explorarem a insuficiência do juiz, e não por eliciarem conteúdo prejudicial. Os autores propõem o *ReliableBench* e o *JudgeStressTest* como resposta.

#### Síntese

As três fontes convergem num problema de **medição**. A superfície cresce em direção ao agente [1][2]; ao mesmo tempo, o sucesso aferido na resposta final esconde comprometimento intermediário [2] e o juiz automático que produz essa aferição degrada para acaso [3]. Tomadas em conjunto, as taxas de sucesso publicadas hoje informam pouco sobre risco real — e informam menos justamente no cenário que a Abin projeta.

#### Ligação com o material da disciplina

O minicurso do SBSeg 2024 [4] já exibe esse problema em miniatura. No experimento com a ferramenta PAIR, uma iteração que produziu instruções maliciosas é descartada pela função juiz *"pelo início da sequência não ser idêntico ao prompt objetivo"* — isto é, casamento de cadeia de caracteres no lugar de avaliação semântica. O próprio capítulo reconhece que julgar um jailbreak é um problema semântico difícil. É exatamente a falha que Schwinn et al. [3] formalizam e quantificam dois anos depois, e o tema retorna como objeto da **Aula 6 (uso de LLMs como juiz)**.

#### Referências

[1] PEDUZZI, Pedro. **Abin: segurança nas eleições e ataques com IA são desafios para 2026.** Agência Brasil, 2 dez. 2025. Disponível em: https://agenciabrasil.ebc.com.br/geral/noticia/2025-12/abin-seguranca-nas-eleicoes-e-ataques-com-ia-sao-desafios-para-2026

[2] MIA, Md Jueal; WU, Yanzhao; ULUAGAC, Selcuk; AMINI, M. Hadi. **SoK: Rethinking Jailbreaking in the Era of Agentic AI: Attacks, Defenses, and Practical Consideration.** arXiv:2609.12413, 11 set. 2026. Disponível em: https://arxiv.org/abs/2609.12413

[3] SCHWINN, Leo; LADENBURGER, Moritz; BEYER, Tim; MOFAKHAMI, Mehrnaz; GIDEL, Gauthier; GÜNNEMANN, Stephan. **A Coin Flip for Safety: LLM Judges Fail to Reliably Measure Adversarial Robustness.** arXiv:2603.06594, fev. 2026 (rev. mar. 2026). Disponível em: https://arxiv.org/abs/2603.06594

[4] MIERS, Charles Christian et al. **Ferramentas de Jailbreaking para Grandes Modelos de Línguas – Aprendizado de Máquina no Contexto Adversário.** In: Minicursos do SBSeg 2024. Porto Alegre: SBC, 2024. cap. 2. DOI: 10.5753/sbc.15101.8.2

## Disclaimer de Uso Ético

Este repositório foi desenvolvido exclusivamente para fins acadêmicos e de pesquisa no contexto da disciplina **PCS5917 – IA Adversarial**.

Alguns experimentos, datasets, prompts, códigos e resultados apresentados podem conter **conteúdo potencialmente malicioso**, incluindo exemplos de jailbreaks, payloads e outras técnicas de ataque. Esses materiais são disponibilizados para fins de estudo, análise, reprodução controlada e compreensão de mecanismos de ataque e defesa.

Os conteúdos devem ser utilizados somente em **ambientes autorizados e controlados**, sem direcionamento a sistemas, modelos, redes, dispositivos ou usuários de terceiros. A reprodução dos experimentos deve respeitar as políticas de uso das ferramentas e os termos das plataformas utilizadas.

O conteúdo deste repositório **não constitui recomendação ou incentivo à realização de atividades maliciosas**. O objetivo é compreender riscos de segurança, desenvolver métodos de avaliação e contribuir para o desenvolvimento de sistemas de Inteligência Artificial mais seguros.
