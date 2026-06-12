---
title: "Boot to revovery mode from terminal ?"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by jonttix on 2009-03-30
Is it possible to reboot from terminal so that the recovery mode starts? I have a usb-keyboard and it is now working when I should press ESC.

Please help me

---

### Post by jonttix on 2009-03-30
I have a problem, I can´t boot recovery mode because I my keyboard dont work when I should press ESC.

Please help!

---

### Post by LowSky on 2009-03-30
press escape as the pc is done checking bios at boot and befoe the ubuntu load screen shows up

---

### Post by Chemical Imbalance on 2009-03-30
Check your BIOS for settings having to do with plug and play OSes.  Make sure your BIOS is controlling the detection of devices.

---

### Post by jonttix on 2009-03-30
Thanks!

---

### Post by Chemical Imbalance on 2009-03-30
> **jonttix said:**
> Thanks!

Did it work?

---

### Post by kanikilu on 2009-03-30
I'm not sure if you can set a "one-time" option to boot to recovery mode. However, you can edit /boot/grub/menu.lst and set the default to recovery mode. ```
sudo nano /etc/boot/grub/menu.lst
``` Basically you just need to change the line that (probably) says ```
default  0
``` to match the stanza of the recovery mode. For me it would be ```
default  1
``` To find out which one it is, just find the listing of stanzas, it should look something like this: ```
## ## End Default Options ##

title           Ubuntu 8.10, kernel 2.6.27-11-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.27-11-generic root=UUID=11ba35c7-ca17-4636-892c-0c3fabf4c81a ro quiet splash xforcevesa
initrd          /boot/initrd.img-2.6.27-11-generic
quiet
``` That's the first one, so counting from 0, find the one you want. For me it's the next listed one, so I'd change the default to "1".

When you're done with the recovery mode and what to go back, just boot up and change the default back to what it was.

If that's confusing, just post the contents of your menu.lst file and I can tell you what to change.

---

### Post by CatKiller on 2009-03-30
> **jonttix said:**
> Is it possible to reboot from terminal so that the recovery mode starts? I have a usb-keyboard and it is now working when I should press ESC.

Please help me

Find a non-USB keyboard, and boot with that so that you can get into the BIOS Settings screen. Find the USB Keyboard Support option and enable it.

You'll now be able to use your USB keyboard to enter the BIOS and fiddle with your GRUB options.

---

### Post by bapoumba on 2009-03-30
Threads merged.

---

