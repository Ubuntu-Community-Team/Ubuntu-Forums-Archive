---
title: "Suddenly Unable to Obtain IP via DHCP"
date: 2016-04-10
forum: Networking &amp; Wireless
---

### Post by insomniac2 on 2016-04-10
I have an Ubuntu Server 14.04 installation. It has been running fine for 3 weeks. It is set up as a VM using QEMU (specifically on a QNAP NAS).

On Friday evening I installed LAMP using:

```
sudo apt-get install lamp-server^
```

There were no problems. I set up a database. The next morning I installed RoundCube from a tarball (just unpacked into /var/www/html) and configured it and was able to access it without issue over HTTP.

Later that day my problem started. I first noticed my e-mail client could not connect to the mail server and that I could no longer load RoundCube. I logged in and the MOTD was updated from a few hours before with some updates being available.

I tried:

```
ip addr

...
2: eth0 <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 52:54:00:57:10:64 brd ff:ff:ff:ff:ff:ff
    inet6 fe80:5054:ff:fe57:1064/64 scope link
       valid_lft forever preferred_lft forever
```

I tried:

```
sudo dhclient -v eth0

Internet Systems Consortium DHCP Client 4.2.4
...

Listening on LPF/eth0/52:54:00:57:10:64
Sending on   LPF/eth0/52:54:00:57:10:64
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x685e9559)
... (DHCPDISCOVER repeats 26 more time with different intervals)
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

On boot it hangs for a bit and eventually says:

 ```
Waiting for network configuration...
Waiting up to 60 more seconds for network configuration...
Booting system without full network configuration...
```

Troubleshooting I tried was to restart Ubuntu. Restart the NAS which is running QEMU. Reboot the router. None of those things made a difference. This morning I created a new Ubuntu VM and it obtained an IP no problem during install and has one now. I can take that eth0 up and down and it gets a DHCP lease no issue like the other did before. So it does seem to be a problem specific to this instance not a broader issue.

Here are some common items requested by helpful forum members:

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 52:54:00:57:10:64
          inet6 addr: fe80::5054:ff:fe57:1064/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:215 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27680 (27.6 KB)  TX bytes:10062 (10.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4244 (4.2 KB)  TX bytes:4244 (4.2 KB)
```

/etc/network/interfaces
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

lshw -C network
```
*-network
       description: Ethernet interface
       product: 82450EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 03
       serial: 52:54:00:57:10:64
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:11 memory:feba0000-febbffff ioport:c000(size=64) memory:febc0000-febdffff
```

I can only guess something that was installed as part of the LAMP stack caused a problem, but I don't know what. I also am guessing everything seemed OK until the DHCP lease went to renew. Any help is greatly appreciated. Thanks!

---

### Post by TheFu on 2016-04-10
etho is wrong.
eth0 is correct.

Fix that inside the interfaces file and restart networking.

---

### Post by insomniac2 on 2016-04-10
> **TheFu said:**
> etho is wrong.
eth0 is correct.

Fix that inside the interfaces file and restart networking.

Ohh gosh I wish that was it! That's a typo on my part (I had to type it all since I can only connect via VNC without an IP!). I fixed the typo. That file hasn't been edited in a couple weeks.

---

### Post by TheFu on 2016-04-10
garbage in/garbage out.

If it is a "server" then it needs a static IP.  I'd just set that.

BTW, I don't think apache listens on the public interface by default. After you set the static IP, tell apache to listen on it.
I don't know much about qnap - didn't know they supported being a VM host - most other VM hosts would require setting up a bridge on the host. Guess that had to have been working.

---

### Post by insomniac2 on 2016-04-10
> **TheFu said:**
> garbage in/garbage out.

If it is a "server" then it needs a static IP.  I'd just set that.

BTW, I don't think apache listens on the public interface by default. After you set the static IP, tell apache to listen on it.
I don't know much about qnap - didn't know they supported being a VM host - most other VM hosts would require setting up a bridge on the host. Guess that had to have been working.

