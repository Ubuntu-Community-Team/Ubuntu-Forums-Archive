---
title: "The only thing that sucks about Ubuntu Hardy! Need help with connection sharing"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by felixdzerzhinsky on 2008-06-01
It is 2008 and I am expected to mess around for hours trying to configure a static network for internet sharing!

Why is there not something in the Network Manager like there is for internet sharing like there is in Windoze and OSX?

This is whart is needed!

[http://www.macinstruct.com/node/118](http://www.macinstruct.com/node/118)

---

### Post by hanzomon4 on 2008-06-01
Preach dammit!

---

### Post by FuturePilot on 2008-06-01
Yes that is a pain. I tried doing that and spent hours, days, weeks! trying to get it to work. I got two computers able to ping each other, but I couldn't get them to share the Ethernet. Finally just gave up and bought a router.

---

### Post by bufsabre666 on 2008-06-01
[http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)

worked fine for me a year ago before i got the wireless router, although i dont know how to use your computer as a wireless router, thats pretty cool

---

### Post by tact on 2008-06-01
It just comes down to knowing the tools...  :)   It can be pretty easy if you are using something like firestarter (GUI to do it) or ipkungfu (simple config files) as your interface to iptables.  In either of these you can pretty easily set up, enable or disable internet connection sharing.

---

### Post by regomodo on 2008-06-01
He isn't the only one with this gripe with Ubuntu. My brother told me, after his XP install ate itself, he would have used Ubuntu if it wasn't for the fact he couldn't share his network connection.

His pc has wifi and ethernet and in xp he could connect his ps3 via the pc to the internet. I don't think it is something to be dismissed as non-essential.

I too would like something simple in GUI form to bridge any network connections.

---

### Post by K.Mandla on 2008-06-01
Moved to Networking and Wireless. Perhaps someone will help you get it working in here.

---

### Post by felixdzerzhinsky on 2008-06-01
> **tact said:**
> It just comes down to knowing the tools...  :)   It can be pretty easy if you are using something like firestarter (GUI to do it) or ipkungfu (simple config files) as your interface to iptables.  In either of these you can pretty easily set up, enable or disable internet connection sharing.


It is 2008. I am a user not a sysadmin running a server from the command line. I see a few others share my view that this should be easier. Firestarter has not worked for me so far.

Anyway thanks to those who reply. I have someone on IRC helping me with this. That is the thing that is great about Ubuntu.

---

### Post by felixdzerzhinsky on 2008-06-01
The really great thing about ubuntu is the community. My solution is here:

[http://ubuntuforums.org/showthread.php?p=5092719#post5092719](http://ubuntuforums.org/showthread.php?p=5092719#post5092719)

I hope some network sharing 'thingie' could be a feature of Intrepid Ibex.

---

### Post by ayenack on 2008-06-01
Not sure if any one has mentioned it but Firestarter can do this pretty painlessly. Take a look at this.

[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

---

### Post by tact on 2008-06-01
I think the matter is complicated by the fact that networkmanager (the automatic network connection manager that does a great job) can only allow one network adapter to be up at a time.

For what its intended (find a network adapter with a connection and bring it up, switch to a faster adapter if one comes available, or fall to a slower adapter if the faster connection fails, e.g. switching between wired/wifi) networkmanager is great for the many with simple connectivity needs.

For what its worth - NWAM (network auto magic) in various shades of solaris works much the same.  Like networkmanager its still not full featured yet.  

If you want to share network connection then by definition you need at least 2 network adapters up at the same time.   So step 1 is taking control of those adapters away from network manager and manually configuring.  (As soon as you manually configure a network adapter you take it out of networkmanager's control).

Perhaps some day in the future networkmanager (or its replacement) will be able to handle having more than one network adapter up at one time and permit connection sharing etc.

It is 2008 and even now you can use gui to manually configure network adapters (click nm-applet on upper panel, click "manual configuration"), install firestarter (synaptic), and configure connection sharing (firestarter).

---

