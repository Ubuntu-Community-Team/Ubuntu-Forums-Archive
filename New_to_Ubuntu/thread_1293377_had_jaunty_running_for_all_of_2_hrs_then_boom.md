---
title: "had jaunty running for all of 2 hrs then boom"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by newtocade on 2009-10-17
i need to become more linux savy and all my friends at college are raving about ubuntu. so i installed the lastest version...i think its jaunty on my oldest computer as a dual boot. the specs are a soyo mainboard (their gone now) model p4rc350 socket 478 an ati radeon 8500 and thats about it...everything else is generic or built into the mainboard. cpu is pent 4 3.0 GHz. ubuntu froze about three times then crashed hard core...it wont boot up with any recovery options and when it froze my keyboard went dead so i couldnt use any trick to recover...i would think that a system as old as that would be stable with ubuntu...i guess not...the only thing i can figure is that firefox was on every time it froze and when it crashed...are there any suggestions...trying to do a reinstall now

---

### Post by oboedad55 on 2009-10-17
> **newtocade said:**
> i need to become more linux savy and all my friends at college are raving about ubuntu. so i installed the lastest version...i think its jaunty on my oldest computer as a dual boot. the specs are a soyo mainboard (their gone now) model p4rc350 socket 478 an ati radeon 8500 and thats about it...everything else is generic or built into the mainboard. cpu is pent 4 3.0 GHz. ubuntu froze about three times then crashed hard core...it wont boot up with any recovery options and when it froze my keyboard went dead so i couldnt use any trick to recover...i would think that a system as old as that would be stable with ubuntu...i guess not...the only thing i can figure is that firefox was on every time it froze and when it crashed...are there any suggestions...trying to do a reinstall now

My first thought in a situation like this is that there is a hardware problem. Have you checked your ram?

---

### Post by newtocade on 2009-10-17
checking mem right now...about 80 % done and so far its fine ill post again at 100%...im thinking its video or fire fox(from all the other posts ive read).

---

### Post by oboedad55 on 2009-10-17
> **newtocade said:**
> checking mem right now...about 80 % done and so far its fine ill post again at 100%...im thinking its video or fire fox(from all the other posts ive read).

What kind of video card are you running?

---

### Post by newtocade on 2009-10-17
ati radeon 8500 video...when i installed the catylist it said i didnt have drivers for any radeon card installed...when i was trying to search how to install the drivers on firefox...the system froze...when i rebooted it went bak to a black screen with a slit in it showing my last viewes of the website...then nothing but blurryness...my hd light blinked a little than nothing...poof

---

### Post by newtocade on 2009-10-17
mem pass completed...no errors...according to the ubuntu boot diagnostics

---

### Post by rb0171610 on 2009-10-17
> **newtocade said:**
> ati radeon 8500 video...when i installed the catylist it said i didnt have drivers for any radeon card installed...when i was trying to search how to install the drivers on firefox...the system froze...when i rebooted it went bak to a black screen with a slit in it showing my last viewes of the website...then nothing but blurryness...my hd light blinked a little than nothing...poof
Well at if it is a hardware problem, at least now have a nice looking paper weight. ;)

---

### Post by oboedad55 on 2009-10-17
> **newtocade said:**
> ati radeon 8500 video...when i installed the catylist it said i didnt have drivers for any radeon card installed...when i was trying to search how to install the drivers on firefox...the system froze...when i rebooted it went bak to a black screen with a slit in it showing my last viewes of the website...then nothing but blurryness...my hd light blinked a little than nothing...poof

Very weird. And Windows runs okay on this machine?

---

### Post by newtocade on 2009-10-17
no...windows still works...its dual boot to a seperate hd...im not crazy...im very windows savy and have 5 working comp...im just trying new things...tried win 7but theres absolutely no drivers for anything...i know a little about unix from cade but i need to increase my knowlege with the linx base stuff

---

### Post by oboedad55 on 2009-10-17
> **newtocade said:**
> no...windows still works...its dual boot to a seperate hd...im not crazy...im very windows savy and have 5 working comp...im just trying new things...tried win 7but theres absolutely no drivers for anything...i know a little about unix from cade but i need to increase my knowlege with the linx base stuff

I don't think you're crazy. I have one Linux installation, Mepis which is based on Debian like Ubuntu and it runs horribly slow. Everything else is fine, just the latest version of Mepis. No one can explain it.

---

### Post by newtocade on 2009-10-17
starting to doubt my friends who rave about ubuntu...nothing but trouble so far...just did a reinstall gonna see how it goes.

---

### Post by oboedad55 on 2009-10-17
> **newtocade said:**
> starting to doubt my friends who rave about ubuntu...nothing but trouble so far...just did a reinstall gonna see how it goes.

Like I said above, it may be some hardware issue that Ubuntu doesn't like on your system. If it doesn't fly, try some other Linux distros, like OpenSuse, Fedora, etc. They usually have LiveCDs that you can try. I used to run OpenSuse all the time. It was my favorite distribution. It has a very good version of KDE.

---

### Post by mick55 on 2009-10-17
your problem is that ATI and Linux don't play nice.

Some ATI cards are supported by the new Radeon drivers and some are not.

 The proprietary Linux drivers support neither R100 (Radeon 7000-7500) nor R200 (Radeon 8500-9200, 9250) chips.

Your ATI chipset is not supported ,ergo you have a problem.

Now before you blame Linux, realize that all the drivers supported by Windows are not written by Microsoft,they are provided to Microsoft by the hardware manufacturers.

ATI has chosen not to write Linux drivers for those chipsets.

So be angry at ATI not Linux.

It's not an Ubuntu issue, you will have problems with any
Linux distro and ATI drivers.

peace
mick

---

### Post by newtocade on 2009-10-17
i figured it was the video...im not blaming anything...i was trying to get the drivers installed when it crashed ...and there are drivers for my vid card in linux...i just need to know how to get them installed before a melt down occurs...read my other thread"ati drivers"

---

