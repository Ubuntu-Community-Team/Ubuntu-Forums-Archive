---
title: "VPN not working with Ubuntu 14.04"
date: 2014-05-09
forum: Networking &amp; Wireless
---

### Post by stepheny on 2014-05-09
I have seen other threads regarding this problem, even one marked [SOLVED], but not a solution that works.

Since upgrading to 14.04 my VPN connections GUI no longer works. I have re-installed network-manager-gnome and network-manager-openvpn-gnome but if I try and open a VPN nothing happens.

Could someone offer a workaround for this problem, maybe a command line method of opening a VPN as this is a major issue for me. I have been using Ubuntu with OpenVPN since 10.04 without any problems.

---

### Post by stepheny on 2014-05-10
Over 100 views but no solution.

Until this is fixed I am using this workaround.

From the command line type:

> sudo openvpn --config XXXX.ovpn

---

### Post by stepheny on 2014-05-12
Bump

This is a serious situation with an upgrade to a LTS version breaking a much used service, ie the Gnome VPN application. This thread has had 145 views and there are lots of other unresolved threads describing the same problem which would indicate that many users are experiencing this but not finding an answer.

Very disappointing. Maybe after eight years of using Ubuntu it is now time for me to move to another distribution.

---

### Post by pitchizig on 2014-05-15
Hi!

For several weeks, network-manager and openVPN didn't work together. It seems the last update allows at least to configure the VPN manually through network-manager.
Tell if you need help.

---

### Post by stepheny on 2014-05-16
Thanks for your reply. 

How did you find out that this is a known problem? I have not been able to find out anything about it, in this forum or on the web, other than lots of people are looking for a solution to it.

To be honest I find it astonishing that an LTS release can break something so important but when users report it and ask for advice we are met with a wall of silence. It is as if by ignoring the issue it can be safely assumed not to exist. 

Like I said, after over eight years of using Ubuntu I have never known this forum to be so unresponsive and the product seems to be going backwards in terms of development. Sadly, it is probably time for me to move to another distribution.

---

### Post by stepheny on 2014-05-16
Got posted twice.

---

### Post by pitchizig on 2014-05-17
Hi,
The bug is tracked in launchpad, an example [https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/1294899](https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/1294899). Another one [http://askubuntu.com/questions/450493/openvpn-cant-import-configurations-on-new-14-04-installation](http://askubuntu.com/questions/450493/openvpn-cant-import-configurations-on-new-14-04-installation).
From what I understand, a solution is nearly ready.
You are right, it's strange to see a LTS launched with so many regressions. I had troubles with Samba. My printer stopped working. Plus many other little troubles which I spent a lot of time to fix.
Well, other distributions have their problems too. With Ubuntu, I always manage to find a solution. That's priceless.
Don't lose faith!

---

### Post by stepheny on 2014-10-16
Bump

This is a serious situation with an upgrade to a LTS version breaking a much used service, ie the Gnome VPN application. This thread has had nearly 800 views and there are lots of other unresolved threads describing the same problem which would indicate that many users are experiencing this but not finding an answer.

When will it be fixed? Never?

---

### Post by rachel-g41 on 2014-10-16
I have just discovered I have the same problem. I've had problems with network manager since updating to 14.04 but this is the first time I've tried to connect via VPN which previously was very quick and easy.

---

### Post by deeflex on 2014-11-27
Yes same problem still exist as of 27th November.

---

### Post by rachel-g41 on 2014-11-27
Has anyone found that 14.10 solves the problem? After trying several of the solutions mentioned on other threads I gave up went back to 13.10. It's not ideal but at least I'm connected.

---

### Post by zaax on 2014-11-28
Same problem, no fix found

---

### Post by marc-bolard on 2015-02-09
Hi,

Not sure I had the same problem but I just posted a workaround/solution in this thread: [http://ubuntuforums.org/showthread.php?t=2258555](http://ubuntuforums.org/showthread.php?t=2258555)

I need to click on "VPN Connections" in the Network Manager Gui before clicking the desired VPN setup to start. Just naviguating though the menus didnt work for me.

Hope it helps!

---

### Post by ryu kun on 2015-07-23
VPN in Network Manager is broken on the most popular linux distribution's LTS release.
It is still broken after 15 months.
Really surprising.

---

### Post by stepheny on 2015-08-08
The VPN in the Network Manager is still broken in 14.04 LTS and all following releases! I am using 15.04 and the VPN in the Network Manager still doesn't work. How many years will it take to get this fixed?

---

### Post by matt_symes on 2015-08-08
Hi

That's odd because I have used network manager open vpn in xubuntu to connect to an open vpn server I set up on a windows 7 box quite recently.

This is on 14.04.

Kind regards

---

### Post by stepheny on 2015-08-09
Oh well, I suppose I, and all the others experiencing this problem since 14.04, must be mistaken then. 

Seriously, this is the sort of attitude that prevents a broken feature in a LTS release from being fixed after over a year.

I have discovered that, as marc-bolard suggested above, if you actually left click on the "VPN Connections" menu item and then select the VPN you want it will work. This is not usual behaviour and still it needs fixing.

---

### Post by matt_symes on 2015-08-09
Hi

> **stepheny said:**
> Oh well, I suppose I, and all the others experiencing this problem since 14.04, must be mistaken then. 

Seriously, this is the sort of attitude that prevents a broken feature in a LTS release from being fixed after over a year.

I have discovered that, as marc-bolard suggested above, if you actually left click on the "VPN Connections" menu item and then select the VPN you want it will work. This is not usual behaviour and still it needs fixing.

I'm sorry that you are having problems using network managers open vpn manager. It was not my intention to imply that were not.

However, that does not change the fact that I'm not having these issues.

Kind regards

---

### Post by stepheny on 2015-08-09
Right, we've ascertained that you are not having problems with the Network Manager's VPN Manager but that I am. What is the next step? What do you suggest we do now? Here's a link to the bug report [https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/1294899](https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/1294899)

There are many reported bugs, problems and requests for help on these forums, it would never occur to me to reply to any or all of those with problems that I **haven't experienced** to tell them that I am not having these issues. It just seems a totally useless thing to do unless the OP is asking for information regarding different hardware/software configurations.

If I can help I do, if I can't I keep quiet and let someone who can help, help. Your posts on this thread offer no help, assistance or suggestions at all. I cannot imagine what purpose you think they serve.

Kind regards,

---

### Post by matt_symes on 2015-08-09
Hi

My first post was posted when I was on the bus. 

I subscribed to the thread then with the intention of looking at it in detail to see if I could offer some help when I had more time as, like I stated, network manager's open vpn is working for me.

Your response did not engender any desire for me to help, hence my last post that I maybe should not have posted.

I really hope you do find a solution to the problems you are having but I now have other things to do and will be unsubscribing.

Kind regards

---

### Post by Ponders on 2015-08-12
I am sorry if I am going out of the topic. but I have started a thread similar to this and there is no replies to it either. My problem is where the OpenVPN server is on a Ubuntu and I am trying to use Win 7 OpenVPN client to access. 

Using Android OpenVPN client to access the same OPENVpn Ubuntu Server works very well. but not using OpenVPN Client from a Win 7.  What could be the possible problem? most of my google searches ended up asking me to check on the routing and if masquerading has been added to iptable. it has and as mentioned worked from an Android but not Win 7. 

Any suggestions?

---

### Post by ryu kun on 2015-08-12
This bug and [that bug]("https://bugs.launchpad.net/ecryptfs/+bug/344878"), among others, made me give up with Ubuntu again. I am using debian stable with Gnome now and I don't have any of these problems.

---

