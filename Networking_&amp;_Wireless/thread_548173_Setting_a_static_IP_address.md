---
title: "Setting a static IP address"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by j01101111sh on 2007-09-11
I recently found the need to set a static IP on a network, because there was not a DHCP server available.  When I went to change it from DHCP to static and enter an IP address, it seemed to work fine but when i ran ip addr, it showed that there was a ipv6 address set but no ipv4 set.  I tried a couple more times with the same result.  When i went to change it the second and third times the GUI networking manager still listed the IP address i tried changing the interface to.  I did get it to end up working by restarting the machine, but I was wondering why I had to do that in order to get it to work.  Is this required?

---

### Post by rivalarrival on 2007-09-11
I've run into the same issue on a few occasions...

Seems like if I ran 
```
sudo ifdown eth0
``` 
before I tried to apply a static address, it wouldn't need the reboot.

(replace eth0 with your network card, of course)

---

### Post by Paris Heng on 2007-09-11
Try to set the static IP address in the configuration files, *nano /etc/network/interfaces* it will be more easier.

---

### Post by vamp4life666 on 2008-01-19
I am also having trouble setting the static IP, could someone eleaborate on the  "nano /etc/network/interface" poster previously

---

### Post by eteq on 2008-01-23
I've been encountering this problem, too - my main interest is that I want to be able to use the network GUI to easily switch between two profiles (roaming, and the static wired IP).  I managed to get it to work by switching to the manual mode and running this at the command line:

sudo ifconfig eth0 <ip addr> netmask <subnet mask> up
sudo route add default gw <gateway ip addr>

and I had to disable the wireless.  If I do that, it all works fine, but there's clearly something wrong... Anyone know if this is a new problem with some recent upgrade?  Or perhaps drivers?  I'm not sure exactly what the NIC chipset is (this is a laptop), but the driver (according to the eth0 - related messages I see when I call dmesg) is r8169 .  Anyone else?

---

### Post by eteq on 2008-01-28
It's probably not a driver issue - I just discovered today that if I apply the manual settings, I can "sudo ifup eth0" and it works - no need to specify the address or anything.   But there's still something wrong with network-admin in that it should be calling ifup on its own...

---

