---
title: "How to share Internet Connection in Feisty - Firestarter won't work :-("
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by Tommerz on 2007-04-03
Hey everyone,

I want to share the internet connection from my main computer via a hub to my brother's Mac Mini (running OSX). We've done this before under Windows, but I can't seem to get it running in Ubuntu.

I've tried using the Firestarter tool to enable internet sharing, and various different settings, as well as been googling like crazy, but have had no luck.

The closest I've found is a forum post about how the network manager applet interferes with Firestarter, but disabling it didn't help :confused: 

Anyone have any ideas or advice? I'm on Feisty Beta.

---

### Post by Tommerz on 2007-04-03
Anyone have any ideas? I'm stuck on Windows till I get it sorted :(

---

### Post by dalziel_86 on 2007-04-03
Can you give us some more details of your network layout? Where's the Internet connection coming from, and what's it connected to?

---

### Post by Tommerz on 2007-04-03
My internet connection is coming from a usb cable modem (which works fine in Ubuntu) and shows up as eth1 in Gnome's network configuration tool.

I have an ethernet cable in the ethernet port (known as eth0 in network configuartion) going to a hub. The other machine (Mac Mini) is also connected to the hub via ethernet.

Internet connection sharin works fine when running Windows on the host machine, but I've had no luck getting internet sharing working using Ubuntu as host, even with Firestarter which should work fine.

Any ideas? Thanks in advance :)

---

### Post by dalziel_86 on 2007-04-03
> **Tommerz said:**
> My internet connection is coming from a usb cable modem (which works fine in Ubuntu) and shows up as eth1 in Gnome's network configuration tool.

I have an ethernet cable in the ethernet port (known as eth0 in network configuartion) going to a hub. The other machine (Mac Mini) is also connected to the hub via ethernet.
Why the hub? Why not connect the Mac Mini directly to the Ubuntu machine? Are there other machines plugged into the hub?

If you set up a bridge between eth0 and eth1, every machine connected to the hub will act like it is connected directly to the modem. This might be what you want, but I suspect you may get network traffic problems, though I'm not sure.

Bridging is a whole lot easier than setting up Internet sharing. But it has its own problems too. Ideally, what you want is something to handle routing, so you might look at doing that on the Ubuntu machine.

---

### Post by Tommerz on 2007-04-04
Is it possible to just plug the Mac into the Ubuntu machine? I didn't know that was possible!! There is a chance I'll add another machine to the hub in the future.

So how does bridging work? Are there any good tutorials you know of? It might work well as a short term solution.

What would you recommend, what's the best way to go about doing this?:confused: 

Thanks for your help :guitar:

---

### Post by swedenfox on 2007-04-04
i have a similar problem 

when i share my internet connection on eth1 to the others (eth0 network) firestarter don't work...
please anyone can help us ? why only one connection work on 7.04 ??? this is a bug or a problem with firestarter ?

iptables

---

### Post by Tommerz on 2007-04-04
So, anyone have any ideas? If this is juts a bug, it'll be a pretty common irritation in feisty final.

---

### Post by dalziel_86 on 2007-04-04
> **Tommerz said:**
> Is it possible to just plug the Mac into the Ubuntu machine? I didn't know that was possible!! There is a chance I'll add another machine to the hub in the future.
Sure, if you've only got a hub between the two machines, it's not doing anything different. A hub just connects machines. If it's actually a hub rather than a switch (rare these days) it just repeats traffic to all the connected machines. If it's really a switch (more likely), it connects one port to another, letting the two machines that are talking act like they're directly connected. If you only have two machines plugged in, it's academic anyway. Whether you use the hub/switch or not, the machines will act like they're directly connected. So if there's only the two machines, the hub is kinda pointless. You might as well just plug the Mac into the Ubuntu machine.

> So how does bridging work? Are there any good tutorials you know of? It might work well as a short term solution.
Bridging basically sets up a virtual hub/switch on the host machine. In your case it will allow both the Ubuntu and Mac machines to act like they're directly connected to the modem (so long as the Ubuntu machine is running, of course). This may, as I said, cause traffic problems. I haven't tried bridging to a modem, only to a modem/router, so I dunno. The modem is obviously designed to only be plugged into one machine, so maybe bridging's not the best bet. I can give you instructions if you want, and you can try it, but I can't say it'll work at all, let alone well.

I recommend you connect the two machines directly, and keep trying to get Firestarter to work. It may even be that the hub/switch is interfering with Firestarter sharing the connection. You might be lucky and find that directly connecting solves your problem.

---

