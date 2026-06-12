---
title: "Random disconnects"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by MachineBucket on 2006-09-06
I have a problem using wired ethernet connections with my Gateway laptop. After about 15 minutes or so after being connected, I can no longer recieve any data or go to any web pages through the connection. The integrated card is a Marvell 88E8036 Fast Ethernet Controller, with the OEM vendor being Rioworks. The driver linux is using in the sky2 driver. I also have this problem when using any wireless networks as well. Network manager still shows a connection. Even after unplugging and reconnecting the cable I can't connect. A reboot solves the problem, but rebooting every 15 minutes isn't a plausible solution. Another note: when using a external dialup modem I don't have any problems.

Thanks for any help.

---

### Post by MachineBucket on 2006-09-11
Does anyone have any ideas?

---

### Post by tbonius on 2006-09-11
What (if any) info does dmesg show ?

T

---

### Post by riondluz on 2006-09-25
i have the exact same problem on a toshiba satellite laptop. Very frustrating when trying to xfer files; ssh, wget, whatever: no go. The connection hangs then times out. I have to open the Network manager and repeatedly restart the  interface, or, just as stupidly, /etc/init.d/networking restart, as vain attempts to keep the IF open for traffic. Blows chunks as well as my patience. Wireless OK, no problems there. Same Marvell integrated card, same sky2 drivers. I've searched long and hard and have found no advice, either here or elsewhere.  Lets fix this thing, because i really am happy with ubuntu in general, and everything else (including xen) works fine (AFAIK).
Rion (riondluz_at_gmail_dot_com)

---

### Post by riondluz on 2006-09-25
thought you might like to know, if you havent found out already, that the fix is in and is rather simple. After downloading the latest/greatest marvell sk98lin driver and building it, i found that it wasnt needed after all.
The simple fix is this:
 If lshw -C network
exposes this:
configuration: autonegociation=on
then you can get your network stablilzed by typing this:
ethtool -s ethN autoneg off

After restarting the network (eth1 for me) and doing above, i was able to x-fer anything i cared to w/out interuption.

Hope that it helps and isnt a day late/$ short

---

### Post by ChrisStockton on 2007-02-11
Sir, I had to register for these forums just to thank you, I have had this same problem and since I have to constantly access my computer from work it is very frustrating to lose ssh connection to it.

I've gone to a extreme extent to try and resolve this, but I hope this fixes it. If tomorrow you see no post taking this back :p then you know it's fixed and boy do I want to say thanks.

=)

-Chris

---

