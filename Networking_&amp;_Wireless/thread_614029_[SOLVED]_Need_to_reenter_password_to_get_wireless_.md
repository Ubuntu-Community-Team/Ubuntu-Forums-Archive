---
title: "[SOLVED] Need to reenter password to get wireless connection started"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by HalSF on 2007-11-15
I'm running Ubuntu Gutsy on a Dell Inspiron 600m with an Intel PRO/Wireless 2100 card using WPA encryption. The only way I can get a wireless connection after booting up is to open Network Settings, go to Properties, and re-enter the password. Any idea how I can make my wireless work automatically upon startup?

Here's what I get in Terminal when I enter "sudo lshw -C network":

  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5702X Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:0d:56:7c:a4:12
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 firmware=5702-v2.25 latency=64 link=no mingnt=64 module=tg3 multicast=yes port=twisted pair
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 04
       serial: 00:04:23:a2:d6:a8
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=192.168.1.104 latency=32 link=yes maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=IEEE 802.11b

---

### Post by HalSF on 2007-11-15
Sorry I mean to type I'm running Xubuntu Gutsy, not Ubuntu -- if it makes any difference...

---

### Post by coop925 on 2007-11-16
I'm having the same issue, however, the issue started when I reset my WPA passkey. I've been re-acquiring my connection by clicking on the Network Settings Applet in the applets bar, then clicking Connect to Other Wireless Network and putting in the info there. 
I know there has got to be a way to reenter it in the key ring, but I'm not finding it. Help?

---

### Post by coop925 on 2007-11-16
In another thread (I don't know how to quote other threads, so here goes an old fashioned cut and paste...)

 Re: Changing a WPA password
There is. Go into the Keyring Manager and change your WPA passphrase manually. Get your new passphrase by:

$wpa_passphrase SSID passphrase

SSID = your SSID

passphrase = your passphrase
__________________
Stay away from the craptastic Screens and Graphics Utility!!

Ubuntu Devs to please explain why they included a broken/badly designed tool with Gutsy!!
Reply With Quote

I think it worked. I've rebooted twice, and everything seems to be working right. If there's further, I'll repost.

---

### Post by HalSF on 2007-11-18
I seem to have solved my problem by editing and correcting the /etc/network/interfaces file. 

I posted a quick success report at:

[http://ubuntuforums.org/showthread.php?t=615123](http://ubuntuforums.org/showthread.php?t=615123)

---

