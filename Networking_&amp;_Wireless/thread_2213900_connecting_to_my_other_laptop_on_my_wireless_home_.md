---
title: "connecting to my other laptop on my wireless home network"
date: 2014-03-29
forum: Networking &amp; Wireless
---

### Post by tomaasj on 2014-03-29
Dear Community,

I am sure it has been addressed previously but after extensive searching I was not able to find the answer I need.

The situation:

at home I have a ADSL modem/router.  Through this ADSL modem three laptops are able to access the internet independently.

All laptops run Ubuntu (12.04).

I know it is possible to access the other laptops using a GUI through Desktop Sharing and Remina Remote Desktop client.

But I want to access them through the terminal using the ping command or by ftp or SSH or something similar.

I checked the /etc/hosts files of my laptops.  They all have this IP address : 127.0.1.1 and their name I assigned once I set up the operating system.

Like the graphical user interface clients I mentioned earlier, I must be able to access these laptops through my terminal as well, I guess, without setting up more hardware, or servers and such.

I should be able to assign my laptops unique IP numbers and make them connect with each other using the terminal.  More and more I am using the terminal and reading a lot on this and trying to educate myself.  I would like to dive into networking and try to get familiar with linux commands to access my little network.

How to go about this ?  And is this possible ?

Tomaasj

---

### Post by steeldriver on 2014-03-29
If they are connected via a router, the laptops will each already have a unique (unique within your local network) IP number - the 127.0.1.1 address is just a local "loopback" address used for certain internal services.

To see the actual LAN IP addresses from a terminal, you can use the **ifconfig** command or - if the laptops all use the GUI network manager, **nm-tool**. You should be able to ping each of those IP addresses from each of the others right now without additional software. To establish command line terminal sessions between the computers the most common way would be to install SSH server software (package **openssh-server**) on each one - then you can do stuff like

```

**steeldriver@lap-t61p:~$ ssh 192.168.1.102**
steeldriver@192.168.1.102's password: 
Welcome to Ubuntu 12.04.4 LTS (GNU/Linux 3.2.0-60-generic-pae i686)

 * Documentation:  https://help.ubuntu.com/

  System information as of Sat Mar 29 12:46:10 UTC 2014

  System load:  0.02              Processes:           113
  Usage of /:   7.2% of 88.50GB   Users logged in:     1
  Memory usage: 5%                IP address for eth0: 192.168.1.102
  Swap usage:   0%

  Graph this data and manage this system at:
    https://landscape.canonical.com/

18 packages can be updated.
0 updates are security updates.

Last login: Thu Mar 27 14:12:37 2014 from 192.168.1.2
[B]steeldriver@think60p:~$ 
[/B]
```

You will also likely be able to use host names with the avahi '.local' suffix instead of having to remember the numeric IPs - like

```

ssh *hostname*.local

ssh *username*@*hostname*.local

```

---

### Post by tomaasj on 2014-03-29
Thanks,

so what we did (neighbour got involved) is to check for the ip addresses of both laptops in my own home network using the ifconfig command.  Both laptops A and B are connected wirelessly to the ADSL modem.

laptop A: 192.168.1.6

Laptop B: 192.168.1.11

We were not able to ping the addresses.  However, we took one of the laptops and used the ethernet cabel to physically attach the laptop to the ADSL modem.  We were now able to ping the addresses.  We do not understand why the ping command does not work when the laptops are not physically attached to the ADSL modem but have wireless working.

We connected wirelessly to the network of my neighbour.  Also through his ADSL we were not able to ping the addresses (obtained athrough the ifconfig command entered on both laptops).

Can you elaborate on this ?

Tomaasj

---

### Post by steeldriver on 2014-03-29
Are you sure both laptops are connected to the same LAN (private local network) when you are using wireless? Check the nm-tool output carefully to see what wireless SSID each is connected to (should be indicated by an asterisk *) or use the nmcli command

