---
title: "Ubuntu PPTP VPN Network Setup"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by LoginMaster on 2008-12-05
Hi All. I'm new to the forum and as you can probably tell, new to ubuntu. I am aware of how to install Ubuntu, How to install software via-downloading and a lot of the other basics.

However, I am on a very good internet provider that I really do not want to change, unfortunately I am using a PPTP WAN VPN network. I have no idea what to do.

Are the Ethernet drivers even included in the Ubuntu Main Installation?
If there are things that need to be installed from a file before I attempt to connect, what are they and how do I install things from a pre-downloaded package?

Please help me. :-? [-o<
Thanks in advance. ):P

---

### Post by cmnorton on 2008-12-06
This answer assumes you are connecting to a router that is providing you a DHCP (dynamic) IP address.

For starters, you need to install pptp and the Network Manager add-ons for pptp You would use Synaptic Package Manager to search for and then install these packages. If you are the user who installed Ubuntu, you would use your password when prompted for Root's.

Here is one of many links in these forums.

[http://ubuntuforums.org/showthread.php?t=91249&highlight=pptp+network+manager](http://ubuntuforums.org/showthread.php?t=91249&highlight=pptp+network+manager)

Once you have gotten these components installed, you should be able to right click on Network Manager and VPN connections will show up in the menu. You can create one, and start experimenting on getting connected.

---

