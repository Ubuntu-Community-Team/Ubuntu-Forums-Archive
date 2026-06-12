---
title: "Network problems. Windows?"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by AlexisMclovin on 2008-08-13
Earlier i had a problem connecting to the internet at home, with my parents inhabiting their network with Windows based pcs. I ran ifconfig and my internet started working again.It has been working for quite some time. Recently my mom turned the router and dsl box off, and for the whole day noone was online. I connected my Ubuntu Hardy pc to the router and turned everything back on , and i was the first to get online this day. I turned everything on , and my internet was running just fine. Well, a few hours later my parents tried to get on, but they couldnt. For some reason they couldnt connect to the internet. I have my Ubuntu set for Roaming mode, and we all think the problem is linked directly to me having Ubuntu, and them having Windows. I dont really think that since, directly after i got online i hooked my Xbox 360 up online and played people. I have no idea. Any help would be greatly appreciated. If i dont come up with a solution my dad might do something drastic. Meaning he will miraculously fix the internet, but ban me from it. So you wont ever get to see my lengthy posts again :(

---

### Post by Ryan450 on 2008-08-14
> **AlexisMclovin said:**
> Earlier i had a problem connecting to the internet at home, with my parents inhabiting their network with Windows based pcs. I ran ifconfig and my internet started working again.It has been working for quite some time. Recently my mom turned the router and dsl box off, and for the whole day noone was online. I connected my Ubuntu Hardy pc to the router and turned everything back on , and i was the first to get online this day. I turned everything on , and my internet was running just fine. Well, a few hours later my parents tried to get on, but they couldnt. For some reason they couldnt connect to the internet. I have my Ubuntu set for Roaming mode, and we all think the problem is linked directly to me having Ubuntu, and them having Windows. I dont really think that since, directly after i got online i hooked my Xbox 360 up online and played people. I have no idea. Any help would be greatly appreciated. If i dont come up with a solution my dad might do something drastic. Meaning he will miraculously fix the internet, but ban me from it. So you wont ever get to see my lengthy posts again :(


Alright first off let me put your mind to ease. Ubuntu and Windows will live on the same network without any troubles. I do it all the time. 

What it sounds like is happening is that your router is running out of DHCP leases. 

Every time a computer comes online the first thing it does is send out a packet to the router asking it for an IP ADDRESS. Your router will usually give it one and it can get online. 

However most routers will keep a certain lease time. This is the amount of time a computer can use that address before it expires and the computer needs a new one.

Lately I've seen a lot of routers that set a lease time way too high, and it ends up running out of available addresses without releasing old ones. I'd consult your router's DHCP list and the amount of addressing it has still available, if you have your routers manual handy be sure to consult it.

Also if it helps to convince your parents, I'm a currently studying Network Engineering and Internet Security, about to graduate with honors after one more semester, I'm also working part time as a Network Consultant for both windows and Unix based networks.

---

### Post by cariboo on 2008-08-14
What you can do on the Windows computers is click start-->run, type cmd in the box and hit enter, this will bring you to a dos window. in the dos window type:

```
ipconfig /all
```

this will print out the computers ip address and a lot more information.
Next in the dos window type:

```
ipconfig /release
```

This should echo back something like:

```
0.0.0.0
```

Next in the dos window type:

```
ipconfig /renew
```

This should get the computer a new ip address, and you should be able to connect to the internet.

Do this on the other windows computers on your network and everybody should be happy.

Jim

---

### Post by AlexisMclovin on 2008-08-14
Im unavailable to try either of those at this time, but when i get back home, ill do what i can, then let people know whats going on. Well i got home and everything seems to be ok. I tihnk the router reset iteself nad then my mom's windows computer ran its auto settings so everything is good. Thanks for the concern.

---

### Post by Iowan on 2008-08-14
If you're interested... next time you're on at home, check **ifconfig** to see what address you're assigned.  from an XP box it's Run>cmd to get a "DOS prompt, then **ipconfig**. Dunno about Vista... This *might* give you some idea of what IP addresses are being used.

---

### Post by AlexisMclovin on 2008-08-14
Well the network isnt going so well.I fixed the internet for my parents and their Windows works fine, but now mine wont work. It says a wire is connected but i cant get online.

---

### Post by dmizer on 2008-08-14
What IP address does each computer have when it is online?

also, what kind of router do you have? (make and model)

check the router settings to see how many IP addresses it is set to lease.

---

### Post by AlexisMclovin on 2008-08-14
my address is different from my parents...we have a Network Everywhere, 5-port hub...how would i check the router settings??

---

### Post by Iowan on 2008-08-14
> **AlexisMclovin said:**
> ...how would i check the router settings?? Most "modern" routers have a web interface.  If you can find what addresses the router is handing out (eg. 192.168.1.5), the router can "probably" be reached via browser (eg. [http://192.168.1.1](http://192.168.1.1)). The default address depends a lot on:> **dmizer said:**
> ... what kind of router do you have? (make and model)


---

### Post by dmizer on 2008-08-15
> **AlexisMclovin said:**
> my address is different from my parents...we have a Network Everywhere, 5-port hub...how would i check the router settings??

A hub is not a router.  Are you sure you have a router?  A hub cannot give out IP addresses.  If your IP address is different than your parents IP, then it's possible that your modem is also doing routing, but that routing could be restricted by the ISP when the router settings were configured.

It would really help to know more about your equipment.  It would have also helped to know exactly what IP address you were getting.

---

### Post by AlexisMclovin on 2008-08-16
> **dmizer said:**
> A hub is not a router.  Are you sure you have a router?  A hub cannot give out IP addresses.  If your IP address is different than your parents IP, then it's possible that your modem is also doing routing, but that routing could be restricted by the ISP when the router settings were configured.

It would really help to know more about your equipment.  It would have also helped to know exactly what IP address you were getting.
Oh wow, yes its a network hub, not a router. The correct ip address(one that works) is 99.194.154.10 The wrong one is something way off like 254.168 something. I believe i discovered today that the problem isnt Ubuntu its the fact that im using a hub. Dont know , but i keep messing up our internet.the hub is a Network Everywhere Fast Etherenet 10/100 5-Port Hub. Modle No. NH1005-WM

Do you think having a router would fix mt problems? I remeber when we had one everything was fine.

---

### Post by Iowan on 2008-08-16
> **AlexisMclovin said:**
> Oh wow, yes its a network hub, not a router.Interesting twist... Some modems "lock onto" the MAC of the computer and must be reset to work with a different machine.  Curious how Windows machines get around it (or why they don't have the issue).  A router would give the modem a constant MAC.

---

### Post by dmizer on 2008-08-17
> **AlexisMclovin said:**
> Do you think having a router would fix mt problems? I remeber when we had one everything was fine.
Yes, a router would fix your problem. No, the problem is not Ubuntu.

---

### Post by AlexisMclovin on 2008-08-17
> **dmizer said:**
> Yes, a router would fix your problem. No, the problem is not Ubuntu.

That is fantastic news, thank you. My parents were starting to become angered with my change from Windows to Ubuntu a few monthes ago. They should be glad to hear it....well maybe not we still have to buy a router :/ . Thanks for all the support though. I'll make sure to continue returning to this forum when a problem comes up with Ubuntu.

---

