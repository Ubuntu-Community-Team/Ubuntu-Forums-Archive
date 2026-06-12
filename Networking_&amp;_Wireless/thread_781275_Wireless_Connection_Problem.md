---
title: "Wireless Connection Problem"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by OffHand on 2008-05-04
Hi Guys,

I have problems connecting to my girlfriend's wireless network. Usually it starts working after I reboot the router. I have no issues if I am on Vista.

Help is greatly appreciated.

 lsmod | egrep 'Module|iwl|ipw'
Module                  Size  Used by
iwl4965               105844  0 
iwlwifi_mac80211      219108  1 iwl4965
cfg80211               15112  1 iwlwifi_mac80211


wlan0     IEEE 802.11g  ESSID:"SpeedTouchC26C3F"  Nickname:""
          Mode:Managed  Frequency:2.447 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted


sudo lshw -C Network
Password or swipe finger: 
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1f:3b:41:e7:f7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.1

May  3 23:55:21 Martijn-PC kernel: [  288.174497] wlan0: Initial auth_alg=0
May  3 23:55:21 Martijn-PC kernel: [  288.174502] wlan0: authenticate with AP 00:90:d0:e7:67:f9
May  3 23:55:21 Martijn-PC kernel: [  288.176809] wlan0: RX authentication from 00:90:d0:e7:67:f9 (alg=0 transaction=2 status=0)
May  3 23:55:21 Martijn-PC kernel: [  288.176813] wlan0: authenticated
May  3 23:55:21 Martijn-PC kernel: [  288.176815] wlan0: associate with AP 00:90:d0:e7:67:f9
May  3 23:55:21 Martijn-PC kernel: [  288.180339] wlan0: invalid aid value 0; bits 15:14 not set
May  3 23:55:21 Martijn-PC kernel: [  288.180344] wlan0: RX ReassocResp from 00:90:d0:e7:67:f9 (capab=0x11 status=12 aid=0)
May  3 23:55:21 Martijn-PC kernel: [  288.180346] wlan0: AP denied association (code=12)
May  3 23:55:21 Martijn-PC kernel: [  288.376502] wlan0: associate with AP 00:90:d0:e7:67:f9
May  3 23:55:21 Martijn-PC kernel: [  288.379841] wlan0: invalid aid value 0; bits 15:14 not set
May  3 23:55:21 Martijn-PC kernel: [  288.379848] wlan0: RX ReassocResp from 00:90:d0:e7:67:f9 (capab=0x11 status=12 aid=0)
May  3 23:55:21 Martijn-PC kernel: [  288.379851] wlan0: AP denied association (code=12)
May  3 23:55:21 Martijn-PC kernel: [  288.576387] wlan0: associate with AP 00:90:d0:e7:67:f9
May  3 23:55:21 Martijn-PC kernel: [  288.580247] wlan0: invalid aid value 0; bits 15:14 not set
May  3 23:55:21 Martijn-PC kernel: [  288.580253] wlan0: RX ReassocResp from 00:90:d0:e7:67:f9 (capab=0x11 status=12 aid=0)
May  3 23:55:21 Martijn-PC kernel: [  288.580257] wlan0: AP denied association (code=12)
May  3 23:55:22 Martijn-PC kernel: [  288.717958] wlan0: association with AP 00:90:d0:e7:67:f9 timed out

---

### Post by OffHand on 2008-05-04
bump - both my gf's laptop (running xp) and mine if I am running vista always connect without a problem...

---

### Post by Dougie187 on 2008-05-04
What kind of security is on her router? I mean like WEP, WPA, or mac filtering? or nothing?

---

### Post by OffHand on 2008-05-04
Wpa

---

### Post by Dougie187 on 2008-05-04
Have you tried it turning it off? Not sure if its a router-linux issue or if its just a linux issue. So try making the router open and see if it works.

---

### Post by OffHand on 2008-05-04
Well, since we can both connect under windows the router should be fine. And even if it worked without protection it would be useless because our network needs to be protected. Any other ideas?

---

### Post by Dougie187 on 2008-05-04
Well if you try it open, you might try changing your security to Mac filtering instead of wpa. I know other people who have had issues in the past with wpa. I dont know if it is still an issue, but its just an idea. Other wise, just try some general troubleshooting things to see if you can narrow down the problem. Sorry I am not more familar with setting up wifi on linux. But these are just things i would do to make it more specific.

---

### Post by OffHand on 2008-05-04
Unfortunately mac address filtering is not really secure (they can sniff it) and we have to have a secure network because of our work.

---

### Post by Dougie187 on 2008-05-04
Well. I dont know then. I just thought it might give you an idea of what was wrong. And something working in windows doesn't really mean it should work in linux.

---

### Post by Dougie187 on 2008-05-04
For another idea. Have you gone through this guide?
[http://ubuntuforums.org/showthread.php?t=202834&highlight=intel+4965](http://ubuntuforums.org/showthread.php?t=202834&highlight=intel+4965)

---

### Post by OffHand on 2008-05-04
I figured out what the problem was... The problem was that I could not acquire an IP address from the router. I immediately got connected when I told WICD (wireless manager) to use a static IP.

---

### Post by Dougie187 on 2008-05-04
Nice, glad you got it working.

---

