---
title: "Wifi signal monitor apps"
date: 2016-09-16
forum: Networking &amp; Wireless
---

### Post by poorguy on 2016-09-16
Hello,

I'm using Ubuntu Mate 16.04 / 64bit. 
I have this wireless card / Qualcomm Atheros AR5413/AR5414 Wireless Network Adapter [AR5006X(S) 802.11abg].

All works well and no complaints.
I would like to monitor my signal strength without always going through the terminal to do it.

When I used Ubuntu 14.04 I used an app from the repository that displayed  signal strength / processor / memory usage in the panel. 
I am unable to remember what it is and hope someone can. 


Thanks

The PoorGuy
------------------------------

[Update 09/17/2016]

"System Monitor Indicator"

Worked great in Ubuntu 14.04.

Doesn't display graphs Ubuntu Mate 16.04.

---

### Post by him610 on 2016-09-17
Don't know of any Ubuntu applications that provide wifi signal strength. That said,...

If you own an Android smartphone, there is a free, easy-to-use app, *Wifi Analyzer* that works great.

Added: Actually I do know of a command that will take a snapshot in time of your wifi connection that shows what you want to see...
```
iwlist wlan1 scan 
``` Substitute your wireless designator if not wlan1.

@Duckhook: Thanks

---

### Post by DuckHook on 2016-09-17
> **poorguy said:**
> [Update 09/17/2016]

"System Monitor Indicator"Would you kindly provide further details? For example, the actual package name and the link where it can be found? There are many system monitors with tray notifications in Ubuntu, but I do not know of any GUI monitors that provide signal strength. Also, most indicators involve the addition of a PPA, which I find to be both security and stability concerns and that I would not recommend as good practice for new users (for any new users reading this).

The way I implemented this some years ago was through conky. But I have not used conky for about 2 years and have forgotten everything that I once knew. It did involve the app in the answer to the question below.> **him610 said:**
> Don't know of any Ubuntu applications that provide wifi signal strength.A good CLI app is *wavemon*:```
sudo apt install wavemon
```

---

### Post by poorguy on 2016-09-17
Hey DuckHook,

It is very possible that I've mistaken Mbps as signal strength as my eyes aren't what they used to be. I'm Old. :icon_frown:
I'm almost certain the app is System Monitor Indicator or System Load Indicator.
It displayed in the panel as graphs Processor / Memory / Network / Swap / Load / Hard Disk.

What I found in Ubuntu Mate 16.04 appeared to try to display graphs in the panel but just never worked. 
Seems none of the system monitors / indicators in 16.04 that I have tried ever work right if they work or have been inaccurate.
The only way I can get accurate results is using command terminal.

The wireless signal bar in the panel doesn't show any signal bars at all but *iwconfig* shows signal strength of 77% to 95% and I have excellent internet speed.
Perhaps I'm expecting to much from 16.04 since 14.04 worked well when I was using it.
My apologies for the confusion.

The PoorGuy

---

### Post by DuckHook on 2016-09-17
@poorguy: We are not "old". We are "mature", "wise", "sophisticated" and "well-seasoned". But neither the eyes nor the ears are what they used to be, I admit.

Yes, you are thinking of throughput, which is a more useful measure for everyday purposes. Signal strength tends to be something needed only when you are trying to determine the best connection spot, or checking which channels have the least interference, etc. For those occasional purposes, I highly recommend the aforementioned *wavemon*.

For a mate-capable panel applet, try the following: [http://www.webupd8.org/2016/08/alternative-system-monitor-applet-for.html](http://www.webupd8.org/2016/08/alternative-system-monitor-applet-for.html)

Disclosure: I do not run mate and refuse to add PPAs willy-nilly so am only pointing you to a website that I trust. I have no personal experience with the applet. However, webupd8 is an incredible 'buntu/Linux resource and one of the premier Ubuntu sites around. I doubt that they will lead you astray.

---

### Post by poorguy on 2016-09-18
Hey DuckHook,

Thanks for the encouragement and understanding.

I'm learning.

The PoorGuy :)

---

### Post by DuckHook on 2016-09-18
Hey, we old guys have to stick together. And as for learning, that is a universal condition that all wise people continually aspire to.

Good Luck and Happy Ubuntu-ing!

---

