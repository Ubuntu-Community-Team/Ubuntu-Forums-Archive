---
title: "ndiswrapper on edgy loses wireless connection"
date: 2007-01-01
forum: Networking &amp; Wireless
---

### Post by eggdeng on 2007-01-01
I managed to get my Conceptronic usb wireless adapter up and running on Edgy using ndiswrapper and the Windows driver rt2500usb.inf / rt2500usb.sys. As the default scan is on the wrong frequency, I stuck the following script in /etc/init.d.

```
#!/bin/bash
iwconfig wlan0 freq 2.462G
iwconfig wlan0 essid WLAN ap [ap_mac_address] commit
```

The problem I have now seems to be common to many users (especially with Broadcom cards). Internet will stay up for at best about half an hour and only a reboot will get it back up for more than a few seconds. Performance also degrades over time until after a few days, only reinstalling the driver will get it to work. Even when down, iwconfig reports the ap correctly but I still can't ping the router. The link light on the card is on and the activity light flashes.

Output for ndiswrapper -l
```
Installed drivers:
rt2500usb		driver installed, hardware present
```

Output for sudo iwconfig: (when down) 
```
wlan0     IEEE 802.11g  ESSID:"WLAN"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: [correct_ap_mac_address]   
          RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
```

Output for sudo iwlist wlan0 scan (when down)
```
wlan0     No scan results 
```

I am using static IPs and limiting access to known mac addresses. The hardware works well on the XP partition.
I have tried various solutions including reverting to the old nvidia driver in case of an IRQ conflict and resetting the beacon interval on the router but with no luck. Maybe I need to blacklist a native usb wireless driver? Any suggestions appreciated.

---

### Post by eggdeng on 2007-01-01
Bump.

---

### Post by eggdeng on 2007-01-02
After screwing around with ndiswrapper on and off for weeks, I was told that Edgy has native drivers for this chip. So I did a fresh install and after the usual tinkering, managed to get connected but the story is the same. After a random interval, the connection goes down and each time it requires more radical measures to get it up and working again. At the moment, the card can see the router

```
sudo iwlist wlan0 scan
Cell 01 - Address:  CORRECT MAC ADDRESS                   	ESSID:"WLAN"
                    Mode:Master
                    Frequency:2.412GHz
                    Encryption key:off
                    Extra: tsf=000000029853de7c

```
but won't ping or connect to the Internet.

For a number of reasons, I'm beginning to think that connection attempts are defaulting to the wrong interface, trying to use eth0, which is disabled, instead of wlan0. Any ideas on how I could check / configure this?

---

### Post by jamesstansell on 2007-01-02
"netstat -rn" will show your routing table. (or System -> Administration -> Network Tools if you prefer)

Normally I would expect to see Mode: Managed assuming you have a wireless router.  Are you attempting an ad-hoc network?

---

### Post by eggdeng on 2007-01-04
Thanks for the tips. Unfortunately netstat -rn gives me no output, which I suppose is logical when the connection is down.

I am using a router, with dynamic IPs and no security while I try to get this working. I have tried

```
sudo ifdown wlan0
sudo iwficonfig wlan0 mode managed 
isudo ifup wlan0
```

upon which it goes through the whole DHCPDISCOVER rigmarole and ends up No DHCPOFFERS recieved. Then

```
sudo iwlist wlan0 scan  
wlan0      No scan results
```

---