I'll look at that, it was the next thing I was thinking, just seems so odd that it just "broke". It is a "server". I stood it up to set up an IMAP server and RoundCube to backup my e-mail. It's getting old moving it between clients/OS/laptops and IMAP will be around a long time.

RE: QNAP. They have some models that support Virtualization through the Virtualization Station application which is running QEMU underneath. You do set up a Virtual Switch which can then be bridged. Once you get it figured out, it's pretty nice.

---

### Post by insomniac2 on 2016-04-10
No luck with a static IP. I can't ping/nslookup anything. Odd thing is that the client is listed in my router with the right IP. My updated /etc/network/interfaces:

```
# The loopback network interfaceauto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.7.10
    netmask 255.255.255.0
    gateway 192.168.7.1
    dns-nameservers 192.168.7.1
```

The nameserver is also in /etc/resolv.conf (automatically placed there, I didn't edit the file).

---

### Post by lisati on 2016-04-10
> **insomniac2 said:**
> No luck with a static IP. I can't ping/nslookup anything. Odd thing is that the client is listed in my router with the right IP. 
When I was running my own server several years ago, I found it easier to reserve an IP address on my router, rather than mess around with the contents of /etc/network/interfaces, partly on the basis that its the router's job to hand out IP addresses. Have you looked at that as an option?

---

### Post by insomniac2 on 2016-04-10
> **lisati said:**
> When I was running my own server several years ago, I found it easier to reserve an IP address on my router, rather than mess around with the contents of /etc/network/interfaces, partly on the basis that its the router's job to hand out IP addresses. Have you looked at that as an option?

I think the problem there is that still relies on DHCP, it's just the router assigns it the same IP that you told it to assign. I use that method on a couple machines on my network. It seems like something was fundamentally broken and I was hoping it was something obvious/simple. It doesn't appear to be a DHCP vs static issue. I'm not sure how a virtual interface can fail either. What could be blocking outgoing traffic on the interface?

---

### Post by TheFu on 2016-04-10
Seems like a virtualization question specific to qemu (which I'm weak at).  I can help if virtualbox, ESX, ESXi, KVM, or Xen were involved.  Think this isn't about the client VM, but the hostOS.   The KVM and Xen solutions both allow (and I always used) normal Linux bridges. I never use the automatically created bridges after being burned a few times with flakey results. That was a long time ago, but my habit of manually creating the bridges stands - never any issues.

I also use DHCP reservations for portable devices, but NEVER, NEVER, EVER for servers.  If my router is down, there's no need to impact services running on the LAN over an IP issue. Static IPs don't care if there's a DHCP server available or not.

You showed the new interfaces file, but not that it was used and it is working. Please show that. If it isn't working - seems like a hostOS issue to me.
[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) is my wired network troubleshooter. Doubt there is anything there you don't know already, but perhaps ... 

Have you checked the QNAP forums for solutions? Is this a common issue?

---

### Post by insomniac2 on 2016-04-10
> **TheFu said:**
> Seems like a virtualization question specific to qemu (which I'm weak at).  I can help if virtualbox, ESX, ESXi, KVM, or Xen were involved.  Think this isn't about the client VM, but the hostOS.   The KVM and Xen solutions both allow (and I always used) normal Linux bridges. I never use the automatically created bridges after being burned a few times with flakey results. That was a long time ago, but my habit of manually creating the bridges stands - never any issues.

I also use DHCP reservations for portable devices, but NEVER, NEVER, EVER for servers.  If my router is down, there's no need to impact services running on the LAN over an IP issue. Static IPs don't care if there's a DHCP server available or not.

You showed the new interfaces file, but not that it was used and it is working. Please show that. If it isn't working - seems like a hostOS issue to me.
[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) is my wired network troubleshooter. Doubt there is anything there you don't know already, but perhaps ... 

Have you checked the QNAP forums for solutions? Is this a common issue?

I tried to isolate and show it wasn't QEMU by setting up a new VM.  There were also no updates to the QNAP to cause a change. And as I said, it was fine for weeks and then this after the stuff I did in the first post. I can appreciate alternative ways (and probably better), but I want to stay within the provided framework so firmware updates don't also mean my setting stuff back up again or troubleshooting QNAP's stuff. On their support, it's not very good for me when I use it. I get bad advice like don't use NFS, use Samba (when dovecot says Samba is unlikely to work, and it sure didn't!) or the simpleset of questions like which Network Adapter should I use (5 choices) for Ubuntu that no one answers. I haven't seen any forum topics along these lines.

Here are the results of the commands plus a couple more for troubleshooting.

```
ip addr

...
2: eth0 <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 52:54:00:57:10:64 brd ff:ff:ff:ff:ff:ff
    inet 192.168.7.10/24 brd 192.168.7.255 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80:5054:ff:fe57:1064/64 scope link
       valid_lft forever preferred_lft forever
```

```
ifconfig

eth0      Link encap:Ethernet  HWaddr 52:54:00:57:10:64
          inet addr:192.168.7.10 Bcast:192.168.7.255 Mask:255.255.255.0
          inet6 addr: fe80::5054:ff:fe57:1064/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:169 errors:0 dropped:75 overruns:0 frame:0
          TX packets:73 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17693 (17.6 KB)  TX bytes:4608 (4.4 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:47 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4468 (4.4 KB)  TX bytes:4468 (4.4 KB)
```

```
ping -c 4 192.168.7.1

PING 192.168.7.1 (192.168.7.1) 56(84) bytes of data.
From 192.168.7.10 icmp_seq=1 Destination Host Unreachable
From 192.168.7.10 icmp_seq=2 Destination Host Unreachable
From 192.168.7.10 icmp_seq=3 Destination Host Unreachable
From 192.168.7.10 icmp_seq=4 Destination Host Unreachable

--- 192.168.7.1 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3008ms
pipe 3
```

```
ping -c 4 google.com

ping: unknown host google.com
```

```
route

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.7.1     0.0.0.0         UG    0      0        0 eth0
192.168.7.0     *               255.255.255.0   U     0      0        0 eth0
```

---

### Post by TheFu on 2016-04-11
Thanks for posting that stuff.  All looks fine. If the VM can't ping the router, I'd check the cable and switch/router ports next.  Inside a VM, if the hostOS networking is all still working fine, I'd look at
a) the bridge setup
b) the firewall setup
that's pretty much it.

