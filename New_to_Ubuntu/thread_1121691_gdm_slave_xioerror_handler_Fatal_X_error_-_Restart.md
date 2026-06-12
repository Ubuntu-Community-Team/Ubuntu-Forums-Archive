---
title: "gdm_slave_xioerror_handler: Fatal X error - Restarting :0"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by Jason2gs on 2009-04-10
My X will randomly crash/restart with the error message in my /var/log/syslog:

gdm_slave_xioerror_handler: Fatal X error - Restarting :0

It does it often when I maximize/minimize a window, etc., but sometimes I don't even need to do that. Sometimes it will do it when the monitor is shut off. (That is, I'm not using the computer ATM.)

It's become extremely obnoxious lately, and I'm hoping someone around here can help me with it.

Thanks,

-Mike

---

### Post by Jason2gs on 2009-04-10
Bump.

---

### Post by cariboo on 2009-04-10
How about a little more information, like what kind of graphics adapter do have and what driver are you using?

Jim

---

### Post by Jason2gs on 2009-04-11
Right. Of course. GeForce 8600 GT and the proprietary driver. (From the Restricted Drivers Manager.)

Is that what you wanted?

---

### Post by Jason2gs on 2009-04-12
Bump.

Happened again today.

Wasn't even using the computer. Monitor was unplugged, and I was leaving for church.

gdm[14213]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0

It's getting extremely annoying.

---

### Post by Erektium on 2009-04-25
I have the same problem. I'm using xf86-video-ati from the repos. my card is x800gto. and I'm using compiz. 9.04 in use

---

### Post by peterx14 on 2009-05-03
I'm in the process of configuring my new 9.04 install now and I just encountered the same problem. For me, the screen suddenly had junk on it (just random junk in graphics memory or something... it was mostly horizontal lines), and after about a second (+/- half a second!), I got different junk and shortly after the login screen appeared.

My hardware is:
Dell Dimension 3000, 2.8GHz Celeron, 2GB RAM
nVidia GeForce 6200 PCI graphics card with 256MB RAM

My /var/log/syslog entries around this time say:
```
May  3 23:55:42 kafka kernel: [35450.313695] [22237]: host clock rate change request 83 -> 0
May  3 23:55:42 kafka kernel: [35450.326361] vmmon: Had to deallocate locked 113658 pages from vm driver c5b22000
May  3 23:55:42 kafka kernel: [35450.332123] vmmon: Had to deallocate AWE 5398 pages from vm driver c5b22000
May  3 23:55:42 kafka kernel: [35450.334921] device eth0 left promiscuous mode
May  3 23:55:45 kafka kernel: [35450.334932] bridge-eth0: disabled promiscuous mode
May  3 23:55:45 kafka gdm[2686]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
May  3 23:55:47 kafka acpid: client 2690[0:0] has disconnected 
May  3 23:55:47 kafka acpid: client 2690[0:0] has disconnected 
May  3 23:55:47 kafka acpid: client connected from 22993[0:0] 
May  3 23:55:48 kafka acpid: client connected from 22993[0:0] 
May  3 23:56:16 kafka pulseaudio[23194]: pid.c: Stale PID file, overwriting.

```

I was in the middle of something right when it crashed, so it wasn't like the screensaver was just about to kick in or anything.

Oh... and I am running Compiz!

---

### Post by peterx14 on 2009-05-06
Same problem again.... twice! Actually, I didn't see so much "noise" on the screen if any; just the login screen all of a sudden.

Again, here's the section of /var/log/syslog when the problem occurred:
```
May  6 10:49:48 kafka x-session-manager[3502]: WARNING: Detected that screensaver has left the bus 
May  6 10:49:49 kafka kernel: [  814.848462] [4488]: host clock rate change request 83 -> 0
May  6 10:49:49 kafka kernel: [  814.854769] vmmon: Had to deallocate locked 126762 pages from vm driver f4270000
May  6 10:49:49 kafka kernel: [  814.860204] vmmon: Had to deallocate AWE 5412 pages from vm driver f4270000
May  6 10:49:49 kafka kernel: [  814.878280] device eth0 left promiscuous mode
May  6 10:49:49 kafka kernel: [  814.878291] bridge-eth0: disabled promiscuous mode
May  6 10:49:49 kafka gdm[2952]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
May  6 10:49:50 kafka acpid: client 2956[0:0] has disconnected 
May  6 10:49:50 kafka acpid: client 2956[0:0] has disconnected 
May  6 10:49:50 kafka acpid: client connected from 4640[0:0] 
May  6 10:49:51 kafka acpid: client connected from 4640[0:0] 

```

It may or may not be a coincidence, but I am running VMware Workstation (5.5.9) every time I've had this problem.

---

### Post by cviorel on 2009-05-14
I experienced the same error:
```

[cviorel-T61 ~]$ cat /var/log/syslog | grep x-session
May 14 21:23:01 cviorel-T61 x-session-manager[4031]: WARNING: Detected that screensaver has left the bus

```

Here are the specs of the computer where I ecoutered the error:
```

cat /proc/version
Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009

lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.04
Release:	9.04
Codename:	jaunty

cat /proc/cpuinfo | egrep '^model name'
model name	: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
model name	: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz

lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1)

```

---

### Post by cviorel on 2009-05-21
Solved by installing the latest stable driver from NVDIA. I attached a script that will get the lastest (stable, NOT beta) driver from NVIDIA's ftp and will install it.

---

### Post by geektanic on 2009-06-01
> **cviorel said:**
> Solved by installing the latest stable driver from NVDIA. I attached a script that will get the lastest (stable, NOT beta) driver from NVIDIA's ftp and will install it.

I'm not sure where else you're getting your drivers from but the 1.80 driver is exactly what I've been using and I've been experiencing the exact same issue as you described.

What I've actually done is rollback my system to the 1.73 (which prior to this most recent full wipe/install has been perfectly stable for me)

We'll just have to wait and see if the issue returns though.

System Info: 
```
geektanic@monolith:~$ cat /proc/version
Linux version 2.6.28-11-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009

geektanic@monolith:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty

geektanic@monolith:~$ cat /proc/cpuinfo | egrep '^model name'
model name    : Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
model name    : Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
model name    : Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
model name    : Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz

geektanic@monolith:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)

```

---

### Post by ballin on 2009-08-11
I am getting this problem, and using nVidia drivers 185.18.14

I saw a thread for this dating back to 2005 with no resolution : [http://ubuntuforums.org/showthread.php?t=96068](http://ubuntuforums.org/showthread.php?t=96068)

Some blame nVidia, some don't!

---

