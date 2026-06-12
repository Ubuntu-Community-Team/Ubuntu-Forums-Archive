---
title: "Ubuntu 13.10 Network setup."
date: 2014-01-16
forum: Networking &amp; Wireless
---

### Post by cchat on 2014-01-16
I have a wired lan to communicate with a couple of Windows computers in my home (Win Vista and Win XP) using Samba. I have used Samba in the past, but its been several years.  My purpose is to be able to communicate through the wired lan for sharing windows and application files while learning Ubuntu so that I can migrate to the Ubuntu platform for primary use.  Probably eventually dual booting my other computers to use Ubuntu as my primary system on all three.

I loaded 13.10 and it went flawlessly (after a couple false starts).  My only internet connection is through a tablet that shares its source and the wireless was detected and connected without a hitch.  (I live out in the country, no DSL or cable available, only my tablet or satellite internet here.)  Unfortunately the wired network service was not so smooth.  Would not communicate and could not "ping" other computers and a printer on the wired net.  

After reading many articles about how easy it is to set up NetworkManager and dnsmasq I attempted to get it working with NetworkManager since I figured the GUI interface would make it easier.  Wrong!  Still problems.  

I then tried to go through dnsmasq and set it up instead.  Disabled NM and attempted to set up dnsmasq on the eth0 interface.  First could not get pings to work then figured out the DHCP in the tablet was claiming 192.168.0. for its addressing space.  I changed and set up the dnsmasq to set its server at 192.168.100.1 and with a range of 192.169.100.1 -192.169.100.100 .  That at least got ping to work to both the local devices and to the tablet/internet server as well. (Computers actually use static IP assignments). I even got the Windows computer to recognize that the Ubuntu machine existed with its network name, but no communication with the Samba shares.  

Unfortunately I have still been unable to get dnsmasq to work.  Of late every version of the dnsmasq.conf file I try gets an error msg that it couldn't open 127.0.0.1 for lookups - busy when I attempt to restart dnsmasq using init.d.  I have tried building the config file from several different examples from several sources.  I am not trying to get it to serve internet assets, only the local domain at 192.168.100.* on the eth0 interface.  I can not believe that this is such an unusual task.  

Anyone have a similar system that actually works? Can you point me in the easiest direction for a Ubuntu nubie?

---

### Post by SJR Dorset on 2014-01-17
It could be that the UFW firewall is blocking your Samba shares.

I had a similar problem when trying to access Samba shares from my Tablet. I fixed the problem by allowing access to Samba shares with the following terminal command:

[FONT=Ubuntu Mono]sudo ufw allow Samba

[/FONT]

---

### Post by cchat on 2014-01-18
Don't think the answer is in Samba.  Can't ping on the eth0 port.

OK.  Settled on using dnsmasq to configure this mess.  Researched the setup of the /etc/dnsmasq.conf file and got something that I thought would work based on about a dozen articles about it.  Then tried to start dnsmasq and got this:

```
chuck@Ubuntu:~$ sudo /etc/init.d/dnsmasq restart
[sudo] password for chuck: 
 * Restarting DNS forwarder and DHCP server dnsmasq              
dnsmasq: failed to create listening socket for 127.0.0.1: Address already in use
```

Wireless is running and giving me an internet connection.  I can ping servers on the wireless connection, but nothing on the eth0 connection.  ifconfig gives me this:
```
chuck@Ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:21:d2:d1:51  
          inet6 addr: fe80::219:21ff:fed2:d151/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:542 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15821 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:141348 (141.3 KB)  TX bytes:3335098 (3.3 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2067 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2067 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:203147 (203.1 KB)  TX bytes:203147 (203.1 KB)

wlan0     Link encap:Ethernet  HWaddr 94:44:52:70:68:6c  
          inet addr:192.168.43.245  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: 2600:100b:b111:9d78:144d:3475:2028:4fb1/64 Scope:Global
          inet6 addr: 2600:100b:b111:9d78:9644:52ff:fe70:686c/64 Scope:Global
          inet6 addr: fe80::9644:52ff:fe70:686c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8440 errors:0 dropped:4743 overruns:0 frame:0
          TX packets:8377 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5241854 (5.2 MB)  TX bytes:1607711 (1.6 MB)
```

Eth0 has no dns data wihich is understandable.  Lo is defined at 127.0.0.1 and my wireless lan connection from a wireless tablet/router has dns.  Hosts file has localhost defined.  NetworkManager.conf has "dns=dnsmasq" and  "managed=false" after the [ifupdown] header.  

What could be causing the dnsmasq startup error? Do I have to deactivate the wireless to get this to run?
Thanks
Chuck

---

