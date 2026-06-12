---
title: "Why is dhcdbd/dhclient overriding my static IP, and how do I stop it?"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by oddhack on 2007-08-09
I've got the same problem noted in at least two [other](http://ubuntuforums.org/showthread.php?t=452906&highlight=DHCP) [threads](http://ubuntuforums.org/showthread.php?t=467402&highlight=DHCP): I've assigned a static IP to eth0 in /etc/network/interfaces, but Ubuntu 7.04 is still running dhclient on eth0 and overriding the static IP. The advice about killing dhclient in those threads doesn't  help with the deeper issue; what I want is to understand **why** dhclient is getting fired up on this interface at all, and how to prevent it.

My Linux networking knowledge is mostly based on Fedora Core 5, and even older versions of Mandriva where things are quite a bit different, and I haven't sorted out all the parts of Ubuntu's setup yet. However, it appears that dhcdbd is getting started as a dbus service, and then someone is telling dhcdbd to run dhclient on eth0. It shows up like this in ps:

 5052 ?        Ss     0:00 /usr/sbin/dhcdbd --system
 5668 ?        Ss     0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0

What I've been unable to determine despite a lot of grepping in /etc and /usr/share/dbus-1 is, **where's the config file or script that tells dhcdbd to run dhclient on eth0?** (and, why is it ignoring / being inconsistent with /etc/network/interfaces? Shouldn't the network config app understand that when I configure eth0 for static IP, the system must not run DHCP on that interface?)

---

### Post by oddhack on 2007-08-13
Aha, figured it out. The laptop-net package contains an 'ifd' daemon which detects link down/up transitions and responds by running dhclient. Completely ignoring /etc/network/interfaces, apparently.

In the end I flushed all of network-manager, network-manager-gnome, dhcdbd, and laptop-net, and replaced them with WiCD (from wicd.sourceforget.net). Which has at least two advantages: (a) actually works (b) has responsive developers.

---

