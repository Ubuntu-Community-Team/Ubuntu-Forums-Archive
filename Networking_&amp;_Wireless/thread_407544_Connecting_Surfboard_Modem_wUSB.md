---
title: "Connecting Surfboard Modem w/USB"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by Retired Old Coot on 2007-04-12
Just installed Ubuntu 6.06 on an old laptop over a badly corrupted W98 OS. So far I like what I see. Next step is connecting to internet. Cable modem is Motorola SB4200 using USB outlet to laptop USB port (laptop does not have ethernet connector). 

No internet connection when devices are simply connected. Tried resetting the modem and restart of Ubuntu with modem connected but no joy. Tried running modem installation CD but Ubuntu doesn't recognize and provides error message. 

I'm very new at this, but want to learn. I found this link [http://howtos.linux.com/howtos/Motorola-Surfboard-Modem/prerequisites.shtml](http://howtos.linux.com/howtos/Motorola-Surfboard-Modem/prerequisites.shtml), however it is way over my skill level. Can someone please provide some help with this...I want to believe that Ubuntu "just works". Thanks in advance.

---

### Post by happy-and-lost on 2007-04-12
First of all, welcome to the faboulous free and intriguing world of Linux :D

Well, that article was written in 2003, and Linux progresses quickly. It should work with minimal fuss. First we need to know if Ubuntu can even see your modem. Open up the terminal (Applications -> Accessories -> Terminal) and type *sudo ifconfig*. Post what it says back here.

EDIT: Possibly simpler, System -> Administration -> Networking should show you whether or not anything's been detected. It may be a simple clicking of the "Activate" button if it has seen it.

---

### Post by Retired Old Coot on 2007-04-12
**happy-and-lost:** Thanks for the help. Here's what it says:

Link encap:Local Loopback
inet addr:127.0.0.1   Mask :255.0.0.0
inet6 addr:  ::1/128  Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:55 errors:0 dropped: 0 overruns:0 frame:0
TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:4228 (4.1 KiB)     TX bytes:4228  (4.1  KiB)

---

### Post by Retired Old Coot on 2007-04-12
Just noticed your edit; Network settings, Connections tab, shows:

[SIZE="5"]Modem connection
The interface ppp0 is not configured[/SIZE]

Hope that helps.

---

### Post by happy-and-lost on 2007-04-12
Very odd. Quick question about the modem (Unfamilliar with this type of technology), is it an "always on" connection type of modem, or do you have to dial up with it?

If it's an always on type, it's very strange that it shouldn't be recognised (even my stripped-down Debian install recognises usb modems). I don't know if it was just me, but 6.06 would often do odd things networkingwise on installation. Did you try to get online whilst you were in liveCD mode? It may be worth booting into the liveCD to see if it's detected in the network setting from there.

Sorry I'm not more help, 8 months into full-time Linux and I've still got much to learn!

---

### Post by Retired Old Coot on 2007-04-12
Modem is fed by cable and is always on (there is a stand-by switch on top, but I never use it) and it must be working as I'm able to send this . Trying to be clear here: Cable from outside world goes directly to the modem, USB cable from modem output to the (only) USB connection on the laptop. 

I did not try the LiveCd feature as I had an essentially "dead" laptop, the previous MS OS having been totally screwed by the previous owner who gave it to me rather than putting it into the dumpster. I was able to get it to boot on the Ubuntu disk and did the install immediately thereafter. FWIW, the laptop seems very happy with Ubuntu, Open Office works great, I've installed many of my photos from a CD, and it's playing music from CD's (but not mp3's, an issue I'll worry about much later). No issues that I can see except for failure to "see" the modem.

---

### Post by Retired Old Coot on 2007-04-12
Happy news! My Ubuntu-powered laptop is now connected to the internet. I wish I could tell you what changed, only thing I did was to reset the modem (by unplugging it for a minute), but I'd done that once before without effect. I'm going to chalk it up to gremlins and get on with things. Thanks you happy-and-lost for your patience and advice. =D>

---

### Post by rfs1970 on 2007-05-02
Hi There !

I am so envious you know?

I am trying to connect this bloody modem (sorry, but I am quite frustrate with all the job done), 
and till this exactly moment, I couldn't connect / access the modem via usb.

I am using (now ) Xubuntu 7.04, and my computer, to be honest with you is quite old... It has:

500mhz processor,
128mbytes ram
6 gb HD and
NO ETHERNET PORT.

I tried ubuntu 6.10 and now Xubuntu 7.04,
I even tried the complete recompilation of the kernel
with a few setting that I found in internet
(it took almost 4 hours to complete the process)

Its so sad you know...

Every forum that I look for a help,
I always got replies saying:

- Hey Dude, why dont you buy an ethernet board (/pcmcia) ?

Well... to be honest, I fully understand their point of view,
but I am a kind of broke (just for a change), and 
I am quite frustrate that Linux cannot handle this kind of connection
(cable modem + usb)

- I know I know, for sure someone there has a link comparing how
bad is an usb connection and how amazing is the ethernet one.

But mate... 
Why I can't connect my USB modem in Linux !!!???????

If you, or someone else could help me, 
I really appreciate that !


Thank you in advance !


r.

---

### Post by rfs1970 on 2007-05-06
Hi There...

Finally I figured it out what was going on!
If one of you guys are having the same problem,
take a look at : 
[http://ubuntuforums.org/showthread.php?t=428499&highlight=surfboard](http://ubuntuforums.org/showthread.php?t=428499&highlight=surfboard)

;)

---

