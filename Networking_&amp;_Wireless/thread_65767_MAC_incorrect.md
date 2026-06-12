---
title: "MAC incorrect"
date: 2005-09-15
forum: Networking &amp; Wireless
---

### Post by paxmark on 2005-09-15
I do Kubuntu  5.04

kwifilan tool recognizes the Dlink DWL-520+ and the DI-5214 router.  I am getting fair strength considering the run in house and floor - but I cannot acess the internet via lynx or konqueror or mozilla.  Stumped.  [It also sees the Christian school nearby with no encryption.]

I get via iwlist and iwconfig

wlan0     Scan completed :
          Cell 01 - Address: 00:13:46:3E:B1:B2
                    ESSID:"default"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/100  Signal level=41/100  Noise level=0/100
                    Encryption key:off
                    Bit Rate:36 Mb/s

after iwconfig

lo        no wireless extensions.

wlan0     IEEE 802.11b+  ESSID:"default"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:3E:B1:B2
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=176/255
          Retry min limit:7   RTS thr:off
          Encryption key:off
          Power Management:off
          Link Quality=57/100  Signal level=41/100  Noise level=0/100

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

Funny, the mac is shown as 00-13-46-3e-b1-b3  [Not b2   !!] via browser on 192.168.0.1 (ethernet linkage downstairs to router) and also via Win 98 dlink program on this computer.    

Is it my MAC address being seen as wrong?  Or something else I am overlooking.  I am getting tired of browsing the web in Windows.  

Yes, I will get encryption up and running as soon as I get browsing in linux, that is the next step.

tia   peace mark

---

### Post by mlomker on 2005-09-15
[QUOTE=paxmark]Is it my MAC address being seen as wrong?  Or something else I am overlooking.  I am getting tired of browsing the web in Windows.  
[/QUOTE]

That's normal.  Every ethernet port needs a unique mac address.  In this case, one for wired and another for wireless.

Does the machine get an IP address?

What does **ifconfig** show you?  Try the **dhclient wlan0** command if it doesn't have one.

---

### Post by paxmark on 2005-09-17
I cut and pasted ifconfig ind iwconfig working on a reply, but then tried the dhclient wlan0 and that set something in motion that got it to put in 192.168.0.1 as the ip address and so now I am using kubuntu to roam the internet and syanptic is applying changes.  

Next thing is to install a cipher.  Yeah, makes sense that there is two MAC's, one  for lan and one for wlan.

Thanks much, the dhclient wlan0 worked like a charm.  I still need to find out why wifi does not start out of the box (I have to keep going into sudo to kwifimanager to get it to see the router, but I can handle that.

Thanks again.

peace,  mark

---

