---
title: "Wifi Out of the box with linux-2.6.10-5-386"
date: 2005-07-16
forum: Networking &amp; Wireless
---

### Post by beansbbq on 2005-07-16
Hello all,



   I've pretty much tried everything on the atheros posts to get my Proxim ag card installed with Ubuntu Hoary.  My laptop is an old IBM 600E.  My kernel is the linux-2.6.10-5-386 kernel.  I don't really get why I'm not having any luck with the posts.  

   What I'm looking for is a wifi card that WILL work "out of the box" with my kernel.   My girlfriend has an Acer Travelmate 290 which worked flawlessly with the LiveCD.  I know that the Centrino chip in it does indeed work "out of the box".    

   I'd like the same experience with my older laptop (Ubuntu is installed on it) if anyone can assist me.  I know that Ndiswrapper should work, but I continue to have difficulties.  Does anyone have any suggestions?

Thanks

---

### Post by varunus on 2005-07-17
What does your wireless card show up as in the device manager?  For example, mine shows up as an AR5212 802.11abg NIC.  This may help.  ndiswrapper can be made to work with atheros cards too; i've done this before when madwifi just wouldn't work for me (though I use it now as it has greatly improved).

Good luck.

---

### Post by beansbbq on 2005-07-17
[QUOTE=varunus]What does your wireless card show up as in the device manager?  For example, mine shows up as an AR5212 802.11abg NIC.  This may help.  ndiswrapper can be made to work with atheros cards too; i've done this before when madwifi just wouldn't work for me (though I use it now as it has greatly improved).

Good luck.[/QUOTE]


Hey Varunus,


  Thanks for your response.  I checked the device manager, and my entry is identical to yours.  AR5212 802.11abg NIC.  My Bus type is PCI.  I'm not sure what else I should do.  What card do you have if you don't mind me asking?  I'm thinking about going to pick up the Netgear WG511T, which several users have had success with.  

Thanks

---

### Post by varunus on 2005-07-17
You also have an AR5212?  This chip is supposed to work out of the box with Ubuntu, using the "madwifi" driver.  Unless you're getting the dreaded error that your chip is not supported by the HAL, in which case you need to follow this howto: [http://www.ubuntuforums.org/showthread.php?t=38972&page=2&highlight=madwifi](http://www.ubuntuforums.org/showthread.php?t=38972&page=2&highlight=madwifi)

Though, it seems that you've already posted there...This howto is not to compile ndiswrapper, which needs your windows driver.  This howto compiles its own drivers.

Try booting up your computer, and right after boot is complete, log in and open a terminal, and type
```
dmesg | grep ath
```

Do you see any messages?  Also, what is the output of iwconfig in a terminal?  What about ifconfig in a terminal?  We can get this card to work.

---

### Post by beansbbq on 2005-07-19
[QUOTE=varunus]You also have an AR5212?  This chip is supposed to work out of the box with Ubuntu, using the "madwifi" driver.  Unless you're getting the dreaded error that your chip is not supported by the HAL, in which case you need to follow this howto: [http://www.ubuntuforums.org/showthread.php?t=38972&page=2&highlight=madwifi](http://www.ubuntuforums.org/showthread.php?t=38972&page=2&highlight=madwifi)

Though, it seems that you've already posted there...This howto is not to compile ndiswrapper, which needs your windows driver.  This howto compiles its own drivers.

Try booting up your computer, and right after boot is complete, log in and open a terminal, and type
```
dmesg | grep ath
```

Do you see any messages?  Also, what is the output of iwconfig in a terminal?  What about ifconfig in a terminal?  We can get this card to work.[/QUOTE]


Thanks Varunus for following up.  I'll respond tonight after work.  I hope that we can get it to work.  I know that it's a killer card.  I'd hate to have to down grade to a "b only" card just to get wifi.

---

### Post by beansbbq on 2005-07-19
[QUOTE=varunus]You also have an AR5212?  This chip is supposed to work out of the box with Ubuntu, using the "madwifi" driver.  Unless you're getting the dreaded error that your chip is not supported by the HAL, in which case you need to follow this howto: [http://www.ubuntuforums.org/showthread.php?t=38972&page=2&highlight=madwifi](http://www.ubuntuforums.org/showthread.php?t=38972&page=2&highlight=madwifi)

Though, it seems that you've already posted there...This howto is not to compile ndiswrapper, which needs your windows driver.  This howto compiles its own drivers.

Try booting up your computer, and right after boot is complete, log in and open a terminal, and type
```
dmesg | grep ath
```

Do you see any messages?  Also, what is the output of iwconfig in a terminal?  What about ifconfig in a terminal?  We can get this card to work.[/QUOTE]


Varunus,

   I have run the three commands that you suggested.  I'll provide the results below in order.  Please let me know if you  notice anything or if you have any other suggestions.

FYI, I purchased the Netgear WG511T that elvis used from the "Atheros AR5212 Madwifi HowTo" post.  I figured that it would suffer from the same symptoms that my Proxim card would since they use the same chipset, but I had to try anyways.  I've sinced returned the Netgear card, and prefer to try to get the Proxim card working.  

I appreciate all of your help.

Thanks,

J


**dmesg | grep ath**
ath_hal: module license 'Proprietary' taints kernel.
ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
ath_rate_sample: 1.2
ath_pci: 0.9.6.0 (EXPERIMENTAL)
ath0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
ath0: turboA rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
ath0: H/W encryption support: WEP AES AES_CCM TKIP
ath0: mac 5.6 phy 4.1 5ghz radio 1.7 2ghz radio 2.3
ath0: Use hw queue 1 for WME_AC_BE traffic
ath0: Use hw queue 0 for WME_AC_BK traffic
ath0: Use hw queue 2 for WME_AC_VI traffic
ath0: Use hw queue 3 for WME_AC_VO traffic
ath0: Use hw queue 8 for CAB traffic
ath0: Use hw queue 9 for beacons
ath0: Atheros 5212: mem=0x10400000, irq=9


**iwconfig**
lo        no wireless extensions.

sit0      no wireless extensions.

ath0      IEEE 802.11  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:0 kb/s   Tx-Power:20 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**ifconfig**
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:702603 errors:0 dropped:0 overruns:0 frame:0
          TX packets:702603 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:52178177 (49.7 MiB)  TX bytes:52178177 (49.7 MiB)

---

