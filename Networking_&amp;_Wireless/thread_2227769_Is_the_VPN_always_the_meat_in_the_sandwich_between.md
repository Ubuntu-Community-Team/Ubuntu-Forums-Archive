---
title: "Is the VPN always the meat in the sandwich between a ''system wide proxy'' and home?"
date: 2014-06-03
forum: Networking &amp; Wireless
---

### Post by jiri2 on 2014-06-03
I'm inside a Ubuntu 12.04 Virtualbox guest (Bridged Adapter) and by finding 'Network' in the GUI, I can access three things, a VPN which I've configured to be an OpenVPN to a VPN, a 'Wired' connection which I assume refers to the Wired connection that came as default when the virtualbox or the guest additions were installed (even though this is a wifi), and a 'Network Proxy' which can be applied 'system-wide'.

Neither the proxy nor the VPN will work without the 'wired connection', of course. But the network-proxy and the OpenVPN don't depend on each other to work alright, that too is obvious. But what happens when I connect both? Well, the proxy shows on the browser instead demanding authentication details as soon as I open the browser, but so much for 'system-wide', I get a 407 when apply the proxy in such a way (I assume I have to configure a file to get it working for curl, that's OK I just haven't gone with the trouble because it'd probably take me quite some time). What I'd like to know is, as I can see system-wide didn't work quite so automatically well in practice, can there also be an issue in that the proxy may be overwriting the OpenVPN and connecting directly to my home IP, instead of nesting inside/chaining after the OpenVPN itself? I've done things like run traceroute through terminal but I couldn't make head or tail of it.

---

