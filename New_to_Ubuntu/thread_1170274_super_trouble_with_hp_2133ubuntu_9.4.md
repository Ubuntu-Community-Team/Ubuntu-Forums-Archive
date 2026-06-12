---
title: "super trouble with hp 2133/ubuntu 9.4"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by pertoniddi on 2009-05-26
Hello! Please help me! 
I have a hp 2133 (KX869AT). I am a linux beginner. 
One month ago I changed the BIOS in F.04, then I installed ubuntu 8.10. 
It was working perfectly. 
Now, yesterday I automatically upgraded it to the version 9.04.
I restarted it, but after the ubuntu's bar the screen became total black and I am not able to log in.
In my ignorance before upgrading it I did not check if it was compatible with my model (very stupid, I know, and I know not to know).
 
So. What to do? 
a) I want to save my info (more stupid: I didn't do the backup in the past 2 weeks)
b) shall I reinstall the previous version? If yes, how without losing my datas? If yes, I won't have to change again the BIOS? 
c) Is there any way to keep the 9.04 version in a easy way? 
d) Could you explain or link me somewhere to follow step by step the instructions? 
 
Please help help me!!! 
Sorry for my ignorance!!!
Thanks...
Monica

---

### Post by s.fox on 2009-05-26
Hi and welcome to the forum, 
 
Have you tried safe mode? 
 
 
First you need to enter Grub menu by pushing ESC when your PC boots. There you can select the safe mode. 
 
If that doesn't work I am pretty sure you could try to recover your data by **booting** into the [LiveCD]("https://help.ubuntu.com/community/LiveCD").

Hope this helps.

-Ash R

---

### Post by LubindaMaim on 2009-05-26
Does your laptop have an ATI graphics card? It may be the fact the the proprietary drivers from amd stopped supporting a lot of cards with their release of catalyst 9.4 which unfortunately is the only one ubuntu 9.04 supports.

---

### Post by pertoniddi on 2009-05-26
Hi! thanks everybody..
 
I pressed esc and I saw this list:
 
ubuntu 9.04, kernel 2.6.28-11-generic
ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
ubuntu 9.04, kernel 2.6.27-11-generic 
ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
ubuntu 9.04, kernel 2.6.28-7-generic 
ubuntu 9.04, kernel 2.6.28-7-generic (recovery mode)
 
Then, my laptop is a netbook (hp mini 2133), doesn't have the cd reader. Itryed to boot with ubuntu 8.10 (is in a pendrive) but it did not worked.
 
Then I don't know if I have an ati card. How can I discover? Maybe later at home I'll look on the computer box and let you know.
 
But... even if I'd be able to boot in a safe mode, after saved all my files, what to do to go back to normality?
 
Thanks thanks thanks
 
Monica

---

### Post by pertoniddi on 2009-05-26
ok. I just saw that I can convert the cd in a thumbdrive. I'll try to download it with my super slow connection....

---

### Post by kasimyro on 2009-05-26
i have a similar problem upgrading from 8.10 to 9.04 with FU351EA...
My screen is 1280x768 anche same problem.
So:
[LIST=1]
[*]Start in safe mode and drop to shell
[*]Make a copy of your xorg.conf file in /etc/X11, same it elsewhere in case you need it
[*]run: "sudo dpkg-reconfigure -phigh xserver-xorg"
[*]Now type "sudo reboot" and let computer start in normal mode
[/LIST]
This way should give you GUI mode. 
Sorry for my english, i hope it could help you.

D.

---

### Post by kasimyro on 2009-05-26
> **kasimyro said:**
> i have a similar problem upgrading from 8.10 to 9.04 with FU351EA...
My screen is 1280x768 anche same problem.
So:
[LIST=1]
[*]Start in safe mode and drop to shell
[*]Make a copy of your xorg.conf file in /etc/X11, same it elsewhere in case you need it
[*]run: "sudo dpkg-reconfigure -phigh xserver-xorg"
[*]Now type "sudo reboot" and let computer start in normal mode
[/LIST]
This way should give you GUI mode. 
Sorry for my english, i hope it could help you.

D.

This way will disable 3D acceleration...

---

### Post by pertoniddi on 2009-05-29
Ehi, sono italiana, puoi scrivermi in italiano se vuoi. Come scopro che tipo di risoluzione ho? Sono davvero una principiante... Ora sto scaricando l'immagine [PC (Intel x86) UNR USB image]("http://releases.ubuntu.com/jaunty/ubuntu-9.04-netbook-remix-i386.img") , pensi sia corretta per farlo partire, salvare i dati e poi provare a reinstallare con tutte le varianti del caso (che tu mi hai scritto?)
Beata ignoranza, la mia
Grazie!!

---

### Post by kasimyro on 2009-05-29
Il KX869AT dovrebbe essere WXGA quindi 1280x768. Io ho installato la 8.10 con i driver OpenChrome di VIA ed è un po' complesso.
Hai provato con il consiglio di prima?

( dpkg-reconfigure -phigh xserver-xorg )

Ho provato la UNR ma è drammaticamente lenta perchè non supportando nativamente i driver acceleratori utilizza la CPU per il rendering video e rallenta tantissimo.

---

