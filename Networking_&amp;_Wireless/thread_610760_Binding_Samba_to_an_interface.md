---
title: "Binding Samba to an interface"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by RudolfMDLT on 2007-11-12
Hi there,

I'm trying to bind Samba to eth0 and/or to 10.0.0.0 network. Nothing I try works. After I installed VMware it binds to one of those ipranges. I've now forced it over to 10.0.0.0 but now I see nothing? How is the setting supposed to look? the man page for samba is pretty crap too.

Thanks,

Rudolf

---

### Post by RudolfMDLT on 2007-11-13
I don't know if anybody else has found this but the longer I use Ubuntu, the more complex the problems become and the less support you get on the forums! LOL! bugger...

Anyway, this is what I tried with no succes:

> #### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
[COLOR="Red"] interfaces = 10.0.0.0 / eth0[/COLOR]

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
   bind interfaces only = true




> [COLOR="Red"] interfaces = eth0[/COLOR]


> [COLOR="Red"]interfaces = 10.0.0.0/8
[/COLOR]


> [COLOR="Red"]interfaces = 10.0.0.0/24
[/COLOR]

Can some one please help me and tell me what am I not understanding or doing wrong! Thanks for any help! :)

Rudolf

---

### Post by mpokrywka on 2007-11-13
I don't know if I understood you correctly, but are you are running vmware under ubuntu?
You said "it binds to one of those ipranges" - I didn't run vmvare under ubuntu but I suppose it uses tap0 device?
Samba binds to specific addresses/interfaces at startup so if samba starts and later vmware creates tap device, then configuration with "bind interfaces only" won't work.
Also if addresses specified in "interfaces" line do not exist at samba startup, then samba ignores them.
I see 2 solutions:
1) restart samba (sudo /etc/init.d/samba restart) after starting vmware so that ip address specified in config already exists (btw. add "lo" interface to your "interface" line)
2) use "bind interfaces only = no" and comment your "interface" line - and samba will listen on all interfaces even not existing while starting samba (you may need to use iptables firewall if you need to tighten access to samba resources)

also you can use:
```
sudo netstat -tunlp | grep bd
```
to see where samba daemons listen for connections

---

### Post by RudolfMDLT on 2007-11-15
Thank you for the reply! :)

I am running VMware, when I type "ifconfig" this is the output:

> rudolf@Rudolf:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:D1:17:B5:61  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe17:b561/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51829 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17814 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37213098 (35.4 MB)  TX bytes:1592839 (1.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:258 errors:0 dropped:0 overruns:0 frame:0
          TX packets:258 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15583 (15.2 KB)  TX bytes:15583 (15.2 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.187.1  Bcast:172.16.187.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.57.1  Bcast:192.168.57.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Now, I have commented out my changes to the "bind interfaces section" and this is what your command outputs:

> rudolf@Rudolf:~$ sudo netstat -tunlp | grep bd
[sudo] password for rudolf:
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     15696/smbd          
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     15696/smbd          
udp        0      0 10.0.0.4:137            0.0.0.0:*                          15694/nmbd          
udp        0      0 172.16.187.1:137        0.0.0.0:*                          15694/nmbd          
udp        0      0 192.168.57.1:137        0.0.0.0:*                          15694/nmbd          
udp        0      0 0.0.0.0:137             0.0.0.0:*                          15694/nmbd          
udp        0      0 10.0.0.4:138            0.0.0.0:*                          15694/nmbd          
udp        0      0 172.16.187.1:138        0.0.0.0:*                          15694/nmbd          
udp        0      0 192.168.57.1:138        0.0.0.0:*                          15694/nmbd          
udp        0      0 0.0.0.0:138             0.0.0.0:*                          15694/nmbd  

Now, before I installed VMware, using "sudo smbtree" would be able to see all the machines running windows or Samba on the network. Now I get this:

> rudolf@Rudolf:~$ sudo smbtree
Password: 
Packet send failed to 172.16.187.255(137) ERRNO=Operation not permitted
Packet send failed to 192.168.57.255(137) ERRNO=Operation not permitted
Packet send failed to 172.16.187.255(137) ERRNO=Operation not permitted
Packet send failed to 192.168.57.255(137) ERRNO=Operation not permitted
Packet send failed to 172.16.187.255(137) ERRNO=Operation not permitted
Packet send failed to 192.168.57.255(137) ERRNO=Operation not permitted


Which led me to believe that the VMware interfaces where to blame.

I still can't browse the network Also, when in the run dialog I type: cmb://hh or smb://backup the names don't work anymore. Only the IP address work. I am on the right work group. 

I can live with using IP's but I need to install a printer. Before I installed VMware, Gnome was able to search and install a windows shared printer with the GUI under Administration, but now it only finds an empty work group.

Any advice you could give? I would greatly appreciate any help!

I did not understand what you meant by "adding lo" in front of interfaces?

Thanks,

Rudolf

---

### Post by RudolfMDLT on 2007-11-15
Just and Update - no computer can see my computer. they can ping my pc but not even the VMware XP can see my shared files.

---

