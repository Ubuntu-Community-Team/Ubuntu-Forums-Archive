---
title: "UFW UPNP (No Router)"
date: 2014-07-11
forum: Networking &amp; Wireless
---

### Post by linuxyogi on 2014-07-11
Hi,

My ISP provides a direct ethernet connection. A router can be used but its optional. I dont use one atm.

I have opened port 6881 for bittorrent traffic. 

Frankly I dont understand UPNP fully. All I know is it enables opening of port(s) on demand and on completion the port is closed.

My question is which setup is more superior in terms of security ? If I dont enable upnp I can be sure of the fact that ports will remain closed unless I open them but at the same time the ports which I have deliberately opened remains open all the time. I know that it is possible to manually close them but in practice it becomes really troublesome.

Firstly, please tell me if think its safe to enable upnp. If the answer is yes give me the procedure. 

Note: I am using cable internet which is a LAN connection, there are other users on this network. I need to make sure nobody else gains the privilege to control my firewall.

---

### Post by TheFu on 2014-07-11
UPnP is dangerous.  Anytime a local program can open firewall ports without your explicit approval is bad, IMHO. Any LAN device can request ports be opened - do you have any guests on your network?

Having a separate router with a firewall is the best, cheapest, security that most people can get.  Not running without one is ... er ... just crazy.

So, spend the $25 on a router and disable UPnP inside the router as you change the default password.  More router security thoughts: [http://blog.jdpfu.com/pages/wifi-security](http://blog.jdpfu.com/pages/wifi-security)

---

### Post by linuxyogi on 2014-07-11
> **TheFu said:**
> UPnP is dangerous.  Anytime a local program can open firewall ports without your explicit approval is bad, IMHO. Any LAN device can request ports be opened - do you have any guests on your network?

Having a separate router with a firewall is the best, cheapest, security that most people can get.  Not running without one is ... er ... just crazy.

So, spend the $25 on a router and disable UPnP inside the router as you change the default password.  More router security thoughts: [http://blog.jdpfu.com/pages/wifi-security](http://blog.jdpfu.com/pages/wifi-security)

Okay. No UPnP.

I maintain only 1 PC atm BUT again this is a LAN connection so the answer to your question  is yes, I got lots of guests whom I dont even know.

 2 specific ports are required to be open to allow the Windows PCs to be visible in the Network section of file manager. I dont remember which ports. I tried opening them just to see how many guests show up. I found 10 Windows PCs. Then I closed those ports again and none appear in Network anymore.

I must mention one thing, technically I am behind my ISP's router/Firewall. I did a port scan at grc.com. I found some ports as stealth and some closed. I am pretty sure this was not my Ubuntu installation which was getting scanned because I know for sure that just doing #sudo ufw enable .... puts all ports in stealth mode. Most probably this is some high end Cisco firewall.

So there is at least some protection from the WAN side but yes my system is completely exposed to the LAN.

I am planning to buy [this route]("http://www.flipkart.com/search?q=WNR612&as=off&as-show=off&otracker=start")r next month.

---

### Post by TheFu on 2014-07-11
I don't like netgear though many people do.  They don't have some trivial features that **every** other router has had for 10+ yrs. I've been burned at friends businesses and homes.  I always look for routers that support ddwrt/tomato/openwrt ... that way I know their crap vendor firmware isn't the only option.

I've never been to India, but in Nepal, the ISPs put 200+ clients on the same subnet. We could all see each other and all WAN traffic. It was scary and all the bandwidth was shared, which sucked.  That isn't how it works in the USA - every client has their own subnet and we cannot see traffic to/from any neighbors.

Stealth-mode is just marketing. 

If you can see any more devices on the LAN than you are personally running that is bad. Disconnect now, ASAP. Don't put Windows on that subnet EVER.  Turn up your Linux firewall and leave it enabled until the router is installed.

---

### Post by linuxyogi on 2014-07-11
> **TheFu said:**
> I don't like netgear though many people do.  They don't have some trivial features that **every** other router has had for 10+ yrs. I've been burned at friends businesses and homes.  I always look for routers that support ddwrt/tomato/openwrt ... that way I know their crap vendor firmware isn't the only option.

I've never been to India, but in Nepal, the ISPs put 200+ clients on the same subnet. We could all see each other and all WAN traffic. It was scary and all the bandwidth was shared, which sucked.  That isn't how it works in the USA - every client has their own subnet and we cannot see traffic to/from any neighbors.

Stealth-mode is just marketing. 

If you can see any more devices on the LAN than you are personally running that is bad. Disconnect now, ASAP. Don't put Windows on that subnet EVER.  Turn up your Linux firewall and leave it enabled until the router is installed.

Then I wont buy Netgear. Kindly have a look at the following routers and tell me which one has a) required features and has support for ddwrt/tomato/openwrt. Is it possible to determine ddwrt/tomato/openwrt compatibility by looking at the features or does that need some research on per model basis ?

[TPLINK]("http://www.flipkart.com/tp-link-tl-wr740n-150mbps-wireless-n-router/p/itmdrmmgfwnyhzvy?pid=RTRD7HN3B2FKYXH4&otracker=from-search&srno=t_1&query=TP-LINK+TL-WR740N+150Mbps+Wireless+N+Router&ref=7872dade-4ea4-4efb-984e-03da4702d578")
[Dlink]("http://www.flipkart.com/d-link-dir-600m-n150-wireless-router/p/itmdtg79yhtrykah?pid=RTRDTG78BGXPBE3H&otracker=from-search&srno=t_1&query=D-Link+DIR-600M+N150+Wireless+Router&ref=11d48aa3-7929-4f0f-93ed-064eb04a7c05")

---

