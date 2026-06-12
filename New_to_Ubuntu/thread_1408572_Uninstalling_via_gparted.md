---
title: "Uninstalling via gparted"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by racie on 2010-02-16
Hello everyone.  I have booted the computer with a GParted CD and with to remove the Xubuntu partition for my little brother.  I want to keep the Windows 98 OS that is also installed on the computer.  Like the noob that I am, I really don't know what do to next and I don't want to mess it up.  :P

Okay, so there are four partitions(?) on my screen: fat32, extended, ext3, and linux-swap.  Do I delete the partition called "linux-swap" or do I do something else?  Thanks!

---

### Post by audiomick on 2010-02-16
Hi.
There are a few things to take into consideration.
I would suggest having a look here before you go any further.
[http://members.iinet.net.au/~herman546/p18.html]("http://members.iinet.net.au/%7Eherman546/p18.html")

---

### Post by racie on 2010-02-16
> **audiomick said:**
> Hi.
There are a few things to take into consideration.
I would suggest having a look here before you go any further.
[http://members.iinet.net.au/~herman546/p18.html]("http://members.iinet.net.au/%7Eherman546/p18.html")

Thank you for your response, but I don't really understand a lot of things on the webpage?  What is MBR?  Also, I don't want to backup any of the files on Xubuntu.  Can you explain it in the way someone less educated understands?  :P

---

### Post by audiomick on 2010-02-16
If there is nothing to backup, then just skip that bit. Also, don't worry about the bits that talk about backing up your MBR.

MBR means Master Boot Record, and is the part of the drive where the boot loader is stored. The boot loader is a bit of software that directs the boot process so that the operating system gets found and started.

That is the problem if you just erase the Ubuntu partitions. The boot loader from Ubuntu, Grub, will still be there, will expect to find an Ubuntu partition, and will complain about it not being there. You need to replace the Windows boot loader in the MBR.

Have another look at the page. Read the section "Step One, Prepare the MBR". Herman actually explains it all pretty well, I think. Then I think the section "replace Grub in MBR with ms-sys." might be the easiest way for you.

If you don't think you can manage to do this, then leave the computer as it is until you can get someone to help you. If you just erase the Ubuntu partition, it is likely that the computer wont boot at all.

---

### Post by racie on 2010-02-16
Thanks for explaining.  Right now I'm trying to install ms-sys, but I'm having some difficulties because of a mouse problem and ms-sys is not in the repositories.  I'll post back later to see if it works.

---

### Post by drs305 on 2010-02-16
ms-sys is no longer in the repositories, It has been replaced by "mbr" - however, another bootloader called "lilo" can also prepare the MBR for your return to Windows.

Once you no longer want to boot Ubuntu, you can download "lilo" from Synaptic or with the following command. Disregard the warnings as they don't really apply to your situation.
```
sudo apt-get install lilo
```

Then you will want to run lilo, but not actually install it as a bootloader, with this command. The example uses **sda** which is normally the first drive and the one Windows is installed on. If you aren't sure, ask here first.
```
sudo lilo -M /dev/sd**[COLOR="Red"]a[/COLOR]** mbr
```

This does what the guide you are following was going to have ms-sys do. Continue following the guide and just make sure your Windows drive is the first one listed in your computer's BIOS so it will look on the MBR you just prepared for the boot instructions.

---

### Post by audiomick on 2010-02-16
> **drs305 said:**
> ms-sys is no longer in the repositories, It has been replaced by "mbr" 
Didn't know that. I have PMed Herman to let him know too.

---

### Post by racie on 2010-02-16
I accidentally typed:
```
sudo lilo -M /dev/sda
```

and it said:

```
Backup copy of /dev/sda in /boot/boot.0800
The Master Boot Record of /dev/sda has been updated
```

Did I just mess it up?

---

### Post by racie on 2010-02-16
Whoops, forgot to say that when I typed:
```
sudo lilo -M /dev/sda mbr
```
I got:
```
/boot/boot.0800 exists - no /dev/sda backup copy made
```

---

### Post by audiomick on 2010-02-17
Hi Racie,
how are you going?
I looked at the man page for lilo here
[http://manpages.ubuntu.com/manpages/hardy/man8/lilo.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/lilo.8.html)
I think that is ok.

---

### Post by racie on 2010-02-17
Well, I'm not really sure what to do next.  I've uninstalled and installed Ubuntu before on that computer and I do not recall what I did to uninstall it.  Do you know if there's a step-by-step guide for this somewhere?  Any links would be greatly appreciated.

---

### Post by bodhi.zazen on 2010-02-17
> **racie said:**
> Well, I'm not really sure what to do next.  I've uninstalled and installed Ubuntu before on that computer and I do not recall what I did to uninstall it.  Do you know if there's a step-by-step guide for this somewhere?  Any links would be greatly appreciated.

There is very little to do. Delete or reformat the Ubuntu partition and restore the windows boot loader.

[http://kb.acronis.com/content/1507](http://kb.acronis.com/content/1507)

If you do not have a windows CD / Recovery disk then you may need more help.

FYI : [http://en.wikipedia.org/wiki/MBR](http://en.wikipedia.org/wiki/MBR)

My only other piece of advice would be, if you do not know what your are doing, best stop and read a little first. Removing or installing an operating system should be done with a solid understanding of what you are doing.

---

