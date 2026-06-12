---
title: "NetworkManager DHCP the IPv4LL"
date: 2020-04-08
forum: Networking &amp; Wireless
---

### Post by w2vy on 2020-04-08
I need to connect to another device over USB cdc-ecm using IPv4LL (Link Local 169.254.x.x)

I expected that Ubuntu would support that out of the box, but it appears not.

I did search the forums a few different times and mostly found older posts (12.10 and before)

I also tried the same test on eth0.

When the connection is set for DHCP I do see avahi taking actions on the IPv6 addresses, but nothing for IPv4

I did see the NetworkManager offers configuration options for DHCP and "Link-Local Only"  (as well as MANUAL(static) and DISABLE)

I am surprised that DHCP *then* Link-Local is not an option

Am I missing something?

The ZeroConf concept has been around for  a very long time, it is surprising we don't support it in the default configuration

The "device" is something I provide support for so I am interested in the easiest way to document how to use it on Ubuntu.

At this point it seems the way to make it work is:

[LIST=1]
[*]Plug in the device
[*]Configure the IPv4 interface to be "Link-Local Only"
[*]Remove and reinsert the device
[*]
[/LIST]

Is there an easier way?

Tom

---