And the QNAP itself has correct, similar (diff IP, same subnet) and working connectivity? 
It is just this VM with the issue? 
Set up a small VM and the networking there is working?  Asking so I don't assume any results.

Can you post the bridge settings?  

Can you just restore the system from the backup taken just prior to the update that broken things?  Or just check the diffs between that backup and the current settings? Sometimes that is handy too.

Don't use NFS?  From a storage vendor forum?  Yeah - I agree with your assessment. I'm in the "don't use samba unless no other choice exists" camp myself. If I just wanted samba, I'd get a $50 NAS, not an $800 one.  Ok, so my NAS is a $150 box with 9 disks (no HW RAID) around a G3258 Pentium running Ubuntu server for great flexibility, but ... 

```
brctl show
``` might help. And all the normal ifconfig stuff from the hostOS, please. It is probably fine, but ...

---

### Post by insomniac2 on 2016-04-11
> **TheFu said:**
> Thanks for posting that stuff.  All looks fine. If the VM can't ping the router, I'd check the cable and switch/router ports next.  Inside a VM, if the hostOS networking is all still working fine, I'd look at
a) the bridge setup
b) the firewall setup
that's pretty much it.

And the QNAP itself has correct, similar (diff IP, same subnet) and working connectivity? 
It is just this VM with the issue? 
Set up a small VM and the networking there is working?  Asking so I don't assume any results.

Can you post the bridge settings?  

