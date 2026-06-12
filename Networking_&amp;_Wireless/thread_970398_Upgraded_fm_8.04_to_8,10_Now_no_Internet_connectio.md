---
title: "Upgraded fm 8.04 to 8,10: Now no Internet connection"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by nuttyslack on 2008-11-04
Hi
I've just upgraded my HP laptop that was running 8.04 perfectly to 8.10. The upgrade seemed to have gone fine, but I now can't get my internet connection to work. 
I have a WiFi connection, no problem... but despite diddling around with the Firefox network settings just can't get Firefox to connect. To see if it was just FF I ran the Synaptic Package Manager and tried to "reload". It also couldn't get a connection.
So, in summary, WiFi seems to be working... but no internet connection.
--
Cheers
Mark

---

### Post by otherchirps on 2008-11-04
I'm having similar problems. After upgrading 8.04 to 8.10, my network connection fails to start.

After some hunting, doing a "sudo dhclient eth0" gets things working again -- for a while. Depending on the phase of the moon, it can work all day, or keep dropping out several times in the hour.

I notice during system start, there is now a *long* pause at the message about configuring network connections (followed by a modprobe error message about padlock_aes not being available).

I *never* see any network manager icons on the desktop menubar panel... I notice that the daemon.log, from my system startup, says:

"NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)"

Not sure if that's related.

It's really disappointing. I see all the net-buzz about how great the 8.10 network setup is, and have a very different experience. The main reason I upgraded was the hope that my wireless connection would also be picked up automatically for a change - but instead I lose my wired link as well. D'oh.

Anyone have any ideas?  Network config troubleshooting has never been my forte...

---

### Post by otherchirps on 2008-11-04
I'm having similar problems. After upgrading 8.04 to 8.10, my network connection fails to start.

After some hunting, doing a "sudo dhclient eth0" gets things working again -- for a while. Depending on the phase of the moon, it can work all day, or keep dropping out several times in the hour.

I notice during system start, there is now a *long* pause at the message about configuring network connections (followed by a modprobe error message about padlock_aes not being available).

I *never* see any network manager icons on the desktop menubar panel... I notice that the daemon.log, from my system startup, says:

"NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)"

Not sure if that's related.

It's really disappointing. I see all the net-buzz about how great the 8.10 network setup is, and have a very different experience. The main reason I upgraded was the hope that my wireless connection would also be picked up automatically for a change - but instead I lose my wired link as well. D'oh.

Anyone have any ideas?  Network config troubleshooting has never been my forte...

---

### Post by nuttyslack on 2008-11-05
Otherchirps

Thanks for expanding on the problem. I have to admit that after trying one or two suggested fixes (from another forum section) and not making much progress I chickened-out and re-installed Hardy Heron. My networking is working perfectly again. 
HH always worked perfectly for me so I think I will wait until I have a spare computer, some spare time and Ibex has been patched a bit before trying again.
--
Cheers
Nuttyslack

---

