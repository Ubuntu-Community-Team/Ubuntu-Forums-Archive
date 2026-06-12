---
title: "Networking Nvidia controller not detected"
date: 2006-10-09
forum: Networking &amp; Wireless
---

### Post by jorge_linux on 2006-10-09
Hello, 

I just installed ubuntu on my new computer and it seems as though none of my devices are recognized. The lspci output indicates a message around the lines of "device not found/recognized" for every line. I'm running an Athlon 64 X2, with an ASUS motherboard, and an Nvidia controller. My main problem is getting the network to work. I'm using a wireless usb adapter but that brings a whole other set of problems because it uses windows drivers for 32 bit machines, not 64. 

I think it might be because the nvidia drivers are not installed but I can't upgrade since I don't have an internet connection. I don't even see something with "ethernet" under networking in the menu. I only see a modem connection available.

My system is fine because I'm dual booting with windows xp and everything works well with that. 

Any help would be appreciated.

Thanks,
geo

---

### Post by hw-tph on 2006-10-10
Type **lspci | grep -i net**. This will show you what network controllers are found on your system. If you post the results it would make it a whole lot easier to help you. :)


Håkan

---

### Post by jorge_linux on 2006-10-10
There is no output when I type that command. The lines that are present all say "unknown device".

geo

---

### Post by odyn_owl on 2006-10-11
I have a similar problem with net cards.
I change net card and now server not see network.

lspci |grep -i net

0000:00:04.0 Ethernet controller: nVidia Corporation nforce2 Ethernet Controller (rev a1)
0000:02:01.0 Ethernet controller: 3Com Corporation 3C920B-EMB Integrated Fast Ethernet Controller [Tornado] (rev 40)


How can I fix that problem?
Ubuntu 6.06 LTS Server

---

### Post by hw-tph on 2006-10-11
> **jorge_linux said:**
> There is no output when I type that command. The lines that are present all say "unknown device".

geo

Then just post the output of **lspci**.

[quote=odyn_owl]I have a similar problem with net cards.
I change net card and now server not see network.[/quote]

