---
title: "Network bridge"
date: 2007-05-27
forum: Networking &amp; Wireless
---

### Post by i386DX on 2007-05-27
This is the current situation of my homenetwork

[img]http://users.pandora.be/azone/school/netwerk.png[/img]
(Wireless laptop: 192.168.1.2
Wireless desktop: 192.168.1.1)

At this moment the wireless connection between my desktop and laptop works. The problem is that I want to have internet on my laptop when the wired connection isn't available. As far as I know I have to brigde the networks.

Following the information on [this site](http://linux-net.osdl.org/index.php/Bridge) I installed bridge-utils and tried to set it up, but I was not able to manage this.

An important question: where must I create the bridge? on the laptop or the desktop?
This is a little test (site above) which I tried on my desktop:

```

brctl addbr nwbrug
brctl addif nwbrug eth0
brctl addif nwbrug wlan0
ifconfig nwbrug up

```

After doing this, my whole network (wired and wireless) doesn't work anymore. So does anybody knows how to setup a bridge or what the right method is to achieve what I want?

---

### Post by Austin_KW on 2007-05-27
I dont think you need bridging with differerent subnets, routing/nat might be a better solution. You can do a routing ICS easily using the firestarter GUI. It will even run a mini dhcp server and assign the address to the laptop (similar to the ICS under windows)
sudo apt-get install firestarter

and just run the wizzard

---

### Post by hartz on 2007-05-28
To use routing, you would need to setup a static route on the firewall which routes traffic for 192.168.1.* via 192.168.0.10 .. This might not be possible on your router (depends on the router having this functionality), in which case NAT-ing (on the desktop) is maybe your only option.

A much simpler solution might be to just install a web proxy service on the desktop, allowing wireless systems to use it as a proxy-server.  This proxy server can be caching too, and if so, you can make the web-browse on the desktop use the proxy-server locally with great effect.

Just look in synaptic for a proxy server and pick your poison from there.

You would then have to set the desktop's Wireless interface address as the proxy server on the laptop computer too.

This will all-in-all require a whole lot of config jiggery - It is not impossible, jsut inconvenient.  I recommend that you consider buying a WiFi gateway or WiFi router/gateway combo.

---

### Post by hartz on 2007-05-28
You of course also have other options, such as moving the WiFi card to the Win2K ICS system, or using the Ubuntu system as your internet gateway, or better: get IPCop and put the WiFi card (from the desktop) into the IPCop system.

---

### Post by airtonix on 2007-06-20
just install firestarter and use the inbuilt bridging gui there

---

