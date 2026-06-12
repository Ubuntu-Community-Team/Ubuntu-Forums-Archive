---
title: "Adding Boot parameters installing Lucid from Live CD"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by Blojic on 2010-08-04
Hi,

Silly Question probably - I have a Philips Freevents laptop and am trying to install Lucid. There is a problem with this laptop whereby apparently I need to add "reserve=0xffb00000,0x100000" as a boot parameter when installing - see [URL="http://www.fitzenreiter.de/averatec/index-e.htm"]

Can I add this when installing from the live CD or do I perhaps need the Alternate CD? (I need to get this right as this laptop is the only machine I have internet access with at the moment so don't want to **** it up). I'm currently running Hardy and would like to upgrade.

Thanks in advance/...

---

### Post by Elfy on 2010-08-04
You can add it when you boot the livecd - press any key at the livecd boot to get access to the menu.

Once installed you can add it to grub the first time you boot 

[https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot](https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot)

Then when you have booted, add it to so it is a normal addition to grub, add it to this line of the file

> GRUB_CMDLINE_LINUX_DEFAULT

[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

Put this for anyone who might happen along - unless the thread is marked solved by accident

---

