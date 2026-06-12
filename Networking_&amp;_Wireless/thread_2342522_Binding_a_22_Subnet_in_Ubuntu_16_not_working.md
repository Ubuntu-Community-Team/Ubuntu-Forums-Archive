---
title: "Binding a /22 Subnet in Ubuntu 16 not working"
date: 2016-11-07
forum: Networking &amp; Wireless
---

### Post by Bashed on 2016-11-07
I'm trying to add *secondary* subnet, a /22 in Ubuntu 16 but the IPs don't ping despite proper routing at the switch level. **How do I properly bind the secondary /22 subnet (IPv4) and have these IPs ping?**

I can ping locally, but not from external. Below commands didn't work.

```
root@server:~# iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
root@server:~# iptables -A OUTPUT -p icmp --icmp-type echo-reply -j ACCEPT
```

Routing at the Cisco switch level is fine too:

```
interface Vlan100
 description Server xxx
 ip address xxx.xxx.16.1 255.255.252.0 secondary
 ip address xxx.xxx.105.41 255.255.255.248
```


/etc/network/interfaces shows something like this...

```
    # This file describes the network interfaces available on your system
    # and how to activate them. For more information, see interfaces(5). source /etc/network/interfaces.d/*

    # The loopback network interface
    auto lo
    iface lo inet loopback

    # The primary network interface
    auto eno1
    iface eno1 inet static
        address xxx.xxx.105.42
        netmask 255.255.255.248
        network xxx.xxx.105.40
        broadcast xxx.xxx.105.47
        gateway xxx.xxx.105.41
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 8.8.8.8 8.8.4.4
        dns-search mydomain.com

iface eno1 inet static
  address XXX.XXX.16.0/22
```

```
root@server:~# ifconfig |more
eno1      Link encap:Ethernet  HWaddr d4:be:d9:ed:fb:8a  
          inet addr:xxx.xxx.xxx.42  Bcast:xxx.xxx.xxx.47  Mask:255.255.255.248
          inet6 addr: fe80::d6be:d9ff:feed:fb8a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:457 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:478778 (478.7 KB)  TX bytes:467117 (467.1 KB)

eno1:0    Link encap:Ethernet  HWaddr d4:be:d9:ed:fb:8a  
          inet addr:xxx.xxx.16.1  Bcast:xxx.xxx.19.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
```

---

### Post by SeijiSensei on 2016-11-07
> iface eno1 inet static
  address XXX.XXX.16.0/22

You can't bind a subnet address to an interface.  You'd need to define a single address in the /22 and bind it instead.  

Try doing this manually with ifconfig using something like
```
sudo ifconfig eno1:0 xxx.xxx.16.1 netmask 255.255.252.0
```

Once you get it working with ifconfig, I'd just put the appropriate ifconfig and any associated route commands if needed in /etc/rc.local and forget about using /etc/network/interfaces.

---

### Post by Bashed on 2016-11-07
I'm confused here.

First, I reinstalled using Ubuntu 14 so now the interface is em1 not en0.

So I see this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto em1
iface em1 inet static
        address xxx.xxx.16.2
        netmask 255.255.252.0
        network xxx.xxx.16.0
        broadcast xxx.xxx.19.255
        gateway xxx.xxx.16.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 8.8.8.8 8.8.4.4
        dns-search domain.com
```


Nothing seems to happen when I do the below as you suggested. 

```
user@server:~$ sudo ifconfig em1:0 xxx.xxx.16.1 netmask 255.255.252.0


em1       Link encap:Ethernet  HWaddr d4:be:d9:ed:fb:8a  
          inet addr:xxx.xxx.16.2  Bcast:xxx.xxx.19.255  Mask:255.255.252.0
          inet6 addr: fe80::d6be:d9ff:feed:fb8a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24912 errors:0 dropped:0 overruns:0 frame:0
          TX packets:413 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1625119 (1.6 MB)  TX bytes:63316 (63.3 KB)

em1:0     Link encap:Ethernet  HWaddr d4:be:d9:ed:fb:8a  
          inet addr:xxx.xxx.16.1  Bcast:xxx.xxx.19.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
