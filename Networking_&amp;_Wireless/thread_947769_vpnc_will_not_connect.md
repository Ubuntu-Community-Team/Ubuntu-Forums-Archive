---
title: "vpnc will not connect"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by jarome on 2008-10-14
I am having problems using vpnc.
It works perfectly on my two SUSE 11.0 machines.
But on Ubuntu Hardy Heron (on an HP MiniNote using wireless), it will not connect to the VPN server using the [COLOR="Red"]same[/COLOR] pcf file that works on SUSE.
I get "no response from target"

Is there a way to debug this?

I also tried the Cisco vpn client which does not work at all.

I can't so e-mail without the VPN, so please offer suggestions.

Thanks,
Jim

---

### Post by jobix on 2008-10-17
Try this site, maybe it might help:
[http://www.spiration.co.uk/post/1335/vpnc](http://www.spiration.co.uk/post/1335/vpnc)


According to other posts, some of these problems might have to do with wireless. I guess you could confirm that by trying to connect your laptop via Ethernet and then trying to VPN. This will help you figure out if it's something with Hardy or with your wireless card.

I got the Cisco VPN client working on an AMD 64 m/c with Hardy just a few minutes ago. I'm using Ethernet though, not wireless.

---

### Post by jarome on 2008-10-17
Adding the Traversal line did not help. I had a lot of problems getting the wireless to work, and now I can't connect in the wired mode. But I must use wireless in most places I need to use the VPN.

I rebooted and got the wired network to work. But still no response from the server.

---

### Post by jarome on 2008-10-17
> **jarome said:**
> Adding the Traversal line did not help. I had a lot of problems getting the wireless to work, and now I can't connect in the wired mode. But I must use wireless in most places I need to use the VPN.

I rebooted and got the wired network to work. But still no response from the server.

So, I now found out that wicd does not support vpnc. That screws me.
I tried to go back to Network-Manager. I can install that, and Network-Manager-vpn, but am unable to install network-manager-gnome.
Synaptic insists on uninstalling network-manager and the linbm-glib0 library (and Evolution). But then, when I try to accept that, it says that they are prerequisites for the installation.

The wlan1:avahi icon in the upper-right no longer sees my wireless card!

What do I do now?

---

### Post by jobix on 2008-10-19
Sorry, I can't help you with the wireless - I myself haven't been able to get wireless working on 8.04. It used to work for me on 6.06. 

You can try starting here:

[https://help.ubuntu.com/community/WifiDocs/](https://help.ubuntu.com/community/WifiDocs/)

Good luck.

---

### Post by imdano on 2008-10-19
> **jarome said:**
> So, I now found out that wicd does not support vpnc. That screws me.I think you misunderstood what wicd not supporting vpn means.  Wicd doesn't have a vpn plugin like NM, that allows you to configure VPN within the application itself, but there is nothing stopping you from manually configuring a VPN connection with vpnc.

---

### Post by jarome on 2008-10-19
> **imdano said:**
> I think you misunderstood what wicd not supporting vpn means.  Wicd doesn't have a vpn plugin like NM, that allows you to configure VPN within the application itself, but there is nothing stopping you from manually configuring a VPN connection with vpnc.

It does not work with vpnc for me.  Any ideas?

---

### Post by jobix on 2008-10-20
Here's a post on the wicd forum that I found:

[http://wicd.sourceforge.net/punbb/viewtopic.php?id=199](http://wicd.sourceforge.net/punbb/viewtopic.php?id=199)

Looks like he was able to get vpnc working on his wireless.

---

