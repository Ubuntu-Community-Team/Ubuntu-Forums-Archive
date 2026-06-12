---
title: "Ubuntu 7.04 USB/adsl connect problem"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by newbun on 2007-06-26
Hi there
 
As you can guess, I'm new to this forum (and to Ubuntu/Linux).
 
I have broadband, and a ADSL 504 usb modem.  I've disabled the internal 56k (dial up) modem in the bios, and plugged in the USB modem to a USB port.  I need to get UBUNTU(Linux) to recognize my modem - it doesn't.
 
Is it because I haven't got the relevant drivers for MY particular modem???
 
I've used the modem before on a Windows XP system, with a broadband (up to 8/mbits ) connection, and connected fine.  

Another question is: If I were to attach a wireless USB adaptor (Netgear WG111) would Ubuntu automatically pick up my Netgear router, enabling me to connect to the internet????
 
Hope you can help, I've just joined the Ubuntu community ('Newbun).
 
Looking forward eagerly to your reply.
 
 
Newbun
 
ps:  Since I've installed Ubuntu 7.04, I like the look and feel of it....just need to get onto the net, to make full use of the system[/SIZE]

---

### Post by kevdog on 2007-06-26
Please change the font back to the default -- The big style makes it seem like you are screaming!

Anyway, Ive set up my internal modem but never a USB modem so my recommendations are based on hunches.

Start with the scanModem tool to see if even Ubunutu can recognize your modem.  If it can then we probably need to find an appropriate driver:
[https://help.ubuntu.com/community/DialupModemHowto/ScanModem](https://help.ubuntu.com/community/DialupModemHowto/ScanModem)

Let me know the results.

---

### Post by newbun on 2007-06-26
Oops !!! Didn't mean to offend the community 'kevdog'.  I'll run scanModem and
let you know......

---

### Post by t4thfavor on 2007-06-26
Also try wvdialconf (I believe it works for dsl) It will search for your modem. I believe USB modems show up as ttyACMX where X is 0-whatever depending on how many you have.

I have a motorazr that shows up as a ttyACM0 on my ubuntu system, which I found with wvdialconf.

---

