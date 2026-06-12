---
title: "some dualboot help please?"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by cairnzi on 2009-01-28
hi people, i've tried searching google and had a look here but i was wondering if anybody can give me an idiots guide to dualdoot,with ubuntu installed first as i want to reinstall xp pro in a 25GB partition to play dawn of war?

Many Thanks.

---

### Post by Jose Catre-Vandis on 2009-01-28
A couple of useful resources for you:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by BurnChao on 2009-01-28
Try here:
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

Scroll down for Windows after Ubuntu. The guide does state that it's easier to do Windows first, so I don't know if you are going to find an idiot's guide for the hard way.

Good luck!

---

### Post by cairnzi on 2009-01-28
cheers for the replys, think ive got it sorted now, many thanks.

---

### Post by arrk on 2009-01-31
You Ubuntu users are going to hate me!  Apologies in advance.

I tried out MythBuntu to set up a dedicated PC as a home media center on the advice of a colleague, but frankly I have no interest nor no time to learn a whole new OS - just to watch TV and DVDs.

SO - my question is this!  How on earth do I stop my PC default booting to Ubuntu.  I want it to default to XP, with the CHOICE of MythBuntu rather.  Not the other way round - which it currently is.

ARRK

---

### Post by glennzo on 2009-01-31
> **arrk said:**
> You Ubuntu users are going to hate me!  Apologies in advance.

I tried out MythBuntu to set up a dedicated PC as a home media center on the advice of a colleague, but frankly I have no interest nor no time to learn a whole new OS - just to watch TV and DVDs.

SO - my question is this!  How on earth do I stop my PC default booting to Ubuntu.  I want it to default to XP, with the CHOICE of MythBuntu rather.  Not the other way round - which it currently is.

ARRK
You edit the file **/boot/grub/menu.lst**. There is a line that reads **default=x** where **x** is a number representing a position in the boot menu. Here's an example from my Fedora system:
```
default=0
timeout=30
splashimage=(hd0,5)/boot/grub/splash.xpm.gz
title   Fedora (2.6.27.12-170.2.5.fc10.i686)
	root (hd0,5)
	kernel /boot/vmlinuz-2.6.27.12-170.2.5.fc10.i686 ro root=UUID=b858b843-29a9-49e5-9979-b947caf9f039 rhgb quiet vga=792
	initrd /boot/initrd-2.6.27.12-170.2.5.fc10.i686.img
title   Fedora 10 (2.6.27.9-159.fc10.i686)
	root (hd0,5)
	kernel /boot/vmlinuz-2.6.27.9-159.fc10.i686 ro root=UUID=b858b843-29a9-49e5-9979-b947caf9f039 rhgb quiet vga=792
	initrd /boot/initrd-2.6.27.9-159.fc10.i686.img
title   Ubuntu 8.10
	root (hd0,4)
	kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=030304a5-9208-4927-afb7-90111b8da52c ro quiet splash vga=792
	initrd /boot/initrd.img-2.6.27-7-generic
	quiet
title   Windows Vista or Windows 7 Beta
	rootnoverify (hd0,1)
	chainloader +1

```
Here, **default=0** means that the first Fedora option will be the OS booted if I let the timer count down. If I changed it to **default=3** then the Windows loader will be booted if I let the timer count down. If I wanted Ubuntu to be the default then I would change the line to **default=2**.

---

### Post by carml on 2009-01-31
> **arrk said:**
> You Ubuntu users are going to hate me!  Apologies in advance.

I tried out MythBuntu to set up a dedicated PC as a home media center on the advice of a colleague, but frankly I have no interest nor no time to learn a whole new OS - just to watch TV and DVDs.

SO - my question is this!  How on earth do I stop my PC default booting to Ubuntu.  I want it to default to XP, with the CHOICE of MythBuntu rather.  Not the other way round - which it currently is.

ARRK
IMHO you should modify the file called menu.lst in Fyle System/boot/grub.To modify that file you have to go in  Applications->Accessories->Terminal,then write sudo nano /boot/grub/menu.lst;but unfortunately I don't know how to set the order of boot. :(

---

### Post by arrk on 2009-01-31
Thanks Glennzo & Carml - off to go do this!

Highlights my point exactly, don't it - I need even to know the OS just to stop using it!

ARRK

---

### Post by glennzo on 2009-01-31
You can't stop. You're a prisoner now :D

---

### Post by arrk on 2009-01-31
Bizzarre galactic-speak - "sudo nano bla bla" - but it works!

Thank you both!

Another (criminal) question.  What if I wanted to uninstal MythBuntu altogether?  Can I remove the HDD partition form windows or is this inelegant and dangerous?

ARRK

---

### Post by labinnsw on 2009-01-31
The newbies way

You can also use a graphical user interface "GUI"
Go to System>>Adminisstration>>Synaptic Package Manager
Search for "Startup Manager" and install it.

Once installed go to System>>Adminisstration>>Startup Manager

Under the boot options tab, change the default operating system to the one you want.

---

### Post by carml on 2009-01-31
> **arrk said:**
> Bizzarre galactic-speak - "sudo nano bla bla" - but it works!

Thank you both!

Another (criminal) question.  What if I wanted to uninstal MythBuntu altogether?  Can I remove the HDD partition form windows or is this inelegant and dangerous?

ARRK
If you want to get rid of the Ubuntu partition,you have to just download Gparted-Live°(the Live version of Gparted),then write it on a cdrom.Once you've done,reboot with the cdrom inside,when Gparted is loaded just delete the prtition with Ubuntu and expand the partition with Windows.Then shudown.take the cd of Windows and boot in recovery mode.It should restore your PC to the state before the installation of Ubuntu.:)

---

