# 💸 App de Organização de Finanças Pessoais com Vibe Coding

Aprenda a **criar soluções com IA** de forma criativa, guiando ferramentas como o **Copilot** e o **Lovable** com uma comunicação simples e natural. O foco é desenvolver o conceito de um **App de Organização de Finanças Pessoais**, mas, acima de tudo, aprender o **jeito Vibe de programar com IA**.

## ✨ O que é Vibe Coding

**Vibe Coding** é uma forma leve e criativa de desenvolver com IA, baseada em **conversas naturais e bem estruturadas**. Você não precisa escrever código linha por linha. Em vez disso, aprende a **guiar a IA** descrevendo suas ideias de forma clara, com **intenção e contexto**. Em outras palavras:

> Você mostra a vibe da sua ideia e a IA transforma em solução (ou em um caminho para ela).

## 🎯 Desafio

PRD revisado pelo Copilot (v1.0) – “Receita Certa" 💸

Objetivo

Aplicativo Android que permite registrar receitas de forma intuitiva por conversa e análise de imagens (OCR), categorizar automaticamente, calcular total mensal, e emitir relatórios. Foco em comissões, bicos, freelas e rendimentos de investimentos.

Público-alvo

 

Pessoas com renda variável (comissionistas, freelancers, autônomos, investidores).

Usuários que preferem entrada rápida via assistente conversacional e captura por foto.

 

Escopo (MVP)

 

Login Google (Google Sign-In).

Assistente de conversa:

 

Input livre (“Ganhei R$ 250 de comissão da venda de hoje.”).

Detecção: valor, moeda (BRL), data (default: hoje), categoria (comissão/bico/freela/investimentos/outros), descrição opcional.

Perguntas de desambiguação quando necessário.

Confirmação antes de salvar (“Posso registrar?”).

 

 

OCR de fotos:

 

Upload da imagem (extrato/nf/recibo).

Extração de valores, datas e possíveis categorias por palavras-chave (ex.: “comissão”, “serviço”, “PIX”, “dividendo”).

Revisão pelo usuário (tela de confirmação com campos editáveis).

 

 

Cadastro manual (fallback).

Listagem e soma mensal:

 

Dashboard: total do mês, por categoria, últimos lançamentos.

Filtro por mês/ano e categoria.

 

 

Relatórios:

 

Geração em PDF (com tabela + gráfico pizza por categoria + barra por meses).

Exportar CSV.

 

 

Design universal:

 

Layout acessível (contrast ratio AA), textos grandes, navegação simples, ícones + emojis:

 

💼 Comissões | 🧰 Bicos | 🧑‍💻 Freelance | 📈 Investimentos | ➕ Outros

 

 

Suporte português (pt-BR) v1.

 

 

Armazenamento:

 

Cloud (ex.: Firestore) por usuário (autenticado com Google).

Cache local e sync.

 

 

 

Fora do escopo (v1)

 

Planejamento fiscal detalhado, IR automático.

Multi-moeda.

Conexão bancária (Open Finance).

Automação completa de investimentos (rendimentos diários).

Web app.

 

Requisitos funcionais

 

RF1: Login com Google.

RF2: Entrada por chat com NLP para valor, categoria, data, descrição.

RF3: OCR de imagens para detectar valores e datas; sugerir categoria.

RF4: Edição e confirmação antes de persistir.

RF5: Dashboard com total mensal e por categoria.

RF6: Relatórios em PDF e CSV com filtros.

RF7: Histórico com busca (por texto).

RF8: Multidispositivo (conta Google).

RF9: Modo escuro/claro.

 

Requisitos não-funcionais

 

RNF1: Performance: OCR < 4s média em rede 4G.

RNF2: Acessibilidade: TalkBack, labels, tamanho mínimo de fonte 16sp, contraste AA.

RNF3: Segurança: dados em trânsito via TLS; dados em repouso criptografados (Firestore rules por UID).

RNF4: Privacidade: consentimento para processamento de imagens; política LGPD.

RNF5: Disponibilidade: 99% mensal (serviços gerenciados).

RNF6: Compatibilidade: Android 8+ (SDK min 26), target SDK atual.

 

Métricas (MVP)

 

