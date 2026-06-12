---
title: "eth0 goes up when I want it to be down"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by minaev on 2008-05-23
Just installed Ubuntu 8.04 on my desktop. I want to configure eth0 to use a static IP, but I can't. I changed /etc/network/interfaces, but it still uses an address from DHCP range.

OK, said I, and tried to run `ifdown eth0'. It went down, but in 5 seconds it was up again with the same DHCP address as before.

Who is that rascal who turns the interface on? Some NetworkManager? How do I tell him I want him to get out of my way? :)

---

### Post by lisati on 2008-05-23
You might want to try:
```

ifdown eth0 --force

```
and let us know how you get on.

---

### Post by minaev on 2008-05-23
Nothing changes. The interface goes down, but in 10 seconds it's up again.

---

### Post by minaev on 2008-05-23
When I launch Administration->Network, I see the desired settings from /etc/network/interfaces. However, Administration->Network tools shows the settings taken from DHCP. When I attempt to reconfigure eth0 from Network Tools, I receive the message: "The interface does not exist".

---

### Post by ivze on 2008-05-23
Have you made sure that the faulty interface is not marked "for Rooming"? This feature is available in "Network" GUI configuration tool. I had the same, before i had taken away the rooming "V" for the interface.

---

### Post by minaev on 2008-05-23
No, eth0 is not in the roaming mode. But I think I've found the first step to the solution :). To make the interface use the static IP I do the following:

1. 'pkill NetworkManager'
2. Run Administration -> Network
3. Disable the interface
4. Enable the interface, entering all its parameters from scratch
5. Et voilá! It's using the static IP.
6. Then I reboot and repeat everything, because after reboot NetworkManager changes the settings again.

---

### Post by minaev on 2008-05-23
I have disabled NetworkManager (as recommended [here]("https://launchpad.net/ubuntu/+source/network-manager/+bug/82335/comments/19")), but it's more or less the same. After reboot, I have to run network-admin to disable and re-enable the interface to make it work properly :(

---

### Post by minaev on 2008-05-23
Removed NetworkManager completely. No, the interface still goes up automatically with dhcp parameters.

Tried to remove dhcdbd. Still to no avail...

---

### Post by minaev on 2008-05-25
It was `laptop-net' package.

---

