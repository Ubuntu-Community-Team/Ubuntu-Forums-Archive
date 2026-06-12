---
title: "Wireless manual security will not work, roaming mode does."
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by TheHammer23 on 2008-08-24
I am trying to set my computer up with static IP as I plan on using it to route an Xbox over the wireless and also as an NFS server. I have been using the roaming mode to connect to a WPA2 network (TKIP+AES) for a few weeks. The network icon on the taskbar won't let me configure a static ip address in roaming mode, so I selected the manual configuration. In network settings I selected my wireless device and unchecked roaming mode. I input my SSID, wireless security as WPA2 personal, my key and the static ip information. When I check the interface the ip information is correct but my wireless is continually being disassociated from the AP according to syslog. If I turn wireless security off on the router and AP, manual configuration works. WPA1 and WPA2 fail when activated on both sides with manual configuration. (Didn't try WEP, its useless anyways). In addition, when I go back into the manual configuration, sometimes the key is blank, or the security mode is changed back to WPA1 personal.(Although after I make changes I check the /etc/network/interfaces file and it looks ok to me).

my information:
Version: Ubuntu 8.04
Update status: Fully up to date as of today

```
mediapc@mediapc:~/Desktop$ uname -a
Linux mediapc 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux

```

Wireless Card: Linksys WMP54G (ver 4.1?)

```
mediapc@mediapc:~/Desktop$ lspci | grep Network
01:09.0 Network controller: RaLink RT2561/RT61 802.11g PCI

```

Interfaces file:
```
auto lo
iface lo inet loopback

iface wlan0 inet static
address 192.168.1.210
netmask 255.255.255.0
gateway 192.168.1.1
wpa-psk #####Removed for privacy#####
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid Wiresprout

auto wlan0

```

Section out of syslog (Repeats continuously)
```
Aug 23 23:40:59 mediapc kernel: [ 5607.647130] wlan0: authenticate with AP 00:12:17:c4:05:b7
Aug 23 23:40:59 mediapc kernel: [ 5607.647697] wlan0: RX authentication from 00:12:17:c4:05:b7 (alg=0 transaction=2 status=0)
Aug 23 23:40:59 mediapc kernel: [ 5607.647699] wlan0: authenticated
Aug 23 23:40:59 mediapc kernel: [ 5607.647701] wlan0: associate with AP 00:12:17:c4:05:b7
Aug 23 23:40:59 mediapc kernel: [ 5607.648682] wlan0: RX ReassocResp from 00:12:17:c4:05:b7 (capab=0x411 status=0 aid=1)
Aug 23 23:40:59 mediapc kernel: [ 5607.648684] wlan0: associated
Aug 23 23:40:59 mediapc kernel: [ 5607.648687] wlan0: switched to short barker preamble (BSSID=00:12:17:c4:05:b7)
Aug 23 23:41:03 mediapc kernel: [ 5609.182669] wlan0: RX deauthentication from 00:12:17:c4:05:b7 (reason=15)
Aug 23 23:41:03 mediapc kernel: [ 5609.182672] wlan0: deauthenticated
Aug 23 23:41:04 mediapc kernel: [ 5609.565973] wlan0: authenticate with AP 00:12:17:c4:05:b7
```

Other pertinent info: My system runs off a USB flashdrive which caused problems before (Some bug with gnome keyring or something). I mount /var/log and /tmp on tmpfs in memory.

Any tips or info would be appreciated. I've searched the forums and can't find anything other than help with cards that won't connect under any circumstances. I figure I'm missing something basic here.

---

### Post by afreeorange on 2008-08-27
I have exactly the same problem you have but remember getting wireless to work properly on Edgy using this guide posted a while ago:

[http://ubuntuforums.org/showthread.php?t=296822](http://ubuntuforums.org/showthread.php?t=296822)

Haven't tried the guide for 8.04, but will post back here after trying this driver:

[http://www.ralinktech.com.tw/data/drivers/2008_0723_RT61_Linux_STA_v1.1.2.2.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2008_0723_RT61_Linux_STA_v1.1.2.2.tar.bz2)

(Which I got off here: 
[http://web.ralinktech.com/ralink/Home/Support/Linux.html](http://web.ralinktech.com/ralink/Home/Support/Linux.html))

:)

---

### Post by TheHammer23 on 2008-08-30
I tried that guide with the same drivers. I had no luck. Now I have no wireless so I guess that fixes my configuration issues :). I have to figure out how to get back partial wireless now. In the meantime if you are going to try this out I had to make a change to the Makefile. Before running the command ```
$> make all
``` change this line in Makefile ```
CFLAGS+= $(WFLAGS)
``` to read ```
EXTRA_CFLAGS+= $(WFLAGS)
``` Once I did this I was able to compile. Unfortunately I encountered quite a few warnings which makes me think something is wrong. I looked over at linuxforums.org and it seems there are quite a few people who have problems with this chipset across distro's. These forums also list quite a few problems ([Here]("http://ubuntuforums.org/showthread.php?t=903024&highlight=RT61") and [Here]("http://ubuntuforums.org/showthread.php?t=314974")) It's frustrating that the wireless works somewhat in roaming mode, and not at all in manual but this could be related to a bug report I found in launchpad ([Bug 251763:Manual configuration don't work]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/251763")

One additional piece of information. I noticed that even in roaming mode, my wireless constantly disassociates from the AP (reason=3) every few seconds. 

EDIT: Apparently it only does this when I try to go back to roaming mode after trying to use manual mode. On a fresh reboot these messages go away.

Edit: Reinstalled system with AMD64 version. Still same symptoms. Going to try this link in a week or two when I have everything set up again. [http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

---

### Post by GaryParr on 2008-09-04
Same problem, but this is with a Intel 3945 card.

Found this thread... [http://ubuntuforums.org/showthread.php?t=740101]("http://ubuntuforums.org/showthread.php?t=740101") which says that the problem was fixed before Hardy came out of development.

---

