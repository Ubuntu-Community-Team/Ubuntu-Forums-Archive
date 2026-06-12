---
title: "VNC problem.. Firewall?"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by jobsonandrew on 2008-01-31
Hello.. I have **another** VNC question :P... Actually it might be easily solved..
At home I run Ubuntu Gutsy 64bit and have remote desktop enabled.. I also changed the port that the built in remote desktop uses by editing the settings in gconf-editor.. From my windows Vista PC I can VNC to the Laptop using **192.168.0.3:7392** (you have to specify the port if its not 5900..
This works fine of course.. However, i cant access the laptop from work.. (a very large company with very large IT infrastructure) using the correct IP (**external** IP.. I know how this stuff is supposed to work, so im not trying to get at 192.168.... from work lol)..
VNC viewer gives me an error "connection refused by host" and the error code 10061
Googling the error hints that the connection could not even be established.. rather than the connection being made and the host refusing it as the error suggests..
Im wondering if anybody knows of a way to tell if my work's firewall is blocking outgoing VNC connections or something.. or what other options i might have... Other things work from the office, like FTP and p2p web interfaces

Oh and by the way, ports are forwarded correctly on my router ;)

---

### Post by stalker145 on 2008-01-31
> **jobsonandrew said:**
> Im wondering if anybody knows of a way to tell if my work's firewall is blocking outgoing VNC connections or something.. or what other options i might have... 

The only way that I can suggest you to find out if work is blocking you is to find an open hotspot (library, Starbucks, etc) and try it from there. Places like that normally don't block anything. If it turns out your work is blocking your desired port, it'll be trial and error (or a nice admin) to find out an open port for you to use.

NMCI, who runs the USMC network, has the audacity to block port 22. I've ended up having to tunnel 22 through 80 using my Webmin server. The lengths they make us go through ;)

---

### Post by jobsonandrew on 2008-02-01
lol yes.. well this looks pretty strict but ive had massive success now...
tunnelling a VNC connection over SSH works like an absolute gem..

I love it when you teach yourself about something and it works so brilliantly.. especially if it means you're circumventing those in charge :)

---

