---
title: "Wired network with access point (AirPort)"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by Yellowbelly on 2007-10-05
This may not be the place to put this but I don't know where else. Anyway my roommate has that apple airport access point thing. We have 1 modem and that access point only has one cat5 port for it as usual. He has a laptop so he rely's on wireless while i have a desktop and rely on wired. I have a netgear router so I tried plugging the modem to the router as usual and have 2 ports going to my computer and the access point. Ubuntu detects the network but bandwidth can't get through so the internet doesn't work. I hate networks and I don't really have an idea whats going on; maybe change the configuration of the router but I know next to nothing on that.

---

### Post by helgman on 2007-10-05
So you setup is something like this?

MODEM 
|
|
ROUTER -------- DESKTOP
|
|
|
ACCESS POINT ~~~~~ LAPTOP

If it is there are a few things we need to know.

1. Is the MODEM acting like a bridge (does it just transfer packages) or is it working like a router? (This can be a bit tricky to figure out but if you can log into the MODEM then the answer is probably the later.)

2. Is your ROUTER configured so that it can reach the Internet? (You should be able to find information about this if you log into the router, just consult the manual if you run into trouble.)

3. Do your DESKTOP/LAPTOP get there IP addresses via DHCP or are they static (set by you)?

First step, as always, make sure that all cables are where they should be and that all lights shine they way they are suppose to.

Next step for me would be to make sure that the IP configuration on every device is set correctly. Check the IP addresses of every device (including the ROUTER and the MODEM if you can). 

Third step (if all is well with IP) is to make sure that every device have a correct route to the Internet. **route -n** on your DESKTOP/LAPTOP should have an entry for 0.0.0.0 pointing to the IP address of the ROUTER. As for the router, that depends on how the MODEM works.

Next step is then DNS. Make sure that you get a correct answer when using **nslookup** on the DESKTOP/LAPTOP. Here is my output for one query:

```
$ nslookup ubuntuforums.org
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
Name:   ubuntuforums.org
Address: 91.189.94.186
```

You should get a similar answer.

Post back your findings if you don't figure it out and don't be afraid to ask if there is something you don't understand.

Regards,
Helgman

---

### Post by Yellowbelly on 2007-10-06
1. I would have no idea how I could log into the modem. I think it's just a plain modem, no router. No extra ports or anything. But then again I could be wrong.

2. mmm, I don't think I have the manual anymore. I figure this is the problem or some settings need to be changed inside.

3. I've never had to set the ip address manually but then again I havne't really used this router at all.

I'll try this stuff out and get back to ya.

---

### Post by helgman on 2007-10-06
> **Yellowbelly said:**
> 2. mmm, I don't think I have the manual anymore. I figure this is the problem or some settings need to be changed inside.

3. I've never had to set the ip address manually but then again I havne't really used this router at all.

You might be able to find your manual [here](http://kbserver.netgear.com/downloads_support.asp).

So you get your IP address from the routers DHCP server then. That is good to know.

Please let me know if there is anything I said in my previous post that you need help with.

Regards,
Helgman

---

