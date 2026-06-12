---
title: "Installation Network Problem Sis190"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by ahobo on 2007-03-28
Hey Friends,

Alright. So I finally decided to put Ubuntu on my computer -- because other previous versions of Linux havn't agreed with my box. But I downloaded the 6.10 version of Ubuntu and popped it in. It went through the install process fine except after the partitioning. It was checking some 'mirrior' probably a server for some updates. Well this seemed to take a really stinkin long time. So I exited out of the install process and opened Firefox to see what was up.

Firefox opened and I went to Google to see if I had a network. Yep. So I searched google about the network problem. That worked to. But when I clicked on Google's link to go to a site that would probably solve my problems-- it didn't work.

I tried gaim to get my friends to help me. Gaim worked, friends did not.
I tried ping. Ping worked but there was a HUGE packet loss -- upwards of 50%.

I'm thinkin I have the wrong driver.

I'm running a PC Chips board with a Sis 190 10/100 network guy. I have the pc chips install cd if that helps. But there's little to no network.

Hoping I can get some help soon... if there's more I need to post let me know.

Brad

---

### Post by chili555 on 2007-03-28
I believe the correct module is sis190. Let's see if is loaded correctly:```
lsmod | grep sis
```If a few words of text come back, including sis190, then the correct module is loaded. If it is loaded, as I suspect, let's *sudo gedit /etc/modprobe.d/blacklist* to add the following, on it's own line:```
blacklist ipv6
```Reboot and post back. Are we heroes or zeros?

---

### Post by ahobo on 2007-03-28
Yes, it did bring back some stuff. However, the last part won't / didn't work. I'm running the installation -- so it's on a live cd, and if I reboot it... well, you know.

The problem is that when I go through the installation, after it copies the partitions the disc, and copies the files it says 'checking mirror' and probably wants to update something. I don't remember-- something that starts with an 'a'. So it's stuck at 82 percent. Is there a way to bypass this?

Oh, also! At the beginning of the installation when it asks you the time zone & etc... I told it to scancronize to a webserver, and it tried to download 3 files -- but to no avail.

PS. I'm on my roommate's computer typing these forum posts.

PPS. He smells bad.

PPPS. I'm not sure, but would the campus that I'm on be blocking ubuntu, or is that not really probable? The tech support here doesn't support linux.

---

### Post by ahobo on 2007-03-28
Oh, I did the device manager where it kinda troubleshoots the devices for you. I got through it all, told it that the network didn't work, and added a few notes, and then it was going to send it to something / a server, and then 1) either did it rather fast, or 2) it gave up and exited.

---

### Post by Paul Gibbons on 2007-04-06
See post

[http://ubuntuforums.org/showthread.php?p=2410996#post2410996](http://ubuntuforums.org/showthread.php?p=2410996#post2410996)

---

### Post by charlysbrother on 2007-05-17
I have the same problem.

If i type in a terminal:

**sudo ifconfig eth0 mtu 1492**

then the problem is fixed but returns next time i restart the computer. (the mtu value resets to 1500, which doesn't work properly for some reason).

---

