---
title: "Gnome Network Manager options grayed out?"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by toddpedlar on 2007-07-26
I'm running Feisty Fawn on a new PC, and am trying to use DHCP for my connection to our college network.  When I right click on the Network Manager icon in the toolbar,  "Enable Networking" has the little checkmark beside it just like on my other PCs in the lab.  However, it has "Connection Information" grayed out, UNLIKE the other PCs in the lab.  Also, when I left click on it, "Wired Network" is grayed out.  

If I try the manual configuration, I am set up just like the working PCs - it's set up for dhcp.

Can anyone tell me what's going on?  Clearly something isn't configured properly, but I don't know what.

Todd

---

### Post by toddpedlar on 2007-07-26
This really seems odd.   I wonder if this has to do with something being improperly configured at install time?  My wired interface is from Realtek (RTL8111/8168B PCI Express Gigabit, driver is r8169.  

When I look at the kern.log through the system log browser, i see a ton of "r8169: eth0: link down" messages, followed immediately by a "eth0: link is not ready" message.

Can anyone help me figure out what's going wrong?

---

### Post by toddpedlar on 2007-07-26
Shouldn't be replying to my own thread (but then nobody was doing so).

Here's the problem.  If your linux source is 2.6.20-16-generic or earlier, the Realtek r8169 driver apparently doesn't work properly.   See [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798) for more info.

The workaround:

rmmod 8169
modprobe r8169

That's it.  Then it finds your link and will dhcp right away.

This problem has been around a long time, and is really going to be a pain in the butt.  
Can it be fixed?

---

