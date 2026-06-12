---
title: "Telkom Mega 105WR ADSL"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by phh on 2008-09-16
Can anyone help me get this router working in 8.04? (No success via Network Settings)

---

### Post by prshah on 2008-09-16
> **phh said:**
> Can anyone help me get this router working in 8.04? (No success via Network Settings)

The model looks fine, there should be no problems using this in Ubuntu/Linux.

What exactly is your problem? Are you unable to use the wired ports or the wireless access? What do you mean by "get this router working in 8.04"? What makes you think it's not working? Please be more specific in what the trouble is.

---

### Post by SecretCode on 2008-09-16
I assume you're directly connected via Ethernet.

How is the router set up - bridge mode or router (as shipped)?

I don't go directly into the router in my normal setup as I have a SmoothWall firewall in the way, but I have connected to it directly and run a pppoe connection from Ubuntu 8.04. My router is set up in bridge mode.

---

### Post by phh on 2008-09-18
I did a new 8.04 install for a friend. All OK, except we can't seem to get an internet connection. It looks as if the computer sees the router (connected via USB port) but I cant find where to enter the PPPoE settings. Not sure if the "wired connection" in Network Settings is the router, but in any case am unable to enter PPPoE info for Telkom connection.

---

### Post by SecretCode on 2008-09-18
Still ... are you trying to set up the PPPOE link from Ubuntu? (Which you do with **pppoeconf**, **pon dsl-provider**, and all that - STF.) For this you set the Mega105WR in bridged mode.

Some people have problems with pppoe, so it's worth trying it in router mode.

Can you ping the router's IP address from Ubuntu? I think the default is 10.0.0.2 if you haven't changed it. In fact, does your eth0 receive an IP address from the router via DHCP? 

If you can ping it, can you log in to the router web admin panel? [http://10.0.0.2](http://10.0.0.2) - user admin, password admin unless you've changed it.

I have the Mega 100WR2 but I hope the web admin is the same. 

To set router mode, go to **Advanced **> **WAN **> **quickstart**, and select 'PPPoE', wait, and enter the ISP username and password. Click **Apply** - and then click **Save settings**! This should remove any need to configure anything in Ubuntu, at least for testing.

---

To set bridged mode, on the same page, select 'Bridge' in the Type: dropdown. 

To change the router's IP address and enable/disable DHCP, go to **Basic **> **LAN Configuration**.

---

### Post by SecretCode on 2008-09-18
Wait - I just spotted that you said "connected via USB". I haven't worked with this, and it may be different on your model. But it means either you **have **to set up PPPOE on the router ... or you have to do it in ubuntu. :D

---

### Post by phh on 2008-09-18
Thanks! Tried Ethernet connection first, then USB, with same result - will return to Ethernet. What terminal input will be required for **pppoeconf, pon dsl-provider**? The router is set up as shipped - does that mean it is in router mode? Unfortunately the friend's computer is a distance away hence the time lag in my response to your posting... BTW, the router LED's are all on in the right places.
Ubuntu is great - glad to be free of Windoze!

---

### Post by SecretCode on 2008-09-18
I'm pretty sure 'as shipped' is router mode with address 10.0.0.2 - but of course it won't have any pppoe settings. I presume it's a Telkom ADSL link. Who is the ISP? 

First make sure you can ping the router and get to its web interface ... worry about pppoe on ubuntu after that!

---

### Post by phh on 2008-09-19
ISP is Telkom. Will ping router next time I have access to the machine... Had a Telkom Premium Combo myself on Win XP before - reasonably familiar with web interface. Many thanks again for your help...

---

### Post by phh on 2008-09-26
> **SecretCode said:**
> I'm pretty sure 'as shipped' is router mode with address 10.0.0.2 - but of course it won't have any pppoe settings. I presume it's a Telkom ADSL link. Who is the ISP? 

First make sure you can ping the router and get to its web interface ... worry about pppoe on ubuntu after that!
Justo let you know our router is working now. Your posts pointed me in the right directio. Many thanks again.

---

### Post by SecretCode on 2008-09-26
Good to hear it!

---

