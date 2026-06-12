---
title: "Endless/infinite DHCPNAKs, problems w/ wired and wireless"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by nikkelj on 2008-04-17
Howdy,

So here's my story:
-I had everything worked wired for a while.
-I installed a driver for my Linksys WUSB54g wireless adapter using ndiswrapper...no biggy.
-I was never able to get it to work in Network manager, so I tried via terminal.  I later read about the stupid roaming mode enable problems...this may have been what borked things (?).
-I am now at the point where I cannot bring either eth0 or wlan0 back to life to the point where I have internet access.

My current config:
I am wired to the router (which I know works fine because I'm posting this), my wireless is plugged in, and Ubuntu sees it (I have a wlan0 device, and the driver version, MAC, etc  looks right when I do lshw).

I just an through the steps in the sticky post to get things working, to no avail.

And here I am now...begging for help from the Linux gods...I guess I'm sitll a noob afterall /sigh

I'm having to type this into another computer next to the Ubuntu box, so bear with me....

dmesg looks fine, with the exception of " wlan0: no IPv6 routers present"...similar message for eth0

route -n:
Destination                 Gateway                Genmask           Flags             Metric    Ref      Use   Iface
169.254.0.0               0.0.0.0                   255.255.0.0    U                    0             0         0        eth0
0.0.0.0                       0.0.0.0                    0.0.0.0           U                    1000       0         0        eth0

This doesn't look right...I don't have a route to my gateway, 192.168.2.1.
 
I did a route add default gw 192.168.2.1...

Still no joy....can't ping anything....

ifconfig:
inet addresses can't be right...my router is setup for a 192.168.2.XXX network.  It's showing a 169.254

Trying the steps from the sticky again:
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

The strange thing, which I've noticed before is that when I sudo dhclient wlan0 or eth0, just get an endless stream of DHCPNAK's....forever...

I remember I had this problem when I first set this box up too, but I can't remember how I solved it (and now its been 3 months since I've touched it heh).

Anyone have any suggestion?  I've been banging on this thing for 4 hours now, and I'm about ready to call it quits and just reinstall.

Thanks,

-J

---

### Post by nikkelj on 2008-04-17
Some progress....

I did:
sudo ifconfig eth0 down
sudo dhclient -r eth0
sudo ifconfig eth0 192.168.2.200 netmask 255.255.255.0 up
sudo route add default gw 192.168.2.1

and now I can at least ping my router....still can't get to the outside world though.

---

### Post by nikkelj on 2008-04-17
Solved...well sort of...I still don't know why DHCP is broken, but whatever...screw it...I'll go static. 

I had an empty resolv.conf file...why it was empty...I do not know...

But hey...at least now i'm less of a Linux networking noob =)

---

