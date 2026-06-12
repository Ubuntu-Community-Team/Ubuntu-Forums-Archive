---
title: "Help! Computer requires restart to gain internet connection  after using deluge"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by waka324 on 2008-08-05
Just as the title says. After a few minutes of downloading using Deluge, I loose my internet connection. My wireless indicator remains on, and I can disable and reconnect to my wireless router, but I cannot use firefox, download anything by torrent, when I try to access my router by IP, I cannot. to get internet access again, I must restart my computer. 

Please help, and Thank you.

---

### Post by prshah on 2008-08-05
> **waka324 said:**
>  After a few minutes of downloading using Deluge, I loose my internet connection.

This is a known issue with some el-cheapo wireless routers. You can work around it by limiting the number of connections in deluge;   Open the deluge main window, click Edit-Preferences-Bandwith, then set "Maximum Connections" to 100, Maximum half-open connections to "50" and Maximum Connection Attempts per Second" to 25.

You will find your torrent downloading not quite full speed; you can play around with the numbers until you find a combination that works best for you.

If this doesn't work out for you there is one more (more complicated, less likely) solution available. Post back if you would like to try that (as well).

---

### Post by waka324 on 2008-08-05
I am almost certain it is not my router as it is a D-link DIR-625, one of the higher end N routers, and I have never had issues in vista/XP. The other reason, is that my computer requires a restart, not the router.

Thank you for your input though, I will try it.

---

### Post by waka324 on 2008-08-06
I have found some threads about this, but they don't make entire sense to me. my internet connection still dies when I reach a high bandwidth, and some suggest changing values from wlan0 to lo, though I am not entirely sure what this means. also, if it is any help, I am using ndiswrapper to connect. though it seems to do the same with my wired connections as well.

---

### Post by mhenry35 on 2008-08-23
I am having the same problem, please check out my post as my situation may help eliminate some of the sources of the problem.

I have a gateway laptop with the Intel 945 chipset.  After I post this, I'll get the network card information and add it to this post.

I have been using my DSL connection with my Actiontec M1000 router/DSL modem for about six months while directly connected to my PC through the wired lan connection, and was able to sustain downloads that lasted for two weeks (a very large file) with no problems at all.  With my current bandwidth, I was getting about 160 using Deluge, and never got dropped, not even once.

Qwest sells an add-on for the Actiontec M1000 that adds wireless capability, and allows connection for up to 10 PC's.  Taking the same computer, and the same modem (with the addition of the wireless adapter to the router/modem) I am able to hook up my PS3 and download large files from playstation store and the PS3 never has a problem (through the PS3 wireless.)

I can go online with my laptop wireless connection and browse with no problems at all (I'm using it to type this message now.)  I tried to download a 170mb file using Deluge, and the system dropped my internet connection within 5 minutes, and it's very consistent.  I restarted the PC and hooked up the wire and was able to download the whole thing without error.

I think we can safely say this is an issue on the Linux side, whether it's a wireless network driver or network manager issue, I don't know.  I've also experienced the same problem when I've been out roaming using coffee shop wireless networks with Deluge and this wireless setup.  In the past I thought it was the ISP, but now I can eliminate that.

This is a widely reported problem, I'm going to be searching all the threads here to see if I can find something good.  Thanks for any help, this is an annoying problem, I would love to get rid of the wires running everywhere.

---

### Post by mhenry35 on 2008-08-23
Okay, here's my update...

My wireless card is built in, and Vista reports it as:
Realtek RTL8187 Wireless 802.11G/g 54Mbps USB 2.0 Network Adapter

My wired connection is reported as:
Marvell Yukon 88E8038 PCI-E Fast Ethernet Controller

It's a Gateway MT6707 Laptop.

---

### Post by waka324 on 2008-08-23
I believe that I may have found my problem. I switched out my router, and it worked perfectly. the interesting part is that it was a abg router, whereas the original was bgn router. I think it may have something to do with how ndiswrapper (in my case) handles N. so with my originial router, I switched it to b,g only, and now everything is golden.

---

### Post by dalesomers on 2008-11-25
I hate to necro this thread, but i have a similar problem to the one stated only I am using a WIRED connection and am experiencing the dropped connection.  When I use Deluge, I will lose the ability to surf the net - but, i will continue to d/l the file that I'm d/l'ing.  Also i use virtualbox to have a guest XP running.  I am able to use the net on the Virtualbox XP (bridged connection to the wired ethernet).  Any help would be greatly appreciated

---

### Post by cariboo on 2008-11-25
I see this is your first post, you should really start a new thread, as a lot of people that may be able to help will ignore this thread because of the number of posts. If you decide to start a new thread incluse some more information like at least the output of:

```
sudo lshw -C network
```

The above command must be run in a Applictions-->Accessories-->Terminal.

Jim

---