```
nmcli dev wifi list | awk '$NF ~ /yes/ {print}'
```

Connecting via a different LAN (e.g. your neighbour's network) will involve quite a few more steps (inclduing finding the **public **IP and forwarding ports on the router(s))

---

### Post by tomaasj on 2014-03-29
OK,

laptop A: outout of the terminal command:   nmcli dev wifi list | awk '$NF ~ /yes/ {print}'     is:

'Theresa'                         00:1E:8C:47:44:08   Infrastructure   2437 MHz   54 MB/s    81       WPA WPA2   yes

Theresa is the name of the wifi spot in my home.

The output is the same for laptop B except that the number is not 81 but 74

Tomaasj

---

### Post by untrustytahr on 2014-03-29
Some wireless access points have a 'feature' called AP Isolation (a.k.a client isolation, station isolation).  It's a form of security that prevents wireless clients from communicating with each other and would need to be disabled in order to communicate.  It is also closly related to the 'guest -wifi' option that some access points provide.  Look in your router/access point documentation for such a feature.

---

### Post by tomaasj on 2014-03-29
Hallo untrustytahr,

my ADSL is [http://wiki.openwrt.org/toh/davolink/dv-2020](http://wiki.openwrt.org/toh/davolink/dv-2020)

Could you point out to me were I can find this feature ?

Tomaasj

---

### Post by tomaasj on 2014-03-29
We tested two laptops within a network with additional computers not running Ubuntu.  Only the Ubuntu ones are not able to communicate with each other.  So, it must not be a problem with the modem.  It must be a setting somewhere within the Ubuntu OS preventing them to communicate within the described context.

Where is this setting located ?

Tomaasj

---

### Post by steeldriver on 2014-03-29
There is nothing by default that I'm aware of that would prevent pings between hosts on the same LAN segment in Ubuntu (although it would be possible to configure iptables to drop ICMP packets I think).

Can you post the whole ifconfig outputs (i.e. not just the IP addresses) of the 2 machines when connected via wireless? it's possible there's something in the netmask setings that's preventing it. 

```
ifconfig
```

Also the output of the 'route' command on each machine

```
route -n
```

If you could please use [CODE] tags around the terminal code like I have done that would make it easier to read

---

### Post by tomaasj on 2014-03-29
Thanks for taking your time with this.

See below the output of Laptop B:


```
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 24:b6:fd:0d:f2:89  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 

eth1      Link encap:Ethernet  HWaddr e4:d5:3d:e5:83:bd  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e6d5:3dff:fee5:83bd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22407 errors:7 dropped:0 overruns:0 frame:80164
          TX packets:16895 errors:8 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25096301 (25.0 MB)  TX bytes:2212052 (2.2 MB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:830 errors:0 dropped:0 overruns:0 frame:0
          TX packets:830 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:76856 (76.8 KB)  TX bytes:76856 (76.8 KB)

```

```
~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1

```

---

### Post by tomaasj on 2014-03-29
Below you find the output of ifconfig and route -n for laptop A:


```
~$ ifconfig ; route -n
eth0      Link encap:Ethernet  HWaddr 00:19:b9:74:4e:82  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:139 errors:0 dropped:0 overruns:0 frame:0
          TX packets:139 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12006 (12.0 KB)  TX bytes:12006 (12.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:7e:53:b8:42  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:7eff:fe53:b842/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:452 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:130735 (130.7 KB)  TX bytes:67217 (67.2 KB)

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

```

---

### Post by tomaasj on 2014-03-29
...

After extensively searching the net and playing around with remote desktop client Remmina, I happened to install xrdp: An open source remote desktop protocol(rdp) server. See below:

```
sudo apt-get install xrdp
```

[http://www.xrdp.org/](http://www.xrdp.org/)

Somehow, ping-ing both laptops A to B and vice versa, using the ip addresses obtained with the ifconfig command on both laptops respectively, seems to work.

What happened ?

:confused:

---

