---
title: "Sytem time problem after reboot"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by just4_me_only on 2010-06-03
I have been struggling with this problem for last couple of days. Did lot of googleing on linux date/time but no luck yet. I'm ruuning ubuntu server 8.10. I changed date and time using date command. Set hardware clock to same as system clock. But i don't see my system time changed after the reboot. It still shows old time.  But my hardware clock changes to what i set. Problem is with system time. I'm wondering how on earth it is resetting to old time after the reboot. It must be coming from external system or must be stored somewhere. I made sure that ntpd is not running. Does any one seen this kind of behavior? Any suggestions are welcome.
Or Does ubuntu server getting network time as part of reboot?

note: if i disconnect ethernet cable,i see my date command working even after the reboot.

---

### Post by marshmallow1304 on 2010-06-03
The fact that disconnecting the ethernet cable prevents the time from changing suggests that the time is coming from a time server.  [This page]("https://help.ubuntu.com/9.04/serverguide/C/NTP.html") says that Ubuntu comes with ntpdate by default so if you want to disable time synchronization, you'll need to remove it.

---

### Post by Keith Myers on 2010-06-03
[SIZE=3]I am having problems with date/time also.  In my case, I have been installing Ubuntu 10.04 multiple times in an effort to get Grub2 to see my other OS.  I see that it goes out to an NNTP server at the very beginning of the install.  The desktop time in Ubuntu is correct after install.  I then shut down the OS and reboot into my other OS where I discover that it's time is now off by -7 hrs.  That difference just so happens to be the current daylight savings time zone adjustment for my location relative to UTC time. So why is Ubuntu going into the computer BIOS time setting and making a change there.  Why doesn't it adjust the time via its software settings.  My other OS doesn't do any kind of time server adjustments at all.  It simply reflects the time in the system BIOS.  How can I prevent Ubuntu from messing with the system BIOS time?:(

Keith
[/SIZE]

---

### Post by just4_me_only on 2010-06-04
marshmallow1304,

 Thanks a ton. I moved /etc/network/ntpdate to other folder. It worked.

Keith Myers,

         You can do the same to avoid time sync from network. Not  sure if you can find ntpdate in the same directory as you have different ubuntu version. look for ntpdate and move it to some where else. At least this trick worked for me.


Thanks
Kishore S

---

### Post by marshmallow1304 on 2010-06-05
@ Keith Meyers

It sounds like Ubuntu is on UTC and Windows (I assume this is the "other OS") is on local time.  Ubuntu (like other *nix systems, including Mac) sets the system clock to UTC and then uses software to apply the time zone.  Windows, on the other hand, sets the system clock to the local time.  To fix this, you can set Ubuntu to use local time:


```
gksudo gedit /etc/default/rcS
```

There may be a line that says
```
UTC=yes
```
If so, change it to
```
UTC=no
```
If not, add this line:
```
UTC=no
```


This will cause Ubuntu to use local time so that the system clock will remain "correct" for Windows.

---

### Post by Keith Myers on 2010-06-06
Hi, and thanks for the info and tip.  No the OS I was referring to was eComStation, a variant of OS/2.  I altered the UTC setting and I will reboot to check the time in the BIOS.  I think it will work since I suspected exactly what you explained.  Thanks again.

Keith:P

---

### Post by Keith Myers on 2010-06-06
Just a quick FYI.  Now that I have set UTC=no, I am not getting the system time reset to UTC and messing up the time in eComStation. So that little bit of trouble I was having with Ubuntu is resolved.  Thanks everyone.  Now if I could just figure out why Ubuntu keeps crashing........

Keith
:(

---

