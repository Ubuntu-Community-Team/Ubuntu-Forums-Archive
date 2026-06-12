---
title: "Sonicwall VPN can't acquire ip address"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by Blind Tiger on 2008-06-08
Hi -- I am running Ubuntu 7.10 as a host OS with XP Pro installed as a guest OS with VMware Server 1.0.5.
[LIST]
[*]My internet access is working just fine after some tweaks.
[*]I have installed Sonicwall VPN and am trying to connect to my office network.
[*]The problem is that after a successful login/authentication, the vpn network adapter endlessly tries to acquire  an ip address.
[/LIST]

Any help would be greatly appreciated.

----- note:  added info -----
I have done a clean install of Hardy, a complete install of VMWare Server 1.0.6, yet bridged networking will not work, only NAT functions properly, and I still can't acquire the ip address with Sonicwall.  So my solution has to be to get vmnet0 bridged properly to eth0.  How is this done?

--------solved---------
I have established a vpn connection to my office workstation using Sonicwall Global VPN.  Using NAT networking, the solution was to Enable NAT Traversal in the Advanced section of the VPN menu on Sonicwall's web administration page.
* see [http://ubuntuforums.org/showthread.php?t=891400](http://ubuntuforums.org/showthread.php?t=891400) *

---

