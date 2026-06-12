---
title: "internet not working(wifi connected) and not able to change boot order"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by subincb on 2010-04-06
i installed ubuntu and now my belkin router says connected but firefox is not connecting. i went to about:config and change ipv6 settig to false, but still firefox is not connecting.

another issue is with boot order. i typed su and after that i typed password which i entered during installation but it said authorisation failed.  i tried going to recovery and changing password too but still it did not work. any help appreciated..

---

### Post by mikewhatever on 2010-04-06
> **subincb said:**
> i installed ubuntu and now my belkin router says connected but firefox is not connecting. i went to about:config and change ipv6 settig to false, but still firefox is not connecting.

can you post the output of the following from a Terminal:

ifconfig

ping -c4 74.125.39.99

> another issue is with boot order. i typed su and after that i typed password which i entered during installation but it said authorisation failed.  i tried going to recovery and changing password too but still it did not work. any help appreciated..

This is version specific, since 9.10 uses grub2. 
Anyway, you can run *gksudo gedit /path.../file_name* to edit a specific file, and if you want a persistent root terminal, *sudo -i*.

Edit: I forgot, a lot of people recommend startupmanager for changing boot order.

---

### Post by 3rdalbum on 2010-04-06
> **subincb said:**
> i installed ubuntu and now my belkin router says connected but firefox is not connecting. i went to about:config and change ipv6 settig to false, but still firefox is not connecting.

The router might not be passing the correct DNS addresses to Ubuntu - this sometimes happens with some badly-programmed routers. You can right-click on the Network Manager applet on your top panel and go to Edit Connections, then click Wireless and click on your connection and go to Edit.

Then click on IPv4 Settings and change the method to "Automatic (DHCP Addresses Only)". The DNS field will become active and you can put in your ISP's DNS address. If you don't know your ISP's DNS address, you can use OpenDNS instead:

```
208.67.222.222,208.67.220.220
```

---

