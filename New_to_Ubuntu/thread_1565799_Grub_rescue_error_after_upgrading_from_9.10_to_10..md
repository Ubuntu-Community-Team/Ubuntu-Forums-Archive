---
title: "Grub rescue error after upgrading from 9.10 to 10.04.1"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by patrolman on 2010-09-01
OK, please bear with me. I downloaded Ubuntu 10.04.1 yesterday but on  trying to install it in another partition of a PC which I run windows 7  on, I was given the options to try, install etc. First I selected try  but it seemed unresponsive for a few moments, then changed to a  different screen, kind of distorted with 3 blue bars down the bottom  (sometimes 2 white ones on subsequent attempts) and a kind of blurred,  double vision of the menu at the top of the screen. To the best of my  knowledge I couldn't do anything (nor wanted to withouth being able to  see what to select). I read up a little and figured it might have  something to do with the nvidia graphics card.ee

I tried the  ubuntu 10.04.1 alternate installation version but some of the  instructions were getting slightly complex for a noob like me once I got  to the partition stage, and as it looked like there were a fair few  steps left after that I decided to look for an easier option.

Then  I saw the the option of Wubi and thought it looked like a good option  for me. I came across the same problems as when using the USB stick or  Live CD without wubi. So I decided to try an earlier version.

I  went with 9.04 and came across another problem, I can't remember what to  be honest, and then moved on to 9.10 and finally I was able to see the  menu and managed to install ubuntu 9.10.

Then I started playing  around a little, getting a feel for the system and I came across a  couple of minor problems, one of which was that the screen resolution  wasn't recognised automatically. I had previously installed a few  programs through the ubuntu software centre and went on to update the  existing programs and I noticed the update Ubuntu option. So instead of  looking for a solution to the problem I tried to update.

Everything  seemed to go well until I was asked a question about Grub (which I  didn't know anything about), but from the accompanying text I got the  impression that if in doubt is was safest to install grub to all  partitions - which is what I did. Then when Irestarted, the real  problems started.

The message:
"error: no such device: 9f5f2890-9b12-4578-b2e3-15ebe3312498
grub rescue>" comes up on the screen, and sometimes
"error: fd0 cannot get C/H/S values.
grub rescue>", I think when there's a USB inserted.

 So I read a few forum posts and one of the recommendation was to  recover/repair Windows. I upgraded from Vista to 7, so didn't really  want to have to reinstall again so looked around for alternate solution,  but most of them looked a little too technical for me, so I ended up  going for the recover option, hoping to see repair somewhere, but to no  avail. I recovered Windows 7 with the Vista disc and then when I restart  the machine, thinking everything is going to be alright,"error: no such  device: 9f5f2890-9b12-4578-b2e3-15ebe3312498
 grub rescue>" comes up on the screen again.

I want my computer  to boot again! I don't mind reinstalling everything again (but  obviously if I don't have to that would be better). Please help!

Thanks in advance

---

### Post by tyblogger5 on 2010-09-01
Hi Patrolman,

Yikes, sounds like you got a little too adventurous (like myself:redface:).  I might not be able to help you completely, but I'll try.

First, let me tell you a little about what GRUB is.  GRUB stands for GRand Unified Bootloader which is just the software that allows your computer to start.  Now I'm not sure how much you know about computers so I'll explain everything.  How the computer starts up is shown in picture1_1.png (attached to this post).

When the computer is turned on, it loads a Basic Input/Output System (BIOS) which will look at the Master Boot Record (MBR) located at the very first bytes on the Hard Drive.  On a Windows system, this MBR redirects the BIOS to load the Windows Kernel.  However with GRUB, it redirects it to a basic Linux Interface that allows you to select what operating system you would like to boot.

Now, to tackle your problem; I'm not an expert at Linux (nor will I pretend to be one), but go ahead and try to restore GRUB using   [this tutorial]("https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2").  If you want to reinstall the Windows MBR, check out [this link]("http://www.ehow.com/how_4836283_repair-mbr-windows.html").