```


Still can't ping any IP except .2 only.

---

### Post by Bashed on 2016-11-07
> **SeijiSensei said:**
> Once you get it working with ifconfig, I'd just put the appropriate ifconfig and any associated route commands if needed in /etc/rc.local and forget about using /etc/network/interfaces.

What do you mean by this? What "appropriate ifconfig and any associated route commands" are you referring to?

---

### Post by SeijiSensei on 2016-11-07
First, what happened to the 
```
iface eno1 inet static
  address XXX.XXX.16.0/22
```
directive?  Did you remove it?

Next, you have
```
gateway xxx.xxx.16.1
```
Is that located upstream from this machine?  It appears from your first post that that address is on the Cisco.  If it already exists, you cannot assign 16.1 to the em1:0 interface.  Choose another IP for the virtual interface like 16.3.

Does the Cisco have a routing definition for xxx.xxx.16.0/22? I see a definition for a host at 16.1 but no routing statement.  Are there other directives on the Cisco you did not show us?  I'm not conversant in Cisco-ese so you'll have to figure this out yourself.  

If you want the machine at 16.2 to also support 16.3 and other addresses in the subnet using virtual interfaces, then the Cisco needs a routing command pointing 16.0/22 to the 16.2 address as the gateway for that subnet. 

On a Linux box I would use
```
/sbin/ip route add xxx.xxx.16.0/22 via xxx.xxx.16.2
```
You'd need the Cisco equivalent of that routing statement.

After you've set up the route, try using ifconfig to set em1:0 to 16.3.  Can you then ping that?

---

### Post by Bashed on 2016-11-07
Ok. Here we go. I installed Centos 6 for troubleshooting further on a different O/S. Same issue. So, I'm reinstalling the Ubuntu 16 as originally intended.

In the meantime...

```
Switch #1
ip route xxx.xxx.16.0 255.255.252.0 xxx.xxx.19.53 
```
(this points to .53 switch #2)

Switch #2
Switch2#show run int vlan 100
Building configuration...

Current configuration : 85 bytes
!
interface Vlan100
description Server 100
ip address xxx.xxx.16.1 255.255.252.0
end


**SWITCH #1**

```
Switch 1#ping xxx.xxx.16.2
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to xxx.xxx.16.2, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/2 ms

Switch 1#ping xxx.xxx.16.3
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to xxx.xxx.16.3, timeout is 2 seconds:
.....
Success rate is 0 percent (0/5)

```

**SWITCH #2**

```
Switch2#ping xxx.xxx.16.2
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to xxx.xxx.16.2, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/2 ms

Switch2#ping xxx.xxx.16.1
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to xxx.xxx.16.1, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 2/2/3 ms

Switch2#ping xxx.xxx.16.3
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to xxx.xxx.16.3, timeout is 2 seconds:
.....
Success rate is 0 percent (0/5)
```


**Traceroute**

Works only on .2, not the rest of the /22 subnet

**PLEASE EXPLAIN IN CLEAR, SIMPLIFIED STEP-BY-STEP...**how do I properly add the /22 (as primary) during installation? During install, it asks for the networking info since there's no DHCP but static so I give it the full proper /22 info, and gateway as .1 You're saying use any other number like .3? That means, I shouldn't have to bind after the install considering it's primary subnet?

---

### Post by SeijiSensei on 2016-11-07
I'm doing the best I can.  I have little experience with Ciscos, but I still think the problem lies there.
> 
Switch #2
Switch2#show run int vlan 100
Building configuration...

Current configuration : 85 bytes
!
interface Vlan100
description Server 100
ip address xxx.xxx.16.1 255.255.252.0
end

I still don't see a declaration of a route for xxx.xxx.16.0/22 there, only the 16.1 IP address. What if you add a routing statement to switch 2 like this:
```
ip route xxx.xxx.16.0 255.255.252.0 xxx.xxx.16.2
```

> **Bashed said:**
> how do I properly add the /22 (as primary) during installation? During install, it asks for the networking info since there's no DHCP but static so I give it the full proper /22 info, and gateway as .1 You're saying use any other number like .3? That means, I shouldn't have to bind after the install considering it's primary subnet?

I believe you're trying to have the machine at 16.2 also support additional IP addresses within the same subnet, right?  So one of the virtual addresses could be 16.3.  You can't really set up this stuff during installation, at least I never have.  I've done as you have done and configured the initial networking for one of the addresses like 16.1.  Then I use scripts with ifconfig commands that explicitly define the virtual interfaces.  Here's an example based on a script I've used at clients' sites:
```

