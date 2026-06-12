---
title: "Wireless card parameters"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by promet on 2007-06-23
Heya,

I have a wireless card with which I am trying to connect to some new outdoor access points available in New York. I am able to receive signals from the open wifi area, but only very weak ones; i.e., I am "connected" but not able to send or receive any significant packets.

I am beginning to wonder if this doesn't have something to do with the configuration/slash quality of my wireless network card. At home, like 8 feet from an unobstructed wireless router, I am only achieving 56% or so signal strength as reported by "iwconfig".

Here are some results **for the public wifi (IWCONFIG):**

```
wlan0     IEEE 802.11g  ESSID:"parkwifi"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:12:CF:2F:F7:98   
          Bit Rate=1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Note the link quality of "35/100" I was hoping this might be enough to make a substantive connection but all network requests failed with "network not available" or some such problem. 

What is a reasonable signal strength to expect a useable conection (above 50% I'm assuming)? Are there ways to tweak my driver (wext) or iwconfig commands to tweak Signal level, Noise Level, Frequency etc. to try to improve my card's "gain"? I am wondering if another card might produce more robust results (I worry about the mere 56% Signal Quality on the home router as well) or if my current card can be coaxed to greater effectiveness.
 
This is a (crap) Ehome EH101 pcmcia card (hey, it was on sale for $2.00), running with the "wext" driver on Feisty. Any help or insights would be great. Thanks for your time, oh ye mighty men and women of Linux Renown.

peas,
promet

---

