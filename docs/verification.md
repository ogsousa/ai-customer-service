# Estado e critérios de validação

Data da inspeção local: 08/10/2026.

## O que foi verificado

| Export observado | Nodes | Grupos de conexões | Referências de credencial por node/tipo |
| --- | ---: | ---: | ---: |
| Atendimento WhatsApp | 151 | 121 | 65 |
| Atendimento Instagram DM | 133 | 101 | 50 |
| Calendar Instagram | 9 | 8 | 7 |
| Handoff comercial compartilhado | 27 | 19 | 0 |

Todos os quatro JSONs foram interpretados e todas as conexões verificadas apontavam para nomes de nodes existentes. A contagem de credenciais indica referências de configuração; não comprova validade, acesso ou vínculo com o ambiente atual.

Os exports principais de atendimento registram `active: false`. Esse campo descreve o arquivo local, sem demonstrar o estado de uma instância n8n.

## Limites conhecidos

- **Segurança da publicação:** exports privados contêm material de autenticação e configuração operacional. Por isso, este repositório contém documentação autoral; nenhum desses arquivos foi incluído.
- **Instagram:** o mapeamento lê apenas o primeiro evento do envelope. Assinatura do POST, configuração segura do canal e separação entre echo do bot e mensagem humana ainda precisam de validação operacional.
- **WhatsApp:** há dependências de compatibilidade legada, deduplicação de activities por consulta e cobertura incompleta de falha do envio. Concorrência não foi testada.
- **Calendar:** há ambiguidade de versões do subworkflow e ausência de espelho confirmado em `meetings`.
- **Handoff:** o módulo compartilhado foi inspecionado, mas sua ligação com o destino chamado pelo atendimento não foi confirmada.
- **RAG/SDR:** existem referências de tool, sem os subexports correspondentes no acervo inspecionado.
- **Backend:** tabelas, RPCs, constraints e políticas atuais não foram consultadas nesta auditoria.

## Antes de afirmar uma operação completa

1. Reconciliar cada chamada com a versão real do subworkflow, incluindo contratos de entrada e saída.
2. Remover material sensível dos artefatos de distribuição e manter autenticação fora dos exports.
3. Validar identidade e replay sob concorrência, preservando isolamento de conta.
4. Testar texto, mídia, status, eventos em lote, pausa, handoff e falhas de transporte com uma integração controlada.
5. Confirmar no provedor cada ação de agenda e envio antes de registrar sucesso.
6. Verificar logging, repetição segura e procedimento de retorno à versão anterior.

Nenhuma importação, execução de workflow, mensagem, chamada ao banco ou alteração de produção foi realizada para este estudo. Os exemplos de conteúdo do repositório associado têm validação offline, com entradas sintéticas; isso não substitui os critérios acima.
