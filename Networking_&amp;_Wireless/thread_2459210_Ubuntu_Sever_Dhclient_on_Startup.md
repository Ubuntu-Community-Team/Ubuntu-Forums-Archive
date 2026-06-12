---
title: "Ubuntu Sever Dhclient on Startup"
date: 2021-03-13
forum: Networking &amp; Wireless
---

### Post by mattwag52 on 2021-03-13
I just installed Ubuntu server 20.04 and when I set my network interface up and run dhclient, network works fine. But when I reboot I have to run dhclient on every startup. I have researched this and I have found that I might have to use netplan with yaml config files. Is there an easier way to do this or a very. indepth guide on how to use netplan or is there another distro that can do this easier?

---

### Post by TheFu on 2021-03-13
> **mattwag52 said:**
> I just installed Ubuntu server 20.04 and when I set my network interface up and run dhclient, network works fine. But when I reboot I have to run dhclient on every startup. I have researched this and I have found that I might have to use netplan with yaml config files. Is there an easier way to do this or a very. indepth guide on how to use netplan or is there another distro that can do this easier?

If netplan for DHCP is an issue, I'd suggest that you really don't want to run Ubuntu Server.  The netplan file you need is one of the easiest configs to have on an Ubuntu Server install.

Something like:
```
network:
  version: 2
  renderer: networkd
  ethernets:
    enxc0335eee777f:
      dhcp4: true
      dhcp6: false
```

Just change the ethernet device to match yours which **will be different.**  Use the exact spacing shown.  netplan.yaml files care about indentation. I've never used tabs, so don't know if that works.  The exact number of spaces for each level of indentation isn't important, but consistency is.

Of course, if you already have a netplan file like this and it isn't working, then we need to 
a) see the exact contents of the file - use "code tags" like I have above or the critical indentation won't be seen here.
b) look at other issues, probably with the hardware support or cables or switch port or routing or DHCP server in your location.

DHCP with netplan is pretty bonehead. It is one of the few things that "just works."

And after making any changes to any netplan files, be certain to :
```
sudo netplan generate
sudo netplan apply --debug
```

---

