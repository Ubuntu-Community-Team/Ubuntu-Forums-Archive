---
title: "Networking options for VMWare"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by fakie_flip on 2007-05-21
When setting up a guest OS in VMWare, I have different options for networking.

```
Bridged, NAT, Host-only, and Custom.
```

I have these options. Could someone please explain the difference? In the past, I have had trouble accessing a web server from a guess OS in VMWare that was running Apache.

---

### Post by jwambach on 2007-05-21
Bridged:  Essentially this sets up an alias on your hosts network card, and the guest OS must be assigned an ip in the range of the host.  For example, the host has an IP of 192.168.1.2, the guest should be assigned an IP in the same subnet, 192.168.1.3 for example.  The guest OS will then appear to exist in the same subnet as the host.  

NAT:  Network address translation, this means the guest will be assigned an IP address in a different subnet than the host OS and you can use port forwarding to grant access to the guest OS's services.  I have never configured VMware's nat for port forwarding, but it's possible.

Host Only:  VMWare guest OSs are isolated from the host network.

My rule of thumb is, if you want your guest OS to run as a server (for apache, etc) then you should configure it as Bridged, and assign it an address that you can then use from other clients to gain access.  If you want your guest OS to act as a client, with access to the internet, etc, but no services like web servers, then you should use NAT.  If you want to completely isolate a guest OS from any other networks, use Host-Only.

---