The network cards listed are supported and should work fine. The onboard nvidia uses the forcedeth driver and the 3c920 controller uses the 3c590 or Tornado driver (I don't recall which one at the moment). If you type **sudo ifconfig** do you get both eth0 and eth1 entries? Also, **dmesg | grep eth** might provide some useful information.



Håkan

---

### Post by odyn_owl on 2006-10-11
tornado is old one, now it was removed.
ifconfig:
Link encap: Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
...

dmesg |grep -i eth

found eth0 nvidia

how I can fix problems (kill tornado?) and put correct ip address and mask

---

### Post by jorge_linux on 2006-10-11
Hello Hakan

Here are the output files for dmesg, lspci, and ifconfig.

Appreciate the help, thanks,
geo

---

### Post by jorge_linux on 2006-10-13
Does anyone know the source of this problem? Why is nothing being recognized, and how do I fix it.

Thanks,
geo

---

### Post by Jason_25 on 2006-10-13
Your thread is very confusing.  Are you trying to get your nvidia ethernet working?  It should work out of the box.  Or are you trying to get a USB network adapter working?  If you want decent performance, you might want to look at a non-usb network adapter.  Most aren't very well supported and have terrible performance to boot.  Personally, If I want wireless to a linux box I will use a very well supported chipset (atheros, prism2) or preferably a router in access point mode like the WRT54G running DD-WRT firmware.

---

### Post by jorge_linux on 2006-10-13
Yes I'm trying to get my ethernet to work. It works in windows xp, but I cannot get it to work under ubuntu, along with everything else. See the lspci output file I posted in a previos reply.

geo

---

### Post by jorge_linux on 2006-10-16
Just to clarify, my problem is that all of my nvidia devices are not being recognized in 'lspci'. The main problem is getting the ethernet to work.

I have posted the files with the output of the lspci, dmesg, and ifconfig commands.

Let me know if you have any ideas on a solution.
geo

---

### Post by hw-tph on 2006-10-18
That's very odd. lspci doesn't even list an unknown network controller...

This must be a very new motherboard? What is the exact model name of it?


Håkan

---

### Post by jorge_linux on 2006-10-20
The motherboard is an ASUS M2N-MX with nForce 430. I also tried the beta release for the new Ubuntu 6.10, that one doesn't even boot up. It loads the boot screen, but after selecting boot with safe graphics it freezes after a few procedures are called.

---

### Post by metalspree on 2006-10-24
I Have the same problem...the network card is not at all recognised. Same Motherboard make ASUS M2N-MX. I tried gentoo 2006.1 today & it was able to detect an eth0 card during boot-up (under "-nofb noapic" lines that i had to add up in the boot kernel parameter) but wasnt able to make it work as the card wasnt found under networking settings.

---

### Post by affe on 2006-10-25
Same problem here with ASUS M2N-VM DH motherboard (NForce 430 + 6100). None of the PCI peripherals are recognized.

00:00.0 RAM memory: nVidia Corporation Unknown device 03ea (rev a1)
00:01.0 ISA bridge: nVidia Corporation Unknown device 03e0 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 03eb (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 03f5 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 03f1 (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 03f2 (rev a2)

etc.

Also the graphical installation (Edgy) jammed in various phases of the file copy process, but eventually Ubuntu was successfully installed with the alternate install image.

---

### Post by affe on 2006-10-26
It seems this is related to MCP61 chipset, see NVidia's forum:

[http://www.nvnews.net/vbulletin/showthread.php?t=75920](http://www.nvnews.net/vbulletin/showthread.php?t=75920)

I'll be testing the forcedeth.c change later today.

---

### Post by affe on 2006-10-26
I chose to install the 2.6.18.1 kernel instead. Problem solved.

MCP61 audio can be taken into use by patching the sound/pci/hda/hda_intel.c according to these instructions:

[http://www.archivesat.com/Ubuntu_Kernel_team_discussions/thread1736701.htm](http://www.archivesat.com/Ubuntu_Kernel_team_discussions/thread1736701.htm)

---

### Post by permieshane on 2006-11-07
> **affe said:**
> I chose to install the 2.6.18.1 kernel instead. Problem solved.

MCP61 audio can be taken into use by patching the sound/pci/hda/hda_intel.c according to these instructions:

[http://www.archivesat.com/Ubuntu_Kernel_team_discussions/thread1736701.htm](http://www.archivesat.com/Ubuntu_Kernel_team_discussions/thread1736701.htm)

OK this is my first post & very early experience with Linux.  But how do I install the 2.6.18.1 kernal without internet access on the pc that has the ubuntu installation?
Where do I find the suitable kernal (for 64bit version)?
What do I then need to do to install it?
Thanks in advance.

---

### Post by zasf on 2006-11-22
> **permieshane said:**
>  But how do I install the 2.6.18.1 kernal without internet access on the pc that has the ubuntu installation? 

you download the source with some other comp or with your win partition, then copy the source on linux partition (for example via usb key if you have one), then you follow an [howto about kernel compilation]("http://ubuntuforums.org/showthread.php?t=56835&highlight=kernel+compilation+newbies")

Of course, consider using a later kernel (ie 2.6.18.1) and don't forget to patch it as affe suggested.

> **permieshane said:**
> Where do I find the suitable kernal (for 64bit version)? What do I then need to do to install it?
Thanks in advance.

You will end up with a suitable kernel after compilation, about installation read the howto I posted and you'll see

---

### Post by jorge_linux on 2007-03-05
So I finally reply back. I was the one who initiated this thread, took the advice from all you people who posted, still nothing worked as I got more problems, and then I got discouraged, and stopped using ubuntu for a while.

So I'm going to give it another try.

I downloaded the later kernel (2.6.18.1) as recommended, and got up to the menuconfig part in the explanation of how to recompile your kernel (look at the previous posts so you know what I'm talking about). Then my next step was to actually compile it using the following command: 

sudo make-kpkg clean

But I get the error message, "command not found". I think I'm missing a package, but I do not have an internet connection to download them directly. I therefore used my windows partition to download "kernel-package". This file was in a tar.gz form, and I do not know how to install this once decompressed. This is where I'm at so far. Can someone please help me out?

Thanks,
Jorge

---

### Post by zasf on 2007-03-06
you need kernel-package for sure and libncurses5 only if you want to use 'make menuconfig', I don't advice you to download them from your windows partition because kernel-package depends on other packages that you don't have installed, wich also depend on other packages so you'll end up having a hard time

kernel-package should be in the install cdrom, so you might want to pop in the cd, add the cdrom as a repository (synaptic should help if no pop up shows) and do a 

```
sudo apt-get update
sudo apt-get install kernel-package
```

Matteo

PS: another option you have is to use a more rencent ubuntu version: feisty, wich is still under development but it is good enough for playing around. I assume you are not going to have a 'production' machine on linux, so I would give it a try. This avoids you kernel recompilation since feisty uses kernel 2.6.20.

---

### Post by jorge_linux on 2007-03-06
Great! I downloaded Feisty and it now detects my hardware properly. But now back to the original problem, I have no internet. I now see a DHCP connection in system>administration>network, which is good if I were to use an Ethernet cable. Before I was only able to see a dial-up Modem connection, so this is progress. But I'm using a wireless usb adapter made for windows. Due to space constraints I'm not using a wired connection. 

I installed ndiswrapper and loaded the drivers and modules, and had it run at boot time. The only problem is how do I use it? I do not see any ndiswrapper connection in system>administration>network. How do I activate the usb adapter?


Thanks,
Jorge

---

### Post by zasf on 2007-03-07
I'm happy to know that things are a bit better under feisty, for the ndiswrapper problem you may want to check a specific thread about it. Sorry but I'm not able to help you in that field.

---

