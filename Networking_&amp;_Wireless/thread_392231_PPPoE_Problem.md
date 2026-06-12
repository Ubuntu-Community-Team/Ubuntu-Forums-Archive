---
title: "PPPoE Problem"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by theBIGone on 2007-03-24
Hi guys 

I just upgraded my ubuntu to 7.04. but now my PPPoE connection is gives me problems. I did the pppoeconf, and everything seems to work fine. But when i try to connect my plog gives me this:

```
joost@joost-desktop:~$ plog
Mar 24 14:51:46 joost-desktop pppd[6063]: CHAP authentication succeeded
Mar 24 14:51:46 joost-desktop pppd[6063]: peer from calling number 00:02:3B:02:93:C2 authorized
Mar 24 14:51:46 joost-desktop pppd[6063]: LCP terminated by peer
Mar 24 14:51:46 joost-desktop pppd[5966]: PPP session is 63490
Mar 24 14:51:46 joost-desktop pppd[5966]: Using interface ppp4
Mar 24 14:51:46 joost-desktop pppd[5966]: Connect: ppp4 <--> eth0
Mar 24 14:51:47 joost-desktop pppd[6121]: CHAP authentication succeeded: CHAP authentication success, unit 1137
Mar 24 14:51:47 joost-desktop pppd[6121]: CHAP authentication succeeded
Mar 24 14:51:47 joost-desktop pppd[6121]: peer from calling number 00:02:3B:02:93:C2 authorized
Mar 24 14:51:47 joost-desktop pppd[6121]: LCP terminated by peer

```

and the strange thing is when i execude the "pon dsl-provider" command enough times it will connect. but it won autoconnect anymore. In the 6.10 version of ubuntu everything worked just great. Does anyone have any idea About what to do? and i don want the awnser: go back to 6.10

thnx

Joost

---

### Post by theBIGone on 2007-03-24
now i just found out the connection terminates itself too, even when ie been active a couple of minutes, and it resets too. look:

```
Mar 24 15:14:23 joost-desktop pppd[5903]: Using interface ppp2
Mar 24 15:14:23 joost-desktop pppd[5903]: Connect: ppp2 <--> eth0
Mar 24 15:14:25 joost-desktop pppd[5903]: CHAP authentication succeeded: CHAP authentication success, unit 184
Mar 24 15:14:25 joost-desktop pppd[5903]: CHAP authentication succeeded
Mar 24 15:14:25 joost-desktop pppd[5903]: peer from calling number 00:02:3B:02:93:C2 authorized
Mar 24 15:14:25 joost-desktop pppd[5903]: LCP terminated by peer
Mar 24 15:14:26 joost-desktop pppd[6392]: Connection terminated.
Mar 24 15:14:26 joost-desktop pppd[6392]: Modem hangup
Mar 24 15:14:28 joost-desktop pppd[5903]: Connection terminated.
Mar 24 15:14:28 joost-desktop pppd[5903]: Modem hangup
joost@joost-desktop:~$ plog
Mar 24 15:14:58 joost-desktop pppd[5903]: PPP session is 63970
Mar 24 15:14:58 joost-desktop pppd[5903]: Using interface ppp2
Mar 24 15:14:58 joost-desktop pppd[5903]: Connect: ppp2 <--> eth0
Mar 24 15:15:00 joost-desktop pppd[5903]: CHAP authentication succeeded: CHAP authentication success, unit 543
Mar 24 15:15:00 joost-desktop pppd[5903]: CHAP authentication succeeded
Mar 24 15:15:00 joost-desktop pppd[5903]: peer from calling number 00:02:3B:02:93:C2 authorized
Mar 24 15:15:00 joost-desktop pppd[5903]: not replacing existing default route through ppp0
Mar 24 15:15:00 joost-desktop pppd[5903]: Cannot determine ethernet address for proxy ARP
Mar 24 15:15:00 joost-desktop pppd[5903]: local  IP address 145.94.48.236
Mar 24 15:15:00 joost-desktop pppd[5903]: remote IP address 145.94.1.0

```

---

### Post by neymac on 2007-04-07
In Feisty Fawn 7.04 when start up I have no internet connection.
The command "ps aux" says I have two pppd running.
After command "killall pppd" and "pppd call dsl provider" the internet connection works.
This did not happen in the previous (Ubuntu 6.10).
I don't know how to fix this.
My connection is pppoe through the wired network, and works fine, but not automatically after start the system.
Does anyone know the way to fix this problem?

---

### Post by saygin on 2007-04-27
I have the same problem. and I don't know how to fix it. Everytime I reboot it, I configure pppoeconf again and again. In edgy, it was better. Even after the configuration, connection speed gets 0 and then gets to the normal speed by itself. I don't know why but it is annoying.

---

### Post by saygin on 2007-04-30
And I also have the same problem about connection gets terminated by itself. What can I do? please help

---

### Post by Robban59 on 2007-05-06
Hi there,

this worked for me, try it : [http://ubuntuforums.org/showthread.php?t=422696&highlight=pppoe+dsl](http://ubuntuforums.org/showthread.php?t=422696&highlight=pppoe+dsl)

Hope this helps/Robban59

---

### Post by MarnixV on 2007-05-09
Hi,

I have the same problem. I tried what Robban59 proposed via the other thread (uninstalling network manager) but it did not have any effect.

I have figured out that after booting, when I try "sudo pon dsl-provider" I get the "terminated by peer" message. When I do "sudo poff dsl-provider", then again "sudo pon dsl-provider" I get connection everytime. No need to redo pppoeconf.

But still no automatic connection at boot, so I'm still hoping for a solution.

---

