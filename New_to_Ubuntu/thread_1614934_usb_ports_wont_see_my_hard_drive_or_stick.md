---
title: "usb ports wont see my hard drive or stick"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by costalot on 2010-11-06
mount: only root can mount /dev/sdb1 on /media/sda

what does this mean some one please help

---

### Post by Hippytaff on 2010-11-06
put sudo infront of the command, it will ask for your password. when you type it nothing will appear in the terminal, this is normal :-)

---

### Post by sandyd on 2010-11-06
> **costalot said:**
> mount: only root can mount /dev/sdb1 on /media/sda

what does this mean some one please help

```

sudo mount /dev/sdb1 /media/sda

```

next time, just open the usb drive from the "places" menu

---

### Post by Jackson4christ on 2010-11-06
> **sandyd said:**
> 
next time, just open the usb drive from the "places" menu

It will only be accessible from the "places" menu if it's already been mounted, (which it should of been at boot or when plugged in by Nautilus or Thunar.)

---

