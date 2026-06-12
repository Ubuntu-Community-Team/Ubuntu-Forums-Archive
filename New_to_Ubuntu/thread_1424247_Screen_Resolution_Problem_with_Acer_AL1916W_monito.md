---
title: "Screen Resolution Problem with Acer AL1916W monitor upon upgrade to Ubuntu 9.10"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by Strange1900 on 2010-03-07
Just general background to start with:
I switched to ubuntu three or four weeks ago and really have no experience with it to speak of. As a result, although this issue seems to be somewhat widespread, I can't make heads or tails of the solutions people have posted for this problem.

My graphics card is an Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10) based on the terminal output
My monitor is, as stated in the tittle, an Acer Al1916W
The problem that I'm having is the standard 800x600 max resolution in the display interface while the monitor's resolution should be 1440x900 based on what I've read.

If anyone can give me a hand by putting a solution in terms someone completely new to ubuntu or linux would understand I'd greatly appreciate it. I never expected everything with an OS like ubuntu to be plug and go so I don't mind work to get things running but it's an awfully deep pool to jump right into, I think I need water-wings XD

---

### Post by steindor2 on 2010-03-07
system > preferances > Display 
there is a drop down menu there

---

### Post by Strange1900 on 2010-03-07
Thanks for the advice but I'm afraid that menu is more or less the crux of my problem XD that menu only displays two resolutions to chose from currently: 800x600 and 640x480. The resolution I need does not appear and as a result I can't simply select it that way. As near as I can understand from what I've read this is some sort of auto detection error with the 9.10, one that was not present in 9.04, and requires a significantly more complicated operation to manually specify the proper resolution. That is, unless there's some fix that's been released which I'm unaware of? If there is please let me know XD

---

### Post by patchwork on 2010-03-07
It shouldn't be too complicated....what you will need to do is generate video timings for your monitor and add them manually to the configuration file at /etc/X11/xorg.conf

First, find your timings.....If you have the manual that came with the monitor this info might be in there, if not, you can query the system to generate suitable timings. 

```
cvt 1440 900
``` will give an output similar to this (do not use my timings, use your own!)

```
kevin@crystalpepsi:~$ cvt 1440 900
# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync

```Keep this information handy throughout this process.

Now, open your xorg.conf for editing:

```
 gksu gedit /etc/X11/xorg.conf
```

In the Monitor Section, add:
```
HorizSync 28.00-XX.XX      ###Where XX.XX is slightly above the hsync value from your cvt output (don't go crazy)
Modeline xxxxxxx      ## Copy the Modeline from your cvt output and paste it here

```
In the Display Section, add:```
 Modes "name_of_mode_from_modeline" # "1440x900_60.00" in my example
```

BEFORE RESTARTING THE X SERVER--if you cannot access the GUI , try dropping to the console by hitting CTRL+ALT+F1, and login.

You can edit the /etc/X11/xorg.conf using nano, or view your /var/log/Xorg.0.log from the console if something is still not working correctly.  

Restart X, and let's see where you stand (May still have to tweak some more settings):```
sudo service gdm restart
```

---

### Post by hobo14 on 2010-03-07
Try following this howto: [http://ubuntuforums.org/showthread.php?t=1346125]("http://ubuntuforums.org/showthread.php?t=1346125")

---

### Post by Strange1900 on 2010-03-07
Thanks a ton :D not enough time tonight since I have to be up by 5 or some other ungodly hour for school tomorrow but I'll give it a go as soon as I get home. I quick question though, doesn't 9.10 no longer have the xorg files? I'm not sure but I was under that impression.

---

### Post by patchwork on 2010-03-08
If your system can read your monitor's EDID, a default configuration is loaded for the X server (and the xorg is not required).  Unfortunately, a few systems still require the xorg.conf until this can be resolved.

---

### Post by Strange1900 on 2010-03-09
The link in hobo41's reply was quite excellent. If anyone's having the same problem and stumbles across this thread I'd definitely recommend going with that :)

---

