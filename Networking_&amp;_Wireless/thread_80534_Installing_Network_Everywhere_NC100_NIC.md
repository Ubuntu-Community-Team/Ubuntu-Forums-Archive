---
title: "Installing Network Everywhere NC100 NIC"
date: 2005-10-22
forum: Networking &amp; Wireless
---

### Post by nighttime on 2005-10-22
I just bought a new Linksys NC100 NIC but I can't get it to work in Ubuntu. 

I tried ```
sudo modprobe tulip
``` which is the right module for the card. Then I did ```
lsmod | grep tulip
``` and I got ```
tulip      46112    0
``` Which is ok, I suppose... I mean, the NIC doesn't start working when I do this, I guessed I had to reboot the computer, but when I do it I try to grep tulip again and it's gone...

I tried consulting the Ethernet HOWTO but it says something about using "alias", an unknown command for Ubuntu which I also couldn't find in synaptic.

Oh, and I have the noapic option set, which I read could help, but it was no good.

---

