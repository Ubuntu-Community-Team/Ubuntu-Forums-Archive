---
title: "Uninstall Ubuntu partition - odd situation"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by Monkey God on 2009-08-19
I have a Vista computer with Ubuntu 9.04 installed on an external drive. Now when I power up the computer Grub starts up and expects the external drive there. If I do not have the external drive, I cannot use Vista. This is not a good situation. If the external drive is damaged or gone, no computer.
I understand now that I should have gone under System>Administration>USB Startup Disk creator when using the Live CD.

This situation was created when I did an install on the external drive, using the entire drive. Now I would like to uninstall so my computer can work normally. Then I can create the USB Startup drive and play with Ubuntu before deciding how to partition my main drive.

Any help is appreciated.
I have seen another thread on uninstalling Ubuntu, but it doesn't seem to apply. I am hesitant to do anything drastic, lest I lose access to the data and programs I have.

---

### Post by Penguin Guy on 2009-08-19
Boot into Windows and run [COLOR="Green"]fixmbr[/COLOR] as admin. You can open the command line in Windows by pressing [COLOR="Green"]WinKey + R[/COLOR], then typing [COLOR="Green"]cmd[/COLOR] into the box that pops up. If Windows will not allow you to do this, boot into safe mode (press [COLOR="Green"]F8[/COLOR] on Windows boot) and try again. [COLOR="Red"]This solution will allow Windows to boot normally but will not actually remove Ubuntu from your external hard drive. Removing Ubuntu can be done separately using the Partitioner on the live CD.[/COLOR]

---

### Post by philinux on 2009-08-19
With vista you can also use easybcd as the bootloader to boot both vista and ubuntu. I installed ubuntu of GF's laptop. At the last stage I clicked advanced and told it to install grub to the ubuntu partition. This way it did not overwrite the mbr with grub.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by Monkey God on 2009-08-19
The Windows command line box does not recognize "fixmbr" as a command, program, or batch file.

philinux, it seems to be too late to use EasyBCD. Even before getting to boot selection, grub loader expects my external drive to be connected or it gives an error.

---

### Post by Penguin Guy on 2009-08-19
```

       [COLOR="Silver"]*Hard Disk*[/COLOR]                :
|-----|----------------|        : 
| MBR | Windows  Vista |        : The **M**aster **B**oot **R**ecord tells the Computer
|-----|----------------|        : which partition to boot from. It is currently
   |                            : pointing to your USB drive which has GRUB
   V   [COLOR="Silver"]*USB Drive*[/COLOR]                : on. **GRUB is not on the MBR.**
|------|-------------|          :
| GRUB | Ubuntu 9.04 |          :
|------|-------------|          :

```

```

       [COLOR="Silver"]*Hard Disk*[/COLOR]                :
|-----|----------------|        : 
| MBR | Windows  Vista |        : 
|-----|----------------|        : When the USB drive is removed, the MBR 
   |                            : points to nothing, therefore, nothing
   V                            : will boot.
                                :
                                :
                                :

```

```

       [COLOR="Silver"]*Hard Disk*[/COLOR]                :
|-----|----------------|        : The Windows recovery disk command
| MBR | Windows  Vista |        : [COLOR="Green"]fixmbr[/COLOR] points the **M**aster **B**oot **R**ecord
|-----|----------------|        : back to Windows.
   |          ^                 :
   -----------'                 :


```

---

### Post by philinux on 2009-08-19
I think you need to run fixmbr from the windows recovery cd.

---

### Post by Penguin Guy on 2009-08-19
> **philinux said:**
> I think you need to run fixmbr from the windows recovery cd.
Or if you don't have the CD, boot into Ubuntu and run:
```
sudo apt-get install ms-sys
sudo ms-sys -m /dev/sda
```

---

### Post by philinux on 2009-08-19
> **Penguin Guy said:**
> Or if you don't have the CD, boot into Ubuntu and run:
```
sudo apt-get install ms-sys
sudo ms-sys -m /dev/sda
```

Just recently heard about ms-sys. It's not in jaunty repos though. :(

Apparently from the live cd you can do this I've found.

