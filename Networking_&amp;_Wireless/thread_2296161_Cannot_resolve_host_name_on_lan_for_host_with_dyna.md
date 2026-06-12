---
title: "Cannot resolve host name on lan for host with dynamic IP"
date: 2015-09-23
forum: Networking &amp; Wireless
---

### Post by dkuhlman2 on 2015-09-23
On my LAN I have three Ubuntu systems/hosts.  quail and magpie have static IP addresses.  bluejay has a dynamic IP address.

On quail I can successfully do: ```
ping bluejay
```

But, on magpie, when I do: ```
ping bluejay
```

I get: ```
ping: unknown host bluejay
```.

What is not working on magpie, and how do I fix it?  Is there another program that I need to install?  Where do I look in order to track this down?

Thanks for help.

Dave

---

### Post by TheFu on 2015-09-23
Make them all have static IPs and put the IP info into /etc/hosts on each of the systems.
[http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) would be good for the portable devices.

---

