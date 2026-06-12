---
title: "kubuntu can't find network - router ip address won't stick"
date: 2005-07-21
forum: Networking &amp; Wireless
---

### Post by arjay1 on 2005-07-21
I have three computers on a network through a common router.

I have installed kubuntu on two machines and all is fine.  However, on the third - when booting up it takes nearly 60 seconds over "Configuring network connections" and then continues the boot but when all is done there is no network.

If I look in control center/internet-network/network settings - it is all greyed out with eth0/dhcp/Disabled showing.  The first time I managed to get it to work by logging in as administrator and resetting the router's ip address.  However, the router's ip address won't stick through a reboot.

Now, after a couple of reboots it hangs when I try to click on administrator in the network settings screen with  the word "loading".

Any help greatly appreciated

---

### Post by cwaldbieser on 2005-07-21
Try adding the router's IP address as the default route in the config file mentioned in this thread:

[http://www.linuxquestions.org/questions/history/344658](http://www.linuxquestions.org/questions/history/344658)

---

### Post by arjay1 on 2005-07-22
Thanks for the ideas - I have experimented exhaustively but to no avail.  I modified the interfaces file as you suggested but still no ip address inserted permanently for the router.  I found that I could sudo kcontrol to get into control centre with root permission.  I manually entered the router's ip address in the route section and clicked on apply.  It appeared to stick but the minute I closed control centre and reopened it, the address had vanished.  I am really fed up with this - i have wasted over two days on it and feel that maybe I should re-install?

I rebooted all three computers in Win XP (they all dual boot) - just as well or I'd be in a right pickle. - and they all network and connect to the internet perfectly.

The install file looks like this (manually typed because I have no way of copying the file over to a windows machine!):

The relevant bits are:

auto lo
iface lo inet loopback


mapping hotplug
script grep
map eth0

**This added from your link**
iface eth0 inet static
up route add -net 127.0.0.1/24 gw 192.168.1.1
down route del -net 127.0.0.1/24 gw 192.168.1.1
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1255


NB:  
router's ip = 192.168.1.1
linux loop = 127.0.0.1
dell computer ip = 192.168.1.2, mask 255.255.255.0

A look in KInfoCentre shows the etho up as follows:
eth0, 192.168.1.2, 255.255.255.0, broadcast, Up

and lo as follows:
lo, 127.0.0.1, 255.0.0.0, Loopback, Up

But, as I say - I can see in Control Centre that there is no ip address shown for the router.

Is there anything in the script that is wrong or redundant (I just cut and pasted the additional lines fromk your link)?

BTW - even during boot up I can see the network is not up, as the boot sequence fails to sync the clock because it needs an internet connection and comes up as "failed".

Hope you have some ideas - I'm fresh out!

Cheers

Richard

---

### Post by arjay1 on 2005-07-22
OK - now I feel a lot happier as I have discovered this is a major bug. I never thought there could be such a disastrous error on the KDE developer's part (if that is where it lands up).
 
There is a major, major, bug in KDE 3.4.0 AND 3.4.1.   I have found it is well documented at bug number 8681 at bugzilla.ubunutu.com and 61850 at bugs.kde.org.

There are pages and pages of complaints - a quick google will get you there.

There are a few suggested workarounds but most only work for a few people.  The KDE developers suggest you switch to Gnome for the time being!!!!!!!!!!

I am going to try a couple of things (only a newbie I'm afraid) and I'll let you know if anything works.

---

### Post by gruepig on 2005-07-22
Regardless of KDE bugs, you can edit the file /etc/network/interfaces manually (as root/sudo).  In general, anything which can be done through KDE (or GNOME or X) can be done from the command line.

Do you have a DHCP server on your network?  

If so, delete the eth0 configuration from /etc/network/interfaces and instead add these two lines:

auto eth0
iface eth0 inet dhcp

If you don't have DHCP, you'll want these lines:

auto eth0
iface eth0 inet
address 192.168.0.2
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

(Make sure you use a unique address for each machine.)

Save the file and run 'sudo ifdown eth0' and then 'sudo ifup eth0'.  This should just work (and your network interface should be brought up automatically on boot).  

Run 'ifconfig -a', 'route -n', and 'cat /etc/resolv.conf' to check your IP settings, route tables, and DNS server configuration (respectively).  To make sure everything is working, try pinging your router by IP address, pinging a remote host by hostname, going to a web page, etc.

If that doesn't work, post the contents of /etc/network/interfaces and the output of 'ifconfig -a' and 'route -n'.

---

### Post by arjay1 on 2005-07-22
Thanks for such a helpful reply.  I'll give your suggestions a go in the morning (gone midnight here).  I've added my findings to the various bug reports but, as you say, things can still be done through CLI - just annoying.  As to whether I have  a DHCP server or not - how would I know?  At the moment, the ip address for this computer is configured automatically via DHCP - so I guess that means yes.

I configured my other two computers manually to have static addresses but this dell (the one I am having the problems with) would not find the network if I used a static address but perversely, the same address gets returned time and again by DHCP.

Anyway - I'll experiment tomorrow - oh joy!

Thanks again for your time and trouble.

---

