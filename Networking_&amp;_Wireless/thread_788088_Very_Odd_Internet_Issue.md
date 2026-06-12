---
title: "Very Odd Internet Issue"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by magnezium on 2008-05-09
Hey, this is my first post on here. Also my first time having problems with Ubuntu! (Interesting enough)

I just installed a fresh copy of Ubuntu 8.04 Desktop on my work computer. Everything appears to work properly. Even the Ethernet. However, I can only get intranet and I cannot get outside of the firewall. The DNS is fine. I'm able to ping host names and IPs inside my network, but cannot ping IPs outside the network.

I also am able to access our website hosted locally using our server's host name. So I know that my Eth is working perfectly. 

I've manually assigned the IP, SN, GW, and DNS since we do not use DHCP. I know the settings are all correct and I can even ping the gateway here without a problem.

I dual boot this system with WinXP and the internet works perfectly. Both the XP install and the Ubuntu install have exactly the same network settings.

I'm pulling my hair out trying to figure out why I can't hit the internet. Any ideas?


Matt

---

### Post by ilrudie on 2008-05-09
Can you post the output of a netstat -rn?

---

### Post by magnezium on 2008-05-09
Sure. Let me boot into it. Give me a minute.

---

### Post by magnezium on 2008-05-09
Here's the netstat -rn output:

```
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.0.0.0        0.0.0.0         255.0.0.0       U         0 0          0 eth0


```

I noticed the gateway says 0.0.0.0 which I don't know if that's wrong, but that's obviously not my gateway and I wondering if it never got set even though the manager tells me otherwise.

I uploaded a screenshot of what I'm seeing as far as my settings go. I looked at /etc/network/interfaces and it looked ok. Just to be extra sure (though not sure if it was necessary) I added the broadcast with - obviously - no avail.

---

### Post by ilrudie on 2008-05-09
Try:
```

sudo route add default gw 10.1.1.254

```
and let me know if you can get to the internet after that.  Also check to make sure you can get to hosts on the LAN.

---

### Post by magnezium on 2008-05-09
Yes. This worked. I'm now in Ubuntu and it's working right. How do I make this perminant and what happened?

Thanks,
Matt.

---

### Post by ilrudie on 2008-05-09
I'm not sure if its a bug or what but essentially you only had routing information for one network in your iptables.  You knew how to get to anything on 10.x.x.x which doesn't require a gateway because its local.  Hence the gateway 0.0.0.0.  Now when it tried to access the internet though it has no routing information. Essentially you had no catch all or default routing information.

To make this change permanent you need to add a line to the proper stanza in /etc/networks/interfaces.  add the line ```
up route add default gw 10.1.1.254 dev eth0
```

This should add that route anytime you bring up the the interface eth0.  

Good luck.  Let me know if you run into problems and how it works out.

---

### Post by Eckan on 2008-05-09
Maybe you can help me too. As I am having the same problem.

netstat -rn output
```

Destination   Gateway   Genmask        Flags  MSS  Window  irtt  Iface
192.168.1.0   0.0.0.0   255.255.255.0  U      0    0       0     eth0
169.254.0.0   0.0.0.0   255.255.0.0    U      0    0       0     eth0

```

and sudo route add default gw 10.0.1.1 gives
```

SIOCADDRT: No such process

```

---

### Post by ilrudie on 2008-05-09
> **Eckan said:**
> Maybe you can help me too. As I am having the same problem.

netstat -rn output
```

Destination   Gateway   Genmask        Flags  MSS  Window  irtt  Iface
192.168.1.0   0.0.0.0   255.255.255.0  U      0    0       0     eth0
169.254.0.0   0.0.0.0   255.255.0.0    U      0    0       0     eth0

```and sudo route add default gw 10.0.1.1 gives
```

SIOCADDRT: No such process

```


Hmm... odd try specifying a device as well.

```

sudo route add default gw 10.0.1.1 dev eth0

```how does that work for you?

If it does not work could you post the output from ifconfig -a?

---

### Post by jtrindle on 2008-05-09
Eckan, if you could also post the contents of /etc/network/interfaces...

It looks as if you are dual-homed with a static IP in the 192.168.1.xxx subnet AND are trying to DHCP, which is kind of a rare problem.  I'd love to know how it got that way.

