---
title: "Black screen after login"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by rippin250r on 2010-03-02
I'm running Ubuntu 9.04 on my laptop and it was working perfectly fine until about a week ago.  When I booted it up one day I logged on and it went straight to a black screen, I could see my cursor moving around but it was nothing but that and black.  I shut it down and restarted and it started to load again, the loading bar got about an 1/8 of the way done and it went to a black screen with all sorts of writing (what looks to be error messages) and then straight to a maintenance shell. I can't boot to recovery mode and now it won't even get past the loading screen without going to a maintenance terminal.

---

### Post by Rex Bouwense on 2010-03-02
> **rippin250r said:**
> I'm running Ubuntu 9.04 on my laptop and it was working perfectly fine until about a week ago.  When I booted it up one day I logged on and it went straight to a black screen, I could see my cursor moving around but it was nothing but that and black.  I shut it down and restarted and it started to load again, the loading bar got about an 1/8 of the way done and it went to a black screen with all sorts of writing (what looks to be error messages) and then straight to a maintenance shell. I can't boot to recovery mode and now it won't even get past the loading screen without going to a maintenance terminal.

Can you boot from a live CD?

---

### Post by sandyd on 2010-03-02
try 
```

sudo fsck -y

```
from a livecd.

you **may** need to specify the partition name (/dev/sda1 or whatever) after the "-y" so that it will look something like

```

sudo fsck -y /dev/sdax
```

it looks like hard disk/partition corruption to me.

---

### Post by rippin250r on 2010-03-02
So I could boot with the live cd but could not access the root folder on my linux partition because it said I didn't have permission. I ran the command and when I did a reboot I got to the login again and it went to the black screen with the cursor. I could hear the login sound and the toolbar flashed for a second but nothing ever loaded.

---

### Post by lyall on 2010-03-02
at the login screen 
click on Options
select Failsafe Gnome
then log in

see if it work for you

also see the following link
[http://www.dharwadkar.com/weblog/ubuntu04]("http://www.dharwadkar.com/weblog/ubuntu04")

then look at [http://www.dharwadkar.com/weblog/ubuntu06]("http://www.dharwadkar.com/weblog/ubuntu06")
it is for Ubuntu - Karmic Koala

hope this helps

good luck and have fun learning

---

### Post by sandyd on 2010-03-02
> **rippin250r said:**
> So I could boot with the live cd but could not access the root folder on my linux partition because it said I didn't have permission. I ran the command and when I did a reboot I got to the login again and it went to the black screen with the cursor. I could hear the login sound and the toolbar flashed for a second but nothing ever loaded.
well.... were getting somewhere....
go back to the livecd.

run this (replace sdax with your partition)
```

sudo mount -t ext3 /dev/sdax /mnt
gedit ~/Desktop/xorg.conf
```

paste this in
```

Section "Device"
        Identifier      "Configured Video Device"
EndSection
 
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection
 
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
 
```
save
run 
```

sudo mv /mnt/etc/X11/xorg.conf /mnt/etc/X11/xorg.conf.bak
sudo mv ~/xorg.conf /mnt/etc/X11/xorg.conf
sudo shutdown 0 -r

```
restart. 

and please consider upgrading to 9.10

---

### Post by rippin250r on 2010-03-08
Just got a chance to run those commands.

ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda2 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

