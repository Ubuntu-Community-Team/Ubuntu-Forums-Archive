---
title: "Success with Asus P5W DH Deluxe onboard WiFi (RTL 8187 chipset)"
date: 2006-09-17
forum: Networking &amp; Wireless
---

### Post by nmaquet on 2006-09-17
Hello all,

I'd like to report on my recent success with the onboard WiFi card of the ***Asus P5W DH Deluxe motherboard***, on Ubuntu 6.06 LTS. The wireless card on that MB is USB-based and has a ***RTL8187L chipset***.

Things I tried in order : 

1. use the r8187 opensource driver that is part of the Linux kernel
   RESULTS => 'iwlist scanning' does not see my AP, card does not associate

2. use ndiswrapper (ndiswrapper-utils from Ubuntu repository)
   RESULTS => WinXP driver : nothing works
              Win98ME driver : works but FREEZES after 5min of intense traffic (reproductible)

3. use **ndiswrapper compiled from source** (version 1.23 stable)
   RESULTS => WinXP driver : nothing works
              Win98ME driver : **_works PERFECTLY_** (so far ;))

md5sums of the binary driver :

06a269afedc8b645fdc04ec9eb788b14  Netrtuw.inf
f441e922884b3356f28457106cd718b2  RTL8187.sys

This ends (I hope) about 48 hours of hard and frustrating trial and error, I hope this information will be helpful to other P5W DH Deluxe owners.

Cheers,

Nic

---

### Post by apotsi on 2006-11-18
With which version did it work for you ? I tried both with the Win98 and the WinXP driver ([ver. 1.234]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true")) with ndiswrapper 1.28 from source, but it didn't work.

With iwlist wlan0 scan I see the AP, but I cannot link to it in any way. I put the MAC address of the AP with ```
iwconfig wlan0 ap xx:xx:xx:xx:xx:xx
```, and also essid apotsi (which is the name of the router), but still no luck.

Forgot to say that the Wireless router is a Linksys WAG354G with firmware version 1.01.09 (Annex A - PSTN). No Wep Key, no WPA... In Windows XP works perfectly.

Any ideas ???

---

### Post by apotsi on 2006-11-19
No one ??? Please community... Don't disappoint me...

---

### Post by naht on 2007-01-14
For me ndiswrapper 1.33 and the drivers shipped on the driver-cd work. Newer realtekdrivers do NOT work. =)

---

### Post by SomethingUniqueHere on 2007-01-22
Seems like there are enough of us with the same problem.  I just installed ndiswrapper 1.34 from source and i'm trying version .1230 of the realtek drivers.  ndiswrapper seems to be installed happily, everything looks alright but when i enter iwconfig it says Access Point: Not-Associated.  The wifi is running smoothly cause im using my roomates laptop to post this lol.

Can people with the problem solved/working send links to their working copies of the realtek driver?  

Thanks

---

### Post by Zer0Nin3r on 2007-01-23
I'm running an Asus M2N32-SLI Deluxe motherboard with a 32 x86 Ubuntu 6.10 (I have an Athalon X2) with the RTL8187 drivers blacklisted and I used ndiswrapper (v1.18) with Win98 drivers that came with the Asus CD.

I've tried the 64bit XP (when I was using a 64bit Ubuntu install), 32bit XP, WinMe all without success.  The Win98 drivers seem to be working for me so far with no apparent problems.

---

### Post by semetay on 2007-02-03
I have an asus m2n32 and no success. I have kubuntu edgy x86_64 6.10 installed. it seems that everything is there, the driver, network settings etc but it says no networks could be found which is a big lie. I noticed that adapter's light is not on like in winxp.

I tried ndiswrapper but I guess first I should disable the current drivers. How do I do that?

Thank you all...

semetay

---

### Post by Zer0Nin3r on 2007-02-04
Try the following link:

[http://www.ubuntuforums.org/showthread.php?t=314352&page=2]("http://www.ubuntuforums.org/showthread.php?t=314352&page=2")

I wrote up the process I took to get the WiFi to work, there is also input from others.  Cheers!

---

### Post by semetay on 2007-02-05
thank you for the link but the thing is I cant go back to the 32 bit. I am using more than 4gb memory and a software uses 64 bit. 

I hope sometime soon i will resolve this.

thanks anyway...

semetay

---

### Post by Zer0Nin3r on 2007-02-11
I'm sorry to hear.  I'd really like to upgrade to the 64-bit version as well, it would be nice to utilize my hardware for what it was designed for, but I'll give it a a little more time.  Good luck let us know if you are able to get your WiFi up and running.  Aloha!

---

