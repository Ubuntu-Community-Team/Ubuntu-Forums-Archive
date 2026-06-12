---
title: "Connect to VPN from Ubuntu 8.10 64-bit"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by ieduarte73 on 2008-11-29
Hi,

I am interested in connecting my computer to my workplace VPN, I've used to do that with WinXP but since I have moved to Ubuntu Linux, I am not able to, I just upgraded to Intrepid Ibex, which includes NetworkManager 0.7.0, where I have already configured my VPN connection, but I don't know how to start using it.

Any ideas on this ??

---

### Post by cmnorton on 2008-11-29
You should be able to configure VPN directly from Network Manager. To which kind of VPN are you connecting?

---

### Post by ieduarte73 on 2008-12-02
This is a connection through a Watchguard Firebox, apparently PPTP so I have a username and password configured to log into the firebox, and then, it allows me to navigate through the Internal Network (it assigns me an IP Address 10.1.20.X).

Even though I have the VPN Configuration already under NetworkManager, I don't see a connect button or a way to enable that connection, or maybe is there something via CLI that needs to be done in order to connect through the VPN connection configured.

---

### Post by cmnorton on 2008-12-03
Are pptp-linux and network-manager-pptp installed? (Synaptic Package Manager) Because when you right click on Network Manager -- at least I remember its being a right-click -- you should see some vpn info. And I am assuming this is a Microsoft style vpn, not open vpn or Cisco.

---

### Post by snmahmood on 2008-12-05
I am having the same problem.I have installed ubuntu 8.10 and i goto the configure vpn by right clicking on  the icon but on the configure vpn the add button is not active.I have installed pptp and networkmanager pptp is already installed msg is showing when i am trying to install that package.Plz help.

---

### Post by cmnorton on 2008-12-05
This is beginning to sound like this bug:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/134547](https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/134547)

You could contribute to this bug, already entered, or file a new bug, if you think this is Ubuntu-specific. We've seen this on the Kubuntu side already.

---

### Post by peternz on 2008-12-08
I simply installed vpnc and suddenly it was fine.

Telecommuting once again!

---

