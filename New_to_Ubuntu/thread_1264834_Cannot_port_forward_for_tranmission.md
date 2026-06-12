---
title: "Cannot port forward for tranmission"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by d3vkit on 2009-09-12
So this is really weird: I've been torrenting for years (on Windows w/Utorrent), and understand the basics and port forwarding pretty well, I think. But I cannot get it to work properly on Ubuntu no matter how I try. And the weird part is the inconsistancy.

Basics: I have Ubuntu 9.04 Jaunty.
Static ip 192.168.1.140.
Router is 192.168.1.1.
Port is forwarded on the router (53524) and is set in transmission in the prefs.

But every time I would check it, I would get a blocked port. So I looked around, and after some reading thought it might be the firewall; downloaded Firestarter and under policy tab I have allow service (unknown:53524:everyone). I figured this ought to open the port through my firewall (maybe I'm misunderstanding it though).

The weird part is, if I check my port at canyouseeme.org, it says it's closed; if I turn off the firewall, it reads open immediately. But after about 5 mins, it reads closed, so I turn firewall back on, and it's open again, and on and on forever like this. This makes no sense to me; if a port is open, why would it close after a few minutes? What's changing? I'm not changing anything, just turning the firewall off and on.

I've forwarded the port the same way I've always done successfully with windows, except in windows I know the environment better. In windows I would use Comodo as my firewall and set a policy to allow the port and it worked fine every time. I think this is a firewall issue, but seeing as I'm so new to Ubuntu, I'm not entirely sure.

Appreciate any light you can shed on this for me.

---

### Post by dearingj on 2009-09-12
I think Ubuntu 9.04 comes with the ufw firewall configuration utility installed by default (I know 9.10 does). You can check its status by opening a terminal and entering
```
sudo ufw status
```

ufw might be set to block things by default on your computer.

---

### Post by mcduck on 2009-09-12
> **dearingj said:**
> I think Ubuntu 9.04 comes with the ufw firewall configuration utility installed by default (I know 9.10 does). You can check its status by opening a terminal and entering
```
sudo ufw status
```

ufw might be set to block things by default on your computer.

It's installed, but it's not enabled by default.

The default Ubuntu install has no running firewall, no ports are blocked unless you use some firewall configuration tool (like ufw or Firestarter) to set up the rules to block traffic.

When some port scanning tool/site reports Ubuntu's ports as "closed" that actually just means that no program is listening for incoming connections at that port. So it doesn't necessarily mean that there would be any firewall restricting the traffic.

---

### Post by NESFreak on 2009-09-12
Doesn't your router/modem support upnp? Transmission is able to automatically set up your router for you. It can be enabled in the network part of the transmission preferences dialog.

If thats not a solution, have you both enabled tcp and udp forwarding?

---

### Post by lovinglinux on 2009-09-12
> **d3vkit said:**
> The weird part is, if I check my port at canyouseeme.org, it says it's closed; if I turn off the firewall, it reads open immediately. But after about 5 mins, it reads closed, so I turn firewall back on, and it's open again, and on and on forever like this. This makes no sense to me; if a port is open, why would it close after a few minutes? What's changing? I'm not changing anything, just turning the firewall off and on.

Maybe the firewall thingy is just a coincidence. Firestarter and iptables rules wouldn't change with time on their own. 

In which conditions you have tested the port? I'm asking this because when I was using Deluge with UPnP, the port always closed after a while, even with active torrents. So, if you closed Transmission between tests, it could be the UPnP that is actually opening the port and closing it.

---

### Post by d3vkit on 2009-09-12
@dearingj and mcduck: I checked ufw just in case, it's inactive.

> **mcduck]When some port scanning tool/site reports Ubuntu's ports as "closed" that actually just means that no program is listening for incoming connections at that port. So it doesn't necessarily mean that there would be any firewall restricting the traffic.[/quote]
I assumed that because I had transmission open and the port set in the prefs that it would be listening there, and would then report open. Does it not always listen at the port?

[quote=NESFreak]If thats not a solution, have you both enabled tcp and udp forwarding?[/quote]
It was forwarded on both udp and tcp, yeah.

