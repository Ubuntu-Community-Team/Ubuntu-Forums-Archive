---
title: "Setting network settings via command line"
date: 2005-04-13
forum: Networking &amp; Wireless
---

### Post by philipt18 on 2005-04-13
I have a server running Ubuntu that I need to change the network settings on (from dynamic to static IP). How do I do that via the command line? I can ssh to the machine, so I just need to connect and change the settings.

Thanks.

---

### Post by heimo on 2005-04-13
What you need to do is edit /etc/network/interfaces find the interface you want to configure, something like:
```
iface eth0 inet dhcp
```

and change it to what you want it to be:
```

iface eth0 inet static
     address 192.168.1.1
     netmask 255.255.255.0

```

save and run 
/sbin/ifdown eth0 && /sbin/ifup eth0

You don't want to get the configuration wrong and you don't want to first shut down the interface and uhm... lose the connection. At least if the machine is on another continent. So the stoppig and starting must be entered at once (on same line).

man interfaces (for more options for configuration file)

---

