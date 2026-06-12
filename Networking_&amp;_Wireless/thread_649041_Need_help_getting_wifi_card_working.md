---
title: "Need help getting wifi card working"
date: 2007-12-24
forum: Networking &amp; Wireless
---

### Post by PenquinCoder on 2007-12-24
Greetings everyone.

I have just recently bought a new laptop, and after installing Ubuntu 7.10((for 64bit) on it, tried to begin the rest of the setup. Everything is now working as it should, except for my WiFi card.
Linux list this as an Atheros 5006EG, however in Vista is was shown as an Atheros 5007 model. I have searched these forums for the past two days, and tried almost everything listed in trying to get the WiFi card working. Currently on the system, only the eth0 connection is able to connect. I am using WICD, and ndiswrapper. 
Ndiswrapper states that I have the correct driver for the hardware, and thats its present, System>Admin>Network, the wireless connection shows up, and WICD scans for and sees wireless networks. But I am not able to actually connect to one. I've tried also manually changing the options of wlan0 using iwconfig, but after changing an option, and DCHP broadcasting, it is still unable to optain an IP.

My iwconfig:
```

lo        no wireless extensions.

eth20     no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lspci
```


03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
```

If anyone is able to help me get this laptop working as it it should, and not as a paperweight I would be extremaly grateful. Especially at not having to try and get Vista back installed.
Thanks:popcorn:

---

### Post by PenquinCoder on 2007-12-24
Okay well, now heres an issue. 

I just did IWconfig again, and this time the network shows up as being connected. 
But when I do IW config again, it shows up as off. So its like randomly connecting???

```

~$ iwconfig
lo        no wireless extensions.

eth20     no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
~$ iwconfig
lo        no wireless extensions.

eth20     no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"belkin54g"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
```

---

