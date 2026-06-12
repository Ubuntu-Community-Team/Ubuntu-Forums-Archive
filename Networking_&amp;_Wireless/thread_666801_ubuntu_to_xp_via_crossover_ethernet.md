---
title: "ubuntu to xp via crossover ethernet"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by m3t3ors on 2008-01-13
ive just had to change all my network due to a faulty laptop (windows) so my ubuntu box which was ethernet any way, now connects to wifes xp machine through crossover ethernet
the lead is ok (checked with tester) and the link is there on xp machine (with linited or no connection)?
i cant seem to find how to set the link up on ubuntu though?
any help appreciated guys
:confused::lolflag:

---

### Post by TwoWordz on 2008-01-13
Since you dont have a router, you dont have a DHCP serveravaillable to automaticly give IP addresses to your computers. You need to set them up manually.

In windows, you go to see your network connexion (control panel) you right clic the adapter hooked up to the crossover and you hit properties, go to tcp and setup your ip manually.

On ubuntu you do that by editing the /etc/network/interface file. Read the documentation for that. 

Both should be in the same range with the same mask. You should use something like 192.168.10.2 for the windows and 192.168.10.3 for the linux. You dont need a gateway and the mask should be set to 255.255.255.0.

good luck. 

TW

---

### Post by m3t3ors on 2008-01-14
yes i have a router (belkin G+MIMO) but its too far for the ubuntu box to connect to (pcs upstairs and router downstairs) had a few issues with laptops so i mhad to move things around.
il try what you suggested and post back
thanks

---

### Post by m3t3ors on 2008-01-14
the only file i can see with interface is in etc/network but that only says 
auto lo
iface lo inet loopback
auto lo etho inet dhcp
auto lo
iface eth1 inet dhcp 
and so on for some more
theres a file in 
avahi-autoipd that says my ip is 192.168.2.2 but thats my windows pc with a different subnet mask of 255.255.0.0
when i change it to 255.255.255.0 it wont save. also when i change the ip on my windows in tc/ip it blocks my internet on windows?

---

