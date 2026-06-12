---
title: "How to Make a bootable usb from kubuntu...."
date: 2009-10-15
forum: New to Ubuntu
---

### Post by HamzahQaisar on 2009-10-15
Ok so i installed pure kde and guess what? it sucked so harrd i wanna go back to ubuntu 9.04

Can someone help me make a bootable usb stick for ubuntu in kubuntu ??

---

### Post by HamzahQaisar on 2009-10-15
anyone help ?

---

### Post by beastrace91 on 2009-10-15
Download the Ubuntu ISO you want to use.

Then use unetbootin - ```
sudo apt-get install unetbootin
``` to make your USB stick bootable

~Jeff

---

### Post by zkriesse on 2009-10-15
Make sure that the USB has been formatted to FAT32 and is 1GB or more. You can format the flash drive in Windows. Then, like beastrace91 said, you can use UNetbootin.

---

### Post by tarps87 on 2009-10-15
> **Zachk18 said:**
> Make sure that the USB has been formatted to FAT32 and is 1GB or more. You can format the flash drive in Windows. Then, like beastrace91 said, you can use UNetbootin.

You can also format the drive using gparted if you want the point and click option.

You could just run the commands
```
sudo apt-get install ubuntu-desktop
sudo apt-get purge kubuntu-desktop
```
Although a clean install would give you a cleaner result

---

### Post by MelDJ on 2009-10-15
see this site: [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by arochester on 2009-10-15
...Look at [http://kubuntuforums.net/forums/index.php?topic=3106984.0](http://kubuntuforums.net/forums/index.php?topic=3106984.0) ...

---

