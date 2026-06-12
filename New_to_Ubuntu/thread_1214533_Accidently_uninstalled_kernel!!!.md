---
title: "Accidently uninstalled kernel!!!"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by swarooppatra on 2009-07-16
Hi All,

I am beginner to Ubuntu Linux. My laptop configuration is little low so I installed Ubuntu 5.1. I tried to install VLC & Amarok player with all dependencies through "Add Software" application. During installation it asked for replacing linux kernel. I thought it will replace with a new version so i supplied "YES". The installation was successful. But when I restarted my laptop GRUB is unable to load the kernel. I guess the kernel was not replaced with a new now. Now when I restart my laptop Ubuntu memory test starts not the os. Please help me. 

Thanks in advance. :p
Swaroop

---

### Post by DirtDawg on 2009-07-16
> **swarooppatra said:**
> Hi All,

I am beginner to Ubuntu Linux. My laptop configuration is little low so I installed Ubuntu 5.1. I tried to install VLC & Amarok player with all dependencies through "Add Software" application. During installation it asked for replacing linux kernel. I thought it will replace with a new version so i supplied "YES". The installation was successful. But when I restarted my laptop GRUB is unable to load the kernel. I guess the kernel was not replaced with a new now. Now when I restart my laptop Ubuntu memory test starts not the os. Please help me. 

Thanks in advance. :p
Swaroop

Your biggest problem is you installed Ubuntu version 5.10. You should get the newest Ubuntu (Jaunty 9.04) and reinstall from the beginning. If your computer is slow, using an older version does not help. It simply has more bugs and less hardware support than newer releases.

---

### Post by swarooppatra on 2009-07-16
I went through the system requirement for 9.4 and recommended memory is 384MB where as my laptop got 256MB of ram. I can try with the latest version of the Ubuntu. I was looking for some alternative. Thanks for the reply.

---

### Post by shicy on 2009-07-16
you can install other Linux distributions ;)
see linux Mint (i heard that it's excellent, something like "Ubuntu with codecs")...
get LiveCD of any distribution you wish and try it ;)

---

### Post by freak42 on 2009-07-16
you might look into a low-spec linux version for your system, such as [Xubuntu]("http://www.xubuntu.org/").

---

### Post by SteveNorman on 2009-07-16
xubuntu or puppy linux may be a better choice for you system as they require less resources. You should get more memory asap. If you did get another kernal to install you should be able to use supper grub disc or boot from a removable live cd or pendrive distro. If you have an ubuntu live cd you can try and update grub through that, 

Im not sure what the exact steps are, but the command you want eventually is

```
sudo update-grub
```

here is a place to start
```
http://www.supergrubdisk.org/
```

If you dont have data to save you should probably go with a smaller distro though or a fresh install of xbuntu

---

### Post by CJ Master on 2009-07-16
> **freak42 said:**
> you might look into a low-spec linux version for your system, such as [Xubuntu]("http://www.xubuntu.org/").

I really love Ubuntu, but they dropped the ball on Xubuntu. That thing is a freakin ram hog. If you want a lightweight distro based on Ubuntu try [Crunch-bang Linux](http://crunchbanglinux.org/).

Once you get very comfy with Linux and aren't scared of the command line, then [Arch Linux](http://www.archlinux.org/) is about as minimal as you can get without compiling.

Hope I helped!

---

### Post by Elep.Repu on 2009-07-16
I think you should try Debian sir.
[http://www.debian.org/](http://www.debian.org/)

---

### Post by halitech on 2009-07-16
Debian with XFCE4 or LXDE would be better on that machine (depending on cpu speed)

[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

---

### Post by ~sHyLoCk~ on 2009-07-16
[http://www.puppylinux.org/]("http://www.puppylinux.org/")

---

### Post by LewRockwell on 2009-07-16
nine hours and nine posts later and STILL no one has asked for system specs

AND without KNOWING system specs...you ABSOLUTELY CANNOT make an educated recommendation...especially anything even remotely "heavy"...

although I can see recommending a micro-distro as a baseline starting point

sometimes I just send them here([http://www.atarimuseum.com/computers/8BITS/8-Bit-Menu1/8-bit-menu1.html](http://www.atarimuseum.com/computers/8BITS/8-Bit-Menu1/8-bit-menu1.html)) for their software needs...

go figure...

.

---

### Post by SteveNorman on 2009-07-17
> **LewRockwell said:**
> nine hours and nine posts later and STILL no one has asked for system specs

AND without KNOWING system specs...you ABSOLUTELY CANNOT make an educated recommendation...especially anything even remotely "heavy"...

although I can see recommending a micro-distro as a baseline starting point

sometimes I just send them here([http://www.atarimuseum.com/computers/8BITS/8-Bit-Menu1/8-bit-menu1.html](http://www.atarimuseum.com/computers/8BITS/8-Bit-Menu1/8-bit-menu1.html)) for their software needs...

go figure...

.


post number 3

---

### Post by master_kernel on 2009-07-17
I didn't see anyone post this: [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Instructions for installing Ubuntu on low-memory systems.

---

### Post by DirtDawg on 2009-07-17
> **swarooppatra said:**
> I went through the system requirement for 9.4 and recommended memory is 384MB where as my laptop got 256MB of ram. I can try with the latest version of the Ubuntu. I was looking for some alternative. Thanks for the reply.

Actually, I think the 384MB requirement is for the live disk. I also have a laptop with 256MB Ram and it runs ubuntu. It's not fast, but it does run (it has a 2.4Ghz processor). The key is to use the alternative install disk. This will run a text based installer that is intuitive to use.

If you do decide to install  ubuntu, you may want to look into alternate desktops such as Fluxbox that can be installed after ubuntu is installed. I also recommend looking into some of the more lightweight linux distros suggested elsewhere in this thread. 

Good luck.

---

