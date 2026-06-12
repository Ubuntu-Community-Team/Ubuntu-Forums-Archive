---
title: "RS-232 Analysis/BT Serial Comms"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by antiocles on 2007-10-11
I do a lot of development work on devices that use both RS-232 and now bluetooth serial ports to communicate.  I've recently dumped windows forever (hurrah!) but have been having a little trouble getting things set up correctly on my laptop.

I often need to plug in between devices and analyze serial communcations between them.  While a special cable can be made, and I have one, I much prefer using the laptop to route the communications as it gives me much more control (i can interrupt/modify on the fly and so on)

I have not found a good program yet that will let me bridge rs-232 connections and watch the data stream by.  Any suggestions on this?  I generally use a USB->serial adapter since this comp doesn't have rs232. 

Second question:  I'd like to be able to do the same thing with a bluetooth serial port connection.  I have not figured out how to create 2 bluetooth serial ports, connect one to each device, and use the aforementioned program that has not been found yet to watch the communication.  Can anyone point me in the right direction for that also?

Thanks!

Antiocles

---

### Post by HermanAB on 2007-10-11
Minicom.

Otherwise, download Winhexcom here:
[http://www.aeronetworks.ca/shareware.html](http://www.aeronetworks.ca/shareware.html)

I think it works in WINE - I haven't worked on that program in years, but it is stable and free of bugs.

Cheers,

Herman

---

