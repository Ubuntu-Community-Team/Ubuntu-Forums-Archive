---
title: "DHCP 'interesting' windows/ubuntu results..."
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by bazzer on 2006-11-13
Hi all
Had some rather unusual results with a LAN today, which I put down to a DHCP issue, but I'd appreciate some advice with DHCP in general.

So the network consists of a wired router/modem, a wireless access point, another Windows XP box with a wireless network card (bridged with it's onboard LAN), ANOTHER wireless access point, YET ANOTHER wireless access point, then a good old fashioned switch, where 5 ubuntu clients are to hang off the end. 

With everything connected up, one pc could work at once, no more. So we reverted to adding a couple of windows XP clients to the melee, and here's where it was interesting - one of them reported a duplicate IP on the network.

Now, everything was set to DHCP, with the wired router/modem dishing the IPs out. But the Ubuntu boxes never whined, then just stuck. 

So I'm essentially puzzled as to how it could have happened, and why, when it DID happen, I never got a little fuzzy message telling me something was up? I'm going to read up a little on DHCP stuff now, but is there an app I can sit on an ubuntu machine that will tell me if there is an IP issue, in a similar way to Windoze?

Cheers!

---

### Post by jimbren on 2006-11-13
Why so many wireless access points?  From what you're describing, it sounds like one of the access points is trying to dish out IP addresses and mucking the whole thing up.

Personally, I would strip it down and build it back up.  Disconnect everything, then connect the router.  Connect the wired Windows box, and confirm that it is getting an IP.  Then set up the wireless on that Windows box, confirm that bridging is working.  Then connect an wireless access point.  It should get an IP, right?  Confirm that it does.  Then try your Ubuntu clients, one by one.  

I'm gonna watch this one, it sounds interesting.

jimbo.

---

### Post by bazzer on 2006-11-13
Well, it's a bit tricky. Essentially, the wireless is needed for a short period of time until BT get the broadband on a new line in a new building. The old building has BB access just fine, so I've hooked up a 'wireless bridge' to extend the WLAN about 30m across a road.

I couldn't agree more with the idea of getting rid of the wireless stuff as much as I can, and I will as soon as I can. I will post back when we have BB in, and I move the router to the switch getting all the wireless stuff out of the equation.

Any thoughts on a DHCP monitor type thing though?

---

### Post by bjd on 2006-11-13
*arpwatch* reports duplicate ip's. It does not popup a message though, just reports to syslog and/or mail.

---

### Post by hearty on 2006-12-09
Doubt regarding Arpwatch

I have two subnets on the network 10.129.0.0/16 and 192.168.0.0/16; But I just want to keep track of the ip-mac mapping of 10.129.112.80-180 .

Is it possible to do this in Arpwatch?
with -z we can ingore network and not networks
sos

---

### Post by bazzer on 2007-01-11
I'm not sure arpwatch can do what I would like - would anyone be able to suggest anything else I can use to detect if DHCP isn't playing ball?

I've recently had another situation where the DHCP server (Apple Xserve on OS X) has dished out IP addresses that have already been taken, on our network. The Windows clients pop up a little dooberry in the task bar and tell you something has gone fluffy but arpwatch never peeped a bit.

Any suggestions?
](*,)

---

