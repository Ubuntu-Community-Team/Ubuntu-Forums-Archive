---
title: "Installing updates of flash drive"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by moch1 on 2010-08-09
I'm new to using Ubuntu and I really just want to run it off my 4GB flash drive. It gets set up fine with a 3GB persistent file but when I try to install update to ubuntu I get errors that say it can't install grub on any of the available drives as well as issues with the iso file. Then when I restart the computer and try to run ubuntu it doesn't work.

Suggestions?

---

### Post by jtarin on 2010-08-09
Here's a [method]("Reinstalling GRUB 2") I use to install/reinstall Grub2 to non-MBR location. Scroll down the page until you see the topic "Reinstalling GRUB 2"....you need the live CD/DVD. I can personally vouch for the "METHOD 3 - CHROOT" as I have used it several times to place Grub where I wanted it. You will then  need to enable your USB bootable in the bios as first boot device.

---

