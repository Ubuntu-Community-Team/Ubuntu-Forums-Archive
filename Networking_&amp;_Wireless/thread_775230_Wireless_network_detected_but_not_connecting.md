---
title: "Wireless network detected but not connecting"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by SomeGuy1 on 2008-04-29
I've been having major issues for quite some time with my wireless connection. For a while, it would work fine and then spontaneously drop out. For some odd reason the problem got worse at night. I would have to click the orange bar with my network name several times (and occasionally reboot) in order to make it work.

Now, I just upgraded to Hardy and had problems with my Broadcom wireless card. I was able to get that fixed (after MUCH trouble involving picking up my computer, monitor, etc. and moving it down two flights of stairs to get a wired connection, my house is a pain), but now it simply won't connect. Period. My network shows up as detected, but when I try to connect I only get the swirly blue thing and no green lights.

What can I do? Help! I'm really sick of dealing with my glitchy Internet connection. (By the way, our other computer in the house works fine, but that one is wired directly to our modem.)

Thanks!

---

### Post by Galls on 2008-04-30
> **SomeGuy1 said:**
> I've been having major issues for quite some time with my wireless connection. For a while, it would work fine and then spontaneously drop out. For some odd reason the problem got worse at night. I would have to click the orange bar with my network name several times (and occasionally reboot) in order to make it work.

Now, I just upgraded to Hardy and had problems with my Broadcom wireless card. I was able to get that fixed (after MUCH trouble involving picking up my computer, monitor, etc. and moving it down two flights of stairs to get a wired connection, my house is a pain), but now it simply won't connect. Period. My network shows up as detected, but when I try to connect I only get the swirly blue thing and no green lights.

What can I do? Help! I'm really sick of dealing with my glitchy Internet connection. (By the way, our other computer in the house works fine, but that one is wired directly to our modem.)

Thanks!

I have the same problem.  I am just gonna downgrade to Gutsy.

---

### Post by SomeGuy1 on 2008-04-30
OK, I poked around in my log and iwconfig, here are the results:

```
 tail /var/log/syslog
Apr 30 17:48:36 Danny kernel: [ 4964.755487] eth1: authenticate with AP 00:0d:72:96:ac:e1
Apr 30 17:48:36 Danny kernel: [ 4964.954026] eth1: authenticate with AP 00:0d:72:96:ac:e1
Apr 30 17:48:36 Danny kernel: [ 4965.153558] eth1: authenticate with AP 00:0d:72:96:ac:e1
Apr 30 17:48:37 Danny kernel: [ 4965.353101] eth1: authentication with AP 00:0d:72:96:ac:e1 timed out
Apr 30 17:48:41 Danny NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Apr 30 17:48:41 Danny NetworkManager: <info>  Activation (eth1/wireless): association took too long (>60s), failing activation. 
Apr 30 17:48:41 Danny NetworkManager: <info>  Activation (eth1) failure scheduled... 
Apr 30 17:48:41 Danny NetworkManager: <info>  Activation (eth1) failed for access point ([our network, I removed the name] ) 
Apr 30 17:48:41 Danny NetworkManager: <info>  Activation (eth1) failed. 
Apr 30 17:48:41 Danny NetworkManager: <info>  Deactivating device eth1. 

```

I took this to mean that the card itself seems to be working, but for whatever reason it won't connect to the network.

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:0D:72:96:AC:E1   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I also tried pinging what the network manager said was my DNS server. It said "Network is unreachable." Anyone have any ideas?

---

