---
title: "Cannot find home network with Hardy"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by Horomancer on 2008-07-14
Hello everyone.
I've just recently tried to view my home network after switching to hardy from gutsy and cannot seem to find anything. I use to be able to view the router and laptop that make up my home network but now when i go to Places> Network> all i see is 'Windows network' which does not lead anywhere (smb:///)
I can not ping the laptop from network tools, though i can ping the router.
I can not view the Ubuntu desktop from the vista laptop.
The vista machine's workgroup is set to 'WORKGROUP' but i'm not certain if this has anything to do with my troubles.

Also when ever I open my networking tools the Network device is set to Loopback. I'm pretty certain it needs to be Ethernet Interface (eth0) but I get an error message if i try to configure it.

---

### Post by superprash2003 on 2008-07-15
you have any firewall running in your laptop which is blocking the pings??

---

### Post by Iowan on 2008-07-15
> **Horomancer said:**
> Also when ever I open my networking tools the Network device is set to Loopback. I'm pretty certain it needs to be Ethernet Interface (eth0) but I get an error message if i try to configure it.
Post results of **ifconfig** and contents of **/etc/network/interfaces** file.

---

### Post by Horomancer on 2008-07-15
jackmo@time-control:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:76:5c:57:3b  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:76ff:fe5c:573b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:281310 errors:0 dropped:0 overruns:0 frame:0
          TX packets:205319 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:299942581 (286.0 MB)  TX bytes:23252909 (22.1 MB)
          Interrupt:21 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8303 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:268966 (262.6 KB)  TX bytes:268966 (262.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:f8:28:cc:da  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-F8-28-CC-DA-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

and the contents of /etc/network/interfaces -

auto lo
iface lo inet loopback

hope that helps

---

### Post by LRD on 2008-07-15
Hi all,
I have the same problem as Horomancer. Before upgrading to Hardy, I could access the shared folders on another computer that runs WinXP. Since then, the workgroup does not appear under "Windows Network" anymore. 
I can successfully ping the router and the other computer.
Have fun,
LRD

---

### Post by LRD on 2008-07-16
Success. 

I found Superprash2003's hint on another [_thread_]("http://ubuntuforums.org/showthread.php?t=859880")
> In your terminal type:
nautilus smb://x.x.x.x 
where x.x.x.x is the ip of the windows machine..
It gave me direct access to my other computer's hard drive and I was able to select the Windows shared directory.

As reported by others, it does not work for everyone. Unable to ping the computer may be the problem.

Horomancer, as Superprash2003 already asked: 
[LIST]
Have you added/enabled a firewall to the windows laptop lately? eg Zonealarm, or MS Firewall. [/LIST]A firewall will stop your computer from responding to pings.

There are other threads covering this problem in more detail:
eg [_http://ubuntuforums.org/showthread.php?t=784259_]("http://ubuntuforums.org/showthread.php?t=784259")

Cheers,
LRD

---

### Post by Horomancer on 2008-07-16
That got me to the files i needed to transfer over to my desktop, but it doesn't resolve neither computer seeing each other. Makes it a bugger to have LAN gaming.

---

### Post by Iowan on 2008-07-17
One option is to build a **/etc/hosts** file with name/address resolution.  My network DNS server has my static-addressed servers mapped this way.

---

### Post by Horomancer on 2008-07-18
How would i go about doing this?

EDIT:

My Fiancee tried to do some adjustment on Vista to get it visiable in Windows Networks. The end result is that i can no longer access the shared files by using the

nautilus smb://x.x.x.x

command. Any idea what she did to vista that would make this happen? If i try to punch in the laptop IP i just get a blank window.

---

### Post by dmizer on 2008-07-23
make sure all computers are a part of the same workgroup.
[LIST]
[*]vista: [http://technet.microsoft.com/en-us/library/bb727037(TechNet.10).aspx](http://technet.microsoft.com/en-us/library/bb727037(TechNet.10).aspx)
[*]XP: [http://support.microsoft.com/kb/295017](http://support.microsoft.com/kb/295017)
[*]ubuntu: system > administration > networking > general > enter the workgroup name next to "domain name"
[/LIST]

---

### Post by Horomancer on 2008-07-25
Both computers have a new domain/workgroup name fallowing the instructions you provided. There has been no change. Neither the laptop can see the desktop or vice versa.

---

### Post by dmizer on 2008-07-25
i've read several threads indicating that this may fix your problem.

```
sudo aptitude install libgnomevfs2-extra
```

---

### Post by Horomancer on 2008-07-26
ok here is what i got from that command

```
jackmo@time-control:~$ sudo aptitude install libgnomevfs2-extra
sudo: unable to resolve host time-control
[sudo] password for jackmo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  libwxbase2.8-0 libwxgtk2.8-0 python-wxgtk2.8 python-wxversion 
0 packages upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 55.7MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 159005 files and directories currently installed.)
Removing python-wxversion ...
Removing python-wxgtk2.8 ...
Removing libwxgtk2.8-0 ...
Removing libwxbase2.8-0 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done 
```

No change.


EDIT: Just thought i would throw this info in, incase it is relevent.
Places> Network>
Shows me two items. One is TIME which is my computer and the other is Windows Network. Opening TIME takes me to an overview of what folders i have shared. Opening Windows Network takes me to another network icon labeled WORKGROUP. there is only TIME again in WORKGROUP and my domain/Workgroup name is HOME on both computers.

---

