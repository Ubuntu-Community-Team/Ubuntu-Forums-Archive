---
title: "No wireless connection on Acer Travelmate 4314"
date: 2008-02-15
forum: Networking &amp; Wireless
---

### Post by the_walrus on 2008-02-15
Hello everyone, I'm Roberto.
I installed xubuntu 7.10 on my Acer Travelmate 4314WxMi. I fixed all the problems but the Wireless. 

This is the output of lspci command after the update of pci.
```
02:00.0 Ethernet controller: Atheros Communications, Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

Before the pci update the output of lspci told me the nb had the Atheros AR5006EG, so I installed ndiswrapper with the drivers of that card.

Now, if I type iwconfig I can read the follow:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:108 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

But I can't connect to the net via wi fi. How can I fix this problem??

---

### Post by fbuchele on 2008-02-15
Well it says that its not connected to anything. Are you using Ad-Hoc or an Acess point? We need more information on the error. Try connecting and post what happens, as well as anything else you can tell about the error.

Does wired internet work? do you know? More information!

---

### Post by the_walrus on 2008-02-15
I'm using an Access point with wpa-psk and I can see it with wifi-radar but i can't connect on it. Where should i put my wpa key, using wifi-radar? Maybe the problem is in the configuration but i didn't find anything helpful for the setting of radar-wifi. For example, what's the WPA driver textfield on it??
 The wired connection works, thank you 4 your support!:popcorn:

---

