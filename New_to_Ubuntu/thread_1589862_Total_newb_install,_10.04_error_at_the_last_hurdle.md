---
title: "Total newb install, 10.04 error at the last hurdle!"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by MilouB on 2010-10-07
Hi all
Trying to install alongside Win7-64 using the 10.04.1 Live Cd, right at the end it says

> >>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {0b8e39ab-4226-11df-a619-83991259ffc3} device partition=U:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
10-07 08:49 DEBUG  TaskList: New task modify_bcd
10-07 08:49 DEBUG  TaskList: New task modify_bcd
10-07 08:49 DEBUG  TaskList: ## Finished modify_bootloader
10-07 08:49 DEBUG  TaskList: # Finished tasklistAny idea what this is and how to fix it?
I made a small 25Gb partition call U: to put the system in to
Thanks all in advance,
M

---

### Post by jtarin on 2010-10-07
Wubi does not require its own partition,AFAIK (didn't when I installed some time ago) it installs within Windows. If you want to install to a separate partition you should install regular Ubuntu however doing that will overwrite your Win7 MBR with Grub2 bootloader which will be used to boot Win and Ubuntu. You should re-evaluate what you want to do before you proceed further.

---

### Post by MilouB on 2010-10-07
Ok, I want to try Ubuntu. I have a newish laptop with so much bloatware that I'm about to reformat and put a clean Win7 install on, so before I do that I want to try it out.

I tried the 'install alongside' option but when I get to the Where do you want to install?' bit it says that installing on my C drive will erase partitions which is not afaik what I want to do!
KI watccxhed a couple of install Wubi videos but they seem to have a slider option of where you want to install Ubuntu, which deos not appear on my installation options. I have a backup but use the laptop constantly, so the prospect of losing it all and spending hours reinstalling does not thrill me, at least until I plan for it and do the whole thing!

---

### Post by mastablasta on 2010-10-07
delete U partition and create a new one again. only this time do not format it.
 
then boot up linux, and install it to largest free dsik space (which will be your unformated partition).

---

### Post by MilouB on 2010-10-07
Thanks for the swift reply, but when doing it that way, the 25gb unformatted partition still doesn't appear, I have 450Gb, and 44Gb in the list. What I don't get on the options is the 'Install side by side' and the slider option at the bottom as on page 17 of the Ubuntu guide linked in an earlier post. Any further suggestions welcome!

---

### Post by mastablasta on 2010-10-07
> **MilouB said:**
> Thanks for the swift reply, but when doing it that way, the 25gb unformatted partition still doesn't appear, 
strange.  You are doing the propper install and not wubi, right? What kind of partition did you create (Primary? Extended?)? it seems installer is not recognising that there is windows 7 already installed.
 
What happens if you go to option erase and use entire disk, can you then select the partition? Also you could try to do manual partitioning. what partitions does it show in that place?
 
> 
I have 450Gb, and 44Gb in the list.
What is the 44GB partition? Swap partition?
 
> 
 What I don't get on the options is the 'Install side by side' and the slider option at the bottom as on page 17 of the Ubuntu guide linked in an earlier post. Any further suggestions welcome!
 Slider option is nice and easy to use, but people reported problems with win7 (it can ruin some files...)

---

### Post by MilouB on 2010-10-07
Uhhh... ok I'll try the non-wubi disk... :oops:

Did I nemtion I was an Ubuntu Noob?

---

### Post by MilouB on 2010-10-07
Ok, I have 10.04.1 Desktop version I thought, but it still has Wubi as the .exe.. I'll look for a different one...
Thanks to all posters for their patience!

---

### Post by MilouB on 2010-10-07
Well, i've looked around a lot and all I can find is desktop version ISO, 10.04.1 32 bit, which still is Wubi.exe. Am I missing something??
ubuntu-10.04.1-desktop-i386.iso is the file.

---

### Post by oldos2er on 2010-10-07
If you want to install Ubuntu to its own partition, you need to boot the LiveCD, not run it from Windows.

---

### Post by mastablasta on 2010-10-07
> **oldos2er said:**
> If you want to install Ubuntu to its own partition, you need to boot the LiveCD, not run it from Windows.

Exactly. You need to go to bios and change the boot order (so that first device is CD) then just put in the cd and boot the computer. sometimes going to bios to change boot order is not necessary. some newer motherboards  give the option (i think you will need to press F12 immediatelly after turning on the computer and it will give you a menu where oyu can choose the first device to boot from)

after you boot from CD, you will get a menu form where you can install or you can just try the system without installing or making any changes to your current OS (note that this will be slow because everything is read form CD)

---

### Post by MilouB on 2010-10-07
Thankyou for that oldOS2er, just tried it. I get exactly the same. no choices, and no 25Gb drive to install to. I'm not inexperienced with PCs, I've been building my own since a P2 175MHz was fast. Maybe something is trying to tell me Ubuntu is not for me. I do get jittery at "Delete all partitions", so maybe I'll wait until I do the full wipe
Thanks to all repondeurs for all the help

---

### Post by Quackers on 2010-10-07
When you get to the disk partitioning part you need to click on the manual one. Then you should see a picture of your disc layout where you can choose the 25GB partition.

---

### Post by bcbc on 2010-10-07
Is the 25gb partition a windows7 dynamic 'disk'? I'm not sure if ubuntu supports those since they are a windows construct.

---

### Post by MilouB on 2010-10-08
It is indeed a RAW dynamic disk, as are all the other partitions. is there a way to un-dynamic it maybe? :)

---

### Post by MilouB on 2010-10-08
Would changing the U: drive to a fixed size VHD do it maybe?

---

### Post by bcbc on 2010-10-08
You can have up to 4 primary partitions. Windows is probably switching to dynamic since you are trying to create a 5th partition.

You don't have any ability to create a new (non-dynamic) partition unless you can delete one of the other existing 4 primary partitions first. And create an extended partition in it's place (after which you can create many logical partitions within it).

If you were trying to install wubi, then you don't need a partition at all - it installs to a virtual disk. The wubi install probably failed because you tried to install it to the dynamic disk (it looks like it's windows that is preventing this) - so just install it to C: and it will probably work fine.

---

### Post by MilouB on 2010-10-09
Ok, tried all that, got to the end of the install and reboot. Looked like it was all going ok, untill the command line came up with all this;

[I]Plymouth stop pre-start Process (488) Terminated with status 2

Filesystem check or mount failed proc/self/fd/8 :20: /sbin/sulogin input/output error

5.709787 Kernel Panic - Not Syncing.

[/I]That's not all that was on screen, but it seemed to be the most relevant bit. It was late....

Thanks for all the patienxce folks..
M

---

