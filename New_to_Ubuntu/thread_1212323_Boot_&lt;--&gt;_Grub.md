---
title: "Boot &lt;--&gt; Grub"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by James Dee on 2009-07-13
Hello everybody,

I have three systems on my computer.
1st installed --> WinXP
2nd installed --> Intrepid Ibex
3rd installed --> Hardy Heron

At the moment while booting the grub from 3rd system is on.
How to setup that grub from 2nd system is on during booting?

I'm just curious and like to learn something new.

Ade
James Dee

:guitar:

---

### Post by zika on 2009-07-13
> **James Dee said:**
> Hello everybody,

I have three systems on my computer.
1st installed --> WinXP
2nd installed --> Intrepid Ibex
3rd installed --> Hardy Heron

At the moment while booting the grub from 3rd system is on.
How to setup that grub from 2nd system is on during booting?

I'm just curious and like to learn something new.

Ade
James Dee

:guitar:It depends if You are using grub or grub2 ... I'll assume You are using grub (the "old" one) ... In that case in file **/boot/grub/menu.lst **change the line "*default 0*" to "*default x*" where x+1 is the order of OS in the grub list (the order You see at boot i.e. the order in which they are listed in aforementioned file) You want to use. 
**Be careful** since if You mess up that file You could be left out of Your computer for a while before You master using LiveCd to regain control ...
To edit that file You could use ```
sudo nano /boot/grub/menu.lst
``` I'm a bit rusty on using grub so take this *with a grain of salt* ... :)

---

### Post by James Dee on 2009-07-13
> **zika said:**
> In that case in file **/boot/grub/menu.lst **change the line "*default 0*" to "*default x*" where x+1 is the order of OS in the grub list (the order You see at boot i.e. the order in which they are listed in aforementioned file) You want to use.

Thnx zika...

How to remove 3rd system, that grub from 2nd system is called during booting? I think that this will not happened automatically.

---

### Post by zika on 2009-07-13
> **James Dee said:**
> Thnx zika...

How to remove 3rd system, that grub from 2nd system is called during booting? I think that this will not happened automatically.This question I did not understand fully ...
(Nisam baš razumeo pitanje ... :))

---

### Post by bodhi.zazen on 2009-07-13
I am not sure what you are asking either, but this thread has some suggestions :

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")

---

### Post by James Dee on 2009-07-13
> **zika said:**
> This question I did not understand fully ...
(Nisam baš razumeo pitanje ... :))

How to remove 3rd system properly?
At the moment menu.lst from 3rd system is called during booting. If I want to remove 3rd system (menu.lst will not exist anymore) I need to change that menu.lst from 2nd system is called. How to do that?

---

### Post by zika on 2009-07-13
> **James Dee said:**
> How to remove 3rd system properly?
At the moment menu.lst from 3rd system is called during booting. If I want to remove 3rd system (menu.lst will not exist anymore) I need to change that menu.lst from 2nd system is called. How to do that?I've never done something like that, so I'll pass on answer even though I have several solid ideas ... but I do not like to speak about something I've only read about. ... Sorry.

---

### Post by LewRockwell on 2009-07-13
Super Grub Disk should correct any grub difficulties you have after deleting your 3rd system([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/))

If you are going to change/alter/edit the grub file "menu.lst" then you should make a back-up copy first```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
```Then you can open an editing session with```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by bodhi.zazen on 2009-07-13
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Boot Ubuntu.

Fire up grub :

```
sudo grub
```

At the grub prompt :

```
grub> root (hd0,x)
setup (hd0)
```

You need to know which partition is the second OS.

See : [HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018")

---

### Post by James Dee on 2009-07-15
> **bodhi.zazen said:**
> 

Fire up grub :

```
sudo grub
```

At the grub prompt :

```
grub> root (hd0,x)
setup (hd0)
```

You need to know which partition is the second OS.


This is helpful hint. :popcorn:
Thnx...

---

