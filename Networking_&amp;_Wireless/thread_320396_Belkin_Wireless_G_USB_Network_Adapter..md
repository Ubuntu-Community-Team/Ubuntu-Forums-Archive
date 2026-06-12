---
title: "Belkin Wireless G USB Network Adapter."
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by score_under on 2006-12-17
I am new to linux and I am using belkin's "Belkin Wireless G USB Network Adapter" with Kubuntu live disc, and I cannot install it at the moment (hard drive has important data on it). I opened konsole and typed "sudo wlassistant", and it worked fine, I connected to the network, told it to use dhcp, etc, and then it blurted out "Connection Failed" at the bottom of the window, and what I think may be causing the problem is the DHCP client. It says:
```

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/rausb0/(my MAC address)
Sending on  LPF/rausb0/(my MAC address)
Sending on  Socket/fallback
DHCPRELEASE on rausb0 to 192.168.1.1 port 67
CONNECTION FAILED.

```

Does anyone know what to do?

---

### Post by hoggbottom59 on 2006-12-17
Just a suggestion but have you tried it with a static IP address?

If the error seems to do with DHCP, try a static IP address. It may not be to do with DHCP but is something related and gives an error with DHCP.

If static addressing works then you can investigate problems to do with DHCP (you might not have the correct DHCP services running in Linux).

If it doesn't then you need to sort out the networking with Static IPs to make sure that's all working first.

DHCP is an excellent feature for networking but does add an extra layer of potential problems.

As you're new to Linux don't expect it to be as straightforward as Windows to set things up, you'll need a logical approach and be prepared to be adventurous and patient.

The satisfaction when you get things working and the stability of Linux more than make up for it! Plus the fact you're also using free software that is very efficient and is worlds ahead of Windows.

Hope this helps
Leon.

---

### Post by score_under on 2006-12-17
Thanks a bunch! It was DHCP causing the problem. I don't think I can fix it without tweaking the router, though, because my Nintendo DS had trouble with the router as well.

---

