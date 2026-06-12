---
title: "Ubuntu 16.04 - Where is IP4.ADDRESS set and/or stored?"
date: 2018-07-21
forum: Networking &amp; Wireless
---

### Post by ralph+shnelvar on 2018-07-21
This question is related to [https://ubuntuforums.org/showthread.php?t=2396848&p=13785680#post13785680](https://ubuntuforums.org/showthread.php?t=2396848&p=13785680#post13785680)

In Ubuntu 16.04 when I issue an ifconfig I get
```

ens33     Link encap:Ethernet  HWaddr 00:50:56:23:5e:09 
          inet addr:192.168.29.205  Bcast:192.168.29.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fe23:5e09/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:172509 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:17885761 (17.8 MB)  TX bytes:329267 (329.2 KB)
 
lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4393 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4393 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:1545500 (1.5 MB)  TX bytes:1545500 (1.5 MB)


```

And if I issue nmcli dev show ens33
```

GENERAL.DEVICE:                         ens33
GENERAL.TYPE:                           ethernet
GENERAL.HWADDR:                         00:50:56:23:5E:09
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.CONNECTION:                     --
GENERAL.CON-PATH:                       --
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.29.205/24
IP4.GATEWAY:                            192.168.29.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP6.ADDRESS[1]:                         fe80::250:56ff:fe23:5e09/64
IP6.GATEWAY:                           

```

My /etc/network/interfaces file is
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
 
source /etc/network/interfaces.d/*
 
# The loopback network interface
auto lo
iface lo inet loopback
 
# The primary network interface
auto ens33
iface ens33 inet dhcp

```


In my ASUS router I do port forwarding so I can host my own website from my own computer running Ubuntu 16.04.

I just don't remember what I did so as to set my ip address to 192.168.29.205.

I'm attempting to replicate this behavior in 18.04.

Help is appreciated.

---

### Post by chili555 on 2018-07-21
May I assume this is a desktop machine and not a server? In Ubuntu 18.04, the netplan file reads:```
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager

```In other words, Network Manager is the place to set the static IP address.

[http://i.imgur.com/Sqh8P.png](http://i.imgur.com/Sqh8P.png)

---

### Post by The Cog on 2018-07-21
It looks to me as though you were using DHCP. In which case yoru router was configured to issue that IP address to the old machine's MAC address when it issued a DHCP request.
If you are just replacing the server then you probably want to change the DHCP entry in your router so it gives the 192.168.29.205 IP address to your new box instead.
Or give the new box a new IP address and edit the port forwarding to point to the new box.

---

### Post by ralph+shnelvar on 2018-07-21
The way I built this server (it is the same machine that used to run 16.04 so the MAC address is the same, i.e. 00:50:56:23:5e:09) is I installed ubuntu-18.04-live-server-amd64.iso. I then did a

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-desktop
```

to install a desktop.  I find this far far more convenient than working from only a command line.  Other than having the (small?) cpu overhead and disk space for the desktop, I see no other downsides to having it.


So I checked my ASUS TM-AC1900 router and I have 00:50:56:23:5E:09 assigned to 192.168.29.205.


If I have the following for /etc/netplan/50-cloud-init.yaml
```

# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: networkd
  ethernets:
    ens33:
     dhcp4: yes
     gateway4: 192.168.29.1
     nameservers:
       addresses: [8.8.8.8,8.8.4.4]

```

and then reboot Ubuntu 18.04
and then issue a
[FONT=courier new]nmcli dev show ens33[/FONT],
I then get
```

GENERAL.DEVICE:                         ens33
GENERAL.TYPE:                           ethernet
GENERAL.HWADDR:                         00:50:56:23:5E:09
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.CONNECTION:                     --
GENERAL.CON-PATH:                       --
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.80.170/24
IP4.GATEWAY:                            192.168.80.2
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.80.2, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.80.0/24, nh = 0.0.0.0, mt = 0
IP4.ROUTE[3]:                           dst = 192.168.80.2/32, nh = 0.0.0.0, mt = 100
IP6.ADDRESS[1]:                         fe80::250:56ff:fe23:5e09/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[2]:                           dst = ff00::/8, nh = ::, mt = 256, table=255

```

As one can see, the gateway is wrong (192.168.80.2 instead of 192.168.29.1) and the ip address is wrong (192.168.80.170 instead of 192.168.29.205).

What am I doing wrong?


And, of course, thank you to both chili555 and The Cog.

---

### Post by chili555 on 2018-07-21
> As one can see, the gateway is wrong (192.168.80.2 instead of 192.168.29.1) and the ip address is wrong (192.168.80.170 instead of 192.168.29.205).
Before you proceed, please verify the address of the router and the range of other connected devices. Is it x.80 or x.29?

If this is not a cloud instance, and I suspect it is not, I'd change the yaml file as I describe here: [https://askubuntu.com/questions/1051655/convert-etc-network-interfaces-to-netplan/1052141#1052141](https://askubuntu.com/questions/1051655/convert-etc-network-interfaces-to-netplan/1052141#1052141)

If you want the address to be static, then the yaml file would read:```
network:
  version: 2
  renderer: networkd
  ethernets:
    ens33:
      addresses:
        - 192.168.29.205/24
      gateway4: 192.168.29.1
      nameservers:
          addresses: [192.168.29.1, 8.8.8.8]
```Spacing, indentation, etc. are crucial and must be exact. Proofread carefully twice. 
Now do:

```
sudo netplan apply
```
Reboot.

---

### Post by ralph+shnelvar on 2018-07-21
[IMG]https://drive.google.com/open?id=1Bwh8O_lV6m0CRj3p-9QMlrWnzmIEPo0_[/IMG]

As you can see:
my router (i.e. the gateway) is at [http://192.168.29.1](http://192.168.29.1).
DHCP is turned on.
My MAC address is 00:50:56:23:5E:09 and points to 192.168.29.205

I will now follow your suggestion for the yaml file and ... Progress has been made!

ifconfig and nmcli now return
```

ens33: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.29.205  netmask 255.255.255.0  broadcast 192.168.29.255
        inet6 fe80::250:56ff:fe23:5e09  prefixlen 64  scopeid 0x20<link>
        ether 00:50:56:23:5e:09  txqueuelen 1000  (Ethernet)
        RX packets 1767  bytes 111097 (111.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 147  bytes 11960 (11.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 538  bytes 65396 (65.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 538  bytes 65396 (65.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

*nmcli dev show ens33*
GENERAL.DEVICE:                         ens33
GENERAL.TYPE:                           ethernet
GENERAL.HWADDR:                         00:50:56:23:5E:09
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.CONNECTION:                     --
GENERAL.CON-PATH:                       --
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.29.205/24
IP4.GATEWAY:                            192.168.29.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.29.1, mt = 0
IP4.ROUTE[2]:                           dst = 192.168.29.0/24, nh = 0.0.0.0, mt = 0
IP6.ADDRESS[1]:                         fe80::250:56ff:fe23:5e09/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[2]:                           dst = ff00::/8, nh = ::, mt = 256, table=255

```

Which I belive to be correct.

Now I can access index.html from within the Ubuntu machine via Firefox but ...
when I attempt to access the page from Firefox on windows on a different machine the request times out.

I suspect my problem is now a nameserver problem related to using no-ip.com


		chili555 you clearly know what you are doing. Would you be interested in doing a bit of *paid *consulting for me in order for me to actually connect to the internet?  If you are (or even if you aren't) please contact me at **ralphs at dos32.com**.

---

### Post by chili555 on 2018-07-21
I am happy to help anyone in the context of a forum post. I cannot accept any payment as my only job is to make sure I don't need to have a job!> Now I can access index.html from within the Ubuntu machine via Firefox but ...
when I attempt to access the page from Firefox on windows on a different machine the request times out.
This sounds like an apache issue to me, a subject that I know almost nothing about.

I assume that you have the needed IP address and that you can access the internet with the server:```
ping -c3 www.google.com
```

---

### Post by ralph+shnelvar on 2018-07-22
[**[COLOR=#DD4814][B]chili555**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=35909"), I want to thank you for your help.  Sadly, I need more help.

[SIZE=4]**I can reach Google with the following but Apache does not work both locally and remotely**[/SIZE]
In the version below the index.html page that Apache points to does not come up in Firefox.

When I have in /etc/hosts
(Please note the possible error in "www. mydomain.com" where I seem to have an embedded blank.)
```

127.0.0.1    localhost mydomain.com
# 127.0.1.1    ubuntu-server-2016-11-28-001


192.168.80.170  mydomain.com
192.168.80.170  www. mydomain.com


# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

and in [FONT=Calibri]/etc/netplan/50-cloud-init.yaml
```

# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    ethernets:
        ens33:
            addresses: []
            dhcp4: true
            optional: true
    version: 2

```
I can get to Google with no problem.


[B][SIZE=4][SIZE=4]I fail to get to Google with the following but Apache works locally but not remotely.[/SIZE]
[/SIZE][/B]In the version below the index.html page that Apache points to is coming up correctly in Firefox.

(Please note I removed the blank in "www.mydomain.com" below.)
[/FONT][FONT=Calibri]/etc/hosts
```

127.0.0.1    localhost mydomain.com
# 127.0.1.1    ubuntu-server-2016-11-28-001


192.168.29.205  mydomain.com
192.168.29.205  www.mydomain.com


# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
[/FONT]
[FONT=Calibri]/etc/netplan/50-cloud-init.yaml[/FONT]
```

# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: networkd
  ethernets:
    ens33:
      addresses:
        - 192.168.29.205/24
      gateway4: 192.168.29.1
      nameservers:
          addresses: [192.168.29.1, 8.8.8.8]

```


I have tried several variations of /etc/netplan/50-cloud-init.yaml . 

dhcp4: true

 dhcp4: true
optional: true

dhcp4: false

All to no avail.

N.B. I have done
  **[FONT=century gothic]sudo netplan apply --debug[/FONT]**
and a reboot after every change to /etc/netplan/50-cloud-init.yaml

**[SIZE=4]Questions:[/SIZE]**
What am I doing wrong? Is there another file I need to set to get this to work?

---

### Post by chili555 on 2018-07-22
I'm sorry. As I said, I know almost nothing about apache. I suggest that you transfer this information to a new question with apache in the title to attract the expertise of those who understand it better than me.

My supposed specialty is to get a driver associated with the hardware and get it configured to connect to the internet. All of the other magic, apache, LAMP, virtual machines, bridging, VLANs, cloud, etc., are beyond me.

---

### Post by ralph+shnelvar on 2018-07-22
chili55, I thank you but let me pester you a bit more.

Let's ignore Apache completely.  I suspect when I get ping working accessing my website will fall right into place.

So let's focus on why I can't do a
ping -c3 [www.google.com]("http://www.google.com")

I get
```

mydomain@ubuntu07:~$ ping -c3 www.google.com
PING www.google.com (172.217.2.4) 56(84) bytes of data.
From mydomain.com (192.168.29.205) icmp_seq=1 Destination Host Unreachable
From mydomain.com (192.168.29.205) icmp_seq=2 Destination Host Unreachable
From mydomain.com (192.168.29.205) icmp_seq=3 Destination Host Unreachable

--- www.google.com ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2003ms
pipe 2

```

My configuration at the moment is
[FONT=Calibri]/etc/netplan/50-cloud-init.yaml[/FONT]
```

# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: networkd
  ethernets:
    ens33:
      addresses: [192.168.29.205/24]
      dhcp4: true
      gateway4: 192.168.29.1
      nameservers:
          addresses: [192.168.29.1, 8.8.8.8]

```

```

127.0.0.1              localhost mydomain.com
# 127.0.1.1            ubuntu-server-2016-11-28-001
 
 
192.168.29.205  mydomain.com
192.168.29.205  www.mydomain.com
 
 
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

And as further background:
```

mydomain@ubuntu07:~$ networkctl status ens33
&#9679; 2: ens33
       Link File: /lib/systemd/network/99-default.link
    Network File: /run/systemd/network/10-netplan-ens33.network
            Type: ether
           State: routable (configured)
            Path: pci-0000:02:01.0
          Driver: e1000
          Vendor: Intel Corporation
           Model: 82545EM Gigabit Ethernet Controller (Copper) (PRO/1000 MT Single Port Adapter)
      HW Address: 00:50:56:23:5e:09 (VMware, Inc.)
         Address: 192.168.29.205
                  192.168.80.170
                  fe80::250:56ff:fe23:5e09
         Gateway: 192.168.29.1
                  192.168.80.2 (VMware, Inc.)
             DNS: 192.168.29.1
                  8.8.8.8
                  192.168.80.2
  Search Domains: localdomain

```

In summary, from my Ubuntu server:
I can connect to:

[LIST]
[*][http://192.168.29.205/](http://192.168.29.205/)
[*][http://www.bestrealestatecommissions.com/](http://www.bestrealestatecommissions.com/)
[*][http://bestrealestatecommissions.com/](http://bestrealestatecommissions.com/)
[/LIST]
I cannot connect to:

[LIST]
[*]Google
[*][http://192.168.80.170/](http://192.168.80.170/)
[*][http://192.168.80.2/](http://192.168.80.2/)
[*][http://192.168.29.1/](http://192.168.29.1/)
[/LIST]

Any thoughts? Should dhcp be true?

Oh, yes, I'm running Ubuntu in a VMWare VM hosted on Windows 7.

---

### Post by chili555 on 2018-07-22
> Any thoughts? Should dhcp be true?
Not if you want a static address. See my example above.

What, exactly, is [http://192.168.80.170/](http://192.168.80.170/) and why do you want to reach it?

I doin't think you shoud eliminate the 127.0.1.1 line in /etc/hosts. For comparison, my hosts file reads, in part:```
127.0.0.1       localhost
127.0.1.1       T440p

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```Where T440p is the name of my computer and agrees with:```
cat /etc/hostname
```> mydomain@ubuntu07This suggests that the hostname is ubuntu07. I believe that should be reflected in hosts opposite 127.0.1.1.

Please make some corrections, test and I'll check in tomorrow.

---

### Post by ralph+shnelvar on 2018-07-23
[**[COLOR=#DD4814][B]chili555**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=35909"), I want to say thank you so very much for your help.

As usual, when one cannot find a bug, one is likely looking in the wrong place.

I was so frustrated at not being able to track down why things were not working on 18.04 I reinstalled 16.04.

Things did not work in 16.04.  Huh?  I have another machine running 16.04 where everything works.

All the stuff **in **my new 16.04 was nearly identical to the 16.04 on my other machine.  A real head scratcher.

After pulling out the last strands of hair on my head I found the problem.  It was in the VMWare setup of the network adapter.  Specifically, on the machine that works, I had the adapter set to bridged.   On the one that was giving bizarre results the network adapter was set to NAT.

Again, chili55, I thank you for your time and effort.  I hope all of this helps others.

---

