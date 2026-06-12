---
title: "VPN - network icon disappears"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by RotR on 2008-09-23
Hi,

I've just installed Ubuntu (latest version) on my Toshiba M200.

Progress:

* Installation
* Wireless works
* Installing vpnc and vpnc network manager
* Setting up a new VPN connection using a valid config file (successfully worked on a Windows machine, so the settings are OK, username is set OK)

The problem:

* I click the wireless icon (4 blue bars)
* I select "VPN connections"
* I select my VPN connection
* The "Authenticate VPN" window pops up
* I enter my password and leave the group password blank
* I click OK
* The network icon disappears (!) [no error msg]
* I am still connected to the wireless network
* However, I'm not on VPN: I still have my old IP address and thus can't access any of the resources I should.

How can I solve this?

Thanks!

---

### Post by DJAVAH on 2008-10-09
I have a very similar problem - I've setup my VPN connection using the nm-applet VPN connections option - and I know that I am connected fine using the VPN as I can access sites that are not available outside of my company network.

But when I change my wireless connection to use the VPN connection, nm-applet also disappears from the panel - my connection to the VPN is still live though.

The only way I can get the nm-applet to reappear in the panel is to reboot Ubuntu. Is this a bug?

---

### Post by Cliff283 on 2008-12-02
I'm having a similar problem as well. 

I'm new to Ubuntu  (Had it installed for about 4 days now) but I've worked with FreeBSD for the last 5 years so I'm not completely lost. 

My problem is actually two fold.

Part one;
Like the other people in the thread when I submit my VPN credentials the network icon just goes away. No error message or anything. I am *not* on a wireless network so I suspect that doesn't have much to do with it. 

Part two;
I have a static IP but I can only edit the VPN settings if I switch to the roaming setting. 

Anybody dealt with this before? I've been looking online and reading various things that haven't helped me yet.

Thanks,
Cliff

---

### Post by dollylamb on 2008-12-02
this is a bug of network-manager applet. see more here: [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/212054](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/212054)

---

