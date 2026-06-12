---
title: "Twinview Ubuntu 9.10"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by chriscross93 on 2009-12-19
Hello,

I just installed ubuntu 9.10 and have two monitors.  My graphics card is a GeForce 9500GT and I have the nvidia restricted drivers enabled.  My problem is that upon enabling TwinView, Gnome Panel spread across both.  Full screening windows does the same.  How can I go about setting it so that each monitor was treated as "separate" so tha tI can do things like full screen a window and only have it span the monitor it is on?  This worked for me on ubuntu 9.04 with identical hardware (and from what I can tell settings also...).  Thanks for your help!

---

### Post by audiomick on 2009-12-19
hallo.
for the panel, un-maximize it, move it to the screen you want, and maximize it. Right click on the panel, properties, the top option on the first tab "general". Might be called something slightly different, mine is in German.

As far as maximizing windows goes, that works to me. It _may_ have something to do with desktop effects. I don't remember exactly, but I know I had to mess around a bit to make it all happy.

---

### Post by Conzar on 2010-02-20
I recently upgraded to 9.10 from 9.04 and have an nvidia Geforce 8600 GT with the nvidia drivers installed.  I also have the problem of windows maximizing across both monitors. 

Anyone figure out a fix for this?  I installed the compiz manager thinking that might fix the problem, but it has not.

---

### Post by klap-in on 2010-05-02
Are you sure you use the 'twinview' option in the Nvidia drivers settings? This does handle the screens as two separate screens and not as one big screen.

---

### Post by lyall on 2010-05-02
check Twinview in Community Documentation
[https://help.ubuntu.com/community/NvidiaMultiMonitors]("https://help.ubuntu.com/community/NvidiaMultiMonitors")

and XineramaHowTo in Community Documentation
[https://help.ubuntu.com/community/XineramaHowTo]("https://help.ubuntu.com/community/XineramaHowTo")

good luck and have fun learning

---

### Post by SFCampbell on 2010-05-03
> **chriscross93 said:**
> How can I go about setting it so that each monitor was treated as "separate" so that I can do things like full screen a window and only have it span the monitor it is on?

I hate to say it but while I've been unsuccessful getting TwinView to work in the nVidia X-Server manager in versions prior to 10.04, Lucid set up TwinView on my first try without breaking a sweat.  

After I installed and enabled the nVidia proprietary drivers my x-server crashed, but after adding the following modules to my '/etc/modprobe.d/blacklist.conf'  :

[B]blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv[/B]

TwinView is finally working like it never has for me in Linux before.  I hope this info helps if you do try moving into 10.04.

---

