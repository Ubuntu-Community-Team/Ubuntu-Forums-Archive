---
title: "So I'm switching from wireless to wired connections, need some assistance"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by jms1989 on 2008-09-29
Hi, I need some help with my little problem.

I am currently trying to switch from wireless to wired connections and I'm have a little difficulty configuring my server to working the new ip address.

Desired IP:
Mom's PC: 192.168.2.2

The following are connected to a switch that's connected to the router. 
My PC: 192.168.2.3
Sister's PC: 192.168.2.4
Server: 192.168.2.50


The Modem uses 192.168.1.254 and the router uses 192.168.2.1.

I've ben working on this for several hours now and gotten little progress on the server. I've edited /etc/dhcp3/dhclient.conf, /etc/network/interfaces, and /etc/resolv.conf.

My Ubuntu PC seems to not like to use static ip address on the wired connection but works fine with dhcp. However, when I boot another OS, like windows or a live cd, they work fine but I want to try to fix ubuntu before I attempt to reinstall to fix any bugs.

dhclient.conf
```

# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
nameserver 192.168.2.1;
nameserver 192.168.1.97;

lease {
interface "eth0";
fixed-address 192.168.2.50;
option subnet-mask 255.255.255.0;
option gateway 192.168.2.1
expire 0 2030/12/31 11:59:59;
}

```

interfaces
```

auto lo
iface lo inet loopback

iface eth0 inet static
auto eth0
address 192.168.2.50
netmask 255.255.255.0
gateway 192.168.2.1

#iface eth0 inet static
#address 192.168.2.100
#netmask 255.255.255.0
#gateway 192.168.2.254

```

Please help, thank you.

---

### Post by superprash2003 on 2008-09-29
are you able to ping 192.168.2.1 when static ip is assigned?

---

### Post by jms1989 on 2008-09-29
Yes, on both the server and my computer. The other machines are happy now. When I ping 192.168.1.254, I get network is unreachable on the server.

---

### Post by Iowan on 2008-09-29
It would seem that the router isn't routing from this machine to modem.

---

### Post by jms1989 on 2008-09-29
It appears that way. I use MAC address filtering and have added the server's network cards MAC address to the router and still nothing. It allows all the other computers but not the server. Also, I am unsure whether or not the dns setting are working and I hove no gui to work with and I'm not sure where the dns entries are located at.

Here is the output of ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:50:FC:8E:84:17  
          inet addr:192.168.2.50  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::250:fcff:fe8e:8417/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:217 errors:0 dropped:0 overruns:0 frame:0
          TX packets:172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25637 (25.0 KB)  TX bytes:24892 (24.3 KB)
          Interrupt:10 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1520 (1.4 KB)  TX bytes:1520 (1.4 KB)

```

Right now, I have to manually tell it to connect to its IP to gain any access at all. I have the settings saved in the two files posted in my first post.

---

### Post by Iowan on 2008-09-29
Is 192.168.2.3 a Windows or Linux machine?  Is it working - what does it have for DNS?  IF it works, and DNS is set for 192.168.2.1, add the following line to your **/etc/network/interfaces** file: ```
 dns-nameservers 192.168.2.1
```  It really shouldn't affect ability to ping via address, though. What is output from **route**command?

---

### Post by jms1989 on 2008-09-29
192.168.2.3 is both a windows machine and a linux machine, defaults to ubuntu linux. It works fine with dhcp but not with a static ip address.

I added that line to the server and restarted the networking service but it still can't ping the modem (192.168.1.254).

I use 192.168.2.1 and 192.168.1.97 as the dns server. Both IP address point to the router.

Output of route on my pc:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.194.0    *               255.255.255.0   U     0      0        0 vmnet8
192.168.103.0   *               255.255.255.0   U     0      0        0 vmnet1
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.2.1     0.0.0.0         UG    100    0        0 eth0

```

Output of route on the server:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0

```

---

### Post by jms1989 on 2008-09-30
I found a thread about a dude that is having trouble connecting to the net and in the thread, I found a command that enabled access to the internet from my server.

Below is the two commands I must execute to get online, the first to connect to the network.
```

sudo ifconfig eth0 192.168.2.50
sudo route add default gw 192.168.2.1 eth0

```

Now the output of **route** is:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth0

```

Now how can make the configuration perminant so that it loads and connects automaticly from bootup? Something must be missing in my configuration and it not loading the correct data to connect. Hmm...

---

### Post by jms1989 on 2008-09-30
Execellent, by comparing configurations with my working computer and the server, I managed to get the settings saved at the right place and by rebooting, I saw that my settings where working. Its website loaded with a simple refresh and I didn't have to execute the two commands in the above post. The interface define is in the interfaces file, I removed the extra stuff in **dhclient.conf**, and the nameserver define is in the **resolv.conf** file. The internet now works on the compaq.

Now to figure out the deal with static ips on my ubuntu (192.168.2.3) and my wireless issue. I can live without the wireless as I'm switching over to wired connections. So, I wonder why my ubuntu won't work right with a static ip set.

---

