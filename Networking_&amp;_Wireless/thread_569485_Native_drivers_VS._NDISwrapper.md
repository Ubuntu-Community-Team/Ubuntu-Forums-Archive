---
title: "Native drivers VS. NDISwrapper?"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by jingo811 on 2007-10-07
Don't know if I'm formulating the question right.  But I'm curious of how many Linux users out there uses NDISwrapper or the usual Linux native drivers for their wireless hardware?
What solution is being used the most that's the core of my question.

---

### Post by tgoose on 2007-10-07
I do have a Belkin PCMICA card with native drivers, but my internal one only works with ndiswrapper, so that's the one I'll be using in any normal situation.

---

### Post by Chili.willy on 2007-10-07
I got the native driver for Realtek 8180 at Sourceforge. It works great, except it doesn't seem to support WPA encryption, only WEP. WEP is supposed to be very easy to crack. Not that anyone's likely to try, where I am.

---

### Post by aconley1 on 2007-10-07
I was using a Linksys PCMCIA card with Broadcom 4.xx chipset.  I had to use Ndiswrapper to make it work.  The ndiswrapper only gave me WEP security options also.  One day, for no apparent reason, this card simply stopped working.  I went to the list of compatible wireless USB adapters in the Ubuntu documentation pages and found a USB 3com adapter that stated "works out of the box".  I plugged it in and have been up and running ever since.  The native driver for this allows WPA encryption, although I've stuck with the WEP because I'm too lazy to reconfigure everything else in my house.  I have two other PC's that are wireless (one ubuntu and one Vista - vista stinks), I also have two PSP's, PS2, XBox 360 and Wii all using the same WEP encryption.  

The bottom line is, use the native driver if possible.  The USB adapter I bought only cost me $20 on ebay and probably saved me hours of headaches when the other adapter crapped out.

---

### Post by jingo811 on 2007-10-09
Ndiswrapper made this work.

brand: **ASUS WL-161**

specs: 
[LIST]
[*]802.11b
[*]USB 1.1
[*]Data rates: 11 ; 5.5 ; 2 ; 1 Mbps auto select
[*]WEP 64 / 128 bit
[/LIST]

---

