---
title: "Bellsouth DSL -No Connection"
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by SunfireSSR on 2007-11-29
Can't connect to Internet. Using DHCP, not Static. Have tried both. Saw a few questions here with same problem, but there's got solved.

Posted this in Ubuntu Launchpad with no luck. Olivier told me to post here for help. Link to LaunchPad below.

Thanks...

[https://answers.launchpad.net/ubuntu/+question/17589](https://answers.launchpad.net/ubuntu/+question/17589)

---

### Post by caro on 2007-12-01
One thing to check:  BellSouth DSL modems default to 192.168.1.X.  If you are using a router that defaults to the same IP range, you will have a conflict.

Just a thought...good luck.

---

### Post by SunfireSSR on 2008-01-02
I think all BS's routers (NETOPIA 2241N-006) default to 192.168.1.254 as mine does.

Since I'm not a guru at this (but dangerous enough to get myself hurt), what are my options ?

---

### Post by FoxOne on 2008-01-02
Checklist is a good place to start.

1) Internet light blinking, sometimes called connection light. 
2) Are you connecting with an ethernet cable or wireless? 
3) Assuming you're using a hard connection, and you have DHCP enabled, do you get a good IP address, can you ping the router / gateway (some of the newer, nicer DSL modems are gateways... mine is anyway) If all that checks out, see what IP the modem has from BS, if they are using a PPPoe connection, sometimes you need to put in your username and password in the modem for internet connection. Verizon is hit or miss on this, sometimes it matters, sometimes it doesnt. 

4) if all else fails, call them, ask them what's up.

---

### Post by bwtranch on 2008-01-03
Output of lsusb
lspci 
ifconfig

Please?

---

### Post by SunfireSSR on 2008-01-03
[https://answers.launchpad.net/ubuntu/+question/17589](https://answers.launchpad.net/ubuntu/+question/17589)

See the above launchpad Post for details of what I've been through besides this post.

The Modem/router works under XP without fail, and Bell South refuses to support linux at this time.

---

### Post by SunfireSSR on 2008-01-03
[https://answers.launchpad.net/ubuntu/+question/14129](https://answers.launchpad.net/ubuntu/+question/14129)

Found this post with a Google for Bell South DSL and UBUNTU. Nothing worked for me.

---

### Post by SunfireSSR on 2008-01-03
Guys, this looks like my problem, but I don't know what to do here. A freind told me to go buy another router to put between the ethernet card and the DSL Modem/Router. Does any of this make heads or tails to you ???


"He actually does have a router, or to be technical, a DSL modem with basic routing. a Netopia 2241N model.

He would have to set the DSL modem to bridged ethernet mode, then use a PPPoE client on his system to have the WAN IP passed to the connected computer. Otherwise, the DSL modem is assigned the WAN IP, then it uses NAT for translation and DHCP to assign LAN client IPs.

In effect, NAT is providing firewalling. If you want to retain NAT, you will probably need to open ports and do forwarding at the DSL modem.

The IP for the modem is probably 192.168.1.254 if it is a standard AT&T SouthEast (BellSouth) DSL modem."

---

### Post by bwtranch on 2008-01-03
Actually it does to me. Anything to get you up and running saves time and money. Gets you down the road, ya know?

---

