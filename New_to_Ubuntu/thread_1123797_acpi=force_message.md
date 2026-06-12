---
title: "acpi=force message"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by wildsi on 2009-04-12
Hello,

I'm after some help to install Ubuntu please.

I'm trying to run the Ubuntu 8.10 desktop edition live cd. When I re boot with the cd, I get the message:

[0.000000] ACPI, Bios age (1997) fails cut off (2000), acpi=force required to enable ACPI

Loading, please wait.......

Busybox v1.10.2 (Ubuntu 1:1.10.2 1umbuntuu6) buit-in shell (ash)

Enter 'help' for a list of built in commands

(initramfs)_


I have looked at other threads with the same problem. They have suggested trying the ACPI=off option in the f6 main menu or typing /acpi=force at the end of the boot option (again in f6). Neither of these worked (ended up with Busybox).

Is my PC not up to running Ubuntu? I have got a 1.04GHz AMD Duron processer with 632MB of RAM + 20GB hard drive. I'm using Windows XP without any problems at the moment but i am keen to use Ubuntu.


Thanks,

Simon

---

### Post by crf on 2009-04-12
It probably hasn't anything to do with acpi being enabled or disabled that the live-cd loading process ended at busybox (it happened on my dad's Sony Vaio). The Vaio had an usual disk configuration and the CD was attached through the pc-card slot.

And you may be able to install ubuntu linux despite not being able to run the live-cd, except to get to busybox. There is likely no harm in trying to install it. I would use XP to shrink the partition windows in on before hand.

Have you looked on the internet for installing Linux on your computer?

---

### Post by CatKiller on 2009-04-13
It's not /acpi=force. You don't want the / at the start. Just a space between this option and whatever the previous end of the kernel line was. You'll probably also need ACPI enabled in the BIOS for this to work.

---

### Post by wildsi on 2009-04-13
Thanks for the suggestions.

I get the same problem when trying install Ubuntu rather than running the live cd. 

Also, removing the "/" and typing "space" acpi=force at the end of the kernel line didnt work. In the Bios power management setup, APM/ACPI was enabled. I changed this to only ACPI enabled but this did not work either.

Checking my motherboard, it is M810LR by Eagletec (were these made by PC Chips?). The BIOS version is 1.21.06 (American Megatrends). Would updating the BIOS solve the problem? If so is it an easy and safe thing to do?

---

### Post by CatKiller on 2009-04-13
> **wildsi said:**
> Checking my motherboard, it is M810LR by Eagletec (were these made by PC Chips?). The BIOS version is 1.21.06 (American Megatrends). Would updating the BIOS solve the problem? If so is it an easy and safe thing to do?

I don't know that it would help. It's easy enough if you can find the right BIOS for the motherboard; you boot from a disk that has the new image on and a utility to flash the BIOS. It's safe unless you're using the wrong BIOS image, or the process gets interrupted. If the BIOS gets corrupted, you can't boot that motherboard again, unless you remove the chip and solder on a replacement. It doesn't generally go wrong, but if it does go wrong it's pretty catastrophic.

It's also perfectly possible that this is all a red herring, and it's something else that's stopping it from loading properly. That could just be the last message that's displayed before something entirely different stops the boot process.

---

### Post by wildsi on 2009-04-14
Thanks for the tips. I dont fancy messing with the BIOS especially if it probably won't fix the problem. I think I will have to admit defeat.

I might try another Linux distribution. Puppy Linux has caught my attention. Has anyone heard any good reports?


Thanks again for your assistance.


Simon

---

### Post by louieb on 2009-04-14
I have a P2-400, 384mb ram built in 1997. I get the same message about BIOS age. It runs Ubuntu no problem except its slow. I suspect yours boots to the busybox prompt because you did not get a good burn on the CD. All it takes is few twisted bits in the wrong place to give strange results. 

Run the ***check media for defects ***option.

Puppy is great I keep a Puppy CD around for a rescue CD. You just need to try it and see for yourself. Good Luck.

---

### Post by halitech on 2009-04-14
try adding
```
ide=nodma
``` to the boot options

---

### Post by wildsi on 2009-04-15
Hi,

I'll run the check media for defects as you suggest. The cd was bought from [www.8daysaweek.co.uk](www.8daysaweek.co.uk). I might try the cd on my works PC tomorrow (when no one is looking!)

Can I just check I am adding "ide=nodma" in the correct place. The Boot options line is:

file=/cdrom/preseed/ubuntu.seed.boot=casper initrd=/casper/initrd.gz quiet splash -- 

There is a space at the end of --. I have just typed ide=nodma after the end space. Is this correct?

---

### Post by halitech on 2009-04-15
I do believe, been awhile since I've added it and the -- should stay in place

---

### Post by wildsi on 2009-04-15
I have just tried the check cd for defects. I ended up with the busybox.

Trying ide=nodma also ended up with busybox.

I'll let you know what happens on the works PC....

---

### Post by sidcypher on 2009-04-16
I am having this issue as well, with a server install of 8.1.

It is like a 8meg nvidia card from before back in the day, 13.6gig drive, AMD k6-400mhz 256meg ram..*edit video ram

the install still worked, also it boots, however after all the usually Bios stuff, the video goes WAY crazy and is like stretched past the bottom of the screen where no amount of adjustment get me fixed, followed this "[guide]("http://www.howtoforge.com/perfect-server-ubuntu-8.10-ispconfig-3-p3")"  Will try the acpi=force thing, fixing to reinstall, cause I trying to login from 8.1 desktop through puTTY, that is a whole different not working either story..

my system too old? basically it is just a test box for like very simple www host, email server. really simple, small usage, a practice box if you will.

reinstalled, had internet issues, however puTTY works now, got internet fixed..still no go on the ACPI errors, is there anyway I can capture the weird boot up stuff to ask about..also giving me I/O errors after the ACPI errors, i could capture the info through puTTY but can't get the boot stuff. way new to the server side.

---

### Post by wildsi on 2009-04-18
I'm up and running with Puppy Linux. I rebooted with the puppy live cd and everything worked a treat. Its somewhat faster than Windows XP!

There must be a bug with Ubuntu and my M810 motherboard (should I report it?)

---

### Post by gn2 on 2009-04-18
The 2000 BIOS cut-off can sometimes be worked around by pressing F6 at the Live CD splash screen and typing: acpi=off

---

### Post by wildsi on 2009-04-21
Hi,

I've just tried the ACPI=off trick. It didnt work I'm afraid, I just ended up with busybox.

Thanks anyway

---

