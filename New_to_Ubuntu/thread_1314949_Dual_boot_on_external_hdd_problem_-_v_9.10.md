---
title: "Dual boot on external hdd problem - v 9.10"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by lewisdeane on 2009-11-04
Hi all,
Took the plunge and clean installed ubuntu 9.10 to my prepartitioned external maxter hdd and, with the hd plugged in, everything works swimmingly - except - when the external drive is unplugged I can't boot into xp but just get:

GRUB loading
error: no such disk
grub rescue>

Now obviously grub boot loader is looking for the external disk in order to load itself properly but then I can't use my lapttop as a laptop!
Is there any simple procedure to get round this?
Note: my only familiarity with linux was with xebian when I modded an xbox ie sometime ago and I tend to forget anything I don't use!
Anyway if anyone can help I'd much appreciate it,
Lewis
PS I forgot to say I have a HP compaq nc2400 with xp professional sp3.

---

### Post by synicalx on 2009-11-04
When you first boot up and you get the HP logo or something similar, you'll be prompted to hit one of your function keys (normally F11) to go into a boot menu. Go into that when prompted and select you laptop's local HDD as the primary boot drive ;)

---

### Post by lewisdeane on 2009-11-04
Thanks for the quick reply.
I tried that ( with mine it's f9 ) but I just got the same message as above. It's seems grub2 overwrites the windows mbr directing it to the grub package, which as I say, is on the external hard drive. I could quite easily fix that from the xp side but then I would almost definitely loose the ability to boot into ubuntu. Hence my problem: 
There must be a way to re-install grub on the internal hdd, without uninstalling ubuntu as it is, and then be able to boot both os's and, specifically xp *without* the external hdd, no? 
From the windows side, when I go into msconfig, I have 'selective startup' rather than 'normal startup'. In the bios the boot order has not been changed and I was thinking if I moved the internal hdd up that might do the trick. But not if the mbr is grub modified?

---

### Post by lewisdeane on 2009-11-04
I've just been looking at the Super Grub Disk homepage and, if I can get a handle on it, I think it might just be the solution. Post if it is!

---

### Post by synicalx on 2009-11-04
Wow that is an odd sort of predicament!

If the internal HDD is the first boot option under BIOS there's no reason why it shoudln't boot into that. Try reinstalling GRUB with [this guide]("http://www.ubuntugeek.com/how-to-restore-grub-boot-loader-after-installing-windows.html") and see if you have any luck.

---

### Post by lewisdeane on 2009-11-04
Thanks but that assumes that I've installed windows after ubuntu rather than the other way round. The grub4dos, however, might be another way - I'm only acting when I'm pretty sure what I'm doing!

---

### Post by lewisdeane on 2009-11-04
Or, rather, if I restore the original windows mbr ( either fx mbr or re-imaging with ghost), the guide you pointed to would be the right one.

---

### Post by synicalx on 2009-11-04
> **lewisdeane said:**
> Thanks but that assumes that I've installed windows after ubuntu rather than the other way round. The grub4dos, however, might be another way - I'm only acting when I'm pretty sure what I'm doing!

Ah my mistake, for some odd reason I had it in my head that you'd re-installed Windows #-o, must have been another thread I was reading or something...

Anyways, you might be inclined to wait for someone with a bit more experience with Grub than myself - if Ubuntu was installed on an external I can't see any reason why it should overwrite/overrule MBR with GRUB.

Might be worth your while trying one of the Ubuntu IRC channels to so if anyone can help you directly?

---

### Post by lewisdeane on 2009-11-05
Well, i have found a temporary solution: by burning Super Grub Disk SGD2 ( which is just really a diskette of grub 2.0 ) I can boot into xp with it. It just means I have to carry that around when I'm not at home!

---

### Post by lewisdeane on 2009-11-05
Flip that, as they say in Heat, I did a fixmbr in Windows recovery console and, now, I can boot into my laptop as normal and boot into ubuntu with the SGD2 cd as well. So three quarters of the way there and with AutoSuperGrub I'll probably be all the way there. But, heck, booting into ubuntu with the disk seems no slower than before with the normal grub process so I don@t know if I'll bother pushing it further, for now. Anyaway, thanks for the help out - I can now go to sleep!

---

### Post by MeerkatBKK on 2009-11-05
Hi from another Newbie.

Just to say you're not alone - I'm having exactly the same issue with Karmic on an external drive and XP on the laptop internal one. Supergrub not much use to me either as the CD drive is external too. My lappie is slowly morphing into a desktop! (Aside from this niggle my first taste of Linux has been painless.)

Will post here if I find anything out from elsewhere.

Good luck,
Nick

---

### Post by lewisdeane on 2009-11-05
Hi Nick
If you look at the super grub disk home page they have an auto super grub exe, as well, which I think does much the same as the disk but you install it via windows. 
So, in theory one could boot from a windows disk, launch the recovery console ( press 'r' at the prompt ) and then use the fixmbr command  to restore the normal windows boot procedure, as I did. After that, reboot into windows, launch the exe file and you would be able theoretically to boot normally into windows when your away from your external drive and boot into either os when it's plugged in.
But I stress read all the necessary documtation first - there's a wiki for the windows installer, as well.
Anyway, good luck and tell us what solution you found!

---

### Post by lewisdeane on 2009-11-05
But, of course, how can you use a windows disk without being able to use a cdrom.Doh! To little sleep on my part. But the auto super grub exe may just work anyway?

---

### Post by MeerkatBKK on 2009-11-05
Ah well your idea still had merit if I could find a free USB dongle around to use instead of the CD. And cheers for the moral support anyway!

What worries me about SGD though is that whilst this page:

[Link]("http://www.supergrubdisk.org/w/index.php5?title=GrubOnRemovableExternalHardDisk")

implies it can be done, one of the follow-up pages:

[Link]("http://www.supergrubdisk.org/w/index.php5?title=Howto_Boot_Grub_from_windows#GRUB2_solution_.28on_its_own.29")

raises doubts about doing it under Grub2.

Hmm...my turn for shut-eye and will revisit the problem tomorrow. I might try and roll back to Grub 0.97 and work from there.

Cheers,
Nick

---

### Post by Jacdeb6009 on 2009-11-05
Hi,

I have done this to myself twice, and will probably do it again :)

