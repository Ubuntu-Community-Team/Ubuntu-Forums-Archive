---
title: "Connect to local computer using XDMCP"
date: 2015-04-04
forum: Networking &amp; Wireless
---

### Post by d3ngar on 2015-04-04
Hi,

I have a computer here in my local area network that I would like to connect remotely to. Ideally I would be using XDMCP, but I'm having no luck.

I have, for now, created a lightdm.conf file in /etc/lightdm and added: 
```
[SeatDefaults]
xserver-allow-tcp=true
xserver-share=true
xdmcp-port=177
greeter-show-remote-login=true

[XDMCPServer]
enabled=true
port=177
```

I also installed gnome-session-flashback.

When I try to connect to the machine, I just get a blank screen, nothing else.

Thanks

---

### Post by TheFu on 2015-04-05
Any chance I could convince you to try using x2go? 

Put the server on the remote machine and the client on the machine you sit behind. Setup openssh-server on the server and you are done. There are x2go clients for Linux, OSX and Windows.  It is very network efficient and secure enough to use over the internet thanks to NX using ssh automatically.  The performance is excellent - better than RDP, VNC or raw X/Windows (IMHO). 

There is a stable PPA for 14.04: [http://wiki.x2go.org/doku.php/wiki:repositories:ubuntu](http://wiki.x2go.org/doku.php/wiki:repositories:ubuntu) with install instructions for the PPA.

I suppose you've read this [https://wiki.ubuntu.com/xdmcp](https://wiki.ubuntu.com/xdmcp) - notice how it recommends NX?  x2go is NX and easier to use and setup than FreeNX. Plus it supports remote audio, local storage mounts, shared desktops, etc.

---

