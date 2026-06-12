---
title: "Setting up Secondary DNS"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by duceduc on 2010-12-29
I have been playing with my web server for a bit and have configured quit a few services on it. Among other things, I have several domains in which I am hosting. I would like to setup my own dns server; however, I'vve read that you need at least two static ips. I have none.

So, I am using other providers to help me resolve my domains. I have been using zoneedit with no complaints other than their lack of email support. I can't complain too much since I am using their free service. Up until now, I have only two NS. Now, I wish to setup a secondary (backup). My choice for secondary dns is with buddyns.com. I do believe I have configure it properly, but I notice something maybe out of place in regards to the serial #.

Here is what I noticed and it maybe normal but I don't know for sure. Whenever, I make changes to my primary zones(zoneedit), the serial # of my soa goes up by one. When I check the status with intodns.com, I still see the old serial #. My primary NS have changed to the new serial but the secondary hasn't. It is still waiting to be updated from my primary. Shouldn't the serial # always display the most current from my primary and not from the secondary?

Here is a screenie of what I am talking about. The status shows the serial number to be 1284803412 and not 1284803413.

[IMG]http://img.photobucket.com/albums/v645/duceduc/secondary-dns-error.png[/IMG]

---

