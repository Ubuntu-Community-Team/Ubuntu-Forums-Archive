---
title: "ACX111 chipset help (the ndiswrapper wiki is wrong!)"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by agent-s on 2007-05-25
OK so when I first installed the tnet1130 drivers, it could see the networks, but could not connect or create a network.

so after some searching and tweaking i tried adding "acpi=off" to the kernel parameters in /boot/grub/menu.lst

now the wifi card doesn't power on anymore, but sound works (??)

i tried taking it out and reinserting it

i also tried taking out "acpi=off" out but it still doesn't work anymore

can anyone help me out with this? supposedly according to ndiswrapper's wiki it should be working perfectly....

or maybe Windows will always be better than Linux? (at least things work in Windows)

---

### Post by dmizer on 2007-05-25
actually, you shouldn't need ndiswrapper to make that card work in either edgy or feisty.

that doesn't mean you can't use ndiswrapper.  you'll just have to disable the native acx module trying to drive your card instead of ndiswrapper.  for more information check out this thread: [http://ubuntuforums.org/showthread.php?t=324148](http://ubuntuforums.org/showthread.php?t=324148)

---

### Post by agent-s on 2007-05-27
aight i just realized that i had to reload the ndiswrapper module.... even though i did ndiswrapper -m..... :(

---

