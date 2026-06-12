---
title: "Linksys Wireless G card"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by bd_adams on 2007-01-07
Good afternoon ladies and gents,

I'm excited to be a part of the Ubuntu family. I am currently trying to get my Linksys Wireless G card (wmp54g) connected. I am running into a problem trying to get the connection to activate. I think I have installed the driver correctly. When I install the driver using ndiswrapper and do a ndiswrapper -l I see that my rt61 is there and the hardware is detected but I cannot however get the connection to activate. I was wondering if anyone could give me direction on what to do next. I am relatively new to Linus so if you need any specific hardware or version information please let me know.

Edit: I am running Version 6.06 LTS. When I go to administration and look at networking is says my wireless connection is ra0. It now activates but I'm not sure I've got things setup correctly.

I thank you all in advance for your time,

BA

---

### Post by n00b@linux on 2007-01-07
First of all, I don't believe you need to use ndiswrapper for your card.  I think it should be supported 'out of the box'.

If you want to test it to see if it's working, open a terminal (Applications > Accessories > Terminal) and type:```
iwconfig
```You should see your ra0 listed in the output with details about ESSID, Mode, Frequency, etc.  If the 'Access Point' details show a series of hexadecimal numbers (6 sets of 2) you're good to go.

---

### Post by bd_adams on 2007-01-07
I see all that information but I still cannot get an internet connection.

---

### Post by bd_adams on 2007-01-08
Ok backed up everything I wanted to keep and did a fresh install of Ubuntu 6.06 LTS. I was able to put in the SSID the WEP password and now when I try to boot it hangs on congfiguring  network interfaces. Any suggestions?

---

