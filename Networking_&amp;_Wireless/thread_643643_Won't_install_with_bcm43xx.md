---
title: "Won't install with bcm43xx"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by aartz101 on 2007-12-18
I can't get 7.1 to install at all. After booting from CD and trying the install or live boot methods it starts to go thru the usual kernel boot stuff then comes up with:

bcm43xx: Error: Microcode blah blah

It repeats this forever (well, I've waiting about 1/2hr anyway).

I've found TONS of posts about how to fix this AFTER Ubuntu is installed. How do I get it to actually install so I can perform the fixes?? There is probably a simple boot switch I can use, but I have been going nuts trying to find a list of boot options.

Thanks in advance!

---

### Post by csat on 2007-12-18
Just go this site  [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)  

Then download and install WICD.  [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)  

Follow directions made for Ubuntu when download it.

Return here to say SOLVED because, for sure, it will do it for you.

Good luck

---

### Post by Ardrias on 2007-12-18
Boot with --noapic or acpi=off

That works for me to get it installed etc, then you can follow the above tip. I wasted way too many hours trying to get my bcm43xx working tho, and just gave up in the end. At least now I'll never buy another laptop for me or my company that uses that chipset. Lesson learned.

---

### Post by aartz101 on 2007-12-18
No luck. The boot options read:

file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --

I add --noapic, acpi=off, pci=noacpi, etc etc and it makes no difference.

Can you specify exactly what the install boot options should look like for this to work?

Thanks for the help!

---

### Post by aartz101 on 2007-12-21
Its been a few days of playing around trying to get the install to kick past the bcm43xx error, still no luck. I've given up and installed Windoze XP so I can get the laptop working, its a sad day for me....

If anyone has a solution, or simply a way to force the installer past this problem please post it. I would love to set up a dual boot using Ubuntu.

---

