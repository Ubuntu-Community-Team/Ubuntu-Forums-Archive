---
title: "WUSB54G + Ubuntu Feisty"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by mlapaglia on 2007-03-27
alright im more than throughly confused right now...

i have a this:

Ubuntu Feisty Fawn
WUSB54G V.4 network card (usb external)
Intel Pro/Set Wireless 3945abg network card (internal)

here's what i wish to do:

-use the intel card for regular internet.
-use the wusb54g card in monitor mode, or regular internet if need be.

when i plugged in my wusb54g card, my network-manager in the task bar recognizes the card, but has it listed as "Unknown USB Vendor Specific Interface." It shows access points around me, but does not show their signal strength (the intel card does), and it cannot connect to them either.

when i put the wusb54g into monitor mode, it will remain there for a few moments, but then goes back into managed mode. when i disable the network-manager, i cannot use either card at all, monitor or managed mode.

iwconfig returns this:
```

********@***************:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"UDwireless"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:20:48:44:F0   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=90/100  Signal level=-48 dBm  Noise level=-48 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:310   Missed beacon:0

rausb0    RT2500USB WLAN  ESSID:"UDwireless"  Nickname:""
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:11:20:48:44:F0   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=77/100  Signal level:-42 dBm  Noise level:-195 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

********@**************:~$ 

```

so both devices are picking up ESSID's and all that jazz, but it can't connect?

so it's using the correct drivers, but it's not working right.. any ideas? 
thanks sooo much for the help

---

### Post by kolslorr on 2007-03-28
I have WUSB54G card as well, and since the latest kernel feisty upgrade (2.6.xxx-13), it has the same problem as you, detecting the networks but showing all as 0% strength.

It works perfectly with previous kernel (2.6.xxx-12) though, on network manager I can see and select all available networks with correct signal strength showing...

The workaround that works for me is to uninstall the network manager, and use system->admin->networks to manually configure to my wireless network. Remember to restart networking after configuration. (untick and tick the box, I forgot the command to do it)

It works, but I miss the network manager.

---

### Post by mlapaglia on 2007-03-28
is there a place we should be putting a bug in about this, get it fixed for a later release?

---

