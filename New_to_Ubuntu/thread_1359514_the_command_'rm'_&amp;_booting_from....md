---
title: "the command 'rm' &amp; booting from..."
date: 2009-12-19
forum: New to Ubuntu
---

### Post by mydisguise09 on 2009-12-19
is there a command that unremoves or recovers something where you used 'rm'?
 
I'm going to try and do a fresh install of ubuntu 9.10 -
where do I go to download the ISO?
my netbook doesn't have a cd drive but has 2 USB ports so I guess I could get an external cd drive or do you think I could use my 1GB USB stick? would it be bootable? if so, how hould I go about doing that?

---

### Post by Cheesemill on 2009-12-19
> **mydisguise09 said:**
> is there a command that unremoves or recovers something where you used 'rm'?
You could boot from a Live CD or USB and use testdisc or photorec, you may be lucky if you haven't written anything else onto the drive yet.
 
> I'm going to try and do a fresh install of ubuntu 9.10 -
where do I go to download the ISO?
my netbook doesn't have a cd drive but has 2 USB ports so I guess I could get an external cd drive or do you think I could use my 1GB USB stick? would it be bootable? if so, how hould I go about doing that?[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by mydisguise09 on 2009-12-21
ok my roommate dowloaded ubuntu 9.10 and got it on my USB stick but even in BIOS when the USB is first in boot order my comp starts up as normal (taking me to tty1 login) and since i accidentally rm /etc/init.d/gdm i really can't do much and i also tried pressing F6 then ESC and manual boot line editing, add option 'cd-rom-detect/try-usb=true' (didn't know what add option meant :confused:) I pressed O so a new line was added before root and also tried pressing o and adding a new line after root and also tried it before quiet and then pressed b to boot but that didn't work :( what am I doing wrong? why isn't the USB bootable?

---

### Post by NoaHall on 2009-12-21
Try this from the command line -
```
sudo apt-get remove --purge ubuntu-desktop && sudo apt-get install ubuntu-desktop
```

---

### Post by mydisguise09 on 2009-12-21
see the thing is I only have wifi, no direct connection to the internet (like broadband or anything like that :() but I do know someone who has a cable modem that I could probably try using...
 
I guess there's no way to get to the USB while I'm in tty1?

---

### Post by NoaHall on 2009-12-21
Try ```
ifconfig wlan0 up
```

---

