---
title: "have you seen Grub?"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by trinidadflores on 2009-07-21
I need help someone kidnapped grub.  There is no trace of it on my computer how do i reinstall it?

---

### Post by lisati on 2009-07-21
I found evidence that the kidnappers have been paid the ransom: have a look here for info on reinstalling grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by keplerspeed on 2009-07-21
What do u mean kidnapped? No grub on boot?

See here under section 'Restoring GRUB' [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

EDIT: Thanks lisati, that a excellent guide!

---

### Post by wojox on 2009-07-21
Where did you look?

/boot/grub/menu.lst?

Not there?

---

### Post by trinidadflores on 2009-07-21
> **keplerspeed said:**
> What do u mean kidnapped? No grub on boot?

See here under section 'Restoring GRUB' [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

EDIT: Thanks lisati, that a excellent guide!

it was masteriously whipped out when i turned on my computer this morning and it was working fine yesterday.

---

### Post by trinidadflores on 2009-07-21
> **wojox said:**
> Where did you look?

/boot/grub/menu.lst?

Not there?

nothing there at all

---

### Post by lisati on 2009-07-21
> **trinidadflores said:**
> it was masteriously whipped out when i turned on my computer this morning and it was working fine yesterday.

Did you read the information at the links we provided?

---

### Post by trinidadflores on 2009-07-21
> **lisati said:**
> Did you read the information at the links we provided?

im going through it now. gonna reboot and hopefully i have it i'll let you know.

---

### Post by lisati on 2009-07-21
> **trinidadflores said:**
> im going through it now. gonna reboot and hopefully i have it i'll let you know.

good luck. Feel free to ask more questions if you get stuck.

---

### Post by trinidadflores on 2009-07-21
> **lisati said:**
> good luck. Feel free to ask more questions if you get stuck.

I have the boot loader back. But I dont have all of my os's though.

---

### Post by jeppewinther on 2009-07-21
List your menu.lst and the results of
```
sudo fdisk -l
``` and we can talk you through it.

Or alternatively, if you're feeling up for it, go searching the forums for adding Windows to the grub boot loader, I know I have answered that question a couple of times and have seen it pop up quite often.

---

### Post by trinidadflores on 2009-07-21
> **jeppewinther said:**
> List your menu.lst and the results of
```
sudo fdisk -l
``` and we can talk you through it.

Or alternatively, if you're feeling up for it, go searching the forums for adding Windows to the grub boot loader, I know I have answered that question a couple of times and have seen it pop up quite often.

thanks.  I finally figured it out and now everything is working the way it should be.

---