---

### Post by Eckan on 2008-05-09
Still gives the same response.

ifconfig -a output:
```

eth0      Link encap:Ethernet  HWaddr 00:1a:4d:57:c9:76  
          inet addr:192.168.1.62  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe57:c976/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1628012 (1.5 MB)  TX bytes:4719 (4.6 KB)
          Interrupt:219 Base address:0x8000  
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1892 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1892 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:94600 (92.3 KB)  TX bytes:94600 (92.3 KB)

```

---

### Post by Eckan on 2008-05-09
> **jtrindle said:**
> Eckan, if you could also post the contents of /etc/network/interfaces...

It looks as if you are dual-homed with a static IP in the 192.168.1.xxx subnet AND are trying to DHCP, which is kind of a rare problem.  I'd love to know how it got that way.

```

auto lo
iface lo inet loopback


iface eth0 inet dhcp



auto eth0

```

---

### Post by Wicca on 2008-05-09
Hi,

The 169.254 address is given because the machine can't  get an ip from the dhcp server.

In case of routing problems it sometimes will help, especially in dual boot configs with Windows, to shutdown your machine, unplug the powercord for 10 sec, restart your router and then restart your machine.

Never know, just try it.

---

### Post by jtrindle on 2008-05-09
I'm surprised that's the whole file!

I would think that would result in a single line references eth0, not two.

Here is my working setup:

iface eth0 inet dhcp
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1

---

### Post by jtrindle on 2008-05-09
Oops, you still need the other lines you already had.  Just merge mine with yours, adding the address, netmask, and gateway lines after your iface eth0 line and before you auto eth0 line.

---

### Post by ilrudie on 2008-05-09
> **ExpertAnalysis said:**
> The only way to resolve this without any question is a fresh, clean install.  Also make sure all of the drivers in windows are updated.

I disagree with ExpertAnalysis's analysis.  This will not require a clean install.  Seems like we have a good thread going with people who know a little about networking with Linux and from what I have seen there is nothing totally hosed with your system.  Its just configured a little oddly.

---

### Post by jtrindle on 2008-05-09
Well, I was thinking that Wicca's comments about unplugging both the machine and the router were a bit like  magic *grin*, but then again the extra lines in my interfaces file shouldn't matter either.

How about recording the ifconfig -a then route -rn, then doing a 

sudo /etc/init.d/networking restart

and see if the outcome is any different?

or the same approach but do:

sudo ifdown eth0
sudo ifup eth0

in between.


BTW, the literal command to add a route and gateway for 10.0.1.1 is probably not relevant to Eckard's needs, just magnezium's.

---

### Post by ilrudie on 2008-05-09
> **jtrindle said:**
> Well, I was thinking that Wicca's comments about unplugging both the machine and the router were a bit like  magic *grin*, but then again the extra lines in my interfaces file shouldn't matter either.

How about recording the ifconfig -a then route -rn, then doing a 

sudo /etc/init.d/networking restart

and see if the outcome is any different?

or the same approach but do:

sudo ifdown eth0
sudo ifup eth0

in between.


BTW, the literal command to add a route and gateway for 10.0.1.1 is probably not relevant to Eckard's needs, just magnezium's.

True.  Restarting networking is a good idea and adding the static route is probably not relevant because DHCP should provide all the routing information.  These are really two different issues with similar symptoms I think.

---

### Post by fwre01 on 2008-05-09
Eckan, i notice you have two ip addresses on one interface (albeit if ones a 169 address) but the gw you tried adding on the default route was in a 10.0.1.0 subnet. If your nic is on a 192.168.x.x subnet the gw will need to be on this subnet...

...just something i noticed, let us know how your getting on

---

### Post by magnezium on 2008-05-09
OK. I had to reboot my system into XP for a minute. As soon as I get back into my linux install I'll post it. Should only be 5 min from now.

---

### Post by Eckan on 2008-05-09
I tried restarting the network and it did not help.

> Eckan, i notice you have two ip addresses on one interface (albeit if ones a 169 address) but the gw you tried adding on the default route was in a 10.0.1.0 subnet. If your nic is on a 192.168.x.x subnet the gw will need to be on this subnet...
I got the 10.0.1.1 gw from my Windows machine

