---
title: "Question about LAN in building"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by kcirtap on 2008-10-16
I have a question about networks in general and I would appreciate if someone could clear up for me.

I'm living in a building/flat in an apartment. Many other students live in this building so I guess there's some kind of network in this building. Anyways, there's been complains that their network doesn't work and they complain about someone using a router. Is it possible that something like that can cause this?

I mean, let's say there's many rooms in a single building. If I plug in a router in the "RJ-45 socket" in my room instead of plugging in RJ-45 cable directly. Could that possibly ruin the internet connection for the rest of the people in this flat? Personally, i've also had problems getting an IP-address in some occasions so they have a point.

Personally, I find this very strange, because how can someone in a different room cause the network to fail for others, unless it's some kind of ring network (which it isn't). How does this work?

---

### Post by cariboo on 2008-10-16
A router usually includes a dhcp server which provides ip addresses to other computers on the on the network. The router is probably providing ip addresses that conflict with the device that was aready on the network providing ip addresses. The way to solve the problem is to get rid of the router and use a switch, or turn of the dhcp service in the router.

I reread your post and noticed that I had forgotten something. The network in your building is probably all routed to a cable closet somewhere in the building. All the cables are connected to a switch, or patch panel that consolidate the connections, sort of like a one into many splitter.

Jim

---

### Post by Iowan on 2008-10-16
Properly configured and connected, a router (with DHCP server) shouldn't be providing addresses on the "internet" port... but properly configured and connected isn't guaranteed. As Cariboo907 (cari-BOO! 907 - in honor of the holiday?) mentioned, turning off the DHCP server would insure one less source of potential interference.

---

### Post by Agent ME on 2008-10-16
When you plug the ethernet cord from the building network to the router, its going into the internet port, and your networked items (computers, etc) are going into the router ports, right?

Unless the network is being run on a dumb switch, I doubt hooking up a router the wrong way would cause problems for other people - more than likely its the building's router's fault. Cheap routers seem to enjoy failing... I've had too many problems with Linksys, and I resort to unplugging it + plugging it back in semi-often.

---

### Post by kcirtap on 2008-10-17
Just for clarification in case I didn't explain good enough in my first post. Let's say that this is the network (where everyone separately is connected to the network):

Person 1 -------------------------------|NETWORK

Person 2 ------ Person 2's ROUTER ------|NETWORK

Me -------------------------------------|NETWORK

Person 4 -------------------------------|NETWORK

Where NETWORK actually is the same "unit", but it's hard to show in a texted message like this.

Could Person 2's router somehow ruin the internet connection for me, Person 1 or/and 4? We all separately connect to the building's network. I mean, shouldn't the switch/router or whatever the network administrator for this place use, fix these problems automatically?

---

