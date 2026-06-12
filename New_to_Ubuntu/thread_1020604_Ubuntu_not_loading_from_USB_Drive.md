---
title: "Ubuntu not loading from USB Drive"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by Luomeng on 2008-12-24
I got a brand new Samsung NC10 and I wanted to install ubuntu on it. This is my first time with Linux so I followed these instructions here: [https://help.ubuntu.com/community/NC10](https://help.ubuntu.com/community/NC10). I used unetbootin and that was fine, except for a small box that popped up that asked if i wanted to replace autorun? Then, I plugged my USB in and changed the boot settings on the NC10. When I started up my computer, it didn't show ubuntu installation screen. Instead, it said "disk error Press any key to reboot." Why is this happening and how can I fix it? Btw, I'm using a 2GB Kingston Usb drive if it matters

---

### Post by LowSky on 2008-12-24
what method did you use to create the install on the USB

---

### Post by Luomeng on 2008-12-24
I used unetbootin, plugged in my USB drive, selected Ubutnu 8.10Live and clicked install

---

### Post by LowSky on 2008-12-24
did you properly unmount the drive from hte other computer before pluging it into the curreecnt one.

You need to unmount properly, you can't just pull the thing out of the usb port

---

### Post by Luomeng on 2008-12-24
Yeah, I did. I did safely remove harddrive or something like that at the bottom before i pulled it out

---

### Post by Luomeng on 2008-12-24
So I finally, got Ubuntu installed on my NC10 and following the directions I posted on the first post, tried to install the wifi drivers and update the system.I typed in "sudo apt-get install linux-backports-modules-intrepid" to install the wifi drivers. It came back with "E: Couldn't find package linux-backports-modules-intrepid" Why can't I install these drivers?

---

### Post by Luomeng on 2008-12-24
bump

---

### Post by jaseanton on 2008-12-24
First off check that you have an Ethernet connection, then do this:

1) Deactivate the driver that's being used now:

System > Administration > Hardware Drivers > Deactivate

2) Install build-essential

```
sudo apt-get install build-essential
```

3) Download and save to your Desktop the latest Atheros driver from [this site]("http://wireless.kernel.org/download/compat-wireless-2.6/")

At the time of writing, this was: compat-wireless-2008-12-24.tar.bz2

4) Extract it to your Desktop

5) Install Atheros driver

```
cd /home/YOUR_USERNAME/Desktop/compat-wireless-2008-12-24/
```

(replace the directory name with the current version's)

```
make
```
```
sudo make install
```
```
sudo unload
```
```
sudo load
```
That should work.  If not
```
sudo reboot
```
That should

HTH and please confirm if this worked.

---

### Post by Jon Bradbury on 2008-12-24
> **Luomeng said:**
> So I finally, got Ubuntu installed on my NC10 and following the directions I posted on the first post, tried to install the wifi drivers and update the system.I typed in "sudo apt-get install linux-backports-modules-intrepid" to install the wifi drivers. It came back with "E: Couldn't find package linux-backports-modules-intrepid" Why can't I install these drivers?

Looks like it is trying to install off the CD-ROM - is it still connected?

---

### Post by Keen101 on 2008-12-24
> Why can't I install these drivers?

you probably don't have your backports repository active.

go to >System >Administration >Software sources to double check. Then once they are active your command should work i would think.


[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by Luomeng on 2008-12-24
Keen, where do I find backports respitory on software sources? I can't find it

Btw,jaseanton, my ethernet connection won't work either :\

---

### Post by Keen101 on 2008-12-27
> **Luomeng said:**
> Keen, where do I find backports respitory on software sources? I can't find it

see the attachment below. This might not actually be what you want, this is the backports update repository, and i don't know of anything else. Hopefully by enabling this it will fix your problem, if not i don't know how else to help you.

also, i don't have much experience with unetbootin, but i have found this program to work fine when i needed a Live-USB ubuntu installed to a 1GB flash drive. [https://launchpad.net/liveusb](https://launchpad.net/liveusb)



[B]also, it seems weird that you are trying to install drivers on a "live" system. If it is indeed a Live-usb system, once the drivers are installed it will revert back to it's default configuration, therefore gaining nothing.

If you need a modifiable portable version of ubuntu just get an 8GB or larger flash drive and do a normal install to the usb drive. Make sure you unplug the internal drive while doing this to avoid GRUB issues.[/B]



.

---