```
sudo lilo -M  /dev/sda mbr
```
[http://ubuntuforums.org/showthread.php?p=6361212](http://ubuntuforums.org/showthread.php?p=6361212)

---

### Post by Monkey God on 2009-08-19
Doesn't seem to find  ms-sys or lilo commands.

I'm creating a recovery cd to try fxmbr again.

Sadly, this is the only major problem I have had with Ubuntu, as all my hardware has been recognized.

Thanks for all the help so far.

---

### Post by LewRockwell on 2009-08-19
> **Monkey God said:**
> I have a Vista computer with Ubuntu 9.04 installed on an external drive. Now when I power up the computer Grub starts up and expects the external drive there. If I do not have the external drive, I cannot use Vista. This is not a good situation. If the external drive is damaged or gone, no computer.
I understand now that I should have gone under System>Administration>USB Startup Disk creator when using the Live CD.

This situation was created when I did an install on the external drive, using the entire drive. Now I would like to uninstall so my computer can work normally. Then I can create the USB Startup drive and play with Ubuntu before deciding how to partition my main drive.

Any help is appreciated.
I have seen another thread on uninstalling Ubuntu, but it doesn't seem to apply. I am hesitant to do anything drastic, lest I lose access to the data and programs I have.

SuperGrubDisk should correct your MBR situation quickly and easily

[http://www.supergrubdisk.org/wiki/Boot_Problems](http://www.supergrubdisk.org/wiki/Boot_Problems)

Also, it should be noted that a small partition may be created on the primary/master hard drive...where the /boot/grub/menu.lst file can be placed so that the grub in the MBR can be directed there

(this allows one or more external devices to be bootable easily from one central grub menu)

Wheeee, this computin' stuff is fun!

.

---

### Post by Monkey God on 2009-08-19
Well fixmbr from the Vista recovery CD didn't work - didn't find the command or program.

Supergrub is the next thing to try.

---

### Post by Monkey God on 2009-08-19
Maybe I should reinstall Ubuntu from the live CD. My internal hard drive is small though, with only 65 GB left. This is one reason why I installed Ubuntu on an external drive. My thought was that down the road I would wipe it all off and install Ubuntu. But first I wanted to get used to it.

If I reinstall Ubuntu on my internal drive, it should stop looking for that external drive with Ubuntu, right? What is the smallest partition needed?

This should be better than backing everything up and reinstalling Vista.

---

### Post by Monkey God on 2009-08-19
> **LewRockwell said:**
> 
Also, it should be noted that a small partition may be created on the primary/master hard drive...where the /boot/grub/menu.lst file can be placed so that the grub in the MBR can be directed there

(this allows one or more external devices to be bootable easily from one central grub menu)

Can I do this with Supergrub?
I don't want to boot from an external drive exactly. What I want is to not need to have this external drive connected to boot normally (which is Vista, for now).

---

### Post by theozzlives on 2009-08-19
> **Monkey God said:**
> Well fixmbr from the Vista recovery CD didn't work - didn't find the command or program.

Supergrub is the next thing to try.

It's simple, just boot to the Recovery Console off your Windows disk and do:
```
fixmbr
fixboot
```
You don't need Super GRUB, or oogabooga, or fixamadoo! I've done it a million times.

---

### Post by Monkey God on 2009-08-19
I created a Windows Recovery Disk and it did not recognize fixmbr. I will try that fixboot though.

---

### Post by BinaryFeast on 2009-08-19
> **Monkey God said:**
> Well fixmbr from the Vista recovery CD didn't work - didn't find the command or program.

Supergrub is the next thing to try.

You will need the Vista installation DVD for that command. Or this:[ http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") (the repair part of the install disc that was left out from recovery cds).

---

### Post by louieb on 2009-08-19
If you don't have a widows CD then SuperGrub is the easiest way to restore VISTAs boot loader to the MBR.  other ways [IDBS Remove Replace Uninstal Grub]("http://members.iinet.net.au/%7Eherman546/p18.html") 

If you want to run Ubuntu or another OS from an external drive I would make a dedicated GRUB partition on the hard drive and let it control which OS gets to boot. 
[IDBS make a dedicated GRUB partition]("http://members.iinet.net.au/%7Eherman546/p15.html#How_to_make_a_separate_Grub_Partition_") 

Misc. 
**ms-sys** seems to have some legal problems - thats why its not included in Ubuntu and is getting hard to find.

**fixboot** is used to restore a partitions boot record and has to have a drive letter. example **fixboot c:** (won't give an error but won't do anything either without the drive letter).  you probably won't need run it - but if you do.

---

### Post by Monkey God on 2009-08-19
So it is possible to move the Gub to c: without reinstalling anything? Because that should solve my issue.

---

### Post by louieb on 2009-08-19
> **Monkey God said:**
> So it is possible to move the Gub to c: without reinstalling anything? Because that should solve my issue.

No! c: in windows speak is a partition that holds your windows install - GRUB can't be install in a NTFS formatted partition -  It will have to be installed  in its own partition formated with ext3 (recommended) or some other supported file system.

---

### Post by Monkey God on 2009-08-19
I assume Ubuntu creates a suitable partition on a drive that was formatted in NTFS?
How about this solution: I start up the Live Ubuntu CD with the external drive disconnected. I install Ubuntu on my c: in a minimum partition. Then I should be able to boot my computer with nothing connected. After proving that, I format my external drive so I can use it to my liking.

Will that work? If so, what is the minumum partition size for Ubuntu 9.04?

---

### Post by louieb on 2009-08-20
Don't know what the absolute minimum size. But I've done some test installs to a 5GB partition - that size works just fine. plus you'll want another 1/2GB or so for a swap partition.

---

### Post by theozzlives on 2009-08-21
> **louieb said:**
> Don't know what the absolute minimum size. But I've done some test installs to a 5GB partition - that size works just fine. plus you'll want another 1/2GB or so for a swap partition.

I'm pretty sure it's 3.3 GB, but that's with no added programs or data files.

---

