---
title: "So close, yet so far...."
date: 2009-03-04
forum: New to Ubuntu
---

### Post by js@lloyd on 2009-03-04
After installing 8.10 on the manual install, i was not able to boot up XP which was on a seperate partition. This thread has most of the info [http://ubuntuforums.org/showthread.php?t=1086112](http://ubuntuforums.org/showthread.php?t=1086112)
With lots of help, I edited my Grub menu and added the following,

title		Microsoft Windows XP Professional
root		(hd0,4)
savedefault
makeactive
chainloader	+1

I can now see Windows in the menu after hittting Esc when booting up. However, after I select it and press enter, i get the following:

Error 12: Invalid device requested
Press any key to continue

After pressing any key, it reverts me back to the selection menu...Ubuntu generic, recover mode, memtest 86+ and XP Professional.  Now, I'm actually running XP Home Edition, so I don't know if that's a problem.  

In case you need to see sudo fdisk -l,  here are the results:
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb5feb5f

Device Boot Start End Blocks Id System
/dev/sda2 * 1 14593 117218241 f W95 Ext'd (LBA)
/dev/sda5 5743 14593 71095626 7 HPFS/NTFS
/dev/sda6 1 249 1999998 82 Linux swap / Solaris
/dev/sda7 250 5742 44122491 83 Linux

Thanks for the continued help in my quest.

---

### Post by stchman on 2009-03-04
Ubuntu install will detect your Windows partition and make an entry in GRUB.  No need to edit GRUB.

---

### Post by js@lloyd on 2009-03-04
That's the problem that we've been working on. Apparently, it didn't or something else is wrong.

---

### Post by kansasnoob on 2009-03-04
This:

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb5feb5f

Device Boot Start End Blocks Id System
/dev/sda2 * 1 14593 117218241 f W95 Ext'd (LBA)
/dev/sda5 5743 14593 71095626 7 HPFS/NTFS
/dev/sda6 1 249 1999998 82 Linux swap / Solaris
/dev/sda7 250 5742 44122491 83 Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$

(I took that from your previous post) looks like Windows is in an extended partition. In fact it looks like everything is!

Could you post a screenshot of gparted? Since you can boot into Ubuntu, just go to terminal and:

```
sudo apt-get install gparted
```

After it's installed go to System > Admin > Partition Editor (don't change anything - we're just looking) then look in Accessories and you'll see the screen-shot program.

You can attach it using the "paper clip thingy" at the top of these post pages.

---

### Post by mlentink on 2009-03-04
I'm only thinking out loud here:
If I look at the output of your fdisk -l it shows only extended partitions, no primary ones. (no sda1, sda3 , sda4. Normally, you would first fill up your maximum of 4 primary partitions before needing an extended one) I really don't know, but does windows insist on its boot record being on a primary partition? If so, that would explain the error-message you got. 

Aren't there any GRUB/boot gurus around here? Wish I could help you more, but I just got intrigued by your fdisk -l output, the partition table.

Perhaps a route would be to fire up your box with your XP-cd, do a fixmbr, and then after that do a GRUB reinstall (there's plenty of howtos on this forum on how to do that).

Sorry not to be of more help..

---

### Post by js@lloyd on 2009-03-04
Unfortunately, it appears that I don't have an internet connection to install gparted.  It was working the 1st day that I installed it, but hasn't been for the last couple of days.  Any other way to install it?

---

### Post by mlentink on 2009-03-04
You should not have to install it. 
Take a look at System>Administration>Partition Manager

Afterthought: if you don't hav an internet connection, how could you post?

---

### Post by MarblePanther on 2009-03-04
> **mlentink said:**
> You should not have to install it. 
Take a look at System>Administration>Partition Manager

Afterthought: if you don't hav an internet connection, how could you post?

This changed starting with Hardy, I believe (or perhaps it was Intrepid)--gparted gets uninstalled along with the Ubiquity Installer after installation is complete.  Parted is left, but GParted gets removed for some ridiculous reason.

---

### Post by kansasnoob on 2009-03-04
> **js@lloyd said:**
> Unfortunately, it appears that I don't have an internet connection to install gparted.  It was working the 1st day that I installed it, but hasn't been for the last couple of days.  Any other way to install it?

Yes. It's on the Live CD that I'd think you installed with. If you insert the CD and then go to Syatem > Administration > Software sources and tick the option to install from CD you should be able to install gparted .................. but, why no internet?

It sounds to me like you have a real mess!

I'll message someone else that's better at this than I, but I need a gui pic to see what we're dealing with! If it's a total mess then I think it's better to just start over and get it right.

---

### Post by js@lloyd on 2009-03-04
I don't have the Partition Manager Option under System/Admin. I'm on another computer that is working....my desktop which i installed on isn't working.

---

### Post by mlentink on 2009-03-04
> **MarblePanther said:**
> This changed starting with Hardy, I believe (or perhaps it was Intrepid)--gparted gets uninstalled along with the Ubiquity Installer after installation is complete.  Parted is left, but GParted gets removed for some ridiculous reason.


Dunno, I jus' work here after ol' massa done freed us slaves.

But on my intrepid, it's just there.

---

### Post by gletob on 2009-03-04
Could you change your grub entry to 

```
title Microsoft Windows XP Professional
root (hd0,2)
savedefault
makeactive
chainloader +1
```

and see what happens

---

### Post by djbushido on 2009-03-04
Yeah, gparted gets removed. 2 questions then:
Are you really booting ubuntu? because the "bootable" partition is set to the Windows.
Second, have you tried changing to trying to boot the extended partition, not the actual partition? I.e., boot sda2 not sda5 (hd0,1) and (hd0,4) respectively.

EDIT: Sorry, someone else posted the info before I did. Sorry.

---

### Post by kansasnoob on 2009-03-04
You could also boot the Live CD and post a screenshot using Partition Editor from that! (May have to use something like Photobucket)

And if you've not been using the Live CD to try and make the suggested changes that's a large part of the problem!

But, honestly, I don't know how to "see" the full layout of a system without a gui! I can see the partition layout - but not how much used and/or free space ther is on each partition.

And Gparted is just so cool! One picture shows it all!

---

### Post by kansasnoob on 2009-03-04
> **mlentink said:**
> Dunno, I jus' work here after ol' massa done freed us slaves.

But on my intrepid, it's just there.

Must be magic! In Gutsy gparted was installed by default. It has not been in either Hardy or Intrepid!

---

### Post by mlentink on 2009-03-04
> **kansasnoob said:**
> Must be magic! In Gutsy gparted was installed by default. It has not been in either Hardy or Intrepid!


Sure.
Well, nuttin' to do with OP's problem, don't it... 

;-)

---

### Post by kansasnoob on 2009-03-04
> **mlentink said:**
> Sure.
Well, nuttin' to do with OP's problem, don't it... 

;-)

