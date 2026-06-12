---
title: "Drivers?"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by slughappy1 on 2009-03-27
Is there a way to find out what drivers I am using for all my devices?

---

### Post by Ubuntiac on 2009-03-27
Wellll...

You can look at restricted driver manager (sudo jockey-gtk for Ubuntu or sudo jockey-kde for Kubuntu) to see the *restricted* (ie not free) drivers you're using.

As far as any free drivers you're using, lspci will tell you all PCI hardware you're using and lsusb will tell you all hardware recognised in a usb port. From there you can always do a search on the device name to find out which open-source driver Ubuntu uses for it.

Id suggest though that if you let the community know why you want to know, we *may* be able to help you out with your actual purpose better.

---

### Post by asmoore82 on 2009-03-28
you can install the graphical version of `lshw`

```
sudo apt-get install lshw-gtk
```

I don't see it in the menus anywhere after installing it...
it needs root privileges so you can run it with

Alt+F2 and
```
gksudo lshw-gtk
```

---

