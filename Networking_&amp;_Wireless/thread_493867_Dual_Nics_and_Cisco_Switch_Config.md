---
title: "Dual Nics and Cisco Switch Config ??"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by Nortonw on 2007-07-06
I am using Ubuntu as a VMware Server.
I have 2 nics installed and a cisco 3560 switch.

1 nic is in the first Vlan on the switch and the other nic is in the other.

Both nics are in different subnetmasks

I have Samba installed and on and everything seemed fine.

I then rebooted the server and I cannot ping either nic.
If i disable a nic then the ping returns.

Its as if the two nics enabled create some sort of loop to the switch which cause it to turn them off???

How can I make sure that each nic remains isolated from the other in ubuntu ??

---

### Post by Nortonw on 2007-07-06
OK

I am now in a position where by I can ping both Nics.

I now have a 3rd nic installed and am trying to plug that into a differnet switch.
Again this nic has a different Subnet mask.

This time, As soon as I plug nic 3 into the network Nic 1 and 2 both stop pinging ??

How does that work ??

---

