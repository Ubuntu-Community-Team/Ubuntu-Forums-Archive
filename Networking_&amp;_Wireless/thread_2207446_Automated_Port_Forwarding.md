---
title: "Automated Port Forwarding"
date: 2014-02-23
forum: Networking &amp; Wireless
---

### Post by Zachary_Kroeze on 2014-02-23
Hi, 

I'm a little new to networking. I am under the impression that if I want to set up port forwarding, I would need to set up the protocol through the router on my home network. The problem with this is that my router is a Bell router, so to configure port forwarding, I need to go to the settings of my router through [http://192.168.2.1](http://192.168.2.1) . I was wondering if there was a way to ssh into the router, or access the router via terminal commands to set up port forwarding. I know companies like Transporter ([http://www.filetransporter.com/](http://www.filetransporter.com/)) have automatic port forwarding set up for certain routers. Any information on the subject would be appreciated! 

Thanks,

Zach

---

### Post by ian-weisser on 2014-02-23
Most off-the-shelf home routers configure via web only. No ssh. No command line.

Some routers do have ssh access:
- Commercial routers
- Some off-the-shelf home routers ship with Openwrt, a router-specific linux distro.
- Some (not all) off-the-shelf home routers can be re-flashed with linux.

Many off-the-shelf routers support UPnP, a protocol for LAN clients to adjust firewall and forwarding settings. On my routers, UPnP is installed, but not enabled (enable using the web interface). UPnP is sometimes considered a security risk; a malicious application can open holes in your firewall.

---

### Post by Zachary_Kroeze on 2014-02-23
Thanks! I guess I was looking for a package like ```
miniupnpc
```. Setting up port forwarding becomes as easy as ```
sudo upnpc -a 192.168.2.99 80 80 TCP
```

---