I hope this helps, performing a system wipe is not that much fun.  PM me if you have any more questions.

Good Luck,
Tariq

---

### Post by patrolman on 2010-09-01
Thanks for the reply and the explanation about GRUB :)

One quick question, is the GRUB reinstallation process any different if I installed ubuntu using wubi? From what I have read so far, I think it is as the files aren't located where they would normally be.

---

### Post by tyblogger5 on 2010-09-01
Hmmm...did you install Ubuntu as an application or did you restart and boot from the LiveCD?

---

### Post by patrolman on 2010-09-01
I installed it as an application. Something tells me that's not the best way to do it...

---

### Post by patrolman on 2010-09-01
So I started reading and the first thing I did was this:
```
sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        1531       19712   146040316    7  HPFS/NTFS
/dev/sda2           19712       20986    10238976    7  HPFS/NTFS
/dev/sda3           20987       38913   143998627+   f  W95 Ext'd (LBA)
/dev/sda5           20987       38913   143998596    7  HPFS/NTFS

Disk /dev/sdb: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x000bbe54

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7872     2015216    b  W95 FAT32

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 749.5 GB, 749452918784 bytes
255 heads, 63 sectors/track, 91115 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000


```

Does this part - **WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted. - **mean anything special? I googled it but it-s a bit over my head.

---

### Post by tyblogger5 on 2010-09-01
Just to clarify my understanding, you have Windows 7 and Ubuntu.  Do you have multiple hard drives in your computer?

---

### Post by patrolman on 2010-09-01
> **tyblogger5 said:**
> Just to clarify my understanding, you have Windows 7 and Ubuntu.  Do you have multiple hard drives in your computer?
I have one hard drive. It originally came with 2 partitions one for Windows and another for data. I formatted one for Ubuntu last night, but I don-t think it-s really necessary with Wubi. There is also one more partition I-m not sure about, I think it-s unassigned.

---

### Post by patrolman on 2010-09-01
Sorry, I didn-t realise before, the second hard drive is an external hard drive I have plugged in. /slaps head/
I-m backing up some data before it-s too late.

---

### Post by bcbc on 2010-09-01
You probably just need to replace the windows bootloader.

```
bootrec.exe /fixmbr (from win7/vista)
```
or 
```
fixmbr (from xp repair)
```
It shouldn't matter which you use, the bootloader is very simple - it transfer control to the partition marked active.

Or you can use lilo from a live CD
```
sudo apt-get install lilo  #ignore warnings= they don't apply
sudo lilo -M /dev/sda mbr
```

[https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)

---

### Post by tyblogger5 on 2010-09-01
> **bcbc said:**
> You probably just need to replace the windows bootloader.

```
bootrec.exe /fixmbr (from win7/vista)
```
or 
```
fixmbr (from xp repair)
```
It shouldn't matter which you use, the bootloader is very simple - it transfer control to the partition marked active.

Or you can use lilo from a live CD
```
sudo apt-get install lilo  #ignore warnings= they don't apply
sudo lilo -M /dev/sda mbr
```

I think bcbc is right, try to fix the windows bootloader.

---

### Post by patrolman on 2010-09-01
> **bcbc said:**
> You probably just need to replace the windows bootloader.

