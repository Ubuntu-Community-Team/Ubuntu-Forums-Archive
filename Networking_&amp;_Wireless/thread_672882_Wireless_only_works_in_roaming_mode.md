---
title: "Wireless only works in roaming mode?"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by DeadlyMuffin on 2008-01-20
Just a disclaimer: I realize there are a couple threads asking questions similar to this, but none of them have solutions that work, and all of them are old enough that I don't want to resurrect them.

I would like to be able to specify my wireless settings in /etc/network/interfaces instead of using the gui, but for some reason it doesn't work. I can use nm-applet to connect with no problem, but any attempt to do a manual configuration through the gui or to simply edit /etc/network/interfaces results in no connection.

Here's the interfaces file I'm trying to use:

allow-hotplug ath0
iface ath0 inet static
        address 192.168.0.4
        netmask 255.255.255.0
        gateway 192.168.0.1
        wireless-essid ESSID
        wireless-key MYKEY

What am I doing wrong?

---

