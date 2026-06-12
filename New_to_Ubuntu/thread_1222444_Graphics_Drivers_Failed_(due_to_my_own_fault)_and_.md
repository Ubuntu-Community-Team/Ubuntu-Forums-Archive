---
title: "Graphics Drivers Failed (due to my own fault) and cannot boot anymore."
date: 2009-07-24
forum: New to Ubuntu
---

### Post by lildigiman on 2009-07-24
Hello, I will start off with saying I am not new to Ubuntu, as I have used it for about a whole year and a half now. I will say I never had anything this fatal happen, but I've always managed to work well around any problems I have had. That being said I will start out by what I did in my own stupidity:

1. I ended up removing ATI's proprietary driver that I had installed through Hardware Drivers.
2. I downloaded their latest release from their website, and installed it just fine, except for the fact that the Catalyst Control Center never showed up... I could not change any settings or anything. By the way, I had restarted my computer.
3. So that did not work, and I said, well, maybe I should stop what I'm doing and just go back to the way things were, and I reinstalled the proprietary driver from Hardware Drivers. That worked successfully until I restarted, and ended up with a Black screen with some green and red horizontal lines after boot up.

Things I have tried and failed: I logged in to the root system using the recovery boot up (in text only) and tried:
1. sudo dpkg-reconfigure xserver-xorg and (-p high also)
2. sudo remove xorg-driver-fglrx
3. tried deleting all signs of ati within aptitude
4. uninstall ati using sudo sh ./fglrx-uninstall.sh

I probably tried other stuff that I cannot remember off the top of my head... but still no luck...

Any help is greatly appreciated.:D


**PS my graphics card is an ATI RADEON SAPPHIRE HD 3850

---

### Post by cariboo on 2009-07-24
Create a backup of /etc/X11/xorg.conf:

```
sudo mv /etc/X11/xorg.conf.bak
```

the above command will move xorg.cong to a backup file. Then restart without any xorg.conf file at all. Then once back at the desktop you can enable whatever driver you want to use.

---

### Post by lildigiman on 2009-07-24
I tried a modified version of that:

sudo mv /etc/X11/xorg.conf *.bak

it did fail, but thanks anyway,

---

### Post by RomeReactor on 2009-07-24
Hi. Have you tried XFIX after booting in recovery?

---

### Post by lildigiman on 2009-07-24
No I have not, could you provide with some details on how to use "XFIX"?

---

### Post by RomeReactor on 2009-07-24
After booting in recovery mode, you should see XFIX along with the other options (resume, clean, dpkg, fsck, root, xfix).
[IMG]http://1.bp.blogspot.com/_LKra8AUL9bY/SRleYPWhWfI/AAAAAAAAALY/MetRjP9OxqU/s1600-h/20081111149.jpg[/IMG]

---

### Post by lildigiman on 2009-07-24
Yes, I had in fact tried that, and I tried it once more, no luck, the screen has just a bit of pink now toward the top of it. No sign of life.

---

### Post by RomeReactor on 2009-07-24
Please post the contents of your current Xorg.conf, and post how many backups you have of it:
```
ls /etc/X11 | grep xorg
```

Maybe restoring a previous one can be of help.

---

### Post by lildigiman on 2009-07-25
I'm sorry but I am running into other issues with other pcs and devices, and I am unable to copy all the files, but I can tell you I have 16 xorg.conf files, acouple of which include the failsafe, original-0 and backup

---

### Post by lildigiman on 2009-07-27
Ok, now I've used a live CD to gain access to those files, and I have looked at all of them, and tried using a couple of them, and I still get the same Results...

> 
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

### Post by lildigiman on 2009-07-30
Ok, Still no luck after I REINSTALLED the xserver using 

```
sudo apt-get install --reinstall xserver-xorg
```


Help Please! 

and Thanks!

---

### Post by stomper4x4 on 2009-07-30
I'm a noob, but when I borked my drivers (ATI of course) and got the black screen with various colorful lines on it, this is what I did.

Start in safe mode for the command prompt.

sudo apt-get remove xorg-driver-fglrx (because I tried the built in driver upgrade)
then:
sudo apt-get install xserver-xorg-video-radeonhd
then reboot.

---

### Post by lildigiman on 2009-07-30
Well, That looked very promising actually, but no, no luck. Maybe I have some other issue dealing with that... I just cannot find it though!
Any more ideas would be greatly appreciated! Thanks!

---

