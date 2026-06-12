---
title: "adsl connection working but no internet!!!!"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by fugative on 2007-08-29
OK guys, be kind with me i'm not a complete noob but i'm missing something.
my adsl is connecting i can ping my isp but i can't ping google. e-mail, synaptic etc cannot connect  and i'm using doze now so help me quick pleeeease!

sys:
7.04 feisty
adsl internet via usb sagem modem

have checked pap and chap secrets - ok
have checked ueagle-atm -  seems ok
have deactivated firestarter -  no change

network manager shows connection and even a few packages are being transeived BUT no internet etc

what am i missing? 

David

btw wireless won't connect to ad-hoc network either -  maybe coincidence

---

### Post by LinuxMonk on 2007-08-29
I had a similar problem - my DSL was online, my laptop connected to the 'net just fine, but my desktop would not.  Discovered the firewall program was running and blocking *everything*.  Look under "System" for "Firestarter".

---

### Post by Seti on 2007-08-29
Sounds like a DNS issue to me.

---

### Post by fugative on 2007-08-29
Linuxmonk - did mention that i'd deactivated firestarter to no result also had a look through it to see if it'd changed any iptable settings that might have stayed but don't think so.

seti - thanks but would you like to speculate a bit more specificly 

I had something similar with the ad-hoc internet share but i just had to put the ip of the host box in the preferred DNS bit on the network settings. this seems to be a bit more sinister... or too simple to figure out.

keep up the suggestions guys

---

### Post by fugative on 2007-09-04
I've kinda solved it, I uninstalled network manager, which is of no use to me anyway, my modem is USB and my network is ad-hoc which NM doesn't manage. so i got shot of it. Then i could ping my isp, which although i said i could do it stopped working and i was in denial then i pinged myself using the client ip from my isp and checked firestarter which said i was getting an input from my wlan this should not be sending my internet signal so i disabled it with a # before auto wlan0 in interfaces. rebooted and BAM BBC world news live and ... well quite informative, i feel like a geek warrior.

Now can i backtrack and solve the problem that the ubergeeks can't so i can get my wlan working again. I'll try but it seems obvious that NM is the culprit.

Question: somewhere there must be a file which tells the machine the ip to use when connecting to the net for me this had changes to 192.168.1.1 (my wlan static ip) then when i changed that to 192.168.0.1 it followed so it must have wlan0 as default connection to the net something that i changed in firestarter to ppp0 but only on deactivating wlan0 did it work.

got to be enough info there to formulate a cure.:guitar:

---

