---
title: "Wireless came and went"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by east_stingray on 2008-07-04
I just installed Ubuntu 8.04 the other night and was immediately able to connect to my rather peculiar internet connection (Wireless broadband comes through PCI of master computer and is then shared over ethernet to a router).  For some reason, the wireless has stopped working, although a hardwired connection still works.

When I right click on the networking icon, I only have "enable networking" and no "enable wireless".  When I left click, I have "Wired Network", which is ghosted, and "Manual configuration".

To connect in windows, I have to point my machine to the master computer as a gateway, and this is how I originally had the wireless working.  Even though it's not visible when I left click on the networking icon, my wireless shows up in the network settings menu.

I'm new to linux and not very good with command-line stuff.  I tried to work through some of the advice in other threads, but it didn't seem to be helping me.  I did determine through one of the lines of command in another thread that my wireless device DOES have drivers installed (I don't remember the command at the moment).  Any help is much appreciated.

---

### Post by east_stingray on 2008-07-04
Update:

I tried to get this to work for some time by changing settings on the master computer (IP config), router, and my Ubuntu machine and nothing worked.  When I was done I changed them all back so that the rest of the computers around here would work.  Then on a whim I checked the "enable roaming" box and suddenly I had the "enable wireless" on right click and it showed my router on left click.

If I try to uncheck the "enable roaming" so that I can enter my gateway information, both of those things go away.  So, in a way I've made progress... I'm able to connect to my router.  Unfortunately I'm still without internet access through the router.  Any ideas on how to give Network Manager gateway information without it taking away my "enable wireless" and showing my wireless network?

---

### Post by east_stingray on 2008-07-04
Well, at first I was just trying to do this "right", but I got pissed enough that I went non-conventional.  Network manager absolutely WAS NOT going to let me give it a gateway.  I'm sure there's something really simple I was doing wrong or didn't know, but at any rate it wasn't having any of that.

In some menu I discovered (not surprisingly) that Ubuntu was using 0.1 as it's gateway, which was the router itself.  I finally just changed the router's IP to 0.2 and made the master computer 0.1.  I am now typing this on the laptop, running Ubuntu (rather than on the master computer using windows).

This is not an ideal setup as far as I'm concerned, because I like to leave things conventional (like having my routers as 0.1), but I guess if it works I can't do too much complaining.

---

### Post by east_stingray on 2008-07-06
I've discovered something peculiar about this setup: every time I reboot my computer, the gateway changes to whatever the router's IP is.  Thus, each time I reboot I have to go swap the IPs of the router and the master computer.  This is getting old quick.  Any ideas?

---

### Post by tua03332 on 2008-07-06
I have the a similar problem in that wireless networking will not show up under the network manager, but I did read somewhere here that there is a bug with Ubuntu8.04.  If I ever figure this one out, I will let you know.

---

