---
title: "Network Manager Applet not Saving Changes"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by Major_Kong on 2008-11-04
Every time i reboot the network manager resets, and the changes i made to the wired connection are lost (e.g. changing the ip to static).

Any ideas ?

---

### Post by k9fe on 2008-11-04
My question is even more basic.  Where did the network configuration app go?  8.10 was supposed to fix the networking side, but they seem to have broken the app.  Sure the roaming and auto-connect fix works and that is very good, but now I cannot set a static ip that is retained.  Your question is on target.  The DHCP side of our network is not allowed access to the net resources, only the statically assigned addresses are allowed to authenticate with Exchange.  So a fixed ip worked great in 8.04...broken now in 8.10.

Mike

---

### Post by Major_Kong on 2008-11-04
Did you upgrade from 8.04 ?

---

### Post by superprash2003 on 2008-11-04
have you tried setting up static ip manually by editing /etc/network/interfaces

---

### Post by Major_Kong on 2008-11-04
> **superprash2003 said:**
> have you tried setting up static ip manually by editing /etc/network/interfaces

That was the previous solution, but in exchange the network manager applet gets borked. (doesn't even start)

---

### Post by NIT006.5 on 2008-11-04
I'm also having major issues since upgrading to Intrepid. I'm having to manually edit /etc/network/interfaces to switch between wired and wireless. I have two different wireless networks... one at home and one at work. In Hardy I could switch between the two easily enough. In Intrepid, whatever changes I make in the new nm-connection-editor seem to have absolutely no effect. Where are these settings stored (since it's obviously profile-specific and doesn't affect /etc/network/interfaces) and how are changes applied? I use static IP's on both wireless networks for direct net access through routers. After the upgrade my wireless connection at work seemed fine, but I haven't even been able to connect to my home wireless network. I eventually had to take down the wireless interface completely and connect via cable, and even then I couldn't do it through nm-connection-editor and had to manually edit /etc/network/interfaces. The problem described here obviously applies to my laptop.

In addition I have also had problems after upgrading my desktop at home, I would have a wireless connection for about 60 seconds and then it would drop out. I would still see full signal strength but lost all communication. After taking the interface down and bringing it back up, once again I would have wireless for about a minute and then it would drop. I never had any issues on Hardy and this only happened after upgrading to Intrepid. Three days later I'm still using a wired connection and haven't found a solution.

I'm really baffled and confused by this. There doesn't seem to be much of a problem for PC's that have one static address or that use dhcp, but where switching between wired and wireless (or switching wireless networks on static addresses) is concerned, the managing of connections/interfaces in Intrepid is making no sense to me and doesn't behave at all as expected. In fact it seriously doesn't seem to do anything at all. No settings changed via nm-connection-editor actually seem to make any difference.

Of course it's quite possible that I'm being dumb somewhere along the line, but I don't think so. Any thoughts/opinions/solutions welcome!

---

### Post by ryu kun on 2008-11-04
I use Ubuntu 8.10, Network Manager 0.7.0. I lose my DNS changes with reboot. NetworkManager applet doesn't save my changes.

A bug has been filed on this issue: [https://bugs.launchpad.net/ubuntu/+bug/293590/]("https://bugs.launchpad.net/ubuntu/+bug/293590/")

---

### Post by superprash2003 on 2008-11-06
thats probably because your router is overwriting the /etc/resolv.conf file automatically.. try this [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by lowbot on 2009-02-11
Yep, 8.10 Xubuntu does this too. That's an incredible bug to get past the most basic QA. What gives?

My workaround is to uninstall networkmanager altogether and edit the interfaces file.  If networkmanager is installed I found that it ignores the interfaces file. Which is another bug!!

Come on xubuntu maintainers, this is ridiculous.

---

### Post by NIT006.5 on 2009-02-12
> **lowbot said:**
> If networkmanager is installed I found that it ignores the interfaces file. Which is another bug!!

This isn't actually a bug. 8.10 stores network interface info on a per-profile basis, as far as I know. So /etc/interfaces would be ignored, but this has not happened accidentally. 

I initially had problems after upgrading because it would seem that /etc/interfaces was conflicting with the networkmanager settings stored under my profile. Removing all entries from /etc/interfaces (except for the loopback interface) and only using networkmanager, has solved all my problems though.

---

