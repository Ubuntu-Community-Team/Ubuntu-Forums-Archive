---
title: "AR5212 - Feisty - Installation"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by Cobalt Infinity on 2007-09-05
As a moderator on Wind0ze computer support forums I understand the frustration with answering posts from newbies who could have just hit the "search" button and found their answer.  With that being said, I have read every post I found in reference to AR5212, Atheros 5212, Feisty Wireless, Madwifi, etc (took a few days quite honestly) and I have still have not gotten this card to work.  I also read all the stickies in the newbie forum as well as in the wireless forum and while my knowledge of Linux, and Ubuntu in particular, has GREATLY increased (thanks everyone) I am still stuck without wireless.

As everyone seems to ask for steps taken and some background information, I will provide as much as possible but if you need anything else please do not hesitate to ask and THANK YOU for your help!

lshw -C network +output+
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 9
       bus info: pci@00:09.0
       logical name: wifi0
       version: 01
       serial: 00:0b:85:04:37:90
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:febf0000-febfffff irq:19

iwconfig ath0 +output+
ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-93 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

uname -r +output+
          2.6.20-16-generic

ifconfig +output+
ath0      Link encap:Ethernet  HWaddr 00:0B:85:04:37:90  
          inet6 addr: fe80::20b:85ff:fe04:3790/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Now, as it was so difficult to do this the last time I tried (about six months ago and i just ended up giving up) I took a router I had sitting around and disabled all of the encryption and turned on ssid broadcasting.  Obviously for security purposes I would like to re-enable WPA-PSK and turn off ssid but I figured it is probably best to take things one step at a time. 

I tried installing new madwifi drivers, the whole new sharutils and headers, uninstalling the restricted modules madwifi (synaptice and gnome-terminal) and WICD.  The machine is running Feisty and I DO have wired functionality.

The machine dual-boots with d0ze XP Pro so there is no info on the linux partition that I need so formatting and starting from scratch is a possibility as well.  I would really like to understand the process behind all of this so if anyone has gotten a Mini-pci version of the AR5212 chipset card to work and can give me instructions, as explicitly and step-by-step as possible, this newbie would greatly appreciate it!  Thank you so much for time and for your help!

---

### Post by weekdaysailor on 2007-09-05
I'm a NOOB as well, so take this with a grain of salt. But in my reading it appears that Feisty broke something that was working in Dapper. 

When I did a clean install (dual-boot as well) on my T41 laptop (artheros AR5212), everything *appeared* as if it was going to work flawlessly - but I could never get a DHCP address (can't tell from your post precisely what problem you are seeing...)

I've tried everything short of a) installing madwifi-old which some posts seem to imply works (I don't know where it it, because it's not called that anymore apparently...) and b) adding a "kernel boot option" for some irq probe which is also hinted at...

Anyway, after much trial and error I hit upon steps which act as a workaround - and then just put that in a simple script:

#!/bin/sh
wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0
iwconfig ath0 essid MySSID
iwconfig ath0 key nnnnnnnnnnn
dhclient ath0

I run this sudo and it seems to work fine. So the problem seems to me to be some low-level "wap the card upside-the-head" issue - so maybe your higher-order issues with WPSK, etc would be solved in the same manner. The above may be a completely whacky sequence, but it works.

Note that I have to re-run the script after suspend.

Hope this helps - I deemed it acceptable until those madwifi guys find and fix. 

-WDS

---

### Post by Cobalt Infinity on 2007-09-05
Ran through your workaround and still nothing, no DHCP offers received.

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0b:85:04:37:90
Sending on   LPF/ath0/00:0b:85:04:37:90
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


I'm beginning to think this might be some sort of firmware issue with the card.

---

### Post by Cobalt Infinity on 2007-09-06
++PROGRESS++ !!!!!11!!!ONE!!1!!!!!1

Ok, reset the ddwrt router to default and now I can SEE the network I am trying to connect to but I cannot get an IP address.

---

### Post by weekdaysailor on 2007-09-06
OK, my suspicion is your wep key isn't right. So start with a wide-open un-encrypted connection and try my kludge again. Restarting the router may be required to get it to release the key - some are dumb that way. When you turn wep back on, make sure you align what you type (hex or decimal) with what the router expects. Sometimes it's not clear if the router is using hex or decimal.

---

### Post by DPic on 2007-09-18
I am having troubles with the same wireless but i did have it working in feisty. I don't remember ever having problems with it in the past. My friend has the same wireless card and it works fine for him in feisty. Does anybody know what the problem could be?I am not picking up any wireless networks for some reason. And the network isn't the problem

---

### Post by DPic on 2007-09-19
It stopped working when i reinstalled ubuntu. I don't believe it works on the LiveCD now either. Is there a driver i am missing? I have installed madwifi

---

### Post by dmizer on 2007-10-13
not missing much.  i can't get the stupid thing to work either.

tried madwifi (restricted drivers) with no success.  card is active, sees the access point, but refuses to pull an ip address.

tried ndiswrapper.  card activates fine, access point is visible, but refuses to pull an ip address.

if i come up with anything i'll post.

edit:
installed the latest version of ndiswrapper ... still no dhcp lease.  i see this error in dmesg:
```
 ndiswrapper (iw_set_freq:334): setting configuration failed (C0010015)
```

[COLOR="Silver"]this card/chipset looks to be a no go in ubuntu.[/COLOR]

edit II:
it would seem, my problem is because i needed to reboot my router after updating it with the new card's mac address :oops:

ndiswrapper = works great.
madwifi = not working at all.

---

