---
title: "Help With Networking Wireless Router Included Help Me Please"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by apergole on 2007-02-26
Hi everyone i have a big problem at the moment!

i am currntly using a router to share my bigpond internet connection! i use cable for the networking not wireless in my room there is a cable slot for the internet etc... the internet is setup and all the computers work with the internet etc.

My problem now i am able to  be on the internet for half hour or so then it cuts out saying please diagnose or something and then i am unable to use the internet! i unplug the cable then plug it back in and i cannot connect to the internet again until i restart mi whole laptop!

this is the only way the connection comes back!via restarting my computa! my computa also is the only 1 that does this in the house mi brothers works fine and neva disconnects or nothing!

wat is going on!! half an hour or so mi computer disconnects from the internet and to use it again i have restart my computa! even logging out then logging back in dosent fix it!

wat is going on some1 please help me ouT! asap

thanks guyz

---

### Post by ukripper on 2007-02-26
> **apergole said:**
> Hi everyone i have a big problem at the moment!

i am currntly using a router to share my bigpond internet connection! i use cable for the networking not wireless in my room there is a cable slot for the internet etc... the internet is setup and all the computers work with the internet etc.

My problem now i am able to  be on the internet for half hour or so then it cuts out saying please diagnose or something and then i am unable to use the internet! i unplug the cable then plug it back in and i cannot connect to the internet again until i restart mi whole laptop!

this is the only way the connection comes back!via restarting my computa! my computa also is the only 1 that does this in the house mi brothers works fine and neva disconnects or nothing!

wat is going on!! half an hour or so mi computer disconnects from the internet and to use it again i have restart my computa! even logging out then logging back in dosent fix it!

wat is going on some1 please help me ouT! asap

thanks guyz


I don't know what is going on with your computer but to avoid restart you can try following whenever your internet gets disconnected (assuming you using eth0 port):

$ sudo ifdown eth0

$ sudo ifup eth0

---

### Post by apergole on 2007-02-26
wat do u mean try the following wat do i do???

---

### Post by ukripper on 2007-02-27
> **apergole said:**
> wat do u mean try the following wat do i do???

Open your Shell/Terminal/Command line (whatever you call it).
Then type the comands I referred to in my post above exactly.

Goodluck.:guitar:

---

