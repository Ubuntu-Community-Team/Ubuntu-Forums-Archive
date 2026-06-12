---
title: "upgrade"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by johndingli on 2010-02-10
Hi guys I bought an asus netbook eeepc and has ubuntu 8.10 installed how can i upgrade to ubuntu 9.10 as there is no optical drive or can I upgrade by online thanks

---

### Post by snowpine on 2010-02-10
I would recommend a fresh reinstall of Ubuntu 9.10 using a USB thumb drive instead of a CD: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Make sure you thoroughly research and test your specific eee model to feel confident that 9.10 will, indeed, support all of your hardware.

Good luck!

---

### Post by patchwork on 2010-02-10
Without doing a fresh install, it's going to take awhile as you will need to apply every update and every distribution upgrade to become current, and it's always good to backup everything you need to keep before starting (some people have had trouble with corruption on dist-upgrades, and prefer clean installs)

If you're ready for that,

```
sudo apt-get update && sudo apt-get upgrade

```Once that completes, 
```
sudo apt-get dist-upgrade
```And repeat these steps until you have 9.10 installed.

Edit:  Yeah, I think I'd try snowpine's method first...

---

### Post by wojox on 2010-02-10
Is usb an option?

---

### Post by wojox on 2010-02-10
Like snowpine stated. You want a fresh install and not an upgrade.

---

### Post by johndingli on 2010-02-10
Im not sure if it has a usb option in bios it says removable device can that be usb im mixed up now thanks guys

---

### Post by snowpine on 2010-02-10
All models of eee are capable of booting from USB. Read the link in post #2 or use [Unetbootin]("http://unetbootin.sourceforge.net").

---

### Post by johndingli on 2010-02-10
Hi guys I made a bootable pendrive and the eeepc still wont boot from it tried it on an acer netbook and boots like a dream on it any help pls

---

### Post by patchwork on 2010-02-10
Did you set the boot order in BIOS for the USB to boot before the HDD?

---

### Post by snowpine on 2010-02-10
It's got to be something in your BIOS settings. Look for some kind of "quick boot" or "boot booster" that you can turn off maybe?

---

### Post by johndingli on 2010-02-10
disabled quick boot but still didnt boot from pendrive the first boot is removable dev

---

### Post by snowpine on 2010-02-10
Does it show up as a hard drive?

---

### Post by johndingli on 2010-02-10
In bios 1st boot is removable dev 2nd boot is hdd 3rd boot is disabled thanks

---