```
bootrec.exe /fixmbr (from win7/vista)
```or 
```
fixmbr (from xp repair)
```It shouldn't matter which you use, the bootloader is very simple - it transfer control to the partition marked active.
How exactly do I do this? I tried to use the vista recovery CD but I wasn-t given the option of  "Repair Your Computer" or given access to the System Recovery window. 
[LEFT][COLOR=#000000][URL="http://www.ehow.com/how_4836283_repair-mbr-windows.html#ixzz0yJ9VF0iw"]
[/URL][/COLOR][/LEFT]

> 
Or you can use lilo from a live CD
```
sudo apt-get install lilo  #ignore warnings= they don't apply
sudo lilo -M /dev/sda mbr
```[https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)
What do I do with this? Just write it in the Terminal?

Cheers for the ideas

---

### Post by tyblogger5 on 2010-09-01
As far as recovering it with the Windows Vista/7 disc, you have to select the language and when it says "Install Now" there will be an option to "Repair your Computer".  Once you've clicked that, there should be a button/link to open the command prompt, that is where you type in those commands.

To fix it from the live CD, just write it in the terminal.

And (hopefully) Presto, the Windows MBR will be fixed!

-Tariq

---

### Post by bcbc on 2010-09-01
> **patrolman said:**
> How exactly do I do this? I tried to use the vista recovery CD but I wasn-t given the option of  "Repair Your Computer" or given access to the System Recovery window. 
[LEFT][COLOR=#000000][URL="http://www.ehow.com/how_4836283_repair-mbr-windows.html#ixzz0yJ9VF0iw"]
[/URL][/COLOR][/LEFT]


What do I do with this? Just write it in the Terminal?

Cheers for the ideas

Yes, in the Terminal. After you run the first command you'll be prompted to install (enter y) then you'll get a 'popup window' (ignore warnings, TAB to OK and hit ENTER). Then run the second command. Then reboot.

It installs the lilo bootloader in a form that is similar to the windows bootloader. It just transfers control to the partition marked with the boot flag.

---

### Post by patrolman on 2010-09-01
> 
```
sudo apt-get install lilo  #ignore warnings= they don't apply
sudo lilo -M /dev/sda mbr
```So let me just clarify - Should I put exactly this text quoted in Terminal and hope for the best or do I need to change slightly any of that according to my system?

Thanks a lot for all your help

---

### Post by tyblogger5 on 2010-09-01
I don't think so, right bcbc?

I want to double check before telling you!

---

### Post by patrolman on 2010-09-01
Thanks a lot!

It's working! The worst thing is I had already used the recovery disk beforehand hoping to find this "Repair your computer" option, but wasn't given the option, so now the PC is in the process of recovery.

---

### Post by jtarin on 2010-09-01
I would say repair your MBR first and get Win7 back on track.Then there are several ways to get your dualboot accomplished after that.[Windows7 Recovery steps]("http://support.microsoft.com/kb/927392").

---

### Post by tyblogger5 on 2010-09-01
Right On, Post back here if you have any more problems!

-Tariq

---

### Post by patrolman on 2010-09-20
At the the risk of exposing myself as a true noob, I'm going to add to this thread.

I mangaged to install 9.10 and upgrade to 10.04.1 (without wubi, but for some reason I couldn't do anything using a 10.04 live usb - I think it has something to do with nvidia) and had made a few changes and had a look around before deciding to have a clean up.I was trying to clear up some "unallocated" partitions on my hard drive from windows (after briefly trying in ubuntu) and I think I must have formatted the drive ubuntu was on. 

I got the same grub rescue prompt and fixed the grub rescue problem from the live usb (after frantically searching for my previous thread) with this little gem:> **bcbc said:**
> Or you can use lilo from a live CD
```
sudo apt-get install lilo  #ignore warnings= they don't apply
sudo lilo -M /dev/sda mbr
```

[https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)

---

### Post by jtarin on 2010-09-20
> **patrolman said:**
> At the the risk of exposing myself as a true noob, I'm going to add to this thread.

I mangaged to install 9.10 and upgrade to 10.04.1 (without wubi, but for some reason I couldn't do anything using a 10.04 live usb - I think it has something to do with nvidia) and had made a few changes and had a look around before deciding to have a clean up.I was trying to clear up some "unallocated" partitions on my hard drive from windows (after briefly trying in ubuntu) and I think I must have formatted the drive ubuntu was on. 

I got the same grub rescue prompt and fixed the grub rescue problem from the live usb (after frantically searching for my previous thread) with this little gem:

Very creative and I might add Lilo can be a very good boot manager and easier to configure than Grub for some.Learn how to rescue Lilo before you need it. It can happen as with all boot managers.

---

