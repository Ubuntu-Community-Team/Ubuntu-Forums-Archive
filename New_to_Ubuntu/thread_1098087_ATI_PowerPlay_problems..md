---
title: "ATI PowerPlay problems."
date: 2009-03-16
forum: New to Ubuntu
---

### Post by Marbash on 2009-03-16
I've got some problems with my computer getting overheated while running Ubuntu, and last time I had Ubuntu installed, I found a solution to this problem by "down-clocking" my ATI card, so it wouldn't be in "Performance mode" when I didn't need too. I've tried to type in the same command now, but it won't work. Anyone able to help? :(

Here's my terminal window:
raymond@raymond-laptop:~$ aticonfig--set-powerstate=1
bash: aticonfig--set-powerstate=1: command not found
raymond@raymond-laptop:~$ aticonfig --lsp
    core/mem      [flags]
-----------------
  1: 128/144 MHz  [low voltage]
  2: 392/252 MHz
* 3: 473/369 MHz  [default state]
raymond@raymond-laptop:~$ aticonfig --set-powerstate=1
No layout section was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' first or modify your configurationfile manually and run aticonfig again.
aticonfig: parsing the command-line failed.
raymond@raymond-laptop:~$

---

