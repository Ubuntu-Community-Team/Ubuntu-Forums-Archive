---
title: "after changing network card i can't get out of my homenetwork"
date: 2005-07-28
forum: Networking &amp; Wireless
---

### Post by monkman on 2005-07-28
hi!

i just installed kubuntu on a second system here at home. the second pc got an 10mbit network card, which i changed to a 100mbit one after the installation was complete. with the 10mbit card all was working finde network and internet.
after that i'm not able to ping addresses behind my nat/router.

etc/resolv.conf looks fine

ifconfig -a looks good too

dmesg says the new card is set to eth0

route add default gw 192.168.0.1 doesn't help

i can ping other pcs inside the network without problems.
looks like there's an problem with name resolution. but i can't figure out what it may be.

any hints?

THANX

---

### Post by gruepig on 2005-07-28
Are you using DHCP or statically configuring your interface?  Clear out the route you've added, run 'ifdown eth0' and then 'ifup eth0'.  Any luck?  Post the output of 'ifconfig -a' and 'route -n' and I'll see if I spot any configuration problems.  (Also post the contents of /etc/network/interfaces if you're not using DHCP.)

Can you ping the IP address of your nat/router?  Can you ping the IP address of your nameserver?  Can you ping 64.21.33.9 (ubuntuforums.org)?

Are you sure the nat/router is properly working?  (If it's easy to do, you might try rebooting it.)

---

### Post by monkman on 2005-07-28
i'm using static ip's, no dhcp

run 'ifdown eth0' and then 'ifup eth0'
no luck

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0A:CD:08:2C:65
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:cdff:fe08:2c65/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:2898 (2.8 KiB)
          Interrupt:11 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2424 (2.3 KiB)  TX bytes:2424 (2.3 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

/etc/network/interfaces
 This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
        address 192.168.0.4
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.0.1


/etc/resolv.conf
nameserver 192.168.0.1

i played around with ifconfig

ifconfig eth0 192.168.0.5(4) broadcast 192.168.0.1netmask 255.255.255.0 up

after that i wasn't even able to ping the router/gateway.
it's an netgear rp614

as far as i remeber the router blocks clients which changed the networkcard and used the same ip. so i rebootet it. but with no results.

THANX

---

### Post by gruepig on 2005-07-28
Well, everything looks right.  The problem might be with your router. I'm not sure.  Or maybe it has to do with the IPv6 support?  (This is really a long shot, but you can disable IPv6 by modifying your modules alias file -- maybe /etc/modules.conf or /etc/modprobe.d/aliases.  You'll want to replace 'ipv6' with 'off' and then reboot.)  

Does anyone else have some ideas?

---

### Post by FlypSyde on 2005-08-10
Did you guys figure this one out? I'm having what looks like a similar problem. :-(

I'm using a D-Link DI-524 router to share my DSL connection. I've got 3 other computers running Windows and they can ping inside and outside my network, and the internet works fine for them. I did a brand new install of Ubuntu 5.04 and I'm using the onboard NIC which was detected properly. Initially I tried to configure it for DHCP but it wouldn't grab an IP (the Windows machines are running DHCP, the router is my DHCP server, works fine) so I reconfigured it for static IP with the correct subnet mask and default gateway. Now, I can ping the other computers on my network (and they can ping me) but I can't ping my router or anything beyond it. Needless to say, I can't access the internet.

Anyone have an idea?

---

### Post by danielhaden on 2005-08-10
This normally happens whenever the default gateway AND DNS is not set to your nearest router.  

This is also seen if your nearest router is 192.168.0.1 AND the next point is also 192.168.0.1.  Change your D-link to 192.168.16.1  

For Windows, it looks like this.  Just copy the information to Linux.  

My IP 
192.168.16.4
Mask
255.255.255.0
Gateway (D-link home router)
192.168.16.1
DNS1 (D-link home router)
192.168.16.1
DNS2 (cable box, dish box, DSL modem)
192.168.0.1
*altenatively use the DNS given to you by your service or copy it from the listing inside a connected windows machine.  

It is the DNS section that will allow you to see outside of your network.  If your home router is on the same address as your connection (cable box, dish box, DSL modem) then you can get "trapped" inside your own network.  With D-link, it is also helpful to turn the firewall "all the way up" because it engages loopback routing for better security..  For a larger (multiple routers with subnets) network, loopback routing should be disengaged.

---

### Post by FlypSyde on 2005-08-10
Thanks, but that doesn't explain why I can't ping the router itself since it's on the same side of the network as my Ubuntu machine. Both IP addresses are within the same subnet.

Anyway, after further research in these forums, I found another user who was having problems with a D-Link router (different model). He swapped out his NIC and things started working. I went ahead and disabled my onboard NIC, installed an old Linksys NIC I had, but got the same results (can ping everything on my side of the network except the router and nothing beyond the router). On a whim I swapped out my D-Link with an old Netgear one that I had (I had swapped the Netgear out for the D-Link because it had 802.11G wireless) and everything started working! I was even able to switch the NIC over to DHCP and it's working fine now.

I wonder if there's some issue with Ubuntu 5.04 and D-Link routers?

EDIT:
I just removed the PCI NIC I installed and enabled the onboard NIC again. Everything is still working fine. Definitely some issue between Ubuntu 5.04 and my D-Link 524 router? This same hardware worked fine with the router under Windows.

EDIT2: I switched the D-Link router back in and everything stopped working again. Put the Netgear back in and I'm making this 2nd edit to my post :-)

---

