---
title: "unable to change network locations automatically (wifi)"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by xrfang on 2007-01-16
Hi All,

I have been using Ubuntu (Edgy) for several months now, since about 3 weeks ago, my laptop got some strange problem.  I use laptop in office and home with 2 different wireless network. I saved the 2 network loacations, and get the following problems:

1) the network location is not detected automatically and will not connect to wireless network, unless I manually select the location in network configuration.

2) while I try to use net-applet's configuration menu, it tells me that "you have no rights to load the profile" (translated from Chinese message). This is the most piculiar thing and is the primary problem I am now asking for help, because it was ok, and suddenly failed weeks ago.

3) I don't know what the benefit of wifi-radar, except what I can do with iwlist scan... I would like to know a good method to automatically connect to a detected wireless network (either in office or at home), similar to windows xp's zero-configuration wifi.

Thanks!
Shannon

---

### Post by peabody on 2007-01-16
There's an applet known as network manager which is very similar to XP's wireless setup.  I believe it's usually installed by default on Laptops, but it may not be for some reason.  I believe the package name is NetworkManager.  It doesn't quite work with all makes of wireless cards however.

---

### Post by xrfang on 2007-01-16
Hi 

thanks.... the program you are referring to may be called network-admin? That's exactly where the problem is!

While I try to use net-applets to start it, it says I do not have previlige, while I launch it directly from System menu (top toolbar), I get a prompt for password.

I tested again, in terminal, if I run it directly, I get the previlige problem, but if I use gksu, I get password prompt.

So apparently, net-applet (i.e., the systray program) SHOULD use gksu too. The strange thing is that it seemed ok long time ago, while I first installed ubuntu, then someday it didn't work, I don't know what is the programming language of net-applet, and how to check it...

Finally, I hope by using wifi-radar or something, I can get full zero-config network, but I now suspect the problem starts to happen after I install wifi-radar... ](*,) 

Thanks,
Shannon

---

### Post by peabody on 2007-01-16
No, the program in question IS called NetworkManager, unless it underwent a name change from dapper to edgy.

[Edit: here's the page for the package --> [http://packages.ubuntu.com/edgy/net/network-manager](http://packages.ubuntu.com/edgy/net/network-manager) ]

sudo aptitude install networkmanager networkmanager-gnome.

[Edit: the package is apparantly different in edgy

sudo aptitude install network-manager network-manager-gnome

]

Unless this has changed in Edgy, last I heard the program was still active.

---

### Post by xrfang on 2007-01-17
I think either my network is still not fully resumed (backbone problem), or it is indeed renamed in edgy. apt-get tell me no such package called "networkmanager"

I also suspect the problem is some what related to hibernate. In these days, I will shutdown laptop while I move, see if the problem persists after reboot or not...

thanks

---

### Post by xrfang on 2007-01-18
hi,

Preliminary test show that ONLY if I do a "hibernate" will this problem appear, if I reboot, it is ok.

By OK, I mean, network location is successfully changed without needing manual configuration. However, net-applet still cannot correctly call network-admin (saying access denied...).

Any comments please?

Thanks,
Shannon

---

