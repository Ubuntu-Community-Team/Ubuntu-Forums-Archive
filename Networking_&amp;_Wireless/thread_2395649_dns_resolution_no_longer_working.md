---
title: "dns resolution no longer working"
date: 2018-07-04
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2018-07-04
I noticed that on my server (16.04), I can no longer do updates, or resolve ips/hostnames.  On my clients I can.  I am running iptables on my server.  The only thing that has changed, is a new network interface (which got a new interface name - but it was the internal lan interface), but iptables has been already updated with that new name.  Is there something I'm missing here?

---

### Post by rsteinmetz70112 on 2018-07-05
I have a similar problem I haven't resolved yet.
Do nslookup, dig, ping (by name and ip address), ping6(by name and ip address) work?

---

### Post by sniper8752 on 2018-07-07
Neither ping worked (operation not permitted - I haven't allowed it in my iptables), and nslookup fails, saying no servers could be reached.

---

### Post by SeijiSensei on 2018-07-07
Disable the firewall. Does DNS work now? If so, you know where the problem lies. Check the rules for port 53 UDP traffic.

---

### Post by sniper8752 on 2018-07-07
I seem to have found the issue.  In /etc/resolv.conf, updating the nameserver field with 8.8.8.8 fixes the issue.  I thought this was deprecated?  How can I have the nameserver set, instead of pulling it from my ISP?

---

### Post by whistl034 on 2018-07-07
Editing /etc/resolv.conf does work, temporarily. The next time you reboot, the dhcp client will most likely overwrite it with the dhcp assigned dns server.

Making the change permanent depends on how your workstation is configured. Ubuntu desktops by default use Network Manager.  Find the Network Manager applet near the upper right corner, open the Settings, find the DHCP tab, and override the DHCP assigned DNS server(s) here. Then DHCP will continue to work for assigning you an IP address, but it's dns servers will be ignored.

If your network is configured using /etc/network/interfaces, read this [https://help.ubuntu.com/community/StaticDnsWithDhcp](https://help.ubuntu.com/community/StaticDnsWithDhcp)

8.8.8.8 and 8.8.4.4 are Google's anycast nameservers, and should work perfectly fine.

---

### Post by sniper8752 on 2018-07-08
It is ubuntu 16.04  server (no gui).
I do have a "dns-nameservers" line at the bottom.  But it still doesn't seem to work.  Does it need to be closer to the interface that  I want it configured on?

---

