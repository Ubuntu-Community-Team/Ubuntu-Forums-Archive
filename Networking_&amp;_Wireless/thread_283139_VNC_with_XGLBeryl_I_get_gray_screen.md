---
title: "VNC with XGL/Beryl??? I get gray screen"
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by JayTee on 2006-10-23
Yesterday I followed the How-To on installing XGL with NVidia drivers and the Beryl Manager and Emerald Themes. It all worked fine but something has broken my VNC capability. I dug around on the forums and found a good howto and tried loading vnc4server and I was then able to connect but the screen is all gray. I've read through a ton of threads so far and have found a couple people who've posted the same problem but I haven't found a solution yet. Anyone have a link or know what might be the cause. I know it has something to do with using XGL/Beryl and the new NVidia drivers but I'm not sure where to start digging into the configuration and being something of a NOOB I'm afraid I'll mess things up even more.

[Edit} Solved: I used the info in this post reply to a How-To on VNC.
[http://www.ubuntuforums.org/showpost.php?p=1492627&postcount=149](http://www.ubuntuforums.org/showpost.php?p=1492627&postcount=149)
Now I can remote into my Ubuntu 6.06 system on session 0 with XGL/Beryl running and I don't get the gray screen anymore.
Special thanks to kb5won and Tichondrius for the original How-To
This is the best support forum on the planet and YOU ALL ROCK!!!!

---

### Post by jkroto on 2006-10-24
When you remote in to your machine on '0' is it using the Xgl/Beryl settings or does it use a different window manager for the session?  I have Beryl installed now and want to VNC but haven't been able to make it work yet with the vanilla Ubuntu 6.06 remote desktop (as I did prior to installing Xgl/Beryl).

> **JayTee said:**
> 
[Edit} Solved: I used the info in this post reply to a How-To on VNC.
[http://www.ubuntuforums.org/showpost.php?p=1492627&postcount=149](http://www.ubuntuforums.org/showpost.php?p=1492627&postcount=149)
Now I can remote into my Ubuntu 6.06 system on session 0 with XGL/Beryl running and I don't get the gray screen anymore.
Special thanks to kb5won and Tichondrius for the original How-To
This is the best support forum on the planet and YOU ALL ROCK!!!!

---

### Post by JayTee on 2006-10-24
I used X11vnc but I've since discovered that I can't get vnc to do authorization. I can connect fine and to my Ubuntu computer and XGL/Beryl is running but I don't get prompted for a password and reading through the how-to and man files hasn't helped. I posted something here earlier. I'll have to check back in a couple days to see if anyone's answered. I'm glad I don't have to rely on this computer for anything really serious yet since XGL/Beryl is still pretty much beta. I'm not sure what's messing up my authorization but trying to add the lines to xorg.conf to fix the password problem didn't do anything. Adding the lines to start vnc in xorg.conf caused the xserver to crash. Glad I backed up my xorg.conf file before I messed around with it.

---

### Post by jkroto on 2006-10-27
Have you checked out this site.  I haven't tried it yet but plan to  when next I get a chance.
[http://www.karlrunge.com/x11vnc/#faq-passwd]("http://www.karlrunge.com/x11vnc/#faq-passwd")

> **JayTee said:**
> I used X11vnc but I've since discovered that I can't get vnc to do authorization. I can connect fine and to my Ubuntu computer and XGL/Beryl is running but I don't get prompted for a password and reading through the how-to and man files hasn't helped. 

---

### Post by JayTee on 2006-10-27
Yeah, I got that fixed but hadn't been on here to update my post. I used the same site you posted and added the -rfbauth line to the X11vnc startup script that I have setup to run X11vnc whenever I logon. Now it works and works fine over my local lan but it's a bit slow but usuable over the internet from work. I can live with it though. I usually remote into my other home computer from work anyways. I'm glad I got it working because I can see lots of blocked connections to my vnc port on Firestarter.

---

### Post by thespinesplitter on 2007-10-22
use NX it is superior to VNC, logs in via SSH (so it is secure) and uses its own xserver which works no matter what... it is nearly zero-conf

---