If I pinged the DHCP server, shouldn't I get a reply from the server?

---

### Post by fwre01 on 2008-05-11
you will only get a reply if the server responds to ICMP (which it normally does) im confused as to why you have two different subnets, are you getting a 192.168 address from the DHCP server and a 10.0.1.1 address as the default gateway, because that wont work. whats the address of your router? could you explain how your network is setup?

---

### Post by Eckan on 2008-05-12
All computers connect to a managed ProCurve switch and then into a router provided by CBeyond. The router was set up completely by them and I know little about it.
> 
IP Address. . . . . . . . . . . . : 192.168.1.179
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . : 10.0.1.1

Don't know if this helps, but it is some information off my windows machine.

---

### Post by bwallum on 2008-05-12
I'm having serious network problems. One machine keeps retarting with a new eth number, now on eth72. Another machine will connect slowly to the Internet using FF3b5 but will not run update and will not show software sources.

My router is going nuts and indicating port sniffing. Are we under some sort of attack? M$ must be pretty sore at the moment.

Bob

---

### Post by fwre01 on 2008-05-12
Eckan, your DHCP server has been set up incorrectly. either the scope of addresses (the 192.168.1.179 part) is set up wrong, or the default gateway is wrong. can you log into you router (from a webbrowser or command line) to find out what its IP address is? 

You need to be in the same subnet as your router basically (which is going to be difficult at first, because its unclear if its in the 192.168.1.0 subnet or the 10.0.1.0 subnet) you could try setting your IP address manually to 10.0.1.50 / 255.255.255.0 (dont worry about the default gateway) and then try accessing 10.0.1.1 from a webbrowser.

---

### Post by fwre01 on 2008-05-12
bwallum, could you explain a bit more on how the network is setup? could you post the contents of your /etc/network/interfaces file on the problem computer?

---

### Post by bwallum on 2008-05-12
Here is my /etc/network/interfaces file, with the gaps as found. I am on the 64 bit machine of my signature, this machine cannot run Update Manager or Software Sources.

The machine with escalating eth numbers is a 32 bit machine and cannot connect to the network at present.

auto lo
iface lo inet loopback












iface eth0 inet static
address 192.168.1.6
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

---

### Post by fwre01 on 2008-05-12
hmmm, seems OK, can you paste the output from from > cat /etc/resolv.conf

and > route

im assuming your able to access other webpages and from this machine? whats actually happening when you run the update manager? do you get an error?

---

### Post by bwallum on 2008-05-12
> bob@bob-desktop:~$ cat /etc/resolv.conf
nameserver 192.168.1.1
domain BERRYBUSH

> bob@bob-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

Update Manager just greys over and can't be closed. I have just tried to remove blank spaces in /etc/network/interfaces and get no response with gksudo gedit /etc/network/interfaces

Evolution has started to ask for access to keyring at about the same time as these network problems started. Once per session at the first time evolution is opened.

---

### Post by fwre01 on 2008-05-12
Seems asthough its just freezing up, this might not be a network issue, there doesnt seem to be anything wrong with the network setup (it might be a DNS timeout problem) whats the IP address of your ISP's nameserver, i would suggest adding that into your DHCP server settings as a secondary dns server, or adding it underneath "nameserver 192.168.1.1" in your resolv.conf file. (if you can access it) try sudo nano /etc/resolv.conf instead of a using GUI editor

---

### Post by bwallum on 2008-05-14
Hi

One machine back on ok. I had changed the domain name from lower case to uppercase (or the system had). I reset the domain name to be the same case as that found in etc/hosts. Problem went away.

I am now trying to get my 32 bit machine working properly. This is the one with incrementing eth numbers. It went up to eth72 before dropping to eth38, now appears to have settled for that. All my other machines run on eth0. I removed Network Monitor and checked that domain names were all the same case.

I can now access the Internet with FF but Update Manager just hangs (or appears to) when I click the check button. The cursor wheel runs when hovered over the window and I can't close the window.

??

EDIT Ahh! that was cathartic. I have reinstalled from scratch, binned the dual boot in the process. Feels great! Going like a train. Now have 3 machines as Ubuntu solos. one dual boot and one XP as legacy machine. Just need to get Sage accounts running under wine and the dual boot will go.

---

