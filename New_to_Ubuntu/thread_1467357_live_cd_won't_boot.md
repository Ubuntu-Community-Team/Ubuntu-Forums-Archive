---
title: "live cd won't boot"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by Bigbob1942 on 2010-04-30
I burned the Ubuntu 8.10 to a cd, checksum was good. The problem is: my cd/dvd drive is a sata connection, I end up with an a: prompt and no a: drive. is there a way to make the disk find the sata drive?

---

### Post by tica vun on 2010-04-30
Try some of the debug options on the boot menu.

---

### Post by Bigbob1942 on 2010-04-30
The windows boot menu?

---

### Post by oldos2er on 2010-04-30
Ubuntu 8.10 has reached its end-of-life, so you might want to try a newer version.

Make sure your bios is set to boot from cdrom first.

---

### Post by nhasian on 2010-04-30
having the optical drive on a SATA connection is not a problem, its a good thing :)

the only thing you need to do is change the device boot order in your bios.  sometimes you can just press a key during the post screen like F10 or F12 or something it will tell you for BOOT OPTIONS.  if your computer doesnt have this feature then you will need to enter the bios settings (usually DEL or one of the f-keys during the POST screen.  if you see the Windows or Ubuntu logo you've gone to far and have to reboot again.  if the screen goes too fast you can press the PAUSE button on your keyboard to pause the post screen.

the boot order should look like this:

1) Optical Drive
2) HDD
3) other/lan/usb/etc

if you want to install ubuntu from a usb thumdrive instead of a cd, just make sure usb-hdd is the first boot option.

also make sure to make a cd of the latest Ubuntu 10.04 that came out yesterday.

---

### Post by Bigbob1942 on 2010-05-04
I will try the new version, and let you know ... thanks for the advice

---

