---
title: "bug? Only port 80 is working"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by came2die on 2008-03-26
What am I using:

ubuntu 7.10
**Hardware:**(as you can see its a normal comp.)
asus p5k
intel quadcore
2gb geil ram
some sata disks
pny 8800 GT
[B]
Internet connection type:[/B]
I am using ethernet connection with DHCP configuration.

**What happened?**

I have reconnected my computer from a modem to router(I have used the same router before(same config. and everything). First thing I have noticed that Amsn is not working. I tried out skype, azureus... It was all the same thing! I checked my routers port forward settings and everything was ok(same as before). As you can see from the title, port 80 was working(but web msn didn't...) I have checked all the configuration stuff I know(I am a newbie on ubuntu). Then I have reconnected my computer back to modem. I thought that now it should work same as before(perfect...), but it didn't. Only port 80 was. So it had to be ubuntu's problem...

How have I "solved" the problem?
I fired up the firestarter, pressed start firewall, and then stop firewall. That solved all my problems.

NOTE: I have installed ubuntu while I was connected to the modem(not router), so maybe ubuntu bugged up when I connected my comp to the router. I don't know, its just a thought.

I hope I will get some reasonable answers(and questions?) from the gurus :)

---

### Post by SpaceTeddy on 2008-03-27
I have never used firestarted (and probably never will) but i know from other threads that i write iptables rules. You can manually see them in any command shell if you run
> sudo iptables -L

i would guess that firestarter put in some rules that only allowed traffic to come in from port 80 or go out to port 80. that would be the simplest answer to your problem. 

if you want/need more information you will have to ask a more specific question, as i am not really aware of what you are trying to ask or find out :)

hopefully it helps... 

PS: you do not need firestarted to configure iptables - it is just a pretty frontend to long CLI commands :)

---

### Post by came2die on 2008-04-02
I made a new thread that users with similar problems can fix them. I also made it because I would like to know why that happened(it makes no sense to me how can reconnecting my computer from modem to a router "bug" entire internet connection?)


> i would guess that firestarter put in some rules that only allowed traffic to come in from port 80 or go out to port 80. that would be the simplest answer to your problem. 

I've ran firestarter after my problem occured so...

---

