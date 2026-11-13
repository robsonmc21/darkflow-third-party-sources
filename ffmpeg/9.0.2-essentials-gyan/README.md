# FFmpeg 9.0.2 essentials (gyan.dev): fonte correspondente / Corresponding Source

O DarkFlow Studio inclui, como programa separado executado em processo próprio, o `ffmpeg.exe` da compilação
**FFmpeg 9.0.2 essentials** de [www.gyan.dev](https://www.gyan.dev/ffmpeg/builds/). Ele é licenciado sob a **GNU GPL versão 3**.
O binário não foi alterado nem recompilado:

| | |
|---|---|
| `ffmpeg.exe` | SHA-256 `3256173f3f8bffd7df12227c68adf68025edb1832273a9530688a7bb1ed8edec` |
| zip original | `ffmpeg-9.0.2-essentials_build.zip`, SHA-256 `60f467265b1e312373dbcd92200c2618a74850f98d3d078e94296bb3fa2047ba` |

## Download (Release `ffmpeg-9.0.2-essentials-r2`)

| Arquivo | Conteúdo |
|---|---|
| `darkflow-ffmpeg-9.0.2-essentials-fontes-correspondentes-r2.tar.xz` | o pacote de fontes completo (866 882 368 bytes) |
| `….tar.xz.sha256` | SHA-256 do pacote: `e96efcdc287dac6dc584439c206dffcafa89808b2b2d447ca188a7511d4cc433` |
| `….SHA256SUMS-PACOTE` | SHA-256 de cada um dos 314 arquivos dentro do pacote |
| `….json` | metadados do pacote (binário, número de fontes, ressalvas) |
| `ffmpeg-9.0.2-essentials_build-manifest.txt` | o manifesto de dependências e toolchain enviado pelo mantenedor (gyan.dev) em 13/11/2026 |

Conferir: `sha256sum -c darkflow-ffmpeg-9.0.2-essentials-fontes-correspondentes-r2.tar.xz.sha256`. Para extrair:
`tar -xJf …tar.xz` (Linux, macOS, Git Bash) ou 7-Zip no Windows. Depois de extrair, `sha256sum -c SHA256SUMS-PACOTE` dentro da pasta.

## O que o pacote contém

- **84 fontes** na revisão exata do manifesto do mantenedor:
  - `git archive` do commit exato de cada repositório;
  - tarballs oficiais;
  - 35 pacotes-fonte oficiais do **MSYS2** (`.src.tar.zst`, com PKGBUILD, patches e fonte original), cada um com a assinatura `.sig`
    original. As 35 assinaturas foram conferidas como válidas com o chaveiro em `_chaves-msys2/` (msys2/MSYS2-keyring @ `5d249077`).
- **toolchain** do manifesto: GCC 16.2.0-3 e mingw-w64 crt, headers e winpthreads, cujas bibliotecas de runtime estão ligadas
  ao binário.
- `_MANTENEDOR/`: o manifesto do mantenedor.
- `_FFMPEG-BINARIO/`: LICENSE, README e VERSION do zip original e `BUILDCONF.txt` (a configuração de build do binário).
- `_AVISOS/`: a lista de componentes e os textos das licenças de cada um.
- `_AUDITORIA/`:
  - `DIVERGENCIAS.txt`: diferenças entre o manifesto e o binário;
  - `MATERIAIS-COMPILACAO.tsv`: sistema de build de cada fonte;
  - provas usadas.
- `INSTRUCOES-REPRODUCAO.txt`, `LEIA-ME.txt`, `MANIFEST.json`, `SHA256SUMS` (as 84 fontes) e `SHA256SUMS-PACOTE` (todos os arquivos).

Os mesmos textos de auditoria e de instruções estão nesta pasta do repositório, para leitura sem baixar o pacote.

## Ressalvas (registradas, não resolvidas por este repositório)

Este pacote **não é uma declaração de conformidade com a GPL** nem de revisão jurídica concluída. As ressalvas conhecidas são:

1. **Materiais de compilação:**
   - O mantenedor não publica o próprio script de build nem as opções de configuração de cada biblioteca que compila a partir do git.
   - Ele declara que não há patches funcionais e que as instruções padrão de cada repositório bastam.
   - Com este pacote, a recompilação é **funcionalmente equivalente, não idêntica byte a byte**.
2. **Procedência** (ver `DIVERGENCIAS.txt`):
   - **OpenSSL:** 3.6.4-1 do MSYS2, **confirmado**. A data de build gravada no binário é idêntica à do pacote. Ela não consta do manifesto: é dependência do libssh.
   - **pixman 0.46.4:** pacote MSYS2 -2 ou -3, **parcial**. A -1 está excluída pela marca do compilador.
   - **libsodium 1.0.22:** pacote MSYS2 -1, -2 ou -3, **parcial**.
   - Nos dois casos parciais, todas as revisões têm a mesma fonte original e nenhum patch, e todas estão no pacote.
   - **libunibreak:** o manifesto declara 7.0-1, mas o binário contém a **5.1**. A fonte 5.1 incluída tem o mesmo SHA-256 da receita
     5.1-1 do MSYS2. A origem da biblioteca intermediária 5.1 não foi identificada. A 7.0-1 também está incluída.

Nenhuma dessas ressalvas deixa código ligado ao `ffmpeg.exe` sem a respectiva fonte no pacote. Elas tratam de procedência e de
reprodutibilidade exata.

---

**English.** DarkFlow Studio ships the unmodified `ffmpeg.exe` above (FFmpeg 9.0.2 essentials by www.gyan.dev, GNU GPL v3) as a
separate program. The Release `ffmpeg-9.0.2-essentials-r2` contains its Corresponding Source:
- 84 sources at the exact revisions of the maintainer's manifest;
- the official MSYS2 source packages with their verified signatures;
- the toolchain sources;
- the manifest, the build configuration, the license texts and reproduction instructions.

It is free of charge, with no login, license or payment. Caveats:
- the maintainer does not publish per-library configure options, so rebuilding is functionally equivalent, not bit-identical;
- the exact MSYS2 package revision of pixman and libsodium is ambiguous, but every candidate has the same source and is included;
- libunibreak 5.1 is linked although the manifest lists 7.0-1. Both are included.

This is not a statement of completed GPL compliance.