#!/bin/bash
MASK=255.255.252.0
BC=xxx.xxx.19.255

# bring down the virtual interfaces just in case they have already been configured
ifconfig eth0:0 down
ifconfig eth0:1 down
ifconfig eth0:2 down
ifconfig eth0:3 down
ifconfig eth0:4 down

# assign IP addresses to each virtual interface
ifconfig eth0:0 xxx.xxx.16.240 netmask $MASK broadcast $BC
ifconfig eth0:1 xxx.xxx.16.241 netmask $MASK broadcast $BC
ifconfig eth0:2 xxx.xxx.16.242 netmask $MASK broadcast $BC
ifconfig eth0:3 xxx.xxx.16.243 netmask $MASK broadcast $BC
ifconfig eth0:4 xxx.xxx.16.244 netmask $MASK broadcast $BC


```
I run this script from /etc/rc.local so it is executed when the machine boots up but after networking is established.  This runs on a CentOS 6 machine so the interfaces are named "eth" rather than "eno" or other recent naming incarnations.  That gives me five virtual interfaces with addresses between 16.240 and 16.244.  The upstream router has a static route that sends the entire subnet to this host using the primary address, in your case 16.2.

---

### Post by Bashed on 2016-11-07
"I still don't see a declaration of a route for xxx.xxx.16.0/22 there,  only the 16.1 IP address. What if you add a routing statement to switch 2  like this:"

I think you misunderstood. The Cisco routing is setup to point to the secondary Cisco switch (.53 switch). The 252 netmask is the full /22

---

### Post by SeijiSensei on 2016-11-07
Yes, but switch 2 needs to have a routing declaration to know what to do with the traffic in the /22.  Both devices need routing statements.  The first one that you presented above sends traffic for the /22 to switch 2, but switch 2 needs to know where to send traffic for addresses in the subnet other than 16.1 and 16.2.  My understanding is you want all that traffic to go to the Linux host which has virtual interfaces for various addresses in that subnet.  Did you try adding the route I suggested to switch 2?  Did it help?

You cannot rely on Ethernet broadcasts to route this traffic correctly the same way you would on a regular LAN.  All the virtual interfaces will have the same MAC address, so there is no ARP table relating MACs to IPs the way there would be on a regular LAN where each host has a unique MAC address.  There's only one MAC address mapped to the 16.2 address.  The switch knows how to route traffic for 16.2 because it has an ARP entry for that IP address that is tied to the Linux host's MAC.  Without a routing statement on switch 2, I don't think it will know what to do with traffic for 16.3, 16.4, etc.

I'll check in again with this tomorrow morning.

---

### Post by Bashed on 2016-11-07
I just got off the phone with Cisco TAC. It's not a switch configuration issue, which I already knew but double confirmed. It's in Ubuntu. I need to bind the /22 somehow but between 12, 14, 16 it's so different how it's done. This is where I'm stuck.

For the record also, another client on the same switch using another /22 with Ubuntu 14 works fine for him. Same principle. /22 points from switch #1 to #2, and routed there same exact way.

```
auto eno1
iface eno1 inet static
        address xxx.xxx.16.2
        netmask 255.255.252.0
        network xxx.xxx.16.0
        broadcast xxx.xxx.19.255
        gateway xxx.xxx.16.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 8.8.8.8 8.8.4.4
        dns-search domain.com

iface eno1 inet static
        xxx.xxx.16.0/22
```

Then I get this:

root@server:~# sudo ifdown eno1 && sudo ifup eno1
/etc/network/interfaces:23: option with empty value
ifdown: couldn't read interfaces file "/etc/network/interfaces"

---

### Post by Bashed on 2016-11-07
Tried this method too...can't ping any IP but .1 and .2

```
root@server:~# ip addr add xxx.xxx.16.1/22 dev eno1
root@server:~# ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether d4:be:d9:ed:fb:8a brd ff:ff:ff:ff:ff:ff
    inet xxx.xxx.16.2/22 brd xxx.xxx.19.255 scope global eno1
       valid_lft forever preferred_lft forever
    inet xxx.xxx.16.1/22 scope global secondary eno1
       valid_lft forever preferred_lft forever
    inet6 fe80::d6be:d9ff:feed:fb8a/64 scope link 
       valid_lft forever preferred_lft forever
