---
title: "Multi-boot USB"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by afroman10496 on 2010-06-29
Heyall, I have a 4GB USB drive and I want to boot around 7 isos on it. How do you do that? any guides or anything? i tried google and they were all on windows :(

---

### Post by RetchingRabbit on 2010-06-29
I would try partitioning the thing for each .iso with gparted or whatever, and try using unetbootin.

---

### Post by oldfred on 2010-06-29
I used panticz and it worked well but I did not run the full script as it just sets up those versions. I just used the first few commands to install grub and create a grub.cfg. Then I copied some of the grub stanzas from the next site.

MultiBoot USB with Grub2 (boot directly from iso files)
Is full script, I only used some commands
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.


MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk -   has a lot of grub stanza examples in the script
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
CD/DVD multiboot
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644) 
To setup multibooting:
multiboot055.sh

Several other versions:
multicd.sh - combine Linux ISOS into one
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)

---

