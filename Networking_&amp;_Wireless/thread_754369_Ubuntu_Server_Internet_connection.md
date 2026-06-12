---
title: "Ubuntu Server Internet connection"
date: 2008-04-13
forum: Networking &amp; Wireless
---

### Post by sndnichols on 2008-04-13
Hey all. I am new to Ubuntu, but not computers. I understand a little of command prompt stuff from DOS experience 20  years ago, so all is not unfamiliar. I can say it is great to come to the light:) 

The problem I am having is baffling me. I installed server 7.10 yesterday on a home built server. The mobo is a TYAN s2915WA2NRF-E, (2) AMD 2350 Processors (quad core), 8G RAM, 1TB sata 3 HD. The install went well, no hardware problems.I connect t o the internet via cable modem through a DHCP router. I also have internet phone. All devices are assigned a static IP by the router so I can basically use the desktop as a server for files and printing. I set it up as a LAMP server during the install. I then ran apt-get install sshOpenServer, and apt-get install Samba. Again, all went well. I am using cable to connect to the internet. I have a laptop running Vista and a desktop running XP Pro connected to the router (DLink 614+). The server was NOT connected to the router at install. After the install was completed, I connected the server. (Dopey me didn't have enough network cables) I have gone in and configured etc/network/interfaces and etc/resolv.conf according to every help I could find here, sourceforge, etc. I am able to access the server from the laptop and the desktop through Samba. I can also ping both the Laptop and the desktop from the server. I cannot, however, access the internet from the server. I can (obviously) accesss the internet form other locations. I would be happy to post the readouts from the server when running ifconfig, netstat or others, but I don't know how to get them from the screen to a file. I also ran modprobe via-rhine, and nothing happened. If there is a way to print the screen to one of the Samba folders, I can access it from here, but I don't kno how to do it. TIA for any help

---

### Post by sndnichols on 2008-04-13
Well, I can't figure out how to print the screen so here comes some typing.I ran ifconfig -a and received this output:```
eth0  Link encap:Ethernet  HWaddr  XX:XX:XX
                                        inet6 addr: xxxxx /64 Scope:Link
                                        UP BROADCAST RUNNING MULTIAST   MTU:1500  Metric:1
                                        RX packets:10154  errors:0  dropped:0  overruns:0  frame:0
                                        TX packets:272  errors:0  dropped:0  overruns:0  carrier:0
                                        collisions:0  txqueuelen:1000
                                        RX bytes:2650084 (2.5MB)  TX bytes:33862 (33.0 KB)
                                        Interrupt:18

                                eth1  Link encap:Ethernet  HWaddr  XX:XX:XX
                                         BROADCAST RUNNING MULTIAST   MTU:1500  Metric:1
                                         RX packets:0  errors:0  dropped:0  overruns:0  frame:0
                                        TX packets:0  errors:0  dropped:0  overruns:0  carrier:0
                                        collisions:0  txqueuelen:1000
                                        RX bytes:0 (0MB)  TX bytes:0 (0 b)
                                        Interrupt:17  Base address:0x2000

                                 lo     Link encap:Local loopback
                                         inet addr:127.0.0.1  Mask:255.0.0.0
                                         inet6 addr:  ::1/128  Scope:Host
                                         RX packets:0  errors:0  dropped:0  overruns:0  frame:0
                                        TX packets:0  errors:0  dropped:0  overruns:0  carrier:0
                                        collisions:0  txqueuelen:1000
                                        RX bytes:0 (0MB)  TX bytes:0 (0 b)
```

The MAC addresses are vailable if necessary, but tI can ping the server using them.

Thanks

---

### Post by sndnichols on 2008-04-13
OK, I ran modprobe via-rhine and then dhclient eth0. The results are:

```
There is already a pid file /var/run/dhclient.pid with pid 5614
            killed old client process, removed PID file
            Internet Systems Consrtium DHCP Client V3.0.5
            Copyright 2004-2006  Internet Systems Consortium
            All rights reserved.
            For info, please visit http://www.isc.org/sw/dhcp
          
            Listening on LPF/eth0/ mac address
            Sending on LPF/eth0/mac address
            Sending on Socket/fallback
            DHCPDISCOVER on eth0 to 255255.255.255 port 67 interval 8
            DHCPDISCOVER on eth0 to 255255.255.255 port 67 interval 12
            DHCPDISCOVER on eth0 to 255255.255.255 port 67 interval 11
            No DHCPOFFERS received
            No working leases in persistent database - seeping
```

There is that.

---

### Post by sndnichols on 2008-04-13
The /etc/network/interfaces file looks like this:

```
#The loopback network interface
             auto lo
             iface lo inet loopback
             address  127.0.0.1
             netmask  255.0.0.0

              #The primary network interface
               auto eth0
               iface eth0 inet static
                        address  192.168.0.101
                        netmask  255.255.255.0
                        network  192.168.0.0
                        broadcast  192.168.0.255
                        gateway  192.168.0.1
```

That part.

---

### Post by sndnichols on 2008-04-13
Here is the /etc/resolve.conf file:

```
search  www.rr.com
            nameserver 24.28.199.142
```

---

### Post by sndnichols on 2008-04-13
The /etc/hosts file looks like this:

```
127.0.0.1              localhost
            127.0.1.1              BAB
            192.68.0.1            Gateway
            192.168.0.102      Desktop
            192.168.0.103      Laptop


            # The following lines are desirable for IPv6 capable hosts
             ::1            ip6-localhost   ip6-loopback
             fe00::0  ip6-localnet
             ff00::0  ip6-ncastprefix
             ff02::1  ip6-allmodes
             ff02::2  ip6-lallrouters
             ff02::3  ip6-allhosts
```

If there is something else I should show, please let me know.

---

### Post by sndnichols on 2008-04-14
Bump

---

### Post by superprash2003 on 2008-04-14
is eth0 or eth1 connected to the internet? type ping google.com and post results here..could be a DNS problem

---

### Post by sndnichols on 2008-04-14
Superprash,

The server is connected to a Dlink 614+ router through eth0. The router is connected to a Motorola surfboard cable modem. The desktop is connected to the same router and the laptop is connected wirelessly to the same router. They both can get o the internet. I was thinking the problem may be the resolv.conf file. I am not 100% sure that I have the correct address. I got it from ipconfig on the desktop running XP pro SP2.  Posting the result exactly form pinging "outside" will have to waut, since I will be working for the next 6 hours, but asically any ping I sent "outside" came back as no such place. Another thing I am noticing is that there is no ip4 address for eth0 in ifconfig??.

---

### Post by superprash2003 on 2008-04-14
right.. try manually entering an ip by typing ifconfig eth0 192.168.1.10 (for example, considering your router ip is 192.168.1.1 ,change accordingly)

---

### Post by sndnichols on 2008-04-14
eth0 now has an ip4 address(192.168.0.101). It didn't change anything else, though.  Pinging google.com results in an answer of ping:unknown host"

I tried ping 192.168.0.1 nad the result is:```
rootBAB:# ping -c 5 192.168.0.1
                                                                                            PING 192.168.0.1 (192.168.0.1)  56(84) bytes
                                                                                              --- 192,168.0.1 pig stastics---
                                                                                             5 Packets transmitted, 0 received, 100 packet loss, time 3999ms  
```. 

Pinging the laptop and desktop through the router works. I am officially lost.

---

### Post by sndnichols on 2008-04-14
I ran:```
root@BAB:/# netstat -r
                     Kernel IP routing table
                     Destination      Gateway        Genmask             Flags     MSS  Window  irtt  iface
                     192.168.0.0     *                  255.255.255.0       U           0          0         0    eth0
                      defult              Gateway       0.0.0.0                  UG         0          0         0    eth0
```

---

### Post by Iowan on 2008-04-14
> **sndnichols said:**
> Well, I can't figure out how to print the screen so here comes some typing.Are you using the CTRL-ALT-F1 terminal - or the terminal Application?  If Terminal Application, you should be able to copy by click/drag/highlighting the text you want, then copying with Shift-CTRL-C (or use the COPY option under EDIT).

I presume the **hosts** file output was a typo: > 127.0.1.1              BAB
            192[COLOR="Red"].68[/COLOR].0.1            Gateway
            192.168.0.102      Desktop
            192.168.0.103      Laptop

---

### Post by sndnichols on 2008-04-14
I am running only from the command line.  I wouldn't mind running from a GUI, but I can't get one without the web:(

The .68 was a typo. I looed at my router info and it gives, in the WAN section

IP Address          76.177.97.137
Subnet Mask           255.255.248.0
Default Gateway     76.177.96.1
DNS      24.94.163.110 24.94.163.111

This is a differet IP from what I get running ipconfig from this machine. I changed to the one above in resolv.conf, but it didn't work either.

Do you think it would be a good idea to just do a clean install with the server connected to the router, or keep trying to figure this out? I don't mind either way. i think it may help others to follow this, as I have learned from other threads here, but it may take time to walk me through this.

---

### Post by sndnichols on 2008-04-15
bump

---

### Post by sndnichols on 2008-04-15
Please everyone, before you waste the valuable time of the people here, be sure to check the settings on our firewall. Sometimes the simpelest things are the problem. MAC fiters should be updated if you are using them:oops::oops::oops::  

I appreciate the help y'all offered. I certainly learned more about networking.

EDIT- How does one mark a problem solved?  Thanks

---

### Post by Iowan on 2008-04-16
It's an option under **Thread Tools**

---