No. I have messaged two of the top guru's to ask for help.

My point with gparted anyway is that I'm a gui guy! I can tell a lot from a picture! Not everything ............ but a lot!

As my moniker indicates I'm still a nOOb!

Still learning:)

---

### Post by mlentink on 2009-03-04
> **kansasnoob said:**
> 
As my moniker indicates I'm still a nOOb!

Still learning:)


Ain't we all man, ain't we all...


but it ***is*** fun, isn't it!

---

### Post by meierfra. on 2009-03-04
Did you deleted any partitions while installing Ubuntu?   Windows XP always puts the boot files on an primary partition, but since you do not have any primary partition (except for the extended partition /dev/sda2) it usually means that the boot files got deleted. 

To fix your problem use the following  HowTO:

[http://ubuntuforums.org/showthread.php?t=813628]("http://ubuntuforums.org/showthread.php?t=813628")

---

### Post by js@lloyd on 2009-03-04
Sorry for the long delay.  Here's a screen shot using the Live CD.

---

### Post by js@lloyd on 2009-03-04
> **djbushido said:**
> Yeah, gparted gets removed. 2 questions then:
Are you really booting ubuntu? because the "bootable" partition is set to the Windows.
Second, have you tried changing to trying to boot the extended partition, not the actual partition? I.e., boot sda2 not sda5 (hd0,1) and (hd0,4) respectively.

EDIT: Sorry, someone else posted the info before I did. Sorry.

I've been booting from ubunto. No, i have not tried changing to boot from the extended partition. I'm afraid I require almost step by step instructions due to my minimal knowledge of ubuntu.

---

### Post by js@lloyd on 2009-03-05
I'm thinking about just trying this all over again with a fresh install.  Since, I don't have the ability to boot into XP, can anyone tell me how to remove the current version of ubuntu?  Can I do it booting through the Live CD?  Another option is to wipe the HD and start really fresh.  I do know how to do that.  Thanks for the help

---

