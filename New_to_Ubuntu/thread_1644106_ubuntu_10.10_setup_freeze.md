---
title: "ubuntu 10.10 setup freeze"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by pax888 on 2010-12-12
hello ubuntu community,

i tried to install ubuntu 10.10 but after my pc boots from the cd, after 1 minute of loading ubuntu setup it freezes, two leds blink from my keyboard and then it reboots. sometimes it finishes loading and it shows me the install or try screen, sometimes it passes this screen, it starts installing but after a while it freezes with blinking keyboard leds and reboots. it burnt 9 cds, i formated my hdd 5 times, i tried 4 cdroms, 2 hdds, i used different burning software and cds, i removed all my pci cards excluding the nvidia 8600 gts because i dont have integrated graphics on my motherboard, i vacumed my pc for dust, but still it freezes at the white-red-moving-bullets-ubuntu screen with 2 keyboard leds blinking. i am disperate. help me, whats the problem ?

i have 1 gb ddr2, intel dual core 1.86, 500gb hdd, nvidia 8600 gts 256mb

i burnt the 32 bit version

---

### Post by overdrank on 2010-12-12
Hi and welcome, Moved to Absolute Beginner Talk :)

---

### Post by pax888 on 2010-12-12
sorry to tell but this should be moved to main support, not to absolute beginner cause im not retarded. it's a problem not caused by me. i need real answers.

thanks.

---

### Post by amjjawad on 2010-12-12
> **pax888 said:**
> sorry to tell but this should be moved to main support, not to absolute beginner cause im not retarded. it's a problem not caused by me. i need real answers.

thanks.

The thread has been moved not because you're retarded but because the problem itself (the thread) belongs to here, period.

Don't feel bad, your problem will be fixed hopefully shortly ;)

---

### Post by amjjawad on 2010-12-12
> **pax888 said:**
> hello ubuntu community,

i tried to install ubuntu 10.10 but after my pc boots from the cd, after 1 minute of loading ubuntu setup it freezes, two leds blink from my keyboard and then it reboots. sometimes it finishes loading and it shows me the install or try screen, sometimes it passes this screen, it starts installing but after a while it freezes with blinking keyboard leds and reboots. it burnt 9 cds, i formated my hdd 5 times, i tried 4 cdroms, 2 hdds, i used different burning software and cds, i removed all my pci cards excluding the nvidia 8600 gts because i dont have integrated graphics on my motherboard, i vacumed my pc for dust, but still it freezes at the white-red-moving-bullets-ubuntu screen with 2 keyboard leds blinking. i am disperate. help me, whats the problem ?

i have 1 gb ddr2, intel dual core 1.86, 500gb hdd, nvidia 8600 gts 256mb

i burnt the 32 bit version

WOW, you have tired lots of things indeed. However, they are some other stuff that you might or might not tried yet:

1) Did you check [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") after downloading? 

You'll need this: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)


2) Did you try to create a [LiveUSB]("http://www.ubuntu.com/desktop/get-ubuntu/download") instead of LiveCD?

3) Did you search google or this forum for a similar issue? some users had problems with nvidia card.

---

### Post by Zzl1xndd on 2010-12-12
You might try the Alternate Installer as well.

During the years there has been a few times the live installer wouldn't work for me but the Alternate has always got the job done.

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

---

### Post by pax888 on 2010-12-13
@ amjj : i checked the checksum and it's ok and my pc doesen't boot from the usb device. also i searched google but no luck.

@ tweak : i'll give it a try. hope that will do the job.

---

### Post by Supergoo on 2010-12-13
Just another idea, do you have a friend that could make you a cd from another computer, just to rule out a problem with your cd writer ?

---

### Post by plux on 2010-12-13
Sounds like a hardware problem to me. Try running memtest from the live cd.

---

### Post by amjjawad on 2010-12-13
> **pax888 said:**
> @ amjj : i checked the checksum and it's ok and my pc doesen't boot from the usb device. also i searched google but no luck.

Last night, and for the first time for me since I've started to use Linux, I tried to install Ubuntu 10.10 on my PC1 (check my signature for specifications) and I got an error message in the middle of the installation (see attached).
So, I decided to wait until this morning and try again with a LiveUSB.
Yes, I know your machine doesn't support booting from USB but guess what? you still could do it. Check[ this]("http://blog.brothersoft.com/2008/12/09/boot-computer-from-usb-or-cdrom-even-if-bios-not-supported-using-plop/"). 

As someone already mentioned, try to burn the CD at another machine just to narrow down the problem and find out what's causing the issue?.

I've seen lots of posts where users were unable to install or run smoothly due to their Graphics Card (nvidia). 

Also, someone suggested to run the memtest. Yeah, try to do that as well.

Don't lose hope :)

---

### Post by pax888 on 2010-12-14
Because i have not lost hope, now I'm trying to boot ubuntu from USB. I started a thread here : use floppy to boot usb [http://ubuntuforums.org/showthread.php?t=1645434](http://ubuntuforums.org/showthread.php?t=1645434)

---