3: eno2: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether d4:be:d9:ed:fb:8c brd ff:ff:ff:ff:ff:ff
4: eno3: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether d4:be:d9:ed:fb:8e brd ff:ff:ff:ff:ff:ff
5: eno4: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether d4:be:d9:ed:fb:90 brd ff:ff:ff:ff:ff:ff
```

---

### Post by Bashed on 2016-11-08
I really need help here please

---

### Post by SeijiSensei on 2016-11-08
I'm out of suggestions if routing on the Cisco doesn't fix the problem.

---

### Post by Bashed on 2016-11-08
It wasn't related to the switches. I found out from the client the below. Anyone know how to do this via web and Excel?

> 
In interface file, you need to add the following lines per ip:

```

auto eno1:2
iface eno1:2 inet static
address xxx.xxx.16.3
netmask 255.255.252.0
```

and increase the number after : for each one

I just generate a list of all the ip's on the /22 using a free web tool and paste them in excel then i just write a quick formula in excel that creates the above string of 3 lines. Copy and paste in and done.


---

### Post by slickymaster on 2016-11-08
*Thread moved to **Networking & Wireless**.*

---

### Post by Bashed on 2016-11-09
Would appreciate insight on this please, on my last post.

---

### Post by SeijiSensei on 2016-11-10
That's the equivalent of the script I gave you [here](https://ubuntuforums.org/showthread.php?t=2342522&p=13567204&viewfull=1#post13567204).  It just puts the definitions for the virtual hosts in /etc/network/interfaces rather than creating them via a script in /etc/rc.local.

Since you only have to do this once, you can use a text editor to copy the stanza for the interfaces file over and over, then change the virtual interface numbers and IP addresses manually.  Alternatively you can run this bit of code at the command prompt to generate them for you:

```

for i in $(seq 3 254); do echo "auth eno1:$i
iface eno1:$i inet static
address xxx.xxx.16.$i                                                                               
netmask 255.255.252.0                                                                                       
                                                                                                            
"; done

```
That will generate the appropriate stanzas from 3-255.  Don't worry about the not having an eno1:2 interface this way.  It doesn't matter.  You can then copy them into the interfaces file.  Alternatively you can pipe them to a file and append that to the interfaces file like this:
```

for i in $(seq 3 254); do echo "auth eno1:$i
iface eno1:$i inet static
address xxx.xxx.16.$i                                                                               
netmask 255.255.252.0                                                                                       
                                                                                                            
" >> virthosts; done

```
That puts all the stanzas into the file virthosts in the current directory.

---

### Post by Bashed on 2016-11-22
I need to bind a bunch of /24 IPv4 subnets as secondary. The primary /29 is already set during the installation of Ubuntu 14x. How do I bind the remainder /24 subnets in one shot instead of individual single IPs one at a time?

I tried this method by adding the below line in /etc/network/interfaces but it didn't work?

>     up route add [-net|-host] <host/net>/<mask> gw <host/IP> dev <Interface>

    root@server:~# /etc/init.d/networking restart
    root@server:~#

I also tried this method too (below example, but did actual IPs and em1)

> for i in {1..128}; do echo iface eth1:$i inet static >> /etc/network/interfaces; echo address 192.168.0.$i >> /etc/network/interfaces; echo netmask 255.255.255.0 >> /etc/network/interfaces; echo auto eth1:$i >> /etc/network/interfaces; done

> root@server:~# service networking restart
stop: Job failed while stopping
start: Job is already running: networking
root@server:~# ifdown em1 && sudo ifup em1

IPs still don't ping however. They're 100% routed correctly on the Cisco switch though.

---

### Post by Bashed on 2016-11-22
I tried this  method of yours and it didn't work. IPs don't ping, they don't show up in ipconfig nor the networks file

> for i in $(seq 3 254); do echo "auth em1:$i iface em1:$i inet static address xxx.xxx.3.$i netmask 255.255.255.0"; done

I'm seriously stuck here. Running a new Ubuntu 14 server setup and can't get these multiple /24s routed right so they ping (static, permanent).

---

### Post by wildmanne39 on 2016-11-22
Please do not post duplicates, it dilutes community effort. Threads merged

---

### Post by Bashed on 2016-11-22
Sorry about that, it wasn't intentional. 

On a side note, this method below (aside IPs still not pinging, nor showing up in network interface file nor in ipconfig output)...this method ends up re-using em1:1 - 254 when I run the command on the next /24 subnets.

 	 		 			 			 				for i in $(seq 3 254); do echo "auth em1:$i iface em1:$i inet static address xxx.xxx.3.$i netmask 255.255.255.0"; done

---

### Post by Bashed on 2016-11-22
I might be confused here, but this is what I've done.

nano addips.sh

Add:

```
for i in {2..254}
        do ip addr add xxx.xxx.3.$i/24 dev em1
