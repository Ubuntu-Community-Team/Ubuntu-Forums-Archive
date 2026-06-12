---
title: "Ubuntu runs slowly when network is unplugged"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by dmonkey on 2008-01-16
Hi,

I have an HP laptop running Gutsy. At work, I have a permanent ethernet connection. All of this is working fine. The IP address is static (ie. I don't use DHCP).

The problem comes when I want to take the laptop home, where I have no internet connection. Whenever the network cable is unplugged and I boot into Ubuntu, the booting process takes much longer - the booting waits at the login for the (where it says [computer name] login:  ) and also when it tries to load CUPS. Then when login finally completes, the desktop runs extremely slow, and trying to open any programs takes an age.

I found that the problem has been documented here:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/78263](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/78263)

and there is also a solution, namely to clean the /etc/resolv.conf file at startup. The idea is that if you get settings via DHCP then the Network Manager should find settings automatically when the network cable is connected, and if you aren't connected then NM does nothing and you are left with a system that runs properly and an emtpy DNS.

I would like to know if anyone has any ideas about how to tell Ubuntu on startup that if the network cable is connected it should use my fixed DNS and domain name, otherwise it should set the DNS to 0.0.0.0 (as in the fix above), or if anyone knows of something all together better.

I already tried the 'ifplugd' program, but to no avail.

Thanks

---

### Post by dmonkey on 2008-01-22
Just an update: I found that when logging into Ubuntu, unchecking the box for the wired connection in network properties dialog also works, but there is still the problem of the long loading times before I even get to this dialog. How can I switch the wired connection on and off using a bash script?

---

