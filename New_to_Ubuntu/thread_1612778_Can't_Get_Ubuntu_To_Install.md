---
title: "Can't Get Ubuntu To Install"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by newb_untu on 2010-11-03
It was all going along so well...

I just recently purchased an Asus Eee PC 1215N (1.8 GHz Dual Core Intel Atom D525, 2GB) and had plans to install some sort of Linux on it from the start.  I'm attempting to put the desktop 10.10 ubuntu onto it and had the process going along well until I hit a wall.  I installed the ubuntu image onto a 4 gig Patriot flash drive and booted from it.  I went ahead to 'install ubuntu' rather than 'try ubuntu' and my install stops at the following screen: 'Preparing to install Ubuntu'.  I have more than 2.6 gigs free drive space, I'm connected to a power source, as well as the internet.  I have the other two boxes checked in order to download and install updates, click 'Forward'... and nothing... but the rotating lines within the circle icon.  I've waited more than 20 mins. and still cannot advance past that screen.  If more information about my system is needed from me, let me know.  Otherwise, can anyone help?

---

### Post by avtolle on 2010-11-03
The first thing I would try is unchecking those boxes and give it another go. That's what I had to do about a week ago. HTH.

---

### Post by sikander3786 on 2010-11-03
Slightly off topic but it might be needed later as I have seen many threads relating the problem.

10.10 installer has a minor bug. It doesn't tell you/post an error when you type some uppercase characters in username field, instead the Forward button just greys out and one comes wondering to the forums why it happened. So, keep an eye on that as well.

You can always download and install the updates later so unticking those 2 options will not hurt.

---

### Post by newb_untu on 2010-11-03
Maybe I should have waited a bit longer before posting.  I went an alternate route and used wubi to install and I'm up and running (although it downloaded the 64bit amd version instead of the 32bit i386 version I tried).  

Interesting though... I downloaded ubuntu through wubi with my internet connection, but now within ubuntu I have no internet connection.  Odd.

---

### Post by Legeril on 2010-11-03
Try 10.04 it's a lot more stable and you can always upgrade from there

---

### Post by sikander3786 on 2010-11-03
Do you see a Network Icon in the System Tray in Top panel? Right click it and see if Enable Networking is ticked.

If it is grayed out, go to Edit Connections and Add a new connection.

---

### Post by sikander3786 on 2010-11-03
> **Legeril said:**
> Try 10.04 it's a lot more stable and you can always upgrade from there
A clean install is always the better choice than upgrading. 10.04 is stable but it doesn't mean that 10.10 is not stable :-)

10.04 is LTS but 10.10 has the latest software so always, your own choice to decide...

---

### Post by newb_untu on 2010-11-03
I've run ubuntu off a USB flash drive and had my wired ethernet connection recognized immediately after ubuntu started up.  It's been years since I've had to manually enter any sort of internet settings in OS/X and even Windows... they both recognized the wired connection.  If I restart and boot into Windows 7 with the ethernet cable still attached, it recognizes the connection.  If I plug the cable into my MBP OS/X recognizes the connection too.  How is it that ubuntu off a USB drive connects to my ethernet immediately, but the installed version on my computer needs the manual settings in place?

---

