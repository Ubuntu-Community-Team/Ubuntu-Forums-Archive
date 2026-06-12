---
title: "GRUB problem"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by JPtux on 2010-07-17
Hello,
I have installed 10.04 on my computer recently. However, I had trouble at first with a blank screen so I used this tutorial:
[http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)
It works perfectly. The problem is when I try to follow these steps:

> * On first boot after install, press e on getting the GRUB bootloader.
* Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
* Press Ctrl and X to boot
* You should now be able to login to your Ubuntu as usual
I press "e" but it won't take me to the edit grub menu. I dont even see grub at start up. Afterwards, there is just a blank screen like the one on the live CD and I am unable to edit grub.

I tried editing the file from my live CD but I cant run "sudo update-grub". It gives me this error: 

```
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
```

How can I edit grub?
Thanks in advance!

---

### Post by cbowman57 on 2010-07-17
You need to hold down the  shift key to get your grub menu to be visible.   Ubuntu defaults to hiding grub if it is the only OS.

---

### Post by JPtux on 2010-07-17
Thanks a lot!!!!

---