done

ip addr show
```

chmod +x addips.sh
sh addips.sh

Output something like this...

```
    inet xxx.xxx.3.232/24 scope global secondary em1
       valid_lft forever preferred_lft forever
    inet xxx.xxx.3.233/24 scope global secondary em1
       valid_lft forever preferred_lft forever
    inet xxx.xxx.3.234/24 scope global secondary em1
       valid_lft forever preferred_lft forever
    inet xxx.xxx.3.235/24 scope global secondary em1
       valid_lft forever preferred_lft forever
    inet xxx.xxx.3.236/24 scope global secondary em1
       valid_lft forever preferred_lft forever
```

They ping! 

Now, my question is can I do all 20 x /24 in that single script? Would I just copy/paste the above and simply modify the portions? Also, this isn't permanent because I rebooted the server, and the results were gone. How can I set them to be permanent? 

I actually tried this script, didn't work on the remaining 19 x 24s, only first on the list.

```
for i in {2..254}
        do ip addr add xxx.xxx.3.$i/24 dev em1
done        
for i in {2..254}
        do ip addr add xxx.xxx.58.$i/24 dev em1
done        
for i in {2..254}
        do ip addr add xxx.xxx.65.$i/24 dev em1
done        
for i in {2..254}
        do ip addr add xxx.xxx.80.$i/24 dev em1
done        
for i in {2..254}
        do ip addr add xxx.xxx.90.$i/24 dev em1
done        
for i in {2..254}        
        do ip addr add xxx.xxx.21.$i/24 dev em1
done        
for i in {2..254}        
        do ip addr add xxx.xxx.31.$i/24 dev em1
done        
for i in {2..254}        
        do ip addr add xxx.xxx.30.$i/24 dev em1
done        
for i in {2..254}        
        do ip addr add xxx.xxx.40.$i/24 dev em1
done        
for i in {2..254}        
        do ip addr add xxx.xxx.50.$i/24 dev em1
done        
for i in {2..254}        
        do ip addr add xxx.xxx.60.$i/24 dev em1
done        
for i in {2..254}        
        do ip addr add xxx.xxx.70.$i/24 dev em1
done        
for i in {2..254}        
        do ip addr add xxx.xxx.81.$i/24 dev em1
done        
for i in {2..254}        
        do ip addr add xxx.xxx.1.$i/24 dev em1
done        
for i in {2..254}        
        do ip addr add xxx.xxx.6.$i/24 dev em1
done        
for i in {2..254}        
        do ip addr add xxx.xxx.16.$i/24 dev em1
done        
for i in {2..254}        
        do ip addr add xxx.xxx.17.$i/24 dev em1
done        
for i in {2..254}        
        do ip addr add xxx.xxx.29.$i/24 dev em1
done        
for i in {2..254}        
        do ip addr add xxx.xxx.34.$i/24 dev em1
done        
for i in {2..254}        
        do ip addr add xxx.xxx.70.$i/24 dev em1        
done
```


I also tried single (like before) but on the next subnet and noticed this error.

```
root@server:~# sh addips.sh
Error: an inet prefix is expected rather than "xxx.xxx.58.{2..254}/24".
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: em1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether d4:be:d9:f0:fc:44 brd ff:ff:ff:ff:ff:ff
    inet xxx.xxx.105.34/29 brd xxx.xxx.105.39 scope global em1
       valid_lft forever preferred_lft forever
    inet xxx.xxx.3.2/24 scope global em1