Can you just restore the system from the backup taken just prior to the update that broken things?  Or just check the diffs between that backup and the current settings? Sometimes that is handy too.

Don't use NFS?  From a storage vendor forum?  Yeah - I agree with your assessment. I'm in the "don't use samba unless no other choice exists" camp myself. If I just wanted samba, I'd get a $50 NAS, not an $800 one.  Ok, so my NAS is a $150 box with 9 disks (no HW RAID) around a G3258 Pentium running Ubuntu server for great flexibility, but ... 

```
brctl show
``` might help. And all the normal ifconfig stuff from the hostOS, please. It is probably fine, but ...

I can confirm that the router is functioning fine. The QNAP NAS is fine, it is on the same subnet and I can get at it without issue. The only physical cable is from the NAS to the Router and it is functional since the NAS is fine. I also created a test VM with Ubuntu and it was able to get an IP using the same network setup, including the same virtual switch. Yesterday I also created a new instance to just replace the one that I'm having trouble with. This time I installed LAMP during the initial install menus and I set it all back up with the share mounted with NFS, dovecot and RoundCube. It's still working right now, we'll see if it can renew its lease.

Unfortunately I didn't take a snapshot of the VM before adding LAMP (lesson learned!). I think the QNAP forum has many good and well intentioned people, but I think the VM area, and specifically the actual OS stuff is better suited to get help from people who know instead of people who either have tried it or just do it the way they like/prefer.

I have a catch 22 on brctl. I can't run it because it's not installed and I can't install it because I can't connect to the internet. :) I'll have to see if I can get it somehow.

Here is everything from the NAS:

```
[~] # ip addr1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq master br0 state UP qlen 1000
    link/ether 00:08:9b:f6:88:25 brd ff:ff:ff:ff:ff:ff
3: eth1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN qlen 1000
    link/ether 00:08:9b:f6:88:26 brd ff:ff:ff:ff:ff:ff
4: bond0: <BROADCAST,MULTICAST,MASTER> mtu 1500 qdisc noop state DOWN
    link/ether 46:c3:3e:24:55:89 brd ff:ff:ff:ff:ff:ff
5: br0: <BROADCAST,MULTICAST,NOTRAILERS,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP
    link/ether 00:08:9b:f6:88:25 brd ff:ff:ff:ff:ff:ff
    inet 192.168.7.235/24 brd 192.168.7.255 scope global br0
       valid_lft forever preferred_lft forever
11: vnet0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UNKNOWN qlen 500
    link/ether fe:54:00:e9:4a:4e brd ff:ff:ff:ff:ff:ff
12: vnet1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UNKNOWN qlen 500
    link/ether fe:54:00:57:10:64 brd ff:ff:ff:ff:ff:ff
```

```
[~] # ifconfig
br0       Link encap:Ethernet  HWaddr 00:08:9B:F6:88:25
          inet addr:192.168.7.235  Bcast:192.168.7.255  Mask:255.255.255.0
          UP BROADCAST NOTRAILERS RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4404433 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3166556 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3521640589 (3.2 GiB)  TX bytes:2346961579 (2.1 GiB)


eth0      Link encap:Ethernet  HWaddr 00:08:9B:F6:88:25
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4525122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4060191 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3755471966 (3.4 GiB)  TX bytes:2403614720 (2.2 GiB)


eth1      Link encap:Ethernet  HWaddr 00:08:9B:F6:88:26
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:15638818 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15638818 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3021445042 (2.8 GiB)  TX bytes:3021445042 (2.8 GiB)


vnet0     Link encap:Ethernet  HWaddr FE:54:00:E9:4A:4E
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:207385 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:5143779 (4.9 MiB)  TX bytes:157794427 (150.4 MiB)


vnet1     Link encap:Ethernet  HWaddr FE:54:00:57:10:64
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:143 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68416 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:9000 (8.7 KiB)  TX bytes:12515952 (11.9 MiB)
```

