---
title: "Need help multi booting"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by jrdnoland on 2009-09-12
Not sure if this is the right place or really how to use this forum, so please forgive my ignorance.

I have a pc on which I installed windows xp pro, windows vista 32 bit, windows 7 32 bit, and ubuntu 9.04

I used easy bcd in vista to try to get all the systems for boot. All the windows systems boot fine, but can't get the ubuntu to boot. I've tried every option as far as installing on various partitions and such. The documentation and help I've been able to find are always lacking a step or two and are not helpful for someone who needs step by step instructions (most help assumes too much).

Have also tried supergrub and tried to modify neogrub menu from easy bcd; that seems to be the closest fit. If I knew how to modify the neogrub menu to boot into Ubuntu I would be satisfied with that.

My Ubuntu is on (hd1,4) and I can get it to boot with supergrub with this:

/boot/grub/menu.lst   #that brings up the ubuntu menu from which I can load it.

Don't know if I've provided enough or not enough info to help sort out this issue.

Thanks!

---

### Post by oldfred on 2009-09-12
I am not familiar with neogrub but it seems you should just copy your Ubuntu entry from /boot/grub/menu.lst in ubuntu to the menu.lst in neogrub on your c: drive(usually C:\NST\).
Of course everytime ubuntu updates the kernel you will have to update the menu.lst entry in neogrub. 
[http://neosmart.net/wiki/display/EBCD/NeoGrub](http://neosmart.net/wiki/display/EBCD/NeoGrub)

The other choice is to chainboot, see Herman's site. You just add a link in neogrub to a grub in the ubuntu partition (not MBR) and use the ubuntu menu.lst as a second boot menu. I am not sure if the chainboot entry for neogrub is the same as a standard grub chainboot entry?
[http://members.iinet.net.au/~herman546/p15.html](http://members.iinet.net.au/~herman546/p15.html)

---

### Post by jrdnoland on 2009-09-12
Thanks fro replying OldFred! 

> **oldfred said:**
> I am not familiar with neogrub but it seems you should just copy your Ubuntu entry from /boot/grub/menu.lst in ubuntu to the menu.lst in neogrub on your c: drive(usually C:\NST\).
Of course everytime ubuntu updates the kernel you will have to update the menu.lst entry in neogrub. 
[http://neosmart.net/wiki/display/EBCD/NeoGrub](http://neosmart.net/wiki/display/EBCD/NeoGrub)

[COLOR=Red]I tried this and it boots me to the grub> prompt not into Ubuntu. 
Can I start Ubuntu from this prompt?

Again, I know little about Ubuntu just beginning to try it out.[/COLOR]

The other choice is to chainboot, see Herman's site. You just add a link in neogrub to a grub in the ubuntu partition (not MBR) and use the ubuntu menu.lst as a second boot menu. I am not sure if the chainboot entry for neogrub is the same as a standard grub chainboot entry?
[http://members.iinet.net.au/~herman546/p15.html]("http://members.iinet.net.au/%7Eherman546/p15.html")

[COLOR=Red]Sorry - I don't understand what to do with this, will read it more but I really need step by step instructions.


[/COLOR]

---

### Post by jrdnoland on 2009-09-12
Still no luck - is this problem too difficult?

---

### Post by talsemgeest on 2009-09-12
> **jrdnoland said:**
> Still no luck - is this problem too difficult?
The vista bootloader is not designed to load the grub, and no matter what I have tried I haven't been able to do it. Your best bet is to reinstall the bootloader to the mbr (take a look at my tutorial [here](http://talsemgeest.doesntexist.com/2009/09/10/bootloader-how-to/)) then add the different windows OSs to the grub. That way you will have one OS selection menu with all the OSs in it.

---

### Post by whitethorn on 2009-09-12
> **talsemgeest said:**
> The vista bootloader is not designed to load the grub, and no matter what I have tried I haven't been able to do it. Your best bet is to reinstall the bootloader to the mbr (take a look at my tutorial [here](http://talsemgeest.doesntexist.com/2009/09/10/bootloader-how-to/)) then add the different windows OSs to the grub. That way you will have one OS selection menu with all the OSs in it.

I'm pretty sure that only works if each windows installation is on a seperate partition, I remember reading somewhere that grub can only point to windows partitions not really tell two different windows installs apart.

---

### Post by talsemgeest on 2009-09-12
> **whitethorn said:**
> I'm pretty sure that only works if each windows installation is on a seperate partition, I remember reading somewhere that grub can only point to windows partitions not really tell two different windows installs apart.
Of course it can only point to a windows partition. You can only install one instance of windows per partition anyway (that is, you can't install 2 versions of windows on the same partition.)

---

### Post by jrdnoland on 2009-09-12
Thanks to all who attempted to help. 

I was using EasyBCD which is supposed to be able to boot windows and Linux, I just couldn't get it to work. That is what I was trying to explain.

I ended up using system commander which was able to load Grub and the 
Windows Bootloader (which was now EasyBCD). So I have to go through two menu systems, but at least I have all four operating systems booting.

---

### Post by talsemgeest on 2009-09-13
> **jrdnoland said:**
> Thanks to all who attempted to help. 

I was using EasyBCD which is supposed to be able to boot windows and Linux, I just couldn't get it to work. That is what I was trying to explain.

I ended up using system commander which was able to load Grub and the 
Windows Bootloader (which was now EasyBCD). So I have to go through two menu systems, but at least I have all four operating systems booting.
As long as it works for you :)

However, if you ever get tired of going through 2 boot menus, feel free to follow my advice.

---

