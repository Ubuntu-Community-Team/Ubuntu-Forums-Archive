---
title: "Network Connections ALWAYS say Disconnected"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by fiveryanfrenzy on 2007-01-22
eth0 is the hard-line LAN connection and it is plugged in, works fine in XP but for some reason on Ubuntu in the Network Applet it always just says 'Status: Disconnected'...

Same with the wireless, I have full signal strength it shows but the status is always Disconnected.

How do I get these to connect?

The icon on my desktop menu bar has a little triangle exclamation point on it.

It worked FINE with no problems when I was at my parents house but now I am back at my house and it just stopped working! (I have changed nothing in Ubuntu only the router is different, modem AND ISP is the same!)

---

### Post by mindwarp on 2007-01-22
Please post the following:
[LIST=1]
[*]Does your network have a router?
[*]If so, does it do dhcp?
[*]What is the output of "sudo dhclient3 eth0"
[*]If your network does not use dhcp, what is its schema?
[*]Do you have network-manager installed?[/LIST]

---

### Post by fiveryanfrenzy on 2007-01-22
The Network does have a router and it does use DHCP

I have NetworkManager but I can't figure out why it doesn't look like the screen shot I found here: [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)
so I just downloaded the latest one from the gnome site (haven't tried to install yet...)
mine doesn't give me a drop down box or show connections in range or anything that the screenshot at that link shows.

I can connect fine using both wired and wireless on XP...

I am going to reboot into Ubuntu now and post the output of the command "sudo dhclient3 eth0"

> Listening on LPF/eth0/00:11:25:d2:89:0b
Sending on   LPF/eth0/00:11:25:d2:89:0b
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.101 -- renewal in 35040 seconds.


---

### Post by mindwarp on 2007-01-22
Great.  Ok first step is: Do not install network manager outside of apt.  If you want to use network manager, run: sudo apt-get install network-manager-gnome.  Note that if you configured the interfaces through Ubuntu's default network config, network manager will not fuss with their configuration.  If you want it to, you need to disable them.  You can read more at: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

Second, you are getting a dhcp lease from the dhcp server, so your network should be good to go.

Answer these questions please:
[LIST=1]
[*]Post the output of "sudo route -n"
[*]Post the output of "ping www.yahoo.com"
[*]Post the output of "sudo traceroute www.yahoo.com"
[*]Post the output of "cat /etc/resolv.conf"
[*]Post the output of "ifconfig -a"[/LIST]

---

### Post by fiveryanfrenzy on 2007-01-22
done... apt-get failed...

> 

rcalderoni@gabriel:~$ [COLOR="Red"]sudo apt-get install network-manager-gnome[/COLOR]
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dhcdbd libnl1-pre6 libnm-util0 network-manager
The following NEW packages will be installed:
  dhcdbd libnl1-pre6 libnm-util0 network-manager network-manager-gnome
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 726kB of archives.
After unpacking 2863kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main dhcdbd 1.14-2ubuntu2
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main libnl1-pre6 1.0~pre5+svn21-2ubuntu2
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main libnm-util0 0.6.3-2ubuntu6
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main network-manager 0.6.3-2ubuntu6
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main network-manager-gnome 0.6.3-2ubuntu6
  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/dhcdbd/dhcdbd_1.14-2ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/dhcdbd/dhcdbd_1.14-2ubuntu2_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libn/libnl/libnl1-pre6_1.0~pre5+svn21-2ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libn/libnl/libnl1-pre6_1.0~pre5+svn21-2ubuntu2_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-util0_0.6.3-2ubuntu6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-util0_0.6.3-2ubuntu6_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.6.3-2ubuntu6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.6.3-2ubuntu6_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager-gnome_0.6.3-2ubuntu6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager-gnome_0.6.3-2ubuntu6_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
rcalderoni@gabriel:~$ [COLOR="Red"]route -n[/COLOR]
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
rcalderoni@gabriel:~$ [COLOR="Red"]ping [www.yahoo.com](www.yahoo.com)[/COLOR]
ping: unknown host [www.yahoo.com](www.yahoo.com)
rcalderoni@gabriel:~$ [COLOR="Red"]sudo traceroute [www.yahoo.com](www.yahoo.com)[/COLOR]
sudo: traceroute: command not found
rcalderoni@gabriel:~$ [COLOR="Red"]cat /etc/resolv.conf[/COLOR]
search hsd1.va.comcast.net.
nameserver 68.87.73.242
nameserver 68.87.71.226
rcalderoni@gabriel:~$ [COLOR="Red"]ifconfig -a[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:11:25:D2:89:0B  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169 

eth1      Link encap:Ethernet  HWaddr 00:12:F0:B6:1C:B7  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:36 errors:0 dropped:7 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:66 Base address:0x8000 Memory:b4001000-b4001fff 

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)




now what?

---

### Post by mrpeanut on 2007-01-22
Did you hand the connections over to NetworkManager?  To check go to System -> Administration -> Networking and then check the properties of each connection and make sure that "Enable this connection" is unchecked.  This will enable NetworkManager to take over the duties.  From there you should be able to reboot your computer and when you log back in NetworkManager should now be in charge of your connections.

---

### Post by fiveryanfrenzy on 2007-01-22
fixed it, all i had to do was add 'auto eth0' and 'auto eth1' before their iface and settings on the interface file.

---

