---
title: "bug? if i change the MTU of a vpn connection, ubuntu 22.04 suddenly forgets its auth"
date: 2022-07-06
forum: Networking &amp; Wireless
---

### Post by gustypants on 2022-07-06
Hi

I have a vpn connection that works. it runs a bit slow so i open the settings for the vpn connection (using gui) and i go into identity tab/advanced/General tab and enable MTU. Then click apply and apply to save. suddenly i cant connect to the vpn no more. curious.

I open up the settings/identity tab/advanced/TLS Authentication tab and see that the previous settings for Mode, Keyfile, key direction and extra certificates have been cleared. if i put them back then the vpn configuration works again (even with the MTU now checked).

what do we think?

---

### Post by TheFu on 2022-07-06
So, with VPNs, the MTU value MATTER!  Generally, it needs to be a little smaller than the default packet size, to leave room for the VPN header inside each packet.  So, changing the value while it is connected will likely screw that connection, completely.  
[https://www.networkworld.com/article/2224654/mtu-size-issues.html](https://www.networkworld.com/article/2224654/mtu-size-issues.html) explains the overhead needed for a few different types of VPNs. 
> There are many other situations where protocol encapsulation occurs, so you must be aware when this happens and take steps to accommodate it. A packet may originate as a standard IPv4 packet with a designated MTU of 1500 bytes, but depending on its destination it may pass through encapsulation that pushes its size over the MTU.

At first look, this isn't a bug. It is user error unless you have very specific examples where you 
a) stop the VPN
b) change the MTU to be smaller than needed
c) start the VPN
If that happens, I bet you'll never see issues related to the MTU, unless there is a lower-limit somewhere in the network pipeline for MTU size.

Just to put some numbers, the standard ethernet packet size is 1500 bytes.  So, if the VPN overhead is 73 bytes (that's the IPSec spec), then you'd want to set the MTU to be 1500-74 ... 1426 bytes as a starting point.  Increasing the MTU to be 1574 would be a mistake.

---

### Post by gustypants on 2022-07-07
Thank you, I appreciate you taking the time to answer, but perhaps i didnt express myself clearly or you skipped the second part of the question.

The problem I have is not with setting the MTU value, it is that when i do change MTU (or MSS), the auth configuration disappears.

Thanks

---

### Post by #&amp;thj^% on 2022-07-07
I would need to see some pings first, are you "just using network-manager and yes your GUI is using NetWork Manager"???? if so, the MTU is set in the GUI.. and all that does is edit /etc/NetworkManager/system-connections/yourconnectionname.nmconnection with mtu=value

MTU verifying

Ping your default GW or another live close node in your LAN by packets with "do not fragment" option and with specified packet size. Change packet size and find the limit size which is responded by the peer node:

If packet size is bigger than MTU then ping response will look like:
```

ping: local error: message too long, mtu=1500
```

Please note that packet size you use in the ping command (-s option) must be MTU minus 18 bytes, i.e. for instance 1500-18=1472.
I'd try first using Netplan, I'll show an example of new file 02-eth1-mtu.yaml:
```

network:
  version: 2
  renderer: NetworkManager
  ethernets:
    eth1:
      dhcp4: true
      mtu: 1000
 
```
EDIT This is How to set "do not fragment"
```
ping 192.168.1.1 -c 2 -M do -s 2000
PING 192.168.1.1 (192.168.1.1) 2000(2028) bytes of data.
ping: local error: message too long, mtu=1500
ping: local error: message too long, mtu=1500

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 0 received, +2 errors, 100% packet loss, time 1023ms

```
As TheFu pointed out:
>  So, changing the value while it is connected will likely screw that connection, *completely*. 
Including>>>the auth configuration when running.
If this is a Paid VPN I'd open a ticket with them, if not let us know

---

