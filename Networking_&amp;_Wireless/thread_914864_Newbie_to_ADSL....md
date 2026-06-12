---
title: "Newbie to ADSL..."
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by s_raghu20 on 2008-09-09
Hi Guys,

I am fairly new to ADSL connectivity, before this I was using Cable Modems, which were providing connectivity to my router with 24x7 uptime.

Here, back in India, I am using a ADSL connection from a provider - BSNL.

They have provided a Nokia-Siemens Modem cum Router (4 port Ethernet and Wireless) model number SL2_141.

I have a new desktop with both win-xp and Hardy on it (dual boot). Moreover I have a laptop that has vista business and hardy desktop (again dual boot).

The connectivity works normally fine with windows xp/vista.  
the way I connect is like this - 

- The ADSL cable comes till the modem.  
- As I said, its a modem cum router, so, I put in an ethernet cable in one of the LAN ports and put it through to the desktop/laptop network port.
- in windows, I try to dial through a connection that goes through WANminiport (ppoe) and it connects through.

However, when I try to connect through Ubuntu, I just dont manage to move forward.  

Various attempts at finding how-to on google resulted in few ideas, almost all of which pointed to doing a 

<code>
sudo ppoeconf
</code>

However, on both my ubuntu installations, I dont have this command.  If its a package that I need to install, I need internet connection for that, but if I cant connect, how do I get the new package.

Quite a dilemma...

Suggestions/ideas please... 

regards
raghav..

---

### Post by superprash2003 on 2008-09-09
its sudo pppoeconf

---

### Post by s_raghu20 on 2008-09-09
> **superprash2003 said:**
> its sudo pppoeconf

Well, thanks for pointing out the typo.  It did indeed work.  

But, not as I expected.  

As I tried to put it, I have now two systems, and I want to share the ADSL connectivity through the built in router (in the modem).

When I dialled from my laptop ubuntu (using the corrected command and configuration thereafter), I did connect through. However, it did break my other system's connectivity.

The problem is, I am missing the router role of the modem around here.  The modem perspective seems to work, but I am yet to figure out a way to tell the device to share the already connected internet connection to other systems.  

In my point of view that configuration should be with the modem/router device and not with the connecting pc. I am yet to find more around it.

If anybody has tried anything around it, pls help..

regards
raghav..

---

### Post by superprash2003 on 2008-09-10
for multiple pc internet access, you need to change your router to ppoe mode.. then sudo pppoeconf is not required.. to do this follow [http://www.calcutta.bsnl.co.in/dataoneinstall/mu10.html](http://www.calcutta.bsnl.co.in/dataoneinstall/mu10.html) from steps 9 to 13 .

---

### Post by s_raghu20 on 2008-09-17
> **superprash2003 said:**
> for multiple pc internet access, you need to change your router to ppoe mode.. then sudo pppoeconf is not required.. to do this follow [http://www.calcutta.bsnl.co.in/dataoneinstall/mu10.html](http://www.calcutta.bsnl.co.in/dataoneinstall/mu10.html) from steps 9 to 13 .

Thanks a ton... That really helped.

Now I keep my modem on always up mode (I have that unlimited plan from BSNL) and therefore both my desktop and laptop are always connected.

Thanks. :)

---

