---
title: "My laptop won't boot Ubuntu or Windows"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by Beastlyhowls on 2010-12-22
Earlier, I installed Ubuntu with Wubi. I separated part of my hard drive and created hard drive V: with 20GB on it.

When I was installing Ubuntu, I got asked if I wanted to do GRUB updates. After I got them, I had to reboot my laptop.

When I rebooted, I got this screen/error:

error: no such device: 57c33db4-14e5-4e1c-a138-e865adde66f8
grub rescue>

Now I can't boot either Ubuntu or Windows (I'm currently on a different computer right now).

I don't have a Windows Recovery CD, or my installation CD. (I forgot to mention that I have Windows Vista.)

Thanks in advance for any help.

---

### Post by wilee-nilee on 2010-12-23
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

Since you don't have a widows recovery disc you probably just need to boot it to the repair command line and run from this one.
```
bootec.exe /fixmbr
```

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Post the script if you need to though.

---

### Post by Beastlyhowls on 2010-12-23
I can't do the bootscript because I can't boot into my laptop.

And I tried using the code, but it just told me it was an unknown command.

Unless I'm doing something wrong. :\

---

### Post by wilee-nilee on 2010-12-23
> **Beastlyhowls said:**
> I can't do the bootscript because I can't boot into my laptop.

And I tried using the code, but it just told me it was an unknown command.

Unless I'm doing something wrong. :\

You have to do this with the the download link burned to a disc.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

1) Boot with your Vista/Windows 7 recovery disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. Notice the W7 forum link that is a visual version of instructions. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** 
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by Beastlyhowls on 2010-12-23
I don't have my Windows Vista installation disk.

So I assume I need to find a Windows Vista recovery/installation disk, or find a download to burn onto a clean CD?

---

### Post by Rubi1200 on 2010-12-23
Sorry to jump in here, but this is Wubi-related so I hope wilee-nilee will forgive me.

If you don't have a Windows CD you can install a Windows-like bootloader using an Ubuntu CD.

In either case, you need to set BIOS to boot from the CD/DVD drive. This can also be done from USB if your computer allows it.

For how to achieve restoring the bootloader, see problem #1, solution #2:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Don't forget to apply the permanent fix once you are back in Ubuntu.

---

### Post by Beastlyhowls on 2010-12-23
I don't have a Ubuntu CD either (but I don't have the slightest clue what that is). Sorry. xD

---

### Post by wilee-nilee on 2010-12-23
> **Rubi1200 said:**
> Sorry to jump in here, but this is Wubi-related so I hope wilee-nilee will forgive me.

If you don't have a Windows CD you can install a Windows-like bootloader using an Ubuntu CD.

In either case, you need to set BIOS to boot from the CD/DVD drive. This can also be done from USB if your computer allows it.

For how to achieve restoring the bootloader, see problem #1, solution #2:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Don't forget to apply the permanent fix once you are back in Ubuntu.

No problem.:)

---

### Post by wilee-nilee on 2010-12-23
> **Beastlyhowls said:**
> I don't have a Ubuntu CD either (but I don't have the slightest clue what that is). Sorry. xD

Download ths ISO it is a vista recovery cd if burned to a cd.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

follow these instructions and enter the highlighted command in the command terminal. Notice the W7 forum link for a visual representation of the instructions.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** 
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by Beastlyhowls on 2010-12-23
What option do I pick? I don't remember if my laptop is 32-Bit or 64-Bit.

---

### Post by Rubi1200 on 2010-12-23
> **Beastlyhowls said:**
> I don't have a Ubuntu CD either (but I don't have the slightest clue what that is). Sorry. xD
Are you able to get hold of a Windows installation/recovery disk?

If yes, follow the instructions posted previously by wilee-nilee.

If no, this is what I suggest:
download and burn to CD the image for Ubuntu.
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Then use the LiveCD to boot your laptop and repair the bootloader as I previously linked to.
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

I realize this is perhaps more information and hassle than you would have liked, but we can fix this and you will have both Windows and Ubuntu back.

Please read the information and follow the instructions. If there is anything you are not sure about, ask first before doing it.

Thanks.

---

### Post by Beastlyhowls on 2010-12-23
I downloaded Ubuntu, but when I tried to burn it with InfraRecorder, it didn't work. It told me something about data and then some drivers don't like closing in simulation?

I don't think it's normal for a CD to start out with 0 bytes of space, correct? :c

---

### Post by wilee-nilee on 2010-12-23
> **Beastlyhowls said:**
> I downloaded Ubuntu, but when I tried to burn it with InfraRecorder, it didn't work. It told me something about data and then some drivers don't like closing in simulation?

I don't think it's normal for a CD to start out with 0 bytes of space, correct? :c

Make sure the cd's blank and just right click the ISO then burn to disk choose image if asked, and the slowest speed. You may not be asked about the image or speed by the stock cd/dvd burner.

---

### Post by Beastlyhowls on 2010-12-23
I keep getting this:

```
Data does not fit on current disk.
```

Then followed by this:

```
Some drivers don't like closing in simulation mode.
```

I tried making it minimum speed.

---

### Post by theasprint on 2010-12-23
Hi,

Ok if you are using a friend's/relative's Windows 7 laptop/computer, then you would not need to burn using InfraRecorder. 

* OHYA, did you use a CD or a DVD? Use a DVD-RW!!!
To Erase a disc, the disc must be a re-writable one.

Upon inserting the disc into the PC, right-click the disc and Erase it.

Then burn your Ubuntu .iso file into the disc with the slowest speed.

RMB, use a DVD-RW not CD.

---

### Post by Beastlyhowls on 2010-12-23
I just tried with another DVD (DVD-R) and there's always an error. It started writing when it got to 1%, and then it just gave me some error. :\ (I was using InfraRecorder with Vista again.)

* Oh, and I was trying to burn Ubuntu onto the DVD.

---

### Post by Beastlyhowls on 2010-12-24
```
BootRec.exe /fixmbr 
```

For that code, am I supposed to type it in after I open the command prompt, or sometime later?

---

### Post by idavid on 2010-12-24
> **Beastlyhowls said:**
> ```
BootRec.exe /fixmbr 
```For that code, am I supposed to type it in after I open the command prompt, or sometime later?

After you burn the vista or win7 recovery disk, you restart your computer and boot from cd or dvd, after that you'll get a pop window and choose command prompt, in there you type Bootrec.exe /fixmbr.

---

### Post by |Eric| on 2010-12-24
from the looks of it your in simulation mode ( not realy writing anything ) 
disable that option ( its useless)  write at 4x max for dvd and 8x max for CD 
make shure your iso is a full one ( around 700mb for CD )

looks like your BIOS anti-virus protection is on .. make shure it isnt 
( that feature may vary from PC to PC ) 

when you boot choose recovery  or just reinstall ...

---

### Post by wilee-nilee on 2010-12-24
> **Beastlyhowls said:**
> ```
BootRec.exe /fixmbr 
```

For that code, am I supposed to type it in after I open the command prompt, or sometime later?

1) Boot with your Vista/Windows 7 recovery disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. Notice the W7 forum link that is a visual version of instructions. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** 
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by Beastlyhowls on 2010-12-25
I put Windows Vista x64 recovery on a CD and it burned successfully (according to ImgBurn).

Then I tried following the instructions to get to the command prompt screen, but I couldn't get past selecting my driver/system screen.

The thing is that I think that my laptop is 64-Bit. I have a AMD Turion 64 x2 Mobile Technology TL-50.

So did I get the wrong bit? Or what went wrong?

---

