---
title: "Networking question"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by Fidelio on 2009-12-04
Hi,
I have a BT Voyager router and have got sharing sorted OK. I have am Ubuntu Box in the Kitchen and an old laptop in the studio and I can share files between them. I also have a standalone windows PC in the studio running Cubase etc. I really don't want this connected to the web.
Currently if I am on my windows machine and if I want to send a file from it, I copy it to a memory stick and stick it in the old laptop in the studio. 
So, I was wondering, is there anyway I can connect my windows box to my ubuntu laptop with an ethernet cable so that it can copy files to the laptop, but it can't access the internet, and how do I go about it?
Sorry if I should have posted this in the networking section. I still feel like a beginner at this stuff.
Thanks
Andy

---

### Post by Zzl1xndd on 2009-12-04
If you are presently using a router then the easiest way would be to connect the computer to the router, then use your router to block any internet traffic to and from the internet. With most routers it is pretty straight forward. 

For example on my router ( A Linksys) it is listed under Access Restrictions.

You may wish to set a static IP or just set the rule by MAC address.

---

### Post by Fidelio on 2009-12-04
Thanks. I'm a bit confused though. Are you saying I should add a wireless card to the Windows machine, and then configure the router so that it doesnt allow it access to the net? I could try that. I didn't see any options in my router to restrict access to a specific machine, but I'm not really sure what I'm doing.
I was hoping to just stick an ethernet cable between them.

---

### Post by tom.gobel on 2009-12-04
> I was hoping to just stick an ethernet cable between them.

I think this requires a crossover cable.

---

### Post by Fidelio on 2009-12-04
> **tom.gobel said:**
> I think this requires a crossover cable.

In the old days, I'm sure I had two W98 machines connected by just sticking  an ethernet cable between them. I could be wrong though.

---

### Post by sandyd on 2009-12-04
nope. they require an ethernet crossover cable.
just the same as parallel port connections & usb connections between computers.
[http://en.wikipedia.org/wiki/Ethernet_crossover_cable](http://en.wikipedia.org/wiki/Ethernet_crossover_cable)

---

### Post by tom.gobel on 2009-12-04
I'm not sure, but if you wanted to include the Windows box in your LAN (e.g. connect it to the router) but keep it "off the internet", you could try adding a rule to your router's firewall that blocked all traffic from the WAN to the static IP you assign to the Windows box.

---

### Post by Fidelio on 2009-12-04
I guess that's what I have then! So can anyone help with my plight?
I'd really rather do it by ethernet as I have the kit already, the router is two floors down and the connection is slow. 
Two machines, one XP one Ubuntu, 2 feet apart, a cable to connect them, just want to send files from the XP box to the linux one, and don't want to have the XP one on the net.

---

### Post by Iowan on 2009-12-04
> **carlee said:**
> nope. they require an ethernet crossover cable.
just the same as parallel port connections & usb connections between computers.And... if you care to go that far back, a null modem was (is) a crossover for serial (RS-232C).
> **Fidelio said:**
> Two machines, one XP one Ubuntu, 2 feet apart, a cable to connect them, just want to send files from the XP box to the linux one, and don't want to have the XP one on the net.
If the laptop has an ethernet connection, a crossover cable between it and the XP box should do what you want. Without setting up ICS on the Ubuntu machine, the XP box should be unable to get to the internet through the Ubuntu box.
There will be a little IP address configuration required...

---

### Post by Fidelio on 2009-12-14
Thanks for all your help, people. I've ordered a crossover cable for a a couple of quid. I'll let you know how I get on....

---

