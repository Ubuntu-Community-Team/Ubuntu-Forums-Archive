---
title: "[SOLVED] RDP's hang only when using wireless"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by Freaky_Llama on 2008-07-31
All,

Using 8.04, I have an issue where all my RDP's to servers on the local network will freeze, and drop their connections.

It happens with Gnome-RDP, Terminal Server Client, and also using X2 Application Server Client.

Wireless setup is fwcutter for a Broadcom BCM4318 on a Dell D610. I've tried NDIS wrapper, but cannot get the laptop connected to a network at all. (I've also purchased a supported Linksys PCMCIA card and got same results). 

Symptoms are, I can be typing in the RDP window, and it will freeze for a few seconds, then the typing will 'catch up'. Otherwise, if it sits idle, I'll click back to it, and it will just 'disappear'.

This does not occur on wired lan connection. Also, I originally had this issue in Mint, but I loaded 8.04 on another hard drive and have the same results.

---

### Post by Freaky_Llama on 2008-11-19
Well, Its an old thread, and I wanted to update it as I've moved to 8.10 and have found that everything is right again.

The new network manager allows Key index to be used for thus WEP connection. This greatly affects how I connect to wireless since it will automatically connect and there is no need for custom script hacking.

However, I'm fairly certain the issue still exists with the RDP connection. Previously, in syslog, when the pauses and hangs would occur would have accompanying "Switched to short barker preamble" messages. Now on 8.10, I had to setup the b43 driver as STA wouldn't connect to my work network. With b43, Network Manager works now, but I'm now seeing different messages when the RDP sessions freak out.

> Nov 19 13:50:36 7T0GPD1 kernel: [  883.703170] wlan0: associated
Nov 19 13:50:36 7T0GPD1 NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 4 
Nov 19 13:50:36 7T0GPD1 NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 7 
Nov 19 13:50:41 7T0GPD1 NetworkManager: <debug> [1227124241.401960] periodic_update(): Roamed from BSSID (none) ((none)) to 00:0F:24:71:15:D0 ((none)) 
Nov 19 13:52:35 7T0GPD1 NetworkManager: <debug> [1227124355.489064] periodic_update(): Roamed from BSSID 00:0F:24:71:15:D0 ((none)) to (none) ((none)) 
Nov 19 13:52:41 7T0GPD1 NetworkManager: <debug> [1227124361.494051] periodic_update(): Roamed from BSSID (none) ((none)) to 00:0F:24:71:15:D0 ((none)) 
Nov 19 13:52:51 7T0GPD1 modprobe: WARNING: Not loading blacklisted module ipv6 
Nov 19 13:54:35 7T0GPD1 NetworkManager: <debug> [1227124475.570110] periodic_update(): Roamed from BSSID 00:0F:24:71:15:D0 ((none)) to (none) ((none)) 
Nov 19 13:54:41 7T0GPD1 NetworkManager: <debug> [1227124481.577057] periodic_update(): Roamed from BSSID (none) ((none)) to 00:0F:24:71:15:D0 ((none)) 

It would seem that these messages replaced the short barker preamble messages as those often showed I was disconnected, reconnected, etc... I am not sure if maybe it is because I am using an older version of the B43 firmware (As indicated by dmesg itself).

> [   41.569087] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[   41.569098] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed in July 2008.
[   41.569102] b43-phy0 warning: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).


While the initial issue still exists, I'm overwhelmed by the fact that both my wired and wireless connections will be managed by Network Manager, I don't have to write scripts or manually edit the interfaces file. I'll mark this solved, and trump the issue with having to do with the old antiquated architecture of the wireless LAN here at this company.

---

