---
title: "obscure Atheros with DD-WRT problem"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by possumator on 2007-04-14
Hi,

I am a running a DD-WRT router in mixed mode which works perfectly for windows and linux clients and use mac filtering only for security. 

Curiously on a fresh install of Xubuntu 6.10, I put in my Netgear WG511T and it just plain worked. I never configured the SSID or even enabled the ath0 connection...it simply associated with the strongest access point (mine) and worked. 

THEN.....I installed WiFi radar (wireless configuration tool similar to Windows Zero Config), and after manipulating a config, it hasn't worked since. This has been my experience with this card in other installations of Ubuntu. Whenever I try to configure the connection, it just never associates with the access point. 

I do not think the problem is with WiFi radar as this is the only time I have used it. Also, I have a fair amount of experience with wireless on Windows and a little bit in various flavors of Linux. This Antheros card only seems to be supported (natively) in Ubuntu, as Fedora 4 and 5 dont see it and I never bothered with ndiswrapper on this card, but have tried it with other cards and got it working.  

iwconfig shows some problems with NWID which I tried to turn off but cannot. The other things is I cannot set the mode to Master but am unsure which to use anyway (DD-WRT is a gateway router and AP and i've another router running as a Wireless client (to it) giving me a remote 4 port switch for my workbench..which is pretty cool)

 sudo iwconfig ath0 nwid off

Error for wireless request "Set NWID" (8B02) :
    SET failed on device ath0 ; Operation not supported.


 sudo iwconfig ath0 mode master

Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.



iwconfig shows :

ath0      IEEE 802.11g  ESSID:"XXXXXX"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate: 0 kb/s   Tx-Power: 18 dBm   Sensitivity=0/3  
          Retry: off   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid: 635  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0


My question is what might be causing the invalid nwid? Anything else I might be missing?

thanks,

---

### Post by possumator on 2007-04-14
Even though I updated to 2.6.17-11 kernel which apparently breaks wifi, booting the 2.6.17-10 kernel didnt make much difference. The invalid nwid has gone away though. Now I see no packets exchanged whatsoever. 

A little more information:

06:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: Netgear Unknown device 4b00
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 16000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

---

### Post by Jason_25 on 2007-04-14
At a friend's I have set him up running kubuntu with my atheros wg311t and a wrt-54g running dd wrt.  Running pretty well and I have had no problems in the past with the card either, linux or windows.  

I have never used wifi radar.  I would recommend a complete reinstall using the command line tools to connect.  Optionally, you could use network-manager, which works well.

Edit: Last night I was having the invalid NWID problem when the router was set to wpa and I was trying to use WEP to connect.  With no packets exchanged, maybe you have the key wrong?

---

### Post by possumator on 2007-04-18
actually....there is no key because I am only using MAC address filtering. When I get more time I will probably try to dig a little deeper and look into command line as using network manager doesn't seem to help.

---

### Post by possumator on 2007-04-29
I duplicated this in Xubuntu 7.04. 

Simply I plugged the card in and it worked. Configured the interface with the manager and poof...would not work again.

---

