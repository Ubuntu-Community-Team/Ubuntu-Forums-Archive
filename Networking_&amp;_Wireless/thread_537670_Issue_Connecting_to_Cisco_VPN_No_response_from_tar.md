---
title: "Issue Connecting to Cisco VPN: No response from target"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by thomaswebb on 2007-08-29
Hi,

I have just installed both a patched version of Cisco's VPN Client and VPNC. I have setup my profiles in both, but I can't connect by either method.

VPNC: no response from target
vpnclient: Remote peer is no longer responding

I can ping the vpn server, so I know I can reach it, but not getting a VPN connection?

Any help would be grand!

Thomas

---

### Post by upallnight on 2007-11-15
I am having the same problem.

I imported a Cisco 3000 client profile with pcf2vpnc and it created the correct config file.
I also added this line to the conf file just in case:
NAT Traversal Mode cisco-udp

Still, I keep getting "vpnc: no response from target".

I have all the VPN passthrough settings enabled on my router and I too can ping the vpn server.

:(

---

### Post by mattze on 2007-11-26
i had the same problem with vpnc and it seems to be quite common.
i "fixed" it by downgrading to version 0.3.3. 

here is how you do it:

1)remove the current version of vpnc (if installed):
```
 sudo apt-get remove vpnc
```
2) download version 0.3.3: 
```
wget http://archive.ubuntu.com/ubuntu/pool/universe/v/vpnc/vpnc_0.3.3+SVN20051028-3ubuntu2_i386.deb
```
3) install it: ```
gdebi-gtk vpnc_0.3.3+SVN20051028-3ubuntu2_i386.deb
```
click install, .... you know how to do it
4) lock the version in synaptics:
select it, Strg+E and select it [does anyone know how to do this with apt-get?]
5) delete the downloaded deb-file if you want: ```
rm vpnc_0.3.3+SVN20051028-3ubuntu2_i386.deb
```

there might be some security concerns with running an old version, but as far as i know (see [http://www.unix-ag.uni-kl.de/~massar/vpnc/](http://www.unix-ag.uni-kl.de/~massar/vpnc/)) it shouldn't be ok.

hope i helped!

---