```
[~] # cat /etc/network/interfaces
# Configure Loopback
auto lo
iface lo inet loopback
```

```
[~] # route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         router.asus.com 0.0.0.0         UG    0      0        0 br0
127.0.0.0       *               255.0.0.0       U     0      0        0 lo
192.168.7.0     *               255.255.255.0   U     0      0        0 br0
```

```
[~] # brctl show
bridge name     bridge id               STP enabled     interfaces
br0             8000.00089bf68825       no              eth0
                                                        vnet0
                                                        vnet1
```

---

### Post by TheFu on 2016-04-11
Thanks for all the network stuff from the hostOS.

Nothing is really jumping out .... except the router.asus.com name resolution bothers me. Seems like a bad idea if you don't work for asus, but it probably isn't important since router configs (gateway settings) are usually by IP, not a name.  If not, definitely fix that. Use IPs.

I have to admit, I've never done a "LAMP" install - not once in 20+ yrs.  I have installed the individual parts many times. Never liked many of the default settings. Haven't used apache or php or mysql in years.  Nginx, mariaDB/Postgres and Perl/Ruby are my poison now, though there are probably some php things running only available internally - none come to mind right now.

I'd still make the IP static - use the router DHCP reservations if you must, but I'd also come back with a static config.  Not reason for an internal-only service to be down just because the router is. Anything on layer2 should still have access. For my NAS, this isn't a big deal - backups and restoring the system settings isn't an issue. Happens daily, around 2am.

That's pretty much all the ideas I have. Sorry it isn't helpful.

---

### Post by insomniac2 on 2016-04-11
> **TheFu said:**
> Thanks for all the network stuff from the hostOS.

Nothing is really jumping out .... except the router.asus.com name resolution bothers me. Seems like a bad idea if you don't work for asus, but it probably isn't important since router configs (gateway settings) are usually by IP, not a name.  If not, definitely fix that. Use IPs.

I have to admit, I've never done a "LAMP" install - not once in 20+ yrs.  I have installed the individual parts many times. Never liked many of the default settings. Haven't used apache or php or mysql in years.  Nginx, mariaDB/Postgres and Perl/Ruby are my poison now, though there are probably some php things running only available internally - none come to mind right now.

I'd still make the IP static - use the router DHCP reservations if you must, but I'd also come back with a static config.  Not reason for an internal-only service to be down just because the router is. Anything on layer2 should still have access. For my NAS, this isn't a big deal - backups and restoring the system settings isn't an issue. Happens daily, around 2am.

That's pretty much all the ideas I have. Sorry it isn't helpful.

I think the NAS just picks all that stuff up. The Router is a home router, so if it breaks static or DHCP it won't matter all that much for the network.

I went with mostly what was needed. I needed the PHP for RoundCube and a DB as well. LAMP is so ubiquitous, you'd assume it would be easy enough to deploy. I've done the separate installs a while ago and editing all the .conf files is certainly not something I wanted to do now. It's an internal "server" that I really wanted to use to backup my e-mail long term so it's not eating up space on my devices and if for whatever reason GMail has some problem. I planned to spin it up when needed and leave it off otherwise.

I'll switch it over to a static IP at some point if it continues to be accessible, that makes sense. I should probably do the same for the NAS, but it resolves by name fine.

Ubuntu/Linux isn't my native OS. I use it often enough to kind of know what I'm doing but to also forget commands. I was hoping to identify the problem to learn/understand more. Just seems so odd what happened, eth0 seems hopelessly messed up.

I'm hopeful the new VM is all OK now and for whatever reason the LAMP install made some critical change via apt-get. All theories since the problem can't be found.

Thanks for trying to help me out.

---

### Post by TheFu on 2016-04-11
I don't think this is a Linux issue. I think it is a QNAP-funny-networking thing.  I've never seen what you've seen - ever.
It could have been a magical bug at almost any level - host, bridge, guest. No way to know without versioned backups to see what did and didn't change.

---

