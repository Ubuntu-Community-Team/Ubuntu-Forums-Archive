---
title: "no internet access, ping fail, local access only"
date: 2014-06-23
forum: Networking &amp; Wireless
---

### Post by axetone on 2014-06-23
Hi,
I am running Ubuntu 12.04.4 LTS (Precise), and I have set a static IP (172.16.0.101/24), to wit I can only connect/ping locally (i.e. to my LAN, but no internet).


Below are my specific configurations; Ping does not hit anything (via ip-numeric and hostname wise). All other devices on my DMZ are able to access outside (wan) just fine. I am using a cisco appliance as a gw/fw...~its only running ip routes/vlans...all ports forwarding from inside to outside (so should be no issues on gw/fw).


Thank you (in advance) for assisting - below is my console output;

```

-------------------------------------------
:::::::::::::::::::::::::::::::::::
less /etc/network/interfaces
:::::::::::::::::::::::::::::::::::
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
address 172.16.0.101
netmask 255.255.255.0
gateway 172.16.0.1


:::::::::::::::::::::::::::::::::::
less /etc/resolv.conf
:::::::::::::::::::::::::::::::::::
nameserver 8.8.8.8


:::::::::::::::::::::::::::::::::::
route -n
:::::::::::::::::::::::::::::::::::
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 172.16.0.1 0.0.0.0 UG 100 0 0 eth0
172.16.0.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0


:::::::::::::::::::::::::::::::::::
iptables -L
:::::::::::::::::::::::::::::::::::
Chain INPUT (policy ACCEPT)
target prot opt source destination
Chain FORWARD (policy ACCEPT)
target prot opt source destination
Chain OUTPUT (policy ACCEPT)
target prot opt source destination
-------------------------------------------


...
~$ ping -c 4 [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
~$ ping 74.125.228.51
PING 74.125.228.51 (74.125.228.51) 56(84) bytes of data.
^C
--- 74.125.228.51 ping statistics ---
12 packets transmitted, 0 received, 100% packet loss, time 11087ms
```

---

### Post by Bucky Ball on 2014-06-23
Welcome. Better. Please do not post output like that in post #1. It won't get you much support. Also, please use ```
 tags [ /code]. Retains all formatting and easy to read. ;)

I have added them to your last post as an example.

When you click the network icon and 'Edit>Wireless>your wireless connection, make sure you have IPv6 tab set to 'ignore'. Do you have DNS IPs set under the IPv4 tab?

PS: Make this:

[CODE]# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
address 172.16.0.101
netmask 255.255.255.0
gateway 172.16.0.1
```

This:

```
# The loopback network interface
auto lo
iface lo inet loopback
```

That's all you need. Let Network Manager take care of it. I run static IPs on all my machines and no longer use the setup you are using (slightly different on my 12.04 install, I'll just have a look at what I'm using there). Could you also give us the output of:

```
sudo lshw -C network
```

Thanks.

* Update: Just checking 12.04 and I knew it was different. Make /etc/network/interfaces look like this:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto wlan0
iface eth0 inet dhcp
```

... where 'wlan0' is your wireless card.

---

### Post by axetone on 2014-06-23
Bucky Ball,
   I am not running a GUI and I am not running wireless. Thank you for letting me know about the code tag though...~fyi, this site does not allow me to delete my posting...guessing because I'm new(?).

