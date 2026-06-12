---
title: "Please Help, stuck in resolution 800x600 for a week"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by vanspud on 2010-07-12
Hi,

I installed Ubuntu over a week ago now, I'm excited to get up and running but I can't fully enjoy it yet as my screen resolution is stuck in 800x600 as a result everything is grossly over sized.

When I go System - Preferences - Monitors , it doesn't give me a higher option from the dropdown.

I tried System - Administration - Hardware Drivers and it just says "no proprietry drivers are in use on this system"

I google the problem every night when I get in and most posts seem to mention about editing your "xorg.conf" file in /etc/x11/ but when I go to this folder there is no xorg.conf file, so I try creating one but it doesn't allow me to do anything with the folder because I'm not the owner, I tried moving in a xorg.conf file I created starting the command with sudo but I just can't seem to get the file into the x11 folder.

I'm a broken man at this stage, can anybody help? I have an "Advent" laptop that has Vista on it, I have dual booted Ubuntu 10.04 onto it. My plan was to kick Vista off when I got settled in Ubuntu but that seems unlikely if I can't get the screen sorted.

I appreciate any help/ advice I can get, this is my first go at Linux so happy to learn.

---

### Post by j.bell730 on 2010-07-12
Go to **Applications** > **Accessories** > **Terminal** and copy and paste the following...
```
lspci | grep VGA
```

Post here what comes up after that.

---

### Post by roger_1960 on 2010-07-12
Hi

Do post the output from j.bell730's post as we need to know what graphics card you have.

To create xorg.conf use

> sudo gedit /etc/X11/xorg.conf

Note the X11 not x11

---

### Post by vanspud on 2010-07-13
Hey,

Thanks for replying j.bell730 and roger_1960! Here's what I get back when I enter that command in the terminal...

------------------------------

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

-------------------------------

ps is there a quick way to copy terminal output? I had to write that out, control+c didn't do it.

---

### Post by j.bell730 on 2010-07-13
> **vanspud said:**
> Hey,

Thanks for replying j.bell730 and roger_1960! Here's what I get back when I enter that command in the terminal...

------------------------------

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

-------------------------------

ps is there a quick way to copy terminal output? I had to write that out, control+c didn't do it.

Your drivers were pre-installed, so, there is no need to download anything.

I believe [this post]("http://www.linuxforums.org/forum/ubuntu-help/76770-silicon-integrated-systems-sis-driver.html#post396209") (by 'towy71') should help you out with your other issues.

To copy from the terminal, use Control + **Shift** + C.

---

### Post by vanspud on 2010-07-13
I ran the command from "[towy71]("http://www.linuxforums.org/forum/members/towy71.html")" (sudo dpkg-reconfigure xserver-xorg) and the first time I got this back...

"debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline"

I restarted, tried it again and I got no error so I assumed it worked, I checked for a "xorg.conf" file and there was one there, however I couldn't edit it(as I am not the owner I know), so I restarted thinking this is it and on the restart it said something like...

"Ubuntu is running in low graphics mode", anyway it said I had to reconfigure my graphics, so I followed the steps and on start up my screen remains the same and now just has a "xorg.conf.failsafe" file with the following...

---------------------
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
---------------------

Think I'm going to have to call it a night once more, live to fight another day. Thanks for your help, I appreciate it.

---

### Post by vanspud on 2010-07-13
I should have also added, the second time I ran it and it didn't say anything back and I assumed it had worked and seen the created "xorg.conf" file, it contents were as follows...

Section "Device"
    Identifier "device1"
    VendorName "Silicon Integrated Systems [SiS]"
    BoardName "SiS SiS 670 / 671-based cards"
    Driver "sis"
    Option "DPMS"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection


-----------------------

When I restarted is when I was told it's running in low graphics mode and I had to reconfigure.

---

### Post by vanspud on 2010-07-24
Hey,

Just encase anybody is reading this tread with the same issues as me, a good man pointed me in the direction of this tread....

[http://ubuntuforums.org/showthread.php?t=958967&page=38](http://ubuntuforums.org/showthread.php?t=958967&page=38)


and by following the steps their it fixed my problem, so I can now start enjoying Ubuntu.

ps you'll have to write some of the steps out as you've to type them on a blank screen so you can't see what your doing. 

Delighted it's fixed now!

---

### Post by mhgsys on 2010-07-25
;)

~Nice~



Please mark your thread as solved; 

Go to thread tools > Mark this thread as solved. 

mhgsys.

---

### Post by vanspud on 2010-07-25
Thanks for that, I was looking how to mark it solved but couldn't see how.

---

