---
title: "Unity 2D Session Startup Longer than Normal"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by Entyrion on 2011-05-11
Hi!

From a cold start, my Unity 2D desktop took about 15-20 seconds to fully start everything after I signed in. For some reason, when I turned on my computer today it has been taking considerably longer (40-60 seconds). When I log out and back in, the startup time is about the same, but every time I restart the computer, it is taking much longer than it did just yesterday. Does anyone know why this might be, and how to fix it?

I'm thinking back to recent changes on my laptop, but I can't really think of much. I installed LDXE through the Ubuntu Software Center the other day, and I installed a couple of distros in VirtualBox, but I did not experience this problem immediately afterwards. Other than that, I can't think of anything I've messed with that might cause this. (BTW when I log into the LDXE session, it does not really seem to have this same problem, at least not nearly to the same extent.)

Any tips? Thanks!

---

### Post by fabricator4 on 2011-05-11
> **Entyrion said:**
> Hi!

From a cold start, my Unity 2D desktop took about 15-20 seconds to fully start everything after I signed in. For some reason, when I turned on my computer today it has been taking considerably longer (40-60 seconds).

Have a look in Startup Applications and see if a recent app install or other change has added to the startup application list.  You can untick anything that you really don't need and it may speed up things a bit.  I got rid of Ubuntu one other things I don't use and it made a difference.

Chris

---

### Post by Entyrion on 2011-05-11
Thanks for the tip, that did make a small difference, but it didn't really fix the problem :( It still takes about 40 seconds after I log in to fully load my desktop; that's about double what it used to be.

After I log in, the screen hangs at the default Ubuntu wallpaper (the same wallpaper for the log in screen) for about 15-20 seconds and does literally nothing. After about 20 seconds, I get the wireless network manager notification, and about 10 seconds after that, my desktop background loads. About 5 seconds after that, the Gnome/Unity top panel is displayed, and another 5 seconds or so for all the notification apps, clock, and whatnot to finally display properly on the panel.

I think the biggest problem is the initial hang-up after I log in; the startup apps are only a small portion of the latter part of the log in process. Is there anything that would cause some sort of hangup like this immediately after login?

---

### Post by unapendeza on 2011-05-11
> **Entyrion said:**
> Thanks for the tip, that did make a small difference, but it didn't really fix the problem :( It still takes about 40 seconds after I log in to fully load my desktop; that's about double what it used to be.

After I log in, the screen hangs at the default Ubuntu wallpaper (the same wallpaper for the log in screen) for about 15-20 seconds and does literally nothing. After about 20 seconds, I get the wireless network manager notification, and about 10 seconds after that, my desktop background loads. About 5 seconds after that, the Gnome/Unity top panel is displayed, and another 5 seconds or so for all the notification apps, clock, and whatnot to finally display properly on the panel.

I think the biggest problem is the initial hang-up after I log in; the startup apps are only a small portion of the latter part of the log in process. Is there anything that would cause some sort of hangup like this immediately after login?

I experienced the same problem. This worked for me:
Restart your computer or log out. Before you log in again select "Ubuntu Classic" at the bottom panel. 
There might be a way to fix the problem of the unity desktop taking so long to load but I was happy with this solution anyway because I'm not really a fan of the unity desktop.

---

### Post by Entyrion on 2011-05-11
Thanks for the tip :)

Like I said, the LXDE session logs in nice and quick too, so if I get completely fed up, I can use Gnome 2 or LXDE. My issue is that the Unity 2D session did not take so long in the past, so if there is any way to get it back to normal, that would be ideal. Like I said, when I simply log out of one session and into the Unity 2D session, it boots as quickly as it used to; it loads my desktop background almost instantly, and the panel + icons within 15-20 seconds no problem. It just hangs for that extra 20 seconds when booting into Unity 2D from a cold restart. >.<

---

### Post by fabricator4 on 2011-05-13
> **Entyrion said:**
> Thanks for the tip :)

Like I said, the LXDE session logs in nice and quick too, so if I get completely fed up, I can use Gnome 2 or LXDE. My issue is that the Unity 2D session did not take so long in the past, so if there is any way to get it back to normal, that would be ideal. Like I said, when I simply log out of one session and into the Unity 2D session, it boots as quickly as it used to; it loads my desktop background almost instantly, and the panel + icons within 15-20 seconds no problem. It just hangs for that extra 20 seconds when booting into Unity 2D from a cold restart. >.<


It sounds like it's stopping and waiting for some hardware.  Have you changed anything in the config or BIOS?  Try looking at the log entries to see if there's anything obvious in there that's timing out or waiting for an extended period.

Chris

---

### Post by Entyrion on 2011-05-13
Ok, but how do I go about looking up the logs?

---

### Post by wildmanne39 on 2011-05-13
> **Entyrion said:**
> Hi!

From a cold start, my Unity 2D desktop took about 15-20 seconds to fully start everything after I signed in. For some reason, when I turned on my computer today it has been taking considerably longer (40-60 seconds). When I log out and back in, the startup time is about the same, but every time I restart the computer, it is taking much longer than it did just yesterday. Does anyone know why this might be, and how to fix it?

I'm thinking back to recent changes on my laptop, but I can't really think of much. I installed LDXE through the Ubuntu Software Center the other day, and I installed a couple of distros in VirtualBox, but I did not experience this problem immediately afterwards. Other than that, I can't think of anything I've messed with that might cause this. (BTW when I log into the LDXE session, it does not really seem to have this same problem, at least not nearly to the same extent.)

Any tips? Thanks!

Hi, I was have a problem like that and it was my nividia card slowing down the boot screen, I just what to switch drivers.

---

### Post by fabricator4 on 2011-05-14
> **Entyrion said:**
> Ok, but how do I go about looking up the logs?

The logs can be found in /var/logs

You can also use the log file viewer utility.  It's called "Log File Viewer".

Have a look at sys.log, kern.log, dmesg, and Xorg.0.log

You're looking for anything that has an extra large time gap before the next entry, which might indicate a problem loading or setting something.

Chris.

---

