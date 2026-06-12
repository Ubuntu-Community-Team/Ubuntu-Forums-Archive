---
title: "VPNC drops connection after a few minutes"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by Chrieg on 2008-02-01
I can use public hotspots without having to log in or anything if I make a VPN connection to my university. Under Windows this works just fine with the Cisco Client. Under Ubuntu it doesn't. I use Ubuntu 7.10 and connect with VPNC and network-manager-vpnc. At first I can connect without any problems. But after a few minutes the pages just won't load anymore. The networkmanager-icon doesn't indicate that there's anything wrong, there's just no connection. When I then disconnect the VPN I can access the login-page of the access-point again. If I reconnect the VPN it starts from the beginning again.
It seems that I'm not the only one with this problem since I've seen this issue being discussed on a couple of sites across the internet. But none of them could provide a solution that worked for me.
I've tried other network managers like knetworkmanager and wicd. I also downgraded VPNC  to version 3.3 and installed the Cisco Client. None of it worked.

I would be so glad if someone of you could help me! I've been working on this problem for over a month now and got barely any work done. I also posted on other Forums but couldn't get any help either. It's really driving me mad!
Of course I can try some of the stuff I've already done again if you're sure that it has to work.

---

### Post by levmatta on 2008-06-17
I have the same problem. Please help.

---

### Post by lawr_rawr on 2008-06-29
I have the same problem after upgrading to Hardy 8.04 - no problems with 7.10

---

### Post by pkkid on 2008-06-30
Same problems here as well.  I also don't remember this happening on 7.10.  I am using KVpnc.

---

### Post by cmnorton on 2008-07-01
I'm on Kubuntu 7.10, and had several small roadblocks to getting kvpnc running. One of the problems I encountered was the connection dropping off within a few minutes.

I did two things that appear to have fixed the connection dropping problem:

1) I changed mtu to 1408 and took the mru default of 1000.

2) I changed the interval of the Connection Status Check under Network/General (config).

---

