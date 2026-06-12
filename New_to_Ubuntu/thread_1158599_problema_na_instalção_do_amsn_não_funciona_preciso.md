---
title: "problema na instalção do amsn não funciona preciso de ajuda"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by vitoruk on 2009-05-13
[B]Ola Pessoal é a primeira vez que participo de um forum sou totalmente novo e cru no Ubuntu venho tentando aprender mas to apanhando muito , Bom vou relatar o meu problema e ver se voces conseguem me ajudar . 

Acabei de tentar instalar o amsn na minha maquina sem sucesso apareceu o seguinte erro  [/B]** abaixo **[B]vejam . 

usuario@usuario-desktop:~$ sudo apt-get install amsn
[sudo] password for usuario: 
Lendo lista de pacotes... Pronto
Construindo árvore de dependências       
Lendo estado da informação... Pronto
Pacotes sugeridos:
  docker
Os pacotes a seguir serão REMOVIDOS:
  linux-restricted-modules-2.6.27-7-generic
Os NOVOS pacotes a seguir serão instalados:
  amsn
0 pacotes atualizados, 1 pacotes novos instalados, 1 a serem removidos e 1 não atualizados.
1 pacotes não totalmente instalados ou removidos.
É preciso fazer o download de 0B/271kB de arquivos.
Após esta operação, 1335kB de espaço em disco serão liberados.
Quer continuar [S/n]? S
(Lendo banco de dados ... 179580 arquivos e diretórios atualmente instalados.)
Removendo linux-restricted-modules-2.6.27-7-generic ...
rmdir: falha ao remover `/lib/modules/2.6.27-7-generic/volatile/': Arquivo ou diretório inexistente
FATAL: Could not open '/boot/System.map-2.6.27-7-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.27-7-generic
Cannot find /lib/modules/2.6.27-7-generic
update-initramfs: failed for /boot/initrd.img-2.6.27-7-generic
dpkg: erro processando linux-restricted-modules-2.6.27-7-generic (--remove):
 subprocesso post-removal script retornou código de saída de error 1
Erros foram encontrados durante processamento de:
 linux-restricted-modules-2.6.27-7-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
usuario@usuario-desktop:~$ 


Qualquer instalação de qualquer programa que tento fazer sempre aparece com o mesmo erro e a instação trava não sendo completada .
quando tentei instar o wine também aconteceu o mesmo erro . 
e agora quando tento atualizar o sistema sempre da erro no 
[/B][B]linux-restricted-modules-2.6.27-7-generic

[/B][B]Agradeceria e muito a ajuda de voces para resolver esse problema. 

Agradecido[/B]
vitor ):P

---

### Post by quixote on 2009-05-14
vitor: I'm guessing at what the Portuguese means, and I'm hoping you're better at English! :-D

If I understand it right, you're installing a chat client, and when it asks you whether to remove unused packages, you answer "Yes".  Then it complains because it wants to remove the old linux kernel, but is having some sort of problem.

You could try running ```
sudo dpkg --configure -a
```  That should clean up old bits and pieces that confuse the system.  

However, the fact that it can't find the old stuff it wants to clean out shouldn't be bothering the new packages you're installing.  If they're not installing at all because of it, then there's a bigger problem.  :-(

I'd be willing to bet there's a Portuguese ubuntu IRC channel where you could get better help.  If anyone here knows the direct link, maybe they can chime in?

---

### Post by lovinglinux on 2009-05-14
[[color=#CC0000]PT[/color]] Vitor, eu falo Português mas não é permitido postar mensagens em outros idiomas. Este é um fórum de língua inglesa. Se possui dificuldades com este idioma, sugiro que registre-se no site Ubuntu Brasil em [http://forum.ubuntu-br.org](http://forum.ubuntu-br.org)

[[color=#33CC00]EN[/color]] Vitor, I speak Portuguese but we are not allowed to use other languages here. This is strictly an English speaking forum. If you have issues with English you should consider registering on the Ubuntu Brasil forum at [http://forum.ubuntu-br.org](http://forum.ubuntu-br.org)

---

