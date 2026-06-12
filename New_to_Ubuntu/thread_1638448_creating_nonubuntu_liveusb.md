---
title: "creating nonubuntu liveusb"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by ornothaloapq on 2010-12-05
does anyone know how to use ubuntu 10.10 to create a live usb capable of running fedora 14. i have the iso image of fedora and i also downloaded ubuntu but unetbootin on linux seems very old.

---

### Post by Shadowgamon on 2010-12-05
did you try start up disk creator? it should be under the system> administration> Startup Disk Creater.
if you can't find it, just run this 
```
usb-creator-gtk
```if you have a normal install it should work

---

### Post by C.S.Cameron on 2010-12-05
MultiBootUSB works with Fedora:

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by BugBuster on 2010-12-05
Open the Fedora livecd with fileroller and in that there is a folder LiveOS. In that folder there is script livecd-iso-to-disk.
Run that script on ubuntu with root privileges like so
```
sudo livecd-iso-to-disk <complete_path_to_fedora_iso> /dev/sdX 
```
where sdX is your usb device.

For more options checkout
```
sudo livecd-iso-to-disk --help
```

---

### Post by idi0tf0wl on 2010-12-06
> **ornothaloapq said:**
> but unetbootin on linux seems very old.

dd's old too, but neither have ever failed me.

---

### Post by beew on 2010-12-06
Something is missing in the Fedora14 iso, I tried a few usual tools including Fedora's own live usb creator and in all cases the resulting usb was not bootable. There is a thread in the Fedora forum but I can't remember where it is now. 

The only thing that works is Unetbootin, no persistence, but at least it boots. In this case I am going to install it so it doesn't matter. I haven't tried using dd, but will do it when I get a spare usb drive.

P.S. you get get a newer version of unetbootin by using a ppa. Mine is a lot newer than what is offered in the Ubuntu repo.

---

