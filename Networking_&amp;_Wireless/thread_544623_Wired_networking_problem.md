---
title: "Wired networking problem"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by mavrinan on 2007-09-06
I've got 7.04 installed on a virtual machine using Virtual PC 2007. The host OS is Windows XP. The host machine is a Dell Optiplex GX620, with a BroadCom NetXtreme 57xx Gigabit network card.

I have annoying issue with networking. When I boot up, the machine does not have network access. The network icon by the clock has a red triangle and the tooltip says "no network connection". If I click on this, and select "Wired networking" the networking then works. But I don't know how to make the system connect to the networking automatically. 

In Network configuration, "Wired" is checked under connections, and it is the only one checked. (The machine has an ethernet card but no wireless card and no modem).  I've found I can also get the network to connect by either going through "sudo ifdown eth0, sudo ifup eth0", or "sudo dhclient".

---

### Post by Steve1961 on 2007-09-06
In system>admin>network click on the properties for your wired network and try unticking roaming mode

---

### Post by mavrinan on 2007-09-06
Roaming is unticked, and the problem is stil there.

---

### Post by Steve1961 on 2007-09-06
You could try:
```

sudo gedit /etc/rc.local
```

and add

```
dhclient eth0
```

just before the exit 0

Save and close and then do:

```
sudo chmod +x /etc/rc.local 
```

---

### Post by mavrinan on 2007-09-06
Thanks, that sort of works.  The network connection does work, but very slowly.

Also it isn't a very elegant solution, we've just automated running the manual command to fix the problem.  Is there something like a boot log in Ubuntu that might tell us if the system tries to connect to the NIC when starting up and gets an error?

---

### Post by Steve1961 on 2007-09-06
You could try looking at dmesg.  Probably best to pipe it through the less command as it's very large:

dmesg | less

---

