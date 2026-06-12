---
title: "Need monthly bandwidth measurement tool"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by couzin2000 on 2008-06-03
I have scoured the internet and all Ubuntu repos for a tool like this, and what I've found that was closest is the _[Netspeed]("http://www.wh-hms.uni-ulm.de/~mfcn/netspeed/")_ applet.

I have a cap on my downloads and uploads, and I would like to monitor my up and down bandwidth. This is why I installed Netspeed on my Hardy -- unfortunately, the "odometer" resets after a day or two, and there is no way for me to monitor the net usage for other pcs either.

What I want to have is a tool, which will install on any Ubuntu-based PC, where you give it an actual IP adress (such as the IP of my router, of my NIC or of my cable modem) and this tool would monitor how much data goes through. It would also be possible, in the best case-scenario, to give this tool the amount of bandwidth I'm capped at (for me it's 100Gb total, up + down). If I go beyond this I pay extra, so to HELP OUT my ISP I'd like to have an alarm (like a popup message) explaining that I'm at, say. 5% of reaching my cap limit.

Does this exist, and if so, where can I find such an app?

Thanks in advance!

---

### Post by couzin2000 on 2008-06-04
So far, Gkrellm sounds like the best option, and it does what I want it to do - sort of. It can measure the Tx/Rx of my computer's eth0, that is the NIC card. However, this does not help if one has 2, 3 or 17 computers, and a router. How can one measure the Tx/Rx of the cable modem to which this network is all attached?

---

### Post by essexboyracer on 2008-06-05
I would also like a tool for this. I am thinking of moving from Pipex £24.99/month unlimited to a cheaper option like 10GB/month for £6.99 (or whatever, I havn't researched the plans available yet).

Can we first though define a couple of terms. think of the following in plumbing terminology;

Bandwidth: How wide the pipe is

Data Transfer: How much water can flow through the pipe over time (day/month/year)

Thinking about it, if you wanted to monitor at the router level, you may need to put openwrt or similar on the router itself. Otherwise, send all network data through one pc as a proxy?

---

### Post by couzin2000 on 2008-06-06
My ultimate goal is to monitor the data transfer directly at the cable modem's IP. There must be a way to locate this from within the router's network, from a PC located inside the network, and simply monitor the flow? I can't believe that nobody would have designed a tool for this, or that NOBODY is interested in knowing how much transfer they use?

---

### Post by essexboyracer on 2008-06-06
try this, [http://www.nagios.org/about/](http://www.nagios.org/about/). it says it can monitor machines running windows as well. In particular you may want to read

[http://nagios.sourceforge.net/docs/3_0/monitoring-routers.html](http://nagios.sourceforge.net/docs/3_0/monitoring-routers.html)

The ip address of your router will probably be in its documentation, mine for example is 192.168.2.1

If you wanted to monitor traffic even when you are not around then you will need a computer on all the time. I just switch the router off when not in use. there are only two users on it.

---

### Post by essexboyracer on 2008-06-06
ok, got nagios to work! was quite easy on my xubuntu 7.10 laptop. Just follow the quick install guide for ubuntu. the only thing I had to do different was start apache-2 from the applications > system > services GUI.

Next I went on to the Monitor a router/switch monitoring how-to. ran through it but seemed to have hit a wall. I dont think that my router supports SNMP, therefore nogo-nagios. Its a Belkin F5D7632-4 (I think).

Im going to get a 4-port switch, setup a dedicated machine with IPCOP on and give that a go!

---

