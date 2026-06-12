---
title: "ESSID wrong."
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2008-11-27
Hi all.

Strange issue which has only just started happening (and I only just noticed it). Couldn't work out why my web browser were occasionally crashing, progress bar not happening when I go to a web site. It happened today when I was on the forums and noticed my network applet showed I was disconnected. Thought I would have a bit of a look around so I ran iwconfig and this is the result for my wireless connection:

```
wlan0     IEEE 802.11g  ESSID:"default"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:11:84:AF:26   
          Bit Rate=18 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=61/100  Signal level=-67 dBm  Noise level=-67 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```All good you would think, except for the fact the ESSID is wrong! In System->Administration->Network, all is setup with correct ESSID and security details, yet my machine is choosing to use 'default' which I know exists around here (used to use it very occasionally in windoze, but very unreliable, naughty me!) and I am presuming this is the network my machine is now deciding to connect to when I log on. It is called 'default' and has no security.

Didn't make any changes to my setup to make this happen and all I can think of is an update may have screwed things in my otherwise problem-free laptop. Anyone have any suggestions or ideas? I will keep searching for a fix/explanation in the meantime.

Tnx in advance. :)

* UPDATE: Okay, getting somewhere. It keeps dropping my domain. When I checked my network configuration, the hostname is correct but there was no domain name! I set the domain name, restarted and you guessed it, checked the config again and domain name missing. Guessing that is why it is picking up the unsecured one. I shall keep tweaking ...

---

