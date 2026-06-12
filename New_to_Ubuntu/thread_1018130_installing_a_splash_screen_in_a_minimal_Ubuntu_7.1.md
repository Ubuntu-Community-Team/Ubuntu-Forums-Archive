---
title: "installing a splash screen in a minimal Ubuntu 7.10 install"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by rockerphil on 2008-12-21
ok, here's how it goes. since my machine has pretty limited resources by any standards (500 MHz Intel Celeron processor and 128 MB of pc133 SD RAM) i used this walk through to build a minimal Ubuntu 7.10 OS

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

it wasn't this exact walk through, this one has been updated since. well, i'm now putting the refining touches on the OS, and currently when i boot my computer i simply get system messages and not a splash screen as you would with a standard Ubuntu/Xubuntu/Kubuntu install, so i'd like to somehow put a splash screen there. if anyone can help me out with either some instructions on how to do this or at least with a pretty straight forward walk through it would be greatly appreciated.

PS, im using Fluxbox as my WM as i'm sure it makes a difference seeing as my machine can't run Gnome or even XFCE as effeciantly as i'd like. much thanks in advance,

Phil

---

### Post by rockerphil on 2008-12-23
can anyone at all help me with this or am i just stuck with the CLI boot?

---

### Post by LowSky on 2008-12-23
With your amount of ram, I would keep it as simple as possible and stay with the CLI style boot. I know it aint pretty but it works.

if you want to try

```
gksudo gedit /boot/grub/menu.lst
```

look for the kernel that your using
you may need to enter theses to your kernel line
```
splash quiet 
```

example: PLEASE DONT USE IT NOT YOUR KERNEL AND WILL RUIN YOUR BOOT
```


title Ubuntu, kernel 2.6.20-15-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=fccafcc7-d7cc-4594-9459-a8f0db7b9f7f ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
```

---

### Post by Duck2006 on 2008-12-23
From your Synaptic Package Manager install startup-manager you can do it there.

---

### Post by rockerphil on 2008-12-23
Synaptic is a bit too heavy for my resources, it takes at least 5 minutes to complete a search, so i do all of my package management via the command line, and this is what i got when i tried to install "startup-manager" in the command line:

```
phil@Phillip:~$ sudo apt-get install startup-manager
[sudo] password for phil:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package startup-manager
```

PS, i don't even have so much a Usplash installed which of course is the default application Ubuntu uses for managing splash screens

---

