---
title: "How can I install Ubuntu on a USB memory stick"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by Bodsda on 2009-08-19
Hello,

Can anyone provide some insight on installing Ubuntu onto a USB memory stick. I wish to have a complete install on here rather than a bootable live environment.

I have been following paultags guide [here]("http://blog.paultags.com/2009/05/making-a-bootable-usb-drive/") but have so far been unsuccessful, can anyone assist?

Kind regards,
Bodsda

p.s: If you need extra info please just ask.

---

### Post by Stan_1936 on 2009-08-19
Where are you messing up the installation instructions?

EDIT:  Are you sure that those instructions are for Ubuntu?

[http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)

---

### Post by alexlafreniere on 2009-08-19
You can either boot into a LiveCD and select "create USB startup disk" or something similar like that, or use a program called unetbootin. They both accomplish the same task: creating the equivalent of a LiveCD on a USB flash drive. Once booted into that environment you can do a complete install of Ubuntu (this is also how I do Ubuntu installations when working on computers with no CD drive, such as netbooks).

---

### Post by Bodsda on 2009-08-19
> **Stan_1936 said:**
> Where are you messing up the installation instructions?

EDIT:  Are you sure that those instructions are for Ubuntu?

[http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)

I dont think I am following the instructions wrong. I have spoke to paultag about this and he is at a loss.

Yes the instructions are for installing Ubuntu. See the debootstrap process.

Kind regards,
Bodsda

---

### Post by Bodsda on 2009-08-19
> **alexlafreniere said:**
> You can either boot into a LiveCD and select "create USB startup disk" or something similar like that, or use a program called unetbootin. They both accomplish the same task: creating the equivalent of a LiveCD on a USB flash drive. Once booted into that environment you can do a complete install of Ubuntu (this is also how I do Ubuntu installations when working on computers with no CD drive, such as netbooks).

I dont wish to install a livecd on a USB, I want to have a complete ubuntu linux installation on my usb memory stick.

Kind regards,
Bodsda

---

### Post by alexlafreniere on 2009-08-20
Yes, with unetbootin you will essentially have a LiveCD installation but with persistent settings, so you can install programs and save files to it rather than lose all your work afterwards.

---

### Post by Mighty_Joe on 2009-08-20
> **Bodsda said:**
> I dont wish to install a livecd on a USB, I want to have a complete ubuntu linux installation on my usb memory stick.

See my post in [this topic]("http://ubuntuforums.org/showthread.php?t=1193680").  I used the instructions linked there to do a full install to a USB flash drive.

---

### Post by Mighty_Joe on 2009-08-20
> **alexlafreniere said:**
> Yes, with unetbootin you will essentially have a LiveCD installation but with persistent settings

To my knowledge, unetbootin will not create a persistent install. There's nothing about persistence in the [documentation]("http://unetbootin.sourceforge.net/")
The [USB Creator]("http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator") on the Live CD does support persistence.

---

### Post by C.S.Cameron on 2009-08-20
This is how I made a Unetbootin install to flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext3 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, removed CD, rebooted.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.

However if you want a full install, like you would get with an internal hard drive, just plug in a USB stick, 4G or larger, disable the internal hard drive and run install from the Live CD, (ubiquity). You can even use manual partitioning if you want a separate home partitioning. With this method you can update without quickly filling your stick.

---

### Post by suevy Suavae on 2009-08-20
All I had to do was download the .iso file for whichever version of Ubuntu I wanted, then go to System>Administration>USB Startup Disk Creator, and it was pretty self explanatory from there, but maybe thats not what your looking for.

---

