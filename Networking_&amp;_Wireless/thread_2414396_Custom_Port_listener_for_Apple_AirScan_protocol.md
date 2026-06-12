---
title: "Custom Port listener for Apple AirScan protocol"
date: 2019-03-09
forum: Networking &amp; Wireless
---

### Post by markosjal on 2019-03-09
So after looking around on the web , I see much about AirPlay and AirPrint compatibility for Ubuntu but almost nothing about AirScan.

I have a custom app for scanning.  I want to try to inegrate AirScan into, so a modern Apple OS might detect it as an AirScan compatible scanner.

As I understand it , I need to listen on port 8090 , and it must be advertised in Avahi

from [http://testcluster.blogspot.com/2014/03/scanning-from-apple-airprint-airscan.html](http://testcluster.blogspot.com/2014/03/scanning-from-apple-airprint-airscan.html)
AirScan/eSCL devices advertise themselves over mDNS as _uscan._utcp.  One of the fields in the TXT record is "pdl".

How do I create a listener to start at startup then how does one go about "routing"  that listener and replying to it? 

ALso there is the Avahi part in creating a custom app advertisement,. I suppose this is easy if you have worked witth Avahi.

I was wondering if anyone here had some pointers????

---

### Post by markosjal on 2019-03-11
Okay so I found tcpserver and it seems it does what I am looking for but being a total noob at most of this i can only say it seems adequate to listen on port 8090.

Now if I set it up I can listen, but I must first advertise  a scanner via Avahi so some apple device will try to talk to it.

Later I need to try to figure out appropriate responses.

Any input from anyone here?

---

