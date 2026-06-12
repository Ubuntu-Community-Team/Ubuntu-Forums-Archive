---
title: "MTRR: CPU 0: SYSCFG[MtrrFixDramModEn] not cleared by BIOS"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by captain_rob on 2009-04-30
I am a newbie. I made a clear install Ubuntu 9.04 64. At start up I get a strange message, which I have not seen under 8.04:

[Firmware Warn]: MTRR: CPU 0: SYSCFG[MtrrFixDramModEn] not cleared by BIOS, clearing this bit

What does this mean and what to do about it?

---

### Post by jamey0824 on 2009-05-23
yeah i get this too, it shows on screen during boot, and is in kern.log.  It onlys shows on my screen boot when I enable surrondview( ati integrated graphics and a secondary graphics card.  But it might happen when its disabled ,and it just doesn't post it to screen

---

### Post by gnigamica on 2009-05-23
I am experiencing the same issue.  This seems to be post-Grub, during startup.  I did not see it on earlier versions of Ubuntu.  Any way to suppress these warnings?  I already have quiet boot set in grub... this does not appear to be grub related.

---

### Post by C. M .Hughes on 2009-06-09
I too have the same problem. My system still boots fine, but I wonder if there is anything I can do about it. Any advice would be greatly appreciated.

---

### Post by C. M .Hughes on 2009-06-10
Hi all,
Myself and some others have received the above message immediately after GRUB and before the Ubuntu splash screen. We have a thread going here:

[http://ubuntuforums.org/showthread.php?t=1143681](http://ubuntuforums.org/showthread.php?t=1143681)

but so far no suggestions have come. If anyone has any, I'd love to hear them! Thanks for your time.

---

### Post by sdennie on 2009-06-10
Merged this thread and the original thread.

My guess is the problem is that your motherboard/BIOS doesn't correctly support using MTRRs.  You should be able to disable the message by booting with nomtrr.  An example of how to change boot options can be found here: [https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation).  Both temporary and permanent instructions are given.

---

### Post by C. M .Hughes on 2009-06-10
sdennie,
Thanks for your time on this. At present, the entry that I boot from in menu.lst looks like this:

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		9a3ea422-4178-4359-9195-a69120ea5f87
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9a3ea422-4178-4359-9195-a69120ea5f87 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

From the reading I have done, is it true that I should try changing the kernel line to:

kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9a3ea422-4178-4359-9195-a69120ea5f87 ro quiet splash, nomtrr

---

### Post by sdennie on 2009-06-10
> **C. M .Hughes said:**
> sdennie,
Thanks for your time on this. At present, the entry that I boot from in menu.lst looks like this:

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		9a3ea422-4178-4359-9195-a69120ea5f87
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9a3ea422-4178-4359-9195-a69120ea5f87 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

From the reading I have done, is it true that I should try changing the kernel line to:

kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9a3ea422-4178-4359-9195-a69120ea5f87 ro quiet splash, nomtrr

You shouldn't need the comma actually.  Try:

```

kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9a3ea422-4178-4359-9195-a69120ea5f87 ro quiet splash nomtrr

```

---

### Post by C. M .Hughes on 2009-06-10
Hi sdennie,
I tried it as you suggested, but I still get the same messages. Do you have any other suggestions?

Thank you for your time.

---

### Post by C. M .Hughes on 2009-06-10
I tried something else which also hasn't worked. I went into

/etc/X11/xorg.conf

and made this bit

Section "Device"
	Identifier	"Configured Video Device"
EndSection

look like:

Section "Device"
	Identifier	"Configured Video Device"
        Option "NoMTRR"
EndSection

Still no luck...

---

### Post by C. M .Hughes on 2009-07-05
bump

---

### Post by m13p on 2009-07-24
While installing Ubuntu 9.04 in my acer 5050 laptop, i got the following problem....



[ 0.382240] ACPI: Aborted because broken padding
[ 0.436001]{Firmware Warn]:MTRR:CPU 0:SYSCFG[MtrrFixDramModEn]not cleared by BIOS, clearing this bit
[ 3.914977]crc error
[3.9612081]kernel panic-not syncing:VFS:Unable to mount root fs on unknown-block(104,1)


what is the cause ?
right now i dont have any operating system installed in it...
please help...
thanks

---

### Post by LewRockwell on 2009-07-24
> **m13p said:**
> While installing Ubuntu 9.04 in my acer 5050 laptop, i got the following problem....



[ 0.382240] ACPI: Aborted because broken padding
[ 0.436001]{Firmware Warn]:MTRR:CPU 0:SYSCFG[MtrrFixDramModEn]not cleared by BIOS, clearing this bit
[ 3.914977]crc error
[3.9612081]kernel panic-not syncing:VFS:Unable to mount root fs on unknown-block(104,1)


what is the cause ?
right now i dont have any operating system installed in it...
please help...
thanks

does your laptop have the latest BIOS?

[http://support.acer-euro.com/drivers/notebook/as_5050.html](http://support.acer-euro.com/drivers/notebook/as_5050.html)

.

---

### Post by DarkenSX on 2009-08-12
Im getting the same message with my dell inspiron 1526 laptop running ubuntu 8.04 with the latest dell bios which is A15. Any idea Whats Causing it Since Bios version is not the issue.
My Specs:
Dell Inspiron 1526
CPU: AMD Sempron Single Core 3600+ 2.0Ghz 32-Bit
RAM: 2GB Installed Can handle up to 4GB
Org. OS: Win Vista Home Basic
Curr. OS: Ubuntu 8.04 LTS
Video: ATI Radeon X1270
Sound: Sigmatel Stac 9228

---

### Post by isa saids on 2013-04-30
> **LewRockwell said:**
> does your laptop have the latest BIOS?

[http://support.acer-euro.com/drivers/notebook/as_5050.html](http://support.acer-euro.com/drivers/notebook/as_5050.html)

.

I have same problem, thank you for the link. I have already updated bios to newer but still the same, it might another way I could solve that problem?. But thank you thats helpful

---

### Post by Bucky Ball on 2013-04-30
[B][U][U][I]Thread Closed

Reason: [/I][/U][/U][/B]Necromancy. Old thread put to bed.

If a thread has seen no action for around a year or more please post a new thread in the relevant sub-forum with a descriptive title and  info pertinent to your problem rather than resurrecting a three and a half year old thread. You stand minimal chance of getting help doing this. Also, things can (and do) change radically in computers in that time. 

A new thread will greatly increase your chances of help. Good luck.

---