[quote=NESFreak said:**
> Doesn't your router/modem support upnp? Transmission is able to automatically set up your router for you. It can be enabled in the network part of the transmission preferences dialog.
My router does support upnp, but I've never bothered with it, since I always found port forwarding pretty simple and easy. Does upnp basically do the same thing?
I have left the port in transmission, ticked the box, deleted the port forwarding rule in the router, and ticked the box to turn on upnp in the router. Firewall is currently off. Should the port report open now, or does upnp not work this way?

I must say in these last few minutes after doing this, I seem connected better than I was before when trying to port forward on this box; I guess UPnP was the answer. Thanks for all the help guys, very quick and helpful responses. I seem to be showing connectable on the tracker, so I guess this fixes the problem.

---

### Post by talsemgeest on 2009-09-12
> **d3vkit said:**
> So this is really weird: I've been torrenting for years (on Windows w/Utorrent), and understand the basics and port forwarding pretty well, I think. But I cannot get it to work properly on Ubuntu no matter how I try. And the weird part is the inconsistancy.

Basics: I have Ubuntu 9.04 Jaunty.
Static ip 192.168.1.140.
Router is 192.168.1.1.
Port is forwarded on the router (53524) and is set in transmission in the prefs.

But every time I would check it, I would get a blocked port. So I looked around, and after some reading thought it might be the firewall; downloaded Firestarter and under policy tab I have allow service (unknown:53524:everyone). I figured this ought to open the port through my firewall (maybe I'm misunderstanding it though).

The weird part is, if I check my port at canyouseeme.org, it says it's closed; if I turn off the firewall, it reads open immediately. But after about 5 mins, it reads closed, so I turn firewall back on, and it's open again, and on and on forever like this. This makes no sense to me; if a port is open, why would it close after a few minutes? What's changing? I'm not changing anything, just turning the firewall off and on.

I've forwarded the port the same way I've always done successfully with windows, except in windows I know the environment better. In windows I would use Comodo as my firewall and set a policy to allow the port and it worked fine every time. I think this is a firewall issue, but seeing as I'm so new to Ubuntu, I'm not entirely sure.

Appreciate any light you can shed on this for me.
As long as you are getting a reasonable speed with transmission, I wouldn't worry about the message.

---

### Post by d3vkit on 2009-09-12
> **talsemgeest said:**
> As long as you are getting a reasonable speed with transmission, I wouldn't worry about the message.
Well, I'm not getting reasonable speeds (again actually) - I'm not connecting to enough peers. And trackers say I'm unconnectable. In my router admin, it has anUPnP portmap table which doesn't list anything in it. I don't think UPnP is working as it should. Hmm, back to work on this I guess.

edit: I'm beginning to wonder if it is the netgear routers fault. I've had issues in the past but none for a long time, and none like this (it was usually when I tried to specify the port to forward, it would say it was in use and couldn't be added, had to reset the router and start over. It's not giving errors now, but maybe it isn't handling things properly). I don't like the router but my g/f gets mad when I say so because she bought it. So, it could be that. Maybe I'll break down and buy a N router finally, and see how that goes.

---

### Post by lovinglinux on 2009-09-13
> **d3vkit said:**
> Well, I'm not getting reasonable speeds (again actually) - I'm not connecting to enough peers. And trackers say I'm unconnectable.

So, it's a tracker issue, not a port issue. The tracker must be down. Check the [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923) for explanation and solution.

---

### Post by d3vkit on 2009-09-13
> **lovinglinux said:**
> So, it's a tracker issue, not a port issue. The tracker must be down. Check the [BitTorrent optimization and troubleshooting guide]("http://ubuntuforums.org/showthread.php?t=1259923") for explanation and solution.
Yes, I should be able to connect to some peers right, but not all, and they can't connect to me, if I don't have open ports? So it might be a tracker issue, but I've been having this issue across a few trackers that I am fairly certain are fine. And the tracker still says I am not connectible but my speeds are pretty good right now, so maybe it's not an issue. I just know when I was looking at three trackers, and I'm trying to get some well seeded torrents and it says I'm not connected to any peers - and then I would shut off the firewall, port would report open and I would connect - only to have it change back after 10 minutes, it seemed like an issue on my end.

I'll have to boot into my Win7 box and see what I can do there, see if there are any problems. I must  be missing a step or something somewhere but for the life of me don't see it. I've set static IP, forwarded the port on the router (for udp/tcp), and set the port in transmission - am pretty sure that should be it.

---

### Post by talsemgeest on 2009-09-13
> **d3vkit said:**
> Yes, I should be able to connect to some peers right, but not all, and they can't connect to me, if I don't have open ports? So it might be a tracker issue, but I've been having this issue across a few trackers that I am fairly certain are fine. And the tracker still says I am not connectible but my speeds are pretty good right now, so maybe it's not an issue. I just know when I was looking at three trackers, and I'm trying to get some well seeded torrents and it says I'm not connected to any peers - and then I would shut off the firewall, port would report open and I would connect - only to have it change back after 10 minutes, it seemed like an issue on my end.

I'll have to boot into my Win7 box and see what I can do there, see if there are any problems. I must  be missing a step or something somewhere but for the life of me don't see it. I've set static IP, forwarded the port on the router (for udp/tcp), and set the port in transmission - am pretty sure that should be it.
See what you can download with a realiable tracker, something like the Ubuntu ISO.

---

### Post by lovinglinux on 2009-09-13
> **d3vkit said:**
> Yes, I should be able to connect to some peers right, but not all, and they can't connect to me, if I don't have open ports?

Yes, if the port is closed, you will connect to less peers, because they can't request connections to you.


> **d3vkit said:**
> So it might be a tracker issue, but I've been having this issue across a few trackers that I am fairly certain are fine. And the tracker still says I am not connectible but my speeds are pretty good right now, so maybe it's not an issue.

If the tracker says you are not connected, is because your are not connected. The tracker must be down or could be having difficulties to handle the amount of peers trying to scrape it. You are still able to connect to peers and download at a reasonable speed  because of DHT, which allows to connect even when the tracker is not on-line. Nevertheless, DHT will not provide the same number of peers as if you were able to connect to the tracker.

Please follow the advice of the previous post and try a torrent from a reliable tracker like the [Ubuntu releases](http://www.ubuntu.com/getubuntu/downloadmirrors#bt).

Also check the Troubleshooting section of my tutorial. I have just finished it.

---