The problem (if I understand what you have done correctly) is that you installed Ubuntu on an external drive, with Windows on an internal drive.  Problem is that when you do this, there is a little tick box somewhere in the disk setup (which partition to use, etc.) that tells Ubuntu where to install GRUB. If you are not careful, it gets installed on your external drive and the rest is history.  Can only boot with the external drive connected.

The solution is rather simple.  You need to re-install GRUB and tell it where things are.

The following has worked for me on both occasions.

In a terminal type:

```
~$ sudo grub
```This will start GRUB with its own prompt.  Then in GRUB type:

```
grub>find /boot/grub/stage1
```This will return a location such as hd(0,5). If you have more than one, select the installation that you want to provide the grub files.  Then type

```
grub>root (hd?,?)
```where ?,? is replaced with the values from the find command.

Next enter the command to install grub to the mbr

```
grub>setup (hd0)
```Finally exit the grub shell

```
grub>quit
```That is it. Grub will be installed to the mbr.

Remember that grub and Ubuntu deal with drive and partition numbering in different ways, as follows:

GRUB refers to drives as 0,1,2,3, etc.

Linux refers to drives as sda, sdb, sdc, etc.
(can also be hda, hdb and so on).

GRUB numbers partitions starting at 0 while Linux starts at 1

Thus for Grub hd (0,5) would be sda6 for Linux

To check the partitions and drives (if you are not sure what it what), you can boot Ubuntu and run GParted.  This will show you the detailed partitioning information for all drives that are connected to the machine.  Take care not to change anything while running the partition editor as this will be disastrous.

There are a couple of threads that probably explain this whole process better than I do but to be honest, I cannot find the one from which I got the original information.

Oh, BTW, one other thing, having done this, you may well have to change /boot/grub/menu.lst as this may get messed up in the process.

As an aside, there are (in addition to your LiveCD) two other very useful tools that you should have.  The one is SuperGRUB for when things go totally belly up, the other is a Live GParted disc.

Hope this helps and good luck!!

---

### Post by MeerkatBKK on 2009-11-06
Hi Jac,

Thanks for taking the time to try and help us out.

I'm a bit confused though as from what I've read about Grub2 (which the OP and I are trying to set up) on [this page]("https://wiki.ubuntu.com/Grub2"), menu.lst has been superceded by grub.cfg, and now uses a different syntax. Also the issue of partitions having different numbers from Linux seems to have changed, ie Grub2 recognizes the first partition as 1, instead of 0 as in Grub 0.97.

So before I follow your instructions, could I just confirm with you that your method would also work for Grub2 please (newbie flag waving!).

Many thanks again,
Nick

---

### Post by yanceypd on 2009-11-06
The folks here will probably come up with a code solution for you but meantime you might be able to fix your windows MBR then Using a live CD install grub to the USB drive and boot select from bios.  Might be too much trouble but would probably work.

---

### Post by mikechant on 2009-11-06
There's a program called EasyBCD for windows which should enable you to set an option for the Windows boot loader to boot Linux on the external drive if you select it, but otherwise to default to loading Windows. Sounds like this is the sort of thing you want in a case where you have no Linux partitions on your internal drive.

---

### Post by kansasnoob on 2009-11-06
First of all the right way to have done this to begin with;

[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/)

Other "flavors" also available there.

But as far as "fixing" things **in general terms**:

(1)Set BIOS so it tries to boot from CD, then USB, then hard drive.

(2)Restore Windows MBR (varies with version of Win).

(3)Restore GRUB to the mbr of the external drive. The method will vary greatly. If you can get the external drive to boot somehow as the OP did you can just work from that *buntu, in some cases you may have to work from a live desktop (that is from the Live CD).