```

---

### Post by SeijiSensei on 2016-11-22
The [method I gave you before]("https://ubuntuforums.org/showthread.php?t=2342522&p=13568272&viewfull=1#post13568272") had a problem.  I typed "auth" instead of "auto". (I'm sure I reread it a few times, too, and just blithely passed it by. Sorry.) Here is the same script fixed. It creates a file called "virthosts" in the current directory that contains the stanzas for the virtual interfaces that need to be in /etc/network/interfaces. It will give you declarations for eno1:3 with address xxx.xxx.16.3 though eno1:254 with address xxx.xxx.16.254.

```

for i in $(seq 3 254); do echo "auto eno1:$i
iface eno1:$i inet static
address xxx.xxx.16.$i                                                                               
netmask 255.255.252.0                                                                                       
                                                                                                            
" >> virthosts; done

```
You must insert the contents of the virthosts file into /etc/network/interfaces below the declaration of eno1.  Then restart networking or reboot.

Sorry about the typo; I see "auth" probably more often in my work than I see "auto."

---

### Post by Bashed on 2016-11-22
> **SeijiSensei said:**
> The [method I gave you before]("https://ubuntuforums.org/showthread.php?t=2342522&p=13568272&viewfull=1#post13568272") had a problem.  I typed "auth" instead of "auto". (I'm sure I reread it a few times, too, and just blithely passed it by. Sorry.) Here is the same script fixed. It creates a file called "virthosts" in the current directory that contains the stanzas for the virtual interfaces that need to be in /etc/network/interfaces. It will give you declarations for eno1:3 with address xxx.xxx.16.3 though eno1:254 with address xxx.xxx.16.254.

```

for i in $(seq 3 254); do echo "auto eno1:$i
iface eno1:$i inet static
address xxx.xxx.16.$i                                                                               
netmask 255.255.252.0                                                                                       
                                                                                                            
" >> virthosts; done

```
You must insert the contents of the virthosts file into /etc/network/interfaces below the declaration of eno1.  Then restart networking or reboot.

Sorry about the typo; I see "auth" probably more often in my work than I see "auto."


Thanks, I'll try this but first please explain how would I copy the whole bit from virthosts file to the network file? I'm using SecureCRT and I use nano editor. I'm not sure how to do a full, select-all in that program.

---

### Post by Bashed on 2016-11-22
Ok, I figured a way in the program to catch the cat virthosts output to a log file. But, I noticed that this happened now:

Each /24 subnet it outputed started off at #1 again instead of 255, 256, 257, etc all the way through consequetively for all 20 x /24 subnets

auto em1:1
auto em1:254

Then again...

auto em1:1
...

How can I properly change this so it does reset at #1? em1 is the NIC ethernet port (primary) and only port used too.

---

### Post by Bashed on 2016-11-22
Kind of desperate for help here please :/

---

### Post by wildmanne39 on 2016-11-22
There probably are not many people that can answer this question so please be patient, the rule is you can bump your thread once every twelve hours.

---

### Post by SeijiSensei on 2016-11-25
What is the range of IP addresses you want to generate?  Is it xxx.xxx.16.1 through xxx.xxx.18.254?  If so, you could just run the script three times replacing 16 with 17 and then 18.  You'll need to change the entries for "auto eno1:xxx" so that they don't overlap. You can add a constant to $i like this:

```

for i in $(seq 1 254); do 
IFACE=$(expr $i + 300)
echo "auto eno1:$IFACE
iface eno1:$IFACE inet static
address xxx.xxx.17.$i                                                                               
netmask 255.255.252.0   
                                                                                                                                                                                                
" >> virthosts; done

```

Now the interfaces for 17.1 through 17.254 will be numbered from eno1:301 through eno1:554.  Use 600 for the 18 subnet.

If that isn't the range you want, what is?

---

### Post by Bashed on 2016-11-25
That won't work.

They are not consecutive /24 subnets. They are something like 123.125.52.0, 123.130.54.0, etc.

---

