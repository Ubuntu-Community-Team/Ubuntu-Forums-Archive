---
title: "Needed help with connecting PC to beagleboard through USB"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by thunder87l on 2010-09-27
I have a PC and Beagleboard both running Lucid. I need to share internet to BB so that I can apt-get some software for it. BB doesn't have Ethernet port, but it does have USB OTG. (I could use Ethernet>USB adapter but it would cost me approx 30$ + 3 day delivery) First part of the problem is - I don't know how to set up network through usb. Second part - I poorly understand all these IP, mask & gateway things.

Would appreciate a small step-by-step guide on how to make this work.

on PC ifconfig gives:

> eth0      Link encap:Ethernet  HWaddr 00:69:00:12:00:83 
>           UP BROADCAST MULTICAST  MTU:1500  Metric:1 
>
> eth1      Link encap:Ethernet  HWaddr 00:e0:4c:25:7e:6e 
>           inet addr:78.84.232.77  Bcast:78.84.255.255  Mask:255.255.224.0 
>           inet6 addr: fe80::2e0:4cff:fe25:7e6e/64 Scope:Link 
>           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
>
> lo        Link encap:Local Loopback 
>           inet addr:127.0.0.1  Mask:255.0.0.0 
>           inet6 addr: ::1/128 Scope:Host 
>           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
>
> usb0      Link encap:Ethernet  HWaddr 0a:9e:e3:7d:bf:19 
>           inet6 addr: fe80::89e:e3ff:fe7d:bf19/64 Scope:Link 
>           UP BROADCAST RUNNING MULTICAST  MTU:1494  Metric:1

on BB:

> lo        Link encap:Local Loopback 
>           inet addr:127.0.0.1  Mask:255.0.0.0 
>           inet6 addr: ::1/128 Scope:Host 
>           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
>
> usb0      Link encap:Ethernet  HWaddr ca:40:b7:51:5e:ae 
>           inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0 
>           inet6 addr: fe80::c840:b7ff:fe51:5eae/64 Scope:Link 
>           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

---

### Post by jtarin on 2010-09-27
[I don't know your experience with this board and Ubuntu, but....]("http://elinux.org/BeagleBoardUbuntuNetwork")

---

### Post by thunder87l on 2010-09-27
No, this link is not what i need. It is something about how to set up internet wit5h wifi and USB>Ethernet devices.

I simply need to setup network through usb and share internet to BB, something more like this topic [http://www.hardwaresecrets.com/article/248]("http://www.hardwaresecrets.com/article/248") but for Ubuntu.

Shouldn't be different from setting up a USB network for 2 PC's both running Ubuntu.

---

### Post by QLee on 2010-09-27
See if this link helps you set up your network.
[http://ubuntuforums.org/showthread.php?t=993036](http://ubuntuforums.org/showthread.php?t=993036)

---

### Post by jtarin on 2010-09-27
> **thunder87l said:**
> No, this link is not what i need. It is something about how to set up internet wit5h wifi and USB>Ethernet devices.

I simply need to setup network through usb and share internet to BB, something more like this topic [http://www.hardwaresecrets.com/article/248]("http://www.hardwaresecrets.com/article/248") but for Ubuntu.

Shouldn't be different from setting up a USB network for 2 PC's both running Ubuntu.
You didn't mention bridge cable in your post only usb2usb.

---

### Post by thunder87l on 2010-09-27
> You didn't mention bridge cable in your post only usb2usb.

I think I don't have to use a bridge cable, because on BB there is a USB OTG port for A/B USB cable. I think A/A bridge is needed only when connecting two PC's. At least PC and BB are still working fine. As far as I know, if you connect two PC's with a normal USB cable, both USB ports should fry ))

---

### Post by thunder87l on 2010-09-27
> **QLee said:**
> See if this link helps you set up your network.
[http://ubuntuforums.org/showthread.php?t=993036](http://ubuntuforums.org/showthread.php?t=993036)

Ok

1) I connected PC to BB
2) did ifconfig usb0 192.168.1.1 on PC
3) did ifconfig usb0 192.168.1.2 on BB

Now I am able to ping PC from BB. That's great, I guess.

How do I share the internet from PC to BB?


found this, hope it helps [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)
Now I can't find root terminal :D LOL

---

### Post by QLee on 2010-09-27
[QUOTE=thunder87l]...
How do I share the internet from PC to BB?
[/QUOTE]
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

I have a suggestion, you've been asking questions and I have been doing a forum search and providing you with links, next time, maybe we should try eliminating one of the people from the chain, eh?

---

### Post by thunder87l on 2010-09-27
So I followed this topic: [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370) At step 3: "Package ipmasq has no installation candidate." That's a bit disturbing.

Searched for package. Seems that ipmasq exists only for dapper, hardy & jaunty

What do you do for lucid then?

---

### Post by QLee on 2010-09-27
[QUOTE=thunder87l]So I followed this topic: [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370) At step 3: "Package ipmasq has no installation candidate." That's a bit disturbing.

Searched for package. Seems that ipmasq exists only for dapper, hardy & jaunty

What do you do for lucid then?[/QUOTE]
What would I do? 
I would follow the link I gave you in my previous post rather than that old thread from 2005.

---

### Post by thunder87l on 2010-09-27
Hmmm... 10 min ago i tried to open link you gave from Opera (running Ubuntu) and I got a blank page, that's why I followed that old link. Now, under WinXP all seems fine.

I wonder if my Ubuntu Opera is somehow broken or misses some files.... Ok, thanks.

---

### Post by thunder87l on 2010-09-27
So i follow topic (Ubuntu Internet Gateway Method):

eth1 = the network adapter with internet
usb0 = the network adapter to which BB is attached
192.168.0.x = IP subnet

1) *sudo ifconfig usb0 192.168.0.1*

2) *sudo iptables -A FORWARD -i eth1 -o usb0 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT*

