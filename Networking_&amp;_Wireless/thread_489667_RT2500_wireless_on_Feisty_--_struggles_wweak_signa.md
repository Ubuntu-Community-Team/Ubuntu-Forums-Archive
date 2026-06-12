---
title: "RT2500 wireless on Feisty -- struggles w/weak signal"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by MarkusRTK on 2007-07-01
Hi -- I'm loving Ubuntu (newly installed on my Averatec 3250 laptop; best decision I ever made). Having some semi-major wireless problems, though, so maybe you can help me out.

I've got a Ralink RT2500 card (came OEM with the laptop); due to my weird living situation this summer I have to try and pick up a fairly weak signal. (Long story.) It's usually OK, I can pull in between 70 and 90%; in WinXP it works fine with the occasional cutout. But on Linux, when it cuts out, it often struggles to reconnect, and I'm pretty sure this is a software problem.

What happens is, the signal will suddenly drop to 0% when it's trying to send/receive. (This is per the connection-properties applet -- not network-manager, which I uninstalled because I heard it didn't handle Ralink cards well. That seemed true enough, as I couldn't get anything to go through until I kicked network-manager to the curb. I am just using the default drivers, no ndiswrapper or anything.) If the connection is idle, it shows a perfectly good signal, but if Firefox or anything tries to send packets the signal drops back down to 0% and it receives no packets. This lasts an indeterminate amount of time -- sometimes seconds, sometimes up to an hour -- before the signal is suddenly normal again.

The weird part, and what makes me think it's a software problem, is that I can sometimes bring it back momentarily by playing around with ifconfig on my *other* interfaces. Really. The connection will be useless, and I'll "sudo ifconfig eth0 down" and back up, and then for a brief period of time (like, a few seconds up to a minute) I can receive data. Same thing if I bring the lo interface down or up. Sometimes, I kid you not, the connection will momentarily resuscitate if I simply *ifconfig* without making any changes, or if I just open system->administration->network. But it's totally unpredictable and inconsistent; sometimes that works, sometimes it doesn't.

The problem goes away if I bring the laptop down right next to the router, so I know it's related to the weak signal; but I should be able to operate normally on 70-80%, no? 

Other notes: this has been happening less frequently since I blacklisted ipv6, but it's still happening. Also I notice that sometimes avahi steps in, either on my unplugged eth0 or even on ra0 (my wireless interface) if it's disconnected for a while; if that happens on ra0 I have to ifconfig it down and back up before I can receive data (and usually DCHP fails after that, so I have to restart the laptop to get an IP address). Otherwise the interface renames itself "ra0:avahi" and network-admin apparently can't interact with that. Tried to uninstall avahi, but it's linked to ubuntu-desktop so that seems impossible.

(Amusing sidenote: my laptop has a wireless toggle, but apparently it's software-based, since my connection only works when the toggle is *off*. If I toggle it on, I can never receive packets, though Ubuntu still thinks it can see a signal. WinXP handles the toggle normally.)

This is not a serious issue, since I can live with sporadic Internet for the two months I'll be here, but it's annoying. Besides I read that there are all kind of problems with Feisty, network-manager, avahi, and Ralink cards, and this is a weird conglomeration of all of them, so I think people might find this interesting. Thanks in advance for any help.

---

