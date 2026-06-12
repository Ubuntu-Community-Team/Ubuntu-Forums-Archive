---
title: "Change boot preferences, Windows over Kubuntu"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by Cathol on 2010-09-23
Hey, We're working with Kubuntu at college so i thought it'd be a good idea to get it running at home too, to get a better feel and that. liking it so far but my problem is that it's the default OS now, and since my dad can just about use Firefox without my help i was wondering would anyone know how to make Windows 7 the default OS.

I tried 
```
sudo gedit /boot/grub/menu.lst
```From
[http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/)

but got 
```
sudo: gedit: command not found

```Anyone have any ideas?
I'm completely new to Kubuntu so if there's another command like the one above could you please give me a short idea of what it means please.

Thanks.

---

### Post by Rubi1200 on 2010-09-23
Which version of Kubuntu are you using and how was it installed?

---

### Post by Elfy on 2010-09-23
gedit is the gnome text editor you need to use kate, also as you are using a gui app use kdesudo rather than sudo.

It is also possible if you have a newer install that opening menu'lst will get you a blank file if you have grub2 rather than grub legacy

This might help [http://ubuntuforums.org/showthread.php?t=1309890](http://ubuntuforums.org/showthread.php?t=1309890)

and  [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by sanderd17 on 2010-09-23
> **Cathol said:**
> Hey, We're working with Kubuntu at college so i thought it'd be a good idea to get it running at home too, to get a better feel and that. liking it so far but my problem is that it's the default OS now, and since my dad can just about use Firefox without my help i was wondering would anyone know how to make Windows 7 the default OS.

I tried 
```
sudo gedit /boot/grub/menu.lst
```From
[http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/)

but got 
```
sudo: gedit: command not found

```Anyone have any ideas?
I'm completely new to Kubuntu so if there's another command like the one above could you please give me a short idea of what it means please.

Thanks.

One tip: if you use ubuntu, a lot of programs wil start with the G of Gnome, for kubuntu, most programs wil start with a K. So if you see some command with a program that starts with G, be prepared to search an alternative or install the program.

BTW, if Ubuntu complains about a program that isn't installed, you can most of the time install it with 
```

sudo apt-get install XXX

```
with XXX the name of the program. If that doesn't work, try searching it in synaptic.

---

### Post by sanderd17 on 2010-09-23
If you want to learn about the command line, I have a good, short, general tuturial. It explains the basic working of the command line and the linux file system. Once you're used to the CLI (command line interface) you just need to know what tool you can use for what.

[http://gd.tuwien.ac.at/linuxcommand.org/]("http://gd.tuwien.ac.at/linuxcommand.org/")

---

### Post by andrewthomas on 2010-09-23
> **Cathol said:**
> 
```
sudo gedit /boot/grub/menu.lst
```
```
kdesu kwrite /boot/grub/menu.lst
```

---

