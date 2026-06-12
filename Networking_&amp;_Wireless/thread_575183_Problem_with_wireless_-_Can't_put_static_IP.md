---
title: "Problem with wireless - Can't put static IP"
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by Forks Holder on 2007-10-13
Dear Ubuntu users,

I've been trying to put a Static IP on my Festie Intel ubuntu.

I've followed [this thread]("http://ubuntuforums.org/showthread.php?t=232502"), and opened the file /etc/network/interfaces and edited it to something like that:

> iface ath0 inet static
wireless-essid <your_essid>
address 192.168.168.40
netmask 255.255.255.0
network 192.168.168.0
broadcast 192.168.168.255
gateway 192.168.168.230
dns-nameservers 192.168.168.230

Now, my problems are:

- I have no idea what's my "network" or "broadcast".
- I have 2 DNS adress

What do i need to do?

Thanks,
Forks Holder.

---

### Post by j.bunce on 2007-10-13
Use the network manager, editing things like /etc/network/interfaces can go wrong ;)

---

### Post by Forks Holder on 2007-10-14
> **j.bunce said:**
> Use the network manager, editing things like /etc/network/interfaces can go wrong ;)

The gnome-network manager?
Dude, i have been trying it a lot earlier, I also tried them both.. Nothing works..
Other ideas?

---

### Post by Forks Holder on 2007-10-15
Bump?...

---

