---
title: "Wireless:  nm-applet shows no list of available networks."
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by Dimethoxy on 2008-09-26
Hello all,

I recently installed Ubuntu on my Dell, and I'm trying to set up wireless networking.  I purchased a USB D-Link wireless adapter, and installed drivers for it with ndiswrapper.  Following this I used nm-applet to select my wireless network from the list of available networks in the area, entered my password, and connected with no problems.

After returning home from a night of partying, I discovered that both my Windows machine and my Ubuntu machine had lost their connection to the network.  I reset the router.  The Windows machine immediately picked up the connection again, but the Ubuntu machine seems to have lost wireless networking capability entirely, out of the blue.  Nm-applet no longer shows a list of available access points (previously there were 5-10 in this list).

I can see a list of available networks using the Network Tool in System->Administration by disabling roaming.  This tool is able to see a list of available networks while nm-applet is not.  When I set up the connection manually with this tool, however, I still have no connectivity. 

In short, upon initial setup nm-applet functioned perfectly and smoothly; it was the easiest wireless setup I've ever performed.  Once that connection was lost, however, nm-applet stopped functioning entirely.  Even after uninstalling and reinstalling all wireless-related items, still nm-applet remains useless.

In searching for a solution to this problem, I was advised to clean my /etc/network/interfaces files of all entries save for those concerning loopback.  I attempted this, but found that it had no bearing on the problem.

Any insights?

---

