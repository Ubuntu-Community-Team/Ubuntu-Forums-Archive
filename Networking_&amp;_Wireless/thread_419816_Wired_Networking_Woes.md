---
title: "Wired Networking Woes"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by AlexKarm on 2007-04-23
Hello,

I recently updated my system to 7.04 (poor poor update servers... they were really hammered, eh?). The first thing I noticed was a very different way in which Network Adapters were handled. I'm now having rather big issues when dealing with multiple networks...

I have two active network adapters (eth0, and eth1). They are both configured to DHCP.

The first (eth0) is connected to a direct outside internet source running at 15+ MBit. This connection is what I use (or previously used) to access the internet from this computer. This is what I would like to be the default route.

The second (eth1) is connected to a internal network that has it's own internet connection (running at 7 MBit) that is used by the other users on the network. I use many internal servers and resources, as well as share resources back to the network.

My current problem is that with the upgrade to 7.04, they have introduced some form of automation that is causing routing problems on my computer that I'm not aware of how to fix. I would like all local traffic to head to the local network, and all traffic that does not have an internal address to be routed to the other connection.

Previously all I had to do was remove the default route that directed traffic to my internal network, which would result in internal traffic being internal, and external traffic being external. DNS requests were resolved by whichever responded first when booting my computer, which was normally the internal network. I really don't care who resolves my DNS :P

With the update, I seem to have to pick between one adapter and the other, as well as a new adapter is created with whichever one I choose from the drop down list (eg: eth0:avahi).

How do I resolve this in the new Ubuntu, or how to I remove the "automatic" management of network resources? I would prefer not to have to set up route scripts to change my routing table every boot...

(P.S. What is avahi?)

---

### Post by AlexKarm on 2007-04-25
I'm almost positive now that this is a problem with the automatic resource management. I respect that it has probably helped a lot of people, but when you have two network cards it seems to be causing a lot more headaches when anything else.

What is really surprising is that it's not obvious how to disable it. Right clicking on the networking icon that has been added to the upper pannel by default only provides an option for disabling networking, and no aditional configuration options. Going into System->Administration->Networking has not changed since 6.10, and therefore doesn't mention the addition of automatic management.

How do I turn this beast off?

---

### Post by orn on 2007-04-30
I have (had) the same problem.

You can remove the package that does this. It's called avahi-autoipd.
sudo apt-get remove avahi-autoipd also removes the dummy package ubuntu-desktop.
I'm not sure what effect that will have. Might affect system updates/upgrades.

Update: You can also comment out everything in /etc/avahi/avahi-autoipd.action -- that way you don't have to remove any packages.

---