Then you must see how *buntu recognizes the drives/partitions. This can usually be accomplished just by running "sudo fdisk -l" (BTW that's a lower case L). 

You must also see what version of grub you have by running "grub-install -v". Legacy grub (aka: grub) is 0.97 whereas grub2 (aka: grub-pc) is 1.97+.

Then make sure that you install grub to the mbr of the external drive **not the mbr of the Win drive**!

General instructions for legacy grub:

[http://members.iinet.net.au/~herman546/p15.html#Re-install_Grub_with_Live_CD](http://members.iinet.net.au/~herman546/p15.html#Re-install_Grub_with_Live_CD)

Note: you must do the "sudo grub-install /dev/sd**[COLOR="Red"]X[/COLOR]**" where **[COLOR="Red"]X[/COLOR]** indicates the *buntu drive and then also run thru the typical legacy grub setup procedure in a grub shell:

> sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

General instructions for grub2:

If you were able to somehow boot the  *buntu drive just determine which drive *buntu is on then run "sudo grub-install /dev/sd**[COLOR="Red"]X[/COLOR]**" where **[COLOR="Red"]X[/COLOR]** is the *buntu drive, and then "sudo update-grub".

If you are unable to boot your *buntu drive then you'll have to do those same two steps using the Live CD to mount and chroot the *buntu /root partition as described here:

[http://www.openpeta.com/index.php/how-to-recover-ubuntu-grub-after-windows-installation/](http://www.openpeta.com/index.php/how-to-recover-ubuntu-grub-after-windows-installation/)

Clear as mud? If you have any doubts ask more questions!

The end result should be that on boot BIOS will look for it's boot orders from CD, then USB, then the internal hard drive. So if no CD or USB is inserted the BIOS will just slide by to the Win MBR, but if a USB drive is plugged in it will see that MBR and boot that drive.

---

### Post by Jacdeb6009 on 2009-11-15
Hi guys,

Sorry, I was out of town for a couple of days.

Yes, the fix I posted will work for GRUB, but not for GRUB2, sorry, missed that one.

Hope that you manage to get it sorted!!

---

### Post by yanceypd on 2009-11-15
I think someone in an earlier post. Had Grub only installed on external drive.  Fixed MBR of Windows.  Then set bios to boot to usb device first.  If usb wasn't installed it boot to second device (Hard drive).  This would require rebooting to use External drive but probably be a safe solution.

---

### Post by lewisdeane on 2009-11-21
That's a nice idea but if you mean me, as I think you do, I'm still depending on the super grub disk to boot into the second hard drive. I.e., I haven't yet squared the circle of installing grub on my *windows [I] disk, so I can boot into it *with grub[/I] but when I'm away from the external hdd. Hence my solution was to allow windows to re-write the mbr and, when I want to use ubuntu, use the SGD cd.If anyone can tell me how to get around this I'd be gratefull.

---

### Post by lewisdeane on 2009-11-21
I think your right and that is the solution. Problem is I became so afeared of losing windows, as I have done three times, that for the moment I'll depend on the disk! Thanks, anyway!

> **Jacdeb6009 said:**
> Hi,

I have done this to myself twice, and will probably do it again :)

The problem (if I understand what you have done correctly) is that you installed Ubuntu on an external drive, with Windows on an internal drive.  Problem is that when you do this, there is a little tick box somewhere in the disk setup (which partition to use, etc.) that tells Ubuntu where to install GRUB. If you are not careful, it gets installed on your external drive and the rest is history.  Can only boot with the external drive connected.

The solution is rather simple.  You need to re-install GRUB and tell it where things are.

The following has worked for me on both occasions.

In a terminal type:

```
~$ sudo grub
```This will start GRUB with its own prompt.  Then in GRUB type:

```
grub>find /boot/grub/stage1
```This will return a location such as hd(0,5). If you have more than one, select the installation that you want to provide the grub files.  Then type

```
grub>root (hd?,?)
```where ?,? is replaced with the values from the find command.

Next enter the command to install grub to the mbr

```
grub>setup (hd0)
```Finally exit the grub shell

```
grub>quit
```That is it. Grub will be installed to the mbr.

Remember that grub and Ubuntu deal with drive and partition numbering in different ways, as follows:

GRUB refers to drives as 0,1,2,3, etc.

Linux refers to drives as sda, sdb, sdc, etc.
(can also be hda, hdb and so on).

GRUB numbers partitions starting at 0 while Linux starts at 1

Thus for Grub hd (0,5) would be sda6 for Linux

To check the partitions and drives (if you are not sure what it what), you can boot Ubuntu and run GParted.  This will show you the detailed partitioning information for all drives that are connected to the machine.  Take care not to change anything while running the partition editor as this will be disastrous.

There are a couple of threads that probably explain this whole process better than I do but to be honest, I cannot find the one from which I got the original information.

Oh, BTW, one other thing, having done this, you may well have to change /boot/grub/menu.lst as this may get messed up in the process.

As an aside, there are (in addition to your LiveCD) two other very useful tools that you should have.  The one is SuperGRUB for when things go totally belly up, the other is a Live GParted disc.

Hope this helps and good luck!!

---

