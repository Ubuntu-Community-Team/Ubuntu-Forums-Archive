---
title: "Help: Upgrading to 8.04 deleted all OS"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by mafaldaspeaks on 2010-07-23
My friend's netbook was running on 7.04 or 7.10. Since it has _no CD drive _and we _couldn't find or add the usb creator feature_, we decided to upgrade via internet using the upgrade button shown in the update manager.

All the required steps being shown seemed to be going well (creating new channels, downloading upgrades, installing upgrades, etc) until the step "restarting computer". When it restarted, it went into the memory test for almost 2 hours so we decided to stop it. when we restarted, at the "Grub loading", we pressed Esc to see the OS installed: there wasn't any excpet for the "memtest".

What are the options to re-install an OS? I have to say that we don't have an external CD drive. I just have my laptop with a CD drive and which uses Linux Mint 9.

I'd appreciate all your help!

---

### Post by bodhi.zazen on 2010-07-24
Try installing Ubuntu 10.04.

You can create a bootable usb with unetbootin.

---

### Post by kerry_s on 2010-07-24
> What are the options to re-install an OS? I have to say that we don't have an external CD drive. I just have my laptop with a CD drive and which uses Linux Mint 9.

linux mint 9 is ubuntu based, look in synaptic for "usb-creator-gtk", you can use that to make bootable usb installer.

you'll need a ubuntu iso.
[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

---

### Post by mafaldaspeaks on 2010-07-25
> **bodhi.zazen said:**
> Try installing Ubuntu 10.04.

You can create a bootable usb with unetbootin.

Thanks for the reply! I tried unetbootin on my linux mint 9 to create a usb installer for ubuntu 10.04 but the netbook won't recognize it. At startup, it would say something like "remove disk or other media then press any ke to restart". I used "start up disk creator" instead and it worked.

---

### Post by mafaldaspeaks on 2010-07-25
> **kerry_s said:**
> linux mint 9 is ubuntu based, look in synaptic for "usb-creator-gtk", you can use that to make bootable usb installer.

you'll need a ubuntu iso.
[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

I was able to create the usb installer using "start up disk creator" on my linux mint 9 laptop. Installation was successful except for something that's quite inconvenient: the labels of the desktop icons can't be read and the icons themselves don't respond consistently to the touchpad and not at all to the mouse. I tried the monitor settings (guessing among the icons) but it does not resove how the desktop is. Would you know how to fix this?

---

### Post by mafaldaspeaks on 2010-07-29
> **mafaldaspeaks said:**
> I was able to create the usb installer using "start up disk creator" on my linux mint 9 laptop. Installation was successful except for something that's quite inconvenient: the labels of the desktop icons can't be read and the icons themselves don't respond consistently to the touchpad and not at all to the mouse. I tried the monitor settings (guessing among the icons) but it does not resove how the desktop is. Would you know how to fix this?

Well, I didn't really get to fix the problem with the ubuntu netbook desktop (the launcher). I just switched to the gnome desktop and now the netbook's working fine.

---

