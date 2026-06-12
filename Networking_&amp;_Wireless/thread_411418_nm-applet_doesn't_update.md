---
title: "nm-applet doesn't update"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by nullmind on 2007-04-16
I like to start on a quick positive note that networking in Feisty is pretty amazing! I think there are some areas for improvement, but I think it's important that we recognize the great work being done here.

I have a Broadcom 4318, but unlike most others I've had pretty good luck with it since Dapper using either ndiswrapper or bcm43xx (I don't use bcm43xx because I am in the city and most low-signal networks tend to flake out)

Since using Feisty I've noticed the great roaming support, and it has worked really well. There is one showstopper though: sometimes the panel applet (or the underlying network-manager daemon?) displays that it's connected (with the proper signal strength of the network) but it never actually went through the initialization process and I can actually select any network and it will say that I'm connected instantly.

In the shell ifconfig, iwlist and iwconfig will report the proper available networks, signal strength, etc. and nm-applet will say I have an invalid IP address of 0.0.0.0.

This is typically solved by rebooting. I've tried removing the kernel modules (either bcm43xx or ndiswrapper), fiddling with some switches, and doing ifconfig up/down to see if I can get the manager to realize it's NOT connected, and sometimes it works but it usually has some finite period of time before it figures it out (somewhere in the range of 5 minutes) and requires that I stop fooling with it.

Is there any way to tell the the roaming manager that a.) I don't want it to automatically connect to any networks (as this usually causes it) and b.) to forget any information about previous networks and just start over to ensure i get a connection.

As always, thanks for any responses and your time,
Kristopher Ives

---

