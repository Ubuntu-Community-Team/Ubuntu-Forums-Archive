---
title: "Update broke wireless"
date: 2006-08-26
forum: Networking &amp; Wireless
---

### Post by Otto-C on 2006-08-26
I have been following the Xorg update that has broken
so many systems.
I too have have had a problem with downloading an update.
On about July 21 I clicked on the update button on the
desktop. There were supposed to be about 60 items to
download. I was using the wireless function on a public
wireless network. After about an hour with 2 items to go
it acted like it timed out. I went to system > admin >
networking and my wireless connection was gone.
I have followed a number of threads to no avail.
On August 5 I did a full update using apt-get functions.
On August 17 a further update was done also using the
apt-get functions. Now full Kubuntu 6.06.1.
What I want to know is if downgrading to 2.6.15-25-386
would return me to where I was before doing the 1st update?
That is with wireless back working.
If so how would I do this?
Or does someone have a better solution?
tia
Otto-C

Using a Dell Inspiron B130 laptop
60 gb HD,512 MB RAM,Celeron M 1.40 GHz
Dell 1370 minipci wireless, Broadcom NIC
BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller

After downloading the updates my wireless connection was broken.
*
Doing modprobe ndiswrapper

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-26-686/kernal/drivers/
net/ndiswrapper/ndiswrapper.ko): Invalid argument

I can supply further if it will help.

---

### Post by Melcar on 2006-08-27
I have the same problem.  After countless hours of trying to figure it out, I have concluded that the xserver updates are responsible.  I tried nearly everything with no success (wireless simply would not work anymore).  I finally decided to reinstall Ubuntu and update with a k7 kernel (I'm running a Sempron based laptop) and then installing all the updates (includung xserver updates).  It has been 2 days now and have had no problems so far.

---

