---
title: "Installation questions."
date: 2009-04-19
forum: New to Ubuntu
---

### Post by furialis on 2009-04-19
I just bought an [OCZ SSD Drive]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820227393") and I'm having some installation problems. OCZ suggests that the [motherboard]("http://www.gigabyte.us/Products/Motherboard/Products_Overview.aspx?ClassValue=Motherboard&ProductID=2932&ProductName=GA-MA78GM-S2HP") be run in native IDE mode. When the computer is turned on the BIOS recognizes the drive correctly, but as soon as any type of Linux boot disk/LiveCD I get an End Request: I/O error and ata1.00 revalidation failed. After it hangs for a couple of minutes it will boot into the LiveCD, but I can't access the drive and the HD activity light stays on forever. However, when I install XP it installs fine.

According to the OCZ forums (which has very knowledgeable moderators as it's an official site), The problems lies with the firmware of the motherboard. On researching the problem, I found [this thread]("http://ubuntuforums.org/showthread.php?t=1129559&highlight=ssd") which mentions an [I/O scheduler]("http://www.brighthub.com/computing/linux/articles/9170.aspx") and the settings for it. My suspicion is that the Linux default (cfq) is not compatible with my motherboard and I need to change it (to either noop or deadline) on the LiveCD so that it runs on startup. 

How would I do that?

Edit: The command to find what the setting is

cat /sys/block/sda/queue/scheduler

The command to change the setting is

sudo -i echo deadline > /sys/block/sda/queue/scheduler

---

### Post by zvacet on 2009-04-20
I'm not expert but did you tried to set BIOS in AHCI mode?

---

### Post by ||--LethaL--|| on 2009-06-19
I am having a similar problem with a 30G OCZ. That drive had previously worked flawlessly. I installed Ubuntu jaunty with an ext2 boot partition. The installation worked correctly. After reboot, I received same error.> ata1.00 revalidation failed

I am able to boot gentoo, and access the OCZ drive. I formated and then recreated the partition table. I removed the boot flag, but after boot on jaunty live cd... same error occurs =(

As far as a possible motherboard issue... evga 680i mobo had experienced no issues handling the ssd in my rig. I cant recall what my I/O scheduler is at the moment. This is a pretty old thread... did you get it working??

Cuz imma havin same issue now...

---

