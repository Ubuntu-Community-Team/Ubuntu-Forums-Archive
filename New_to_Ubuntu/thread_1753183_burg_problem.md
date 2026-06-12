---
title: "burg problem"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by Dr. div11 on 2011-05-08
hi... i need to know how to install burg on ubuntu 10.10

---

### Post by wilee-nilee on 2011-05-08
> **Dr. div11 said:**
> hi... i need to know how to install burg on ubuntu 10.10

It says Maverick in your info, here is a a ppa to add.
[https://launchpad.net/~bean123ch/+archive/burg](https://launchpad.net/~bean123ch/+archive/burg)

Here is a OMG Ubuntu link as well.
[http://www.omgubuntu.co.uk/2011/05/beautiful-burg-boot-loader-gets-ubuntu-11-04-ppa/](http://www.omgubuntu.co.uk/2011/05/beautiful-burg-boot-loader-gets-ubuntu-11-04-ppa/)

Burg installs basically like grub2, it needs to be loaded to the OS and the mbr as well, ask any questions needed.

---

### Post by Dondermans on 2011-05-08
[https://help.ubuntu.com/community/Burg](https://help.ubuntu.com/community/Burg)

---

### Post by Dr. div11 on 2011-05-08
> **wilee-nilee said:**
> It says Maverick in your info, here is a a ppa to add.
[https://launchpad.net/~bean123ch/+archive/burg](https://launchpad.net/~bean123ch/+archive/burg)

Here is a OMG Ubuntu link as well.
[http://www.omgubuntu.co.uk/2011/05/beautiful-burg-boot-loader-gets-ubuntu-11-04-ppa/](http://www.omgubuntu.co.uk/2011/05/beautiful-burg-boot-loader-gets-ubuntu-11-04-ppa/)

Burg installs basically like grub2, it needs to be loaded to the OS and the mbr as well, ask any questions needed.



i installed burg and now... when i rebooted .. 

i got this msg 

                         BURG version 1.98+20100623-1+maverick 
minimal BASH-like line editing is supported . For the first word ,TAB lists possible command completition anywhere else TAb lists possible device or file completitions

grub>




I AM STUCK NOW...HOw do i go to mu ubuntu screen ...which commandds to put in..please help..

---

### Post by wilee-nilee on 2011-05-08
> **Dr. div11 said:**
> i installed burg and now... when i rebooted .. 

i got this msg 

                         BURG version 1.98+20100623-1+maverick 
minimal BASH-like line editing is supported . For the first word ,TAB lists possible command completition anywhere else TAb lists possible device or file completitions

grub>

I AM STUCK NOW...HOw do i go to mu ubuntu screen ...which commandds to put in..please help..

I suspect the update-burg command was not run, speculating here though.

You still have grub and it will get you in, so boot the live cd of the install, and follow this link on getting grub back into the mbr, just to get into the desktop and a terminal.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

There is a manual boot in from that prompt as well if you're game, instead of the grub reload to get in.
[https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot](https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot)

What I'm trying to do is to get you to the installs desk top to a terminal. If all the burg is installed then these two commands should put it back in the mbr and update it.
```
sudo burg-install /dev/sda
```
then
```
sudo update-burg
```

I'm presuming that the hd is sda, so if it is sdb, or another act accordingly.

When you loaded burg originally you would have loaded the ppa, then in the terminal after updating run.
```
sudo apt-get install burg-pc burg-common
```
then
```
sudo update-burg
```
Does this ring a bell?

---

