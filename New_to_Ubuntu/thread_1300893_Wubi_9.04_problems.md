---
title: "Wubi 9.04 problems"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by matmuc on 2009-10-25
I am currently trying out Ubuntu on 2 PCs, both running Windows XP (SP3). No Problems so far on my Notebook, but plenty on the Desktop PC. My PC uses a rather simple video adapter with an Nvidia 6200 Chipset and AGP 8x. Ubuntu does not identify the adapter and I have to start up with the safe video mode.
After I started Ubuntu this way, I can install a driver, sign off, sign on, everything seems ok, the new driver runs my system with the optimal resolution of 1600 x 1200 pixels.
Ok. But now, the keyboard language is Italian and the Layout is QWERTY (US). I can correct all that, too. I am only new to Linux, but I worked with all kinds of PCs and bigger systems for more tha 20 years.
Then another thing thats strange: The Installation asked for a user name and password, but Ubuntu does not know them, when it starts up. So I create the user as well.
Then, after playing around for a while, I shut down the system.
The next time I start it - big surprise: All my settings are gone. The video driver is not recognized. I have to use safe praphics mode. Ubuntu does not know my user profile. It behaves like a live system from a dvd!
What goes wrong here? My Notebook runs without any problems. I would be very thankful for any kind of helpful information.
Thank you, curiously awaiting tips
Mathias
(p.s.: I also tried the xserver configuration terminal program that Nvidia recommends, but it only lets me change the keyboard.)

---

### Post by Paqman on 2009-10-25
> **matmuc said:**
> It behaves like a live system from a dvd!


Indeed it does. Can you post the output of this command:
```
df -h
```

---

### Post by matmuc on 2009-10-25
Here is what I get:

```

[FONT=Courier New]ubuntu@ubuntu:~$ df -h
Dateisystem            Größe Benut  Verf Ben% Eingehängt auf
tmpfs                1007M  2,4M 1005M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                1007M  2,4M 1005M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M   96K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  184K 1007M   1% /dev
tmpfs                1007M  920K 1006M   1% /dev/shm
rootfs               1007M   34M  974M   4% /
/dev/sda1              75G   65G  9,8G  87% /host
/dev/loop0            699M  699M     0 100% /cdrom
/dev/loop1            676M  676M     0 100% /rofs
tmpfs                1007M   12K 1007M   1% /tmp
/dev/loop2            9,4G  238M  8,7G   3% /target[/FONT]

```

---

### Post by matmuc on 2009-10-27
I tried 2 more installs in the mean time. Including registry clean up and removing all files and directories. The result is always exactly the same: I end up with some kind of live system. The user and password that I provide with the installation prompt are ignored and I get a sign on as "ubuntuuser". Should I simply give up, or can anybody give me an idea how to go on? Thank you for any suggestions.
Mathias

by the way: No (or only minor) problems with the Wubi-installation on my notebook (Samsung P500). Everything works fine except Wireless and the display settings for an external display, which are restricted to the internal screens resolution. But I simply did not deal with these problems, because I dedicate my spare time to the main subject described above.

---