3) *sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT*

4) *sudo iptables -A POSTROUTING -t nat -j MASQUERADE*

5) *sudo iptables-save | sudo tee /etc/iptables.sav*

6) *sudo gedit /etc/rc.local*
and add: *iptables-restore < /etc/iptables.sav*
before *exit 0* line

7) *sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"*

8 ) *sudo gedit /etc/sysctl.conf*
and add these lines:
[I]net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1[/I]

at this point it should be all that was needed for me to do on PC

9) *sudo /etc/init.d/networking stop*

10) *sudo ifconfig usb0 192.168.0.100*

11) *sudo route add default gw 192.168.0.1*

12) *sudo cp /etc/resolv.conf /etc/resolv.conf.backup*
i've looked in it - it contains only string: nameserver 192.168.1.5
which was BB's usb0 initial ip address
why backup file which (according to tutorial) I shouldn't change?

13) *sudo nano /etc/dhcp3/dhclient.conf*
At this point I get problems. I do connect to BB through RS232 with minicom. From time to time it swallows some letters (I guess tx/rx errors of some kind), but when it comes to vi or nano - it is simply impossible to understand what is written in file, where is cursor location and so on. Strings overlay, moving cursor with arrows gives random movement.
*cat /etc/dhcp3/dhclient.conf* shows this:
[I]send vendor-class-identifier "d-i";
request subnet-mask, broadcast-address, time-offset, routers, domain-name, domain-name-servers, host-name, ntp-servers;[/I]
So I dont find a *prepend domain-name-servers* there. Do I erase domain-name-servers from request list and write *prepend domain-name-servers* somewhere?

14) if I do now *sudo /etc/init.d/networking restart* (without completing p.13) it says: Reconfiguring network interfaces... SIOCADDRT: No such process
Failed to bring up usb0. After which usb0 is reset back to initial 192.168.1.5

Any ideas?

---

### Post by thunder87l on 2010-09-28
Tried to modify /etc/dhcp3/dhclient.conf on BB*.* Whole system crashed and doesn't want to boot anymore. Tried to delete all I have added - nothing. Have to reinstall everything.

---

