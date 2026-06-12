---
title: "install help needed acpi and kernal panic errors"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by fashionsofmystery on 2010-01-16
I'm working on converting an old IBM ThinkPad over to Ubuntu 8.4 Hardy .
It had win me installed , a very full 4g hard drive and a bad cmos battery. I got a live CD and selected the full install . The install went fine ,I rebooted and logged in. I let the laptop run over night and it was still running the next morning. I told the system to power down and it wouldn't give me the ok to cut the power so I  just turned it off. The next time I tried to boot the system I got a kernal panic error after a couple of pages of code. Something like "tried to kill the idle task". No response from the keyboard. I looked on here and it sounded like there was a problem with the partitions even though the live CD did it automaticly. So I opened up the case and pulled out the hard drive. I changed the cmos while I was in there.   I got a usb case for the drive so I could hook it up to my win 2k and format it's  little mind.  I pluged the hard drive back in and put the live CD in and told it to install. Now I get the dmi bios year error acpi=force.  There is no year listed in the error. I looked on this site again and I downloaded the bios for my system from Levono. After install I still get the error, no keyboard and not able to boot. I tried running the trial live version and it does not load. I tried the F6 from the menu and selected acpi off and that was no help.  I'm a first time user so if I have to put acpi=force in somewhere I need to know exactly where since the system is not running and I can't access the hyperterm.  Thanks. Btw here is what I know about the hardware. 1 chip marked Ali 100mhz ,1 chip Magic Media 256av , 1 256 MBLT 100 ram card and 1 32mb DIMM ram card.  It's an IBM ThinkPad i series 2611 412 with a celeron processor.

---

### Post by MarkC502 on 2010-01-16
Several things to try

1st when you boot the laptop go into the bios and see if you can try other ACPI settings for the laptop and then see if it boots.

2nd Try a different version of Ubuntu or you could also try using the alternate install disk which works sometimes on systems the live boot will not load up on.

Also be more specific about behavior the system is doing when you try to use a live disk. I would bet that the version you are trying to use has a problem with the hardware in that laptops ACPI.

P.S. A great Ubuntu alternative on old laptops is Xubuntu which is Ubuntu with a different desktop manager, it uses less resources so it runs faster on older equipment but still has all the feature one could need and nice graphics etc. You could probably run Xubuntu 9.04 on this laptop rather than Ubuntu 8.04 and get better results.

---

