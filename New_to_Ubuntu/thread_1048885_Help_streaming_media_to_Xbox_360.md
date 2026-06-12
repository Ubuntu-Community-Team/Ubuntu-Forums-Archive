---
title: "Help streaming media to Xbox 360"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by Bowwizle502 on 2009-01-23
Hey. I am currently running Ubuntu 8.10 on my desktop. My desktop is connected to the internet via wifi and my Xbox 360 is connected to my desktop via ethernet. I am attempting to stream music from my computer to my Xbox, however, I guess the Xbox requires an IP address. How can I assign my xbox an ip address so that i can stream music. Should I use ubuntu as a gateway? Or is there an easier way to just stream music directly to my xbox? I have attempted bridging eth0 and wlan0, but that achieved little. Is there something I'm missing?

---

### Post by mrbiggbrain on 2009-01-23
> **Bowwizle502 said:**
> Hey. I am currently running Ubuntu 8.10 on my desktop. My desktop is connected to the internet via wifi and my Xbox 360 is connected to my desktop via ethernet. I am attempting to stream music from my computer to my Xbox, however, I guess the Xbox requires an IP address. How can I assign my xbox an ip address so that i can stream music. Should I use ubuntu as a gateway? Or is there an easier way to just stream music directly to my xbox? I have attempted bridging eth0 and wlan0, but that achieved little. Is there something I'm missing?


Xbox is a media exstender not a media client, under the terms of the media exstender your xbox360 will only work with windows media center (its not like a DLNA media server support i dont think) so youll need media center, media player 11, or a program 100% compatible with sending out those streams.

so.... i douno if youll get it working under linux. its one of microsofts ways of locking you into their software.

---

### Post by Bowwizle502 on 2009-01-24
Ah... Well I'm not about to install windows.. There's no other workarounds? Possibly running Samba? Or masking a program as "Media Center"? Or maybe running it under an emulator?

---

### Post by mrsudo on 2009-01-24
i think you may be lloking for ushare.  a linux program for multimedia streaming to xbox360 and ps3.  i think you can install through the ubuntu repositories.  then all you have to do is configure the ushare.conf file with your local folder and network interface and you should be good to go.  

start ushare with:

ushare -x&

---

