---
title: "Help with Networking."
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by ajohn2550 on 2008-01-03
I am planning on installing a flavor of Linux ubuntu if possible on a Thin Client i received from a friend.
and using it as a server to manage DHCP for the comps in my house, as well as a local dns server, Firewall, and an anti-virus.

specs are.
333 mhz cpu and 128mb of ram
im waiting on a 44 to 40 pin adapter so i can connect a hard drive to the thin client, but figured i might as well start searching for if this is even doable on it.

If needed i could use the 550mhz with 640mb of ram for this but i currently have a lamp server set up on it for testing and soon a web host for some friends.

---

### Post by compwiz18 on 2008-01-03
333mhz with 128mb of ram is easily doable with Ubuntu Server.  If you use the alternate install CD, you could probably even run a desktop install, but it would be slow.

---

### Post by ajohn2550 on 2008-01-03
you know of any good how to guides for these.
i have gotten somewhat used to using ssh for installing stuff and management but its the actual steps i need help with.

---

### Post by compwiz18 on 2008-01-03
Google around - there are a lot.  Some are good, some aren't.

I'm not sure how you're going to pull antivirus off, but DHCP + DNS can be done all with dnsmasq, which is a nice little program (and fairly easy to setup) and the firewall is build into Ubuntu.  If you're planning to use the box as a router, you can install a web interface for easy configuration of most of these tools.

---

### Post by ajohn2550 on 2008-01-03
for the most part it is going to take over most of what the router is doing.
eventually it may also handle a dmz.
it only has 1 nic tho and no pci slots so i still have to have hub/router to connect the rest of the comps

---

### Post by Dngrsone on 2008-01-03
Unless you are using a telephone modem or USB modem, you won't be able to use that thing as a firewall... at least two network interfaces are needed otherwise.
With that in mind, [Smoothwall Express](smoothwall.org) works great as a firewall on older machines.

---

### Post by ajohn2550 on 2008-01-03
i was hopping to get the firewall and anti-virus on this so i could remove it from my mom/sisters comp and my dads comp.  
have had to remove 3 viruses from moms comp this month and need to reformat it because of them.

---