Ativação D1: % que completam 1º lançamento.

Tempo até 1º valor registrado (TTV).

Precisão de classificação automática (% aceitação sem edição).

Engajamento semanal (lançamentos/usuário).

Exportações de relatório (PDF/CSV).

 

Riscos e mitigação

 

OCR falhar ➜ UI clara para correção manual, recorte/realce, tutorial de foto.

Ambiguidade no chat ➜ perguntas de follow-up (“Foi comissão, freela ou investimento?”).

Rejeição Google Play ➜ atender políticas de privacidade e permissões.

 

 

(3) Backlog – User stories + Critérios de aceite ✅

US1 – Login Google

Como usuário, quero entrar com minha conta Google para ter meus dados sincronizados.

 

CA: Botão “Entrar com Google”; se sucesso ➜ perfil carregado; se falha ➜ erro amigável.

CA: Política de privacidade acessível antes do login.

 

US2 – Registrar por conversa

Como usuário, quero dizer “Ganhei R$ 250 de comissão” e o app captar valor e categoria.

 

CA: NLP extrai valor=250, moeda=BRL, categoria=Comissões, data=hoje, descrição do texto; pede confirmação.

CA: Em ambiguidade ➜ pergunta 1 follow-up no máx. 2.

CA: Após confirmar, aparece no histórico e soma mensal atualiza.

 

US3 – OCR de foto

Como usuário, quero anexar uma foto de recibo e o app reconhecer os valores.

 

CA: Suporta JPEG/PNG; tira foto ou escolhe da galeria; detecta valores e datas; sugere categoria.

CA: Tela de revisão com campos editáveis; múltiplos valores ➜ permitir selecionar qual registrar (ou todos com tags).

 

US4 – Edição rápida

Como usuário, quero corrigir valor/categoria/data antes de salvar.

 

CA: Inputs com máscara BRL, seletor de categoria com emojis, datepicker.

 

US5 – Dashboard mensal

Como usuário, quero ver quanto ganhei no mês, por categoria.

 

CA: Cartão “Total do mês” (R$), gráfico pizza por categoria, lista dos últimos lançamentos.

 

US6 – Relatório PDF/CSV

Como usuário, quero exportar um relatório do mês com meus ganhos.

 

CA: Filtro mês/ano/categoria; gera PDF com sumário, tabela e gráficos; exporta e compartilha (ShareSheet).

 

US7 – Acessibilidade

Como usuário com necessidades de acessibilidade, quero que o app funcione bem com leitor de tela.

 

CA: Todos elementos têm contentDescription; navegação por foco; contraste AA; fontes 16sp+.

### Entregando o Desafio na DIO

Finalize seu projeto criando um **repositório no GitHub** (pode ser um **fork** deste).  
No README do seu repositório, inclua:

- Seu **prompt final** (PRD); (acima)
- Prints ou pequenos vídeos das interações com a IA; 

- Um resumo do que o seu **App de Finanças Pessoais** faz; 
Reúne todos os ganhos eventuais e ou fixos das pessoas que não têm apenas uma fonte de renda.


- Uma breve **reflexão sobre o processo**:
  - O que funcionou bem?  consegui usar bem os três apps, porém com limitações das licenças pagas.
  - O que não funcionou como o esperado? 
necessidade de pagar pela licença
  - O que aprendeu sobre conversar com IAs?
se bem orientadas fazem o que pedimos certinho. Continuarei editando o meu app até ficar 100%.

> [!TIP]
> Publique seu repositório e compartilhe o link na plataforma da DIO! Sua entrega é a prova de que você domina o raciocínio de Vibe Coding, mesmo sem escrever uma única linha de código.

link https://lovable.dev/projects/7eed0c0e-ca2c-445a-8a77-3f7a5600666c?utm_source=lovable-badge

## 💬 Conclusão

Vibe Coding é sobre clareza, curiosidade e criatividade, não sobre perfeição técnica. O verdadeiro objetivo aqui é aprender a pensar junto com a IA, transformando ideias em conceitos reais e enxergando a tecnologia como uma extensão do seu raciocínio criativo. Cada interação é um experimento, quanto mais clara for sua intenção, mais surpreendente será o resultado.
