---
title: "Problem connecting desktop to router via network cable"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by Liet_Kynes on 2008-02-10
I've been having the strangest networking problem.

For some reason my desktop pc cannot seem to connect to my router. (My laptop has no problems connecting via either wireless or network cable)

So far this is what I've tried.

Test if the cable is working:  Plugging the same cable in laptop allows internet access so cable is fine)

Test if the network card in the pc works: Directly connecting laptop to desktop with cable works. I can ssh into both pcs.


I can't even get a ping response from the router on the desktop machine.

ifconfig also shows that there is no cable connected (carrier:0) but if i plug the cable out of the router an into laptop there is connection. Also tested whether all 4 ports of the router work using the laptop and cable.



I'm stumped and can't think of anything else to try.
Any suggestions?

---

### Post by hahahan on 2008-02-10
What OS is running on the desktop?

---

### Post by Liet_Kynes on 2008-02-10
Ubuntu 7.04 Feisty Fawn on both

---

### Post by hahahan on 2008-02-10
You wrote that you connected both computers with a cable succesfull, so one off your cables is a crossover cable.
Maybe you are trying to connect the computer to the router with a crossovercable?

Can you run:
sudo ifconfig eth0 up
sudo dhclient eth0  (eth0 replaced by your NIC)
and post the output.?

Regards.

---

### Post by Liet_Kynes on 2008-02-10
Its gonna be hard to post the results of those since I can't get net access on that machine.
(I'll try typing it later is there any section in particular that would help you?)

However I am sure that the cable is not a Xover its a straight. I can still use it to connect to router with the laptop.

EDIT: dhclient results: No DHCPOFFERS received.

---

### Post by hahahan on 2008-02-10
Since you said you succesfully connected the both machines together I asume your nic is well supported and thus there must be a misconfiguration between desktop and router.
Are both DHCP? Where you online using the LIVE_CD?

Regards

---

### Post by Liet_Kynes on 2008-02-10
Yes the NIC definitely works(worked) under ubuntu before. I have since tried it under xp and live cd of open Suse 10.2. The exact same results. No connection to router. Can connect directly to another pc. I am puzzled.

Is it possible to have a NIC fail (as in hardware failure) in such a way that for some reason it can only connect to a pc directly?

Until I can get a new Motherboard or NIC i think i'll try connecting the desktop to laptop via cable and then bridging the two interfaces allowing the desktop net access.

I have no idea how though :( Is there an option that needs to be set on boot to allow the laptop to be a gateway?

---

### Post by FrankVdb on 2008-02-10
Have you tried disconnecting everything and then connecting the desktop PC to the router using a normal ethernet cable?

Make sure you don't plug the cable into the WAN socket of the router. You have to use one of the LAN connections.

What router do you have? Make sure you're not using the 802.11n protocol. This is not supported yet under Linux. I don't think that is your problem here because a wrong or non-supported would still let you connect to the router. You just wouldn't be able to connect to the internet.

---

### Post by Liet_Kynes on 2008-02-10
lol. If i had plugged into the wan i wouldnt be get net access on the laptop :
)

---

### Post by FrankVdb on 2008-02-10
You are being sarcastic instead of answering my question.

I'll ask my question once more.

Did you connect the desktop directly to the router via one of the router's LAN connections with the router isolated from anything else?

---

### Post by wareagle on 2008-02-10
Do you know your router's ip?

Set up a static IP and try to ping it.  For example, if your router's IP is 192.168.0.1, try this:

```

ifconfig eth0 192.168.0.250/24
ping 192.168.0.1

```

---

### Post by Liet_Kynes on 2008-02-11
> **FrankVdb said:**
> You are being sarcastic instead of answering my question.


Sorry for that. It's just that this problem is frustrating me to no end. I know you guys are just trying to help.

To answer your question. Yes i have connected it with only the pc on lan and no external connection. Also with wireless ap of router disabled. DHCP disabled and static addresses. For some reason the pc NIC just doesn't want to communicate with router but will with another pc.

I've also tried manually setting the speed and duplex of the connection via router and via pc software. Nothing. I'm tempted to just give it up as hardware failure of a very strange kind.

---

### Post by Iowan on 2008-02-11
> For some reason the pc NIC just doesn't want to communicate with router but will with another pc.
Hmmm, almost like the router is blocking the MAC address.

---

### Post by Liet_Kynes on 2008-02-11
I have not blocked any access via mac. (Not that i know of anyway)

---

