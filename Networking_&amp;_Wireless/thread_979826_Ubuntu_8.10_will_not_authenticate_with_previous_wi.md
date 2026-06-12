---
title: "Ubuntu 8.10 will not authenticate with previous wireless when resuming from hibernate"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by speedkreature on 2008-11-12
I looked at _*[this thread]("http://ubuntuforums.org/showthread.php?t=865034")*_ and *_[that thread]("http://ubuntuforums.org/showthread.php?t=816357")_* but neither are really what's happening; and the first one deals with ndiswrapper which makes it completely irrelevant. 

My problem is this: after resuming from hibernate on my IBM T43, my wireless chipset detects all the wireless networks that were previously there.  There is one in particular that I usually connect to.  Now that I have hibernated, I cannot connect to this network.  It used to take about 10 seconds to connect, and it would even connect at boot; now I just get an endless loop of 
1) try to connect...
2) display "Wireless Network Authentication Required"https://dev.openwrt.org/ticket/1222
3) enter password
4) go to step 1

I do not have access to connect to the other networks so I cannot try them.  I have a feeling, the would work though.  I'll try when I get to work.

Oh, I should probably also mention I was connected to my preferred network when I put the notebook in hibernate.

Here's lspci...
>>--------
########@Turtle43:~$ lspci | grep Network
04:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
>>--------

Looks good to me...

Restarting Network Manager does not help.  Restarting the notebook does not help.  This did not happen in Kubuntu 8.10--so I'm suspecting it is less Network Manager and more nm-applet.

Fortunately my AT&T wireless card still works and was a breeze to set up.

Any ideas?

>>>>---------------- EDIT ----------------<<<<
SYMPTOMS: attempting connect to a WPA2 wireless AP appears to result in a loop that eventually fails; or a successful connection drops and is unable to recover while data is being transfered between an IPW2200 chipset and a wireless access point secured via WPA2.

PROBLEM: According to Intel, the power saving features of this card may present compatibility or stability issues with some wireless access points.

PROBLEM NOTES:  This issue is documented on the OpenWRT wiki [here]("https://dev.openwrt.org/ticket/1222") and on a page for troubleshooting connection problems related to the IPW2200 in Intel's site, [here]("http://www.intel.com/support/wireless/wlan/sb/cs-006205.htm").  Note that both links will take you to another site.

RESOLUTION: putting the wireless card in CAM state, that is, disabling the power-saving features of the card, may resolve these symptoms.

RESOLUTION NOTES: I am currently unsure how to perminately disable the power saving features of this card, or indeed at all.

---

### Post by speedkreature on 2008-11-23
I can connect with other wireless networks without any problems.  

Anyone have *any* ideas or a direction to point me?

---

### Post by GuruX on 2008-11-24
I'd guess that you have got some settings "stuck" in the card. Yes, in the wireless card. You probably need to reset it. Try shutting down your computer and removing the battery for a while.

---

### Post by speedkreature on 2008-11-24
Well, I'm willing to give it a try.

In the mean time here's some more stuff I've pulled up on my internal card.

#######@Turtle43:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 11
       serial: 00:10:c6:d0:f7:29
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 firmware=5751m-v3.46a latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:04:02.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:82:4f:9b
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 92:7c:b6:2f:e9:7d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
#######@Turtle43:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=2.422 GHz  Access Point: 00:21:55:D3:23:00   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ppp0      no wireless extensions.

---

### Post by speedkreature on 2008-11-25
Thanks for the suggestion GuruX.  Unfortunately, that did not work.  Still, I do appreciate the reply.


I tried both of the wireless troubleshooting guides I found in the Community Docs [1]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") [2]("https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting"), and the information I found in the Ubuntu Gamers Arena (gwos.org)--which is how I came across the following information.

########@Turtle43:~$iwlist eth1 power
eth1      Current mode: off


Shouldn't the value here be something other than "off?"

---

### Post by speedkreature on 2008-12-23
BUMP!

Is there any way to trace the wireless negotiation?

---

### Post by speedkreature on 2009-01-05
I'm at home and just finished an update, turned off my notebook (because eject doesn't work), undocked it and turned it back on.  I was about to connect to the Internet with my AT&T card when I was alerted that I was connected to our wireless network.  It's stable and it's as fast as it should be.

In an attempt to determine what's going on, I got the output of iwconfig.  Note that the actual ESSID has been edited because it is not appropriate for this forum:
```

eth1      IEEE 802.11g  ESSID:"XXXXXXXXXX_WIFI"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:21:55:D3:23:00   
          Bit Rate:36 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=73/100  Signal level=-49 dBm  Noise level=-83 dBm
          Rx invalid nwid:0 [COLOR=Red] Rx invalid crypt:3[/COLOR]  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:16

```What gives with the RX Invalid Crypt?

---