Any other ideas (#non-gui / #non-dhcp)?

---

### Post by axetone on 2014-06-23
output of "[COLOR=#000000][FONT=Ubuntu Mono]lshw -C network"[/FONT][/COLOR]:

```

  *-network
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:13:20:bd:14:62
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full ip=172.16.0.101 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:feaff000-feafffff ioport:ddc0(size=64)

```

---

### Post by Iowan on 2014-06-23
> **axetone said:**
> ...~fyi, this site does not allow me to delete my posting...guessing because I'm new(?).

You can edit your posts, but only staff can delete them... actually, we usually just move them to a holding area called "the jail".
You can use the "Report Post" button to  request a post/thread be moved.

---

### Post by axetone on 2014-06-23
Lowan,
   Thank you for confirming only admins can quarantine. I just didn't want anyone thinking I'd leave a long-string-post like that. I do still need help resolving this though so please don't delete it -but if you can delete that first posting -that'd be helpful!
-axetone

---

### Post by axetone on 2014-06-23
Update: I noticed that when issuing the route command by itself there is nothing in the route table, also same when issuing route -Cn, _**HOWEVER**_ route -n...comes up with gateway info...-this doesn't make sense to me ...~I've tried restarting/booting...no joy -still cannot hit the internet;

```

~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
<no output, just hangs>
^C


~$ route -Cn
Kernel IP routing cache


~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.16.0.1      0.0.0.0         UG    100    0        0 eth0
172.16.0.0      0.0.0.0         255.255.255.0   U     0      0        0 eth0

```

---

### Post by axetone on 2014-06-23
Update:
I completely reloaded the server, simple generic install ...this is still not pinging anything out on the internet. I've checked my firewall, I do see packets leaving but nothing being returned/denied...very very confused.

```

auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
        address 172.16.0.101
        netmask 255.255.255.0
        network 172.16.0.0
        broadcast 172.16.0.255
        gateway 172.16.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 8.8.8.8

```

---

### Post by Bucky Ball on 2014-06-23
In that case, just use this:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

... in /etc/network/interfaces. All the tweaking you're doing there is probably just complicating things.

If you have your static address set up correctly in Network Manager, the above is ALL you will need in 12.04 ...

Also, I have a sneaking suspicion you have no IPs set for DNS, or the wrong IPs.

```
 # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 8.8.8.8
```

You need to insert them manually and you haven't answered that question. Am I correct? If not, try with the IP of your router. Ideally, the DNS IPs would be provided by your ISP. Check your ISP and use them if you can (they usually provide two).

---

### Post by axetone on 2014-06-23
Bucky,
   I appreciate your advice but I'm not going to be using the GUI and therefore not going to load/use Network Manager. This being a completely fresh install of Ubuntu I have not edited anything, just filled in the prompts of the installer...so everything in the Ubuntu configuration you see above is all default stuff.

That said I have taken another look at my firewall and noted that packets sent from my DMZ (internal network 1 /vlan12, where this Ubuntu box sits) are not returning here but are in-fact being returned to my INSIDE network (internal network 2 / vlan1). I know my Ubuntu server is in the correct vlan12/port physically on the firewall...~but what I don't know is if the source packets being sent (pings) from the Ubuntu server somehow have a default vlan1 assignment that would over-ride the vlan12 port configuration of the firewall?  ...as that would cause the routers return session ID to interpret it as needing to be sent to my INSIDE network instead of the DMZ/vlan12 from where it actually sourced. Anyway, I'm just not sure at this point. I will however update everyone when I figure this out.

 k/r -axetone

---

### Post by axetone on 2014-06-24
It appears that the packets I had seen going back to the INSIDE (10's network) was from another device that was pinging out the saame time I was...~so there was no firewall mis-configuration. To verify this, I also ran a sniff with wireshark (see attached)...what appears now is that the Ubuntu server says it's transmitting ping packets but they are _**NOT being see on the network at all**_! All that was seen from the Ubuntu box was the ssh traffic. Now I'm really lost for why this box is not talking out the interface other than ssh? Is it possible that the basic OS installer (when selecting only SSH during install, ie NOT Lamp, mail, etc. etc) is the problem?

I am truly confused...-but what I'm seeing is (1) a base OS install with basic IP configuration (only selecting SSH during install) not doing anything BUT ssh on the network!

...reminder: please see attached.

---

### Post by Bucky Ball on 2014-06-24
Please do not insert large images in the body of your posts. Attached them by Adv Reply and the paperclip icon or Go Advanced when editing a post and paperclip icon. Thanks.

---

### Post by axetone on 2014-06-24
_***RESOLVED:***_ Bad OS Installation (assumed). Detail of correct parameters for network configuration at bottom of notes.

_***SYNOPSIS:***_
System was sending out bad ip packets which caused loss of network connectivity. Initial triage through eth0 parameters showed no specific mal-configuration. troubleshooting included;
   1. Modification of /etc/network/interfaces
   2. Modification of /etc/hosts
   3. Modification of /etc/hostname
   4. Modification of /etc/resolv.conf  (fyi -not recommended but for immediate TEMPORARY testing).
   5. Physical move to port in another network/vlan to test both Static & DHCP assignment(s).
   6. Re-install with no components (i.e., no ssh, no Lamp selected, etc. etc.)
   7. Re-install with no components _***AND no domain-name***_.

_***RESOLUTION:***_
   It appears that during the initial installation of the Ubuntu (12.04.4 Precise) operating system, it suffered some unknown/not-found corruption. The only item ***selected*** ***at this time of initial install*** was the SSH server component, and entering of the public domain name. The server was operational initially, and then, when changing from a dynamic IP to a static IP the system never recovered network access. Upon re-install, no selection of any OS compnents (i.e. ssh, Lamp, etc.) were selected but doamin-name was entered. System was not functional with static IP assignment, dhcp assignment was not tested on the second load (as in the essence of time I needed to get this to a base install and just start from there).

The third install had no components selected, and no domain name entered. It was booted running DHCP and everything worked fine. Additionally, when changing to a static IP again there were no further problems. Ping and DNS worked accordingly.

Below are the only configuration file changes when changing to static IP, everything works. Hoe this helps!!
Code:
```

------------------------------
less /etc/network/interfaces


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
    address 172.16.0.15
    netmask 255.255.255.0
    gateway 172.16.0.1
    dns-nameservers 8.8.8.8


------------------------------
less /etc/hosts


127.0.0.1       localhost
127.0.0.1       wildweb


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


------------------------------
less /etc/resolv.conf  **_(informational ONLY! Do NOT edit this except for temporary use as it gets over written!)_**
nameserver 8.8.8.8

```

---

### Post by Bucky Ball on 2014-06-24
Excellent news. Please mark as solved from Thread Tools at the top right of this page to help future travelers. Enjoy. ;)

---

