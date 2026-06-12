---
title: "How do I set mtu at boot time over dhcp?"
date: 2004-11-10
forum: Networking &amp; Wireless
---

### Post by rolfpal on 2004-11-10
I need to know how to set the MTU for my desktop machines I am running DHCP.  I used to do it (on Fedora) by adding a line to /etc/sysconfig/networking/devices/eth0 that looked like "MTU=1492"

I am sure there is a conf file in Ubuntu that can accomplish the same thing, I just can't find it.  

I know about "ifconfig eth0 mtu 1492", thats how I do it now by hand, and if worst comes to worst I will add it to a script somewhere.

A few months ago my ISP changed settings and lowered the MTU available over PPPOE but somehow my machines don't see it, except for the router.

Thanks in Advance.

Rolf

---

### Post by alzen on 2004-11-28
same here, i found [this](http://dfarq.homeip.net/article/20040803131427190) but it doesn't work for me, i am still working on it

---

### Post by alzen on 2004-11-28
i broke that beast :D
solution:
make file mtu(or use other name) in /etc/init.d direcroty, my script looks like:

[COLOR=Red]#!/bin/sh[/COLOR]

[COLOR=Red]ifconfig eth0 mtu 500[/COLOR]

now use command:
sudo chmod a+x mtu
ln mtu /etc/rcS.d/S52mtu [number must be 5x; on this level network is loaded]

and this is how i made it on my machine, hope i helped.

---

### Post by rabeldable on 2005-01-24
I was working on my newly installed ubuntu linux system and found that debian does things alot differently.  It is possible to put these mtu settings in a rc script as documented above, however, I'd like to point out another way to accompish this.

At bootup there is a process that sets up the interfaces.  This process allows custom scripts to be placed in a directory depending on the desired outcome. 

Here is my example of setting the mtu to 1450 at bootup, this will work for dhcp or static IP addresses:

Create an executable file called mtu and put it in /etc/network/if-up.d/

root@host:~ # more /etc/network/if-up.d/mtu 
#!/bin/sh
ifconfig eth0 mtu 1450
root@host:~ #

root@host:~ # ls -l /etc/network/if-up.d/mtu 
-rwxr-x---    1 root     root           33 Jan 24 00:39 /etc/network/if-up.d/mtu
root@host:~ #


I found that you can setup many tasks with the following 

       up command
              Run command after bringing the interface up.

       pre-up command
              Run command before bringing the interface up.

       down command
              Run command before taking the interface down.

       post-down command
              Run command after taking the interface down.


For more information check the manpage for interfaces and look in the IFACE OPTIONS section.


David

---

### Post by az on 2005-01-25
man interfaces

...
This method may be used to define ethernet interfaces with statically allocated IPv4 addresses. 
Options 

address address 
Address (dotted quad) required 
netmask netmask 
Netmask (dotted quad) required 
broadcast broadcast_address 
Broadcast address (dotted quad) 
network network_address 
Network address (dotted quad) required for 2.0.x kernels 
metric metric 
Routing metric for default gateway (integer) 
gateway address 
Default gateway (dotted quad) 
pointopoint address     
Address of other end point (dotted quad). Note the spelling of "point-to".

media type 
Medium type, driver dependent 
hwaddress class address 
Hardware Address. class is one of ether, ax25, ARCnet or netrom. address is dependent on the above choice. 
mtu size 
MTU size 
  


So, edit your
/etc/network/interfaces
and add the mtu line.

---

### Post by occy8 on 2005-03-16
o.k. looks like I have to do something like this. But I'm a bloody newbie. that way over my head
Can someone explain this to me differently or copy such a script in here that I can use?

thanks a lot

---

### Post by fat_larry on 2005-10-16
I'd just like to add that alzen's post is the **ONLY** way I have managed to set my MTU on boot.  No combination of mtu xxxx in the /etc/network/interfaces file has ever worked. So thank you alzen!

---

### Post by dvhart on 2005-11-12
I just worked through this, you have to set the interface-mtu option on the server and tell the clients to request the mtu setting.

edit /etc/dhcp3/dhcpd.conf and add

option interface-mtu 1492;

server$ sudo /etc/init.d/dhcp3-server restart

edit /etc/dhcp3/dhclient.conf

add interface-mtu to the end of the request list, ie:

request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope, interface-mtu;

client$ sudo ifdown eth0 && ifup eth0
client$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:30:1B:3B:EA:98
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:1bff:fe3b:ea98/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:39564 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35625 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8372362 (7.9 MiB)  TX bytes:3064377 (2.9 MiB)
          Interrupt:22 Base address:0xe000


So that, I believe is the right way to do this :-)  And it works for me.

---

### Post by eXisor on 2006-08-03
I know this is an old thread, but it took me ages to find the simple answer, ie. requiring no boot script. It was originally posted by mlonker, but is buried in a thread

[http://glasnost.beeznest.org/articles/290](http://glasnost.beeznest.org/articles/290)

---

### Post by graysky on 2006-12-11
I read the thread @ [http://glasnost.beeznest.org/articles/290](http://glasnost.beeznest.org/articles/290) but have a question since it didn't work for me: 

hostname "mymachine" - I'm assuming "mymachine" is the hostname of the local machine?

name LAN Interface - Is this entered as such or do I need to replace LAN interface with eth0 or something?

pre-up /sbin/ifconfig $IFACE mtu 4000 - Again, assuming I type it as it's shown.

Thanks!

---

### Post by nutuub on 2007-08-27
Hi Guys,

Figured it out, see below
____________________________

If you need to adjust your MTU permanently, do the following:
    sudo vim /etc/network/interfaces

If you are using a static address then find the interface you need and simply add the MTU line:
    iface eth0 inet static
        address 192.168.0.1          
        network 192.168.0.0
        gateway 192.168.0.254
        netmask 255.255.255.0
        mtu 1492

If you are using** DHCP addresses** then you need to set this before the interface comes up, by adding this line:
    iface eth0 inet dhcp
       **pre-up /sbin/ifconfig $IFACE mtu 1492**


Then release and renew (or up and down) the interface
    sudo ifdown eth0
    sudo ifup eth0

[http://ubuntuforums.org/showthread.php?t=82093](http://ubuntuforums.org/showthread.php?t=82093)
[http://www.debianadmin.com/change-mtu-maximum-transmission-unit-of-network-interface.html](http://www.debianadmin.com/change-mtu-maximum-transmission-unit-of-network-interface.html)
[https://answers.launchpad.net/ubuntu/+source/network-manager/+question/4630](https://answers.launchpad.net/ubuntu/+source/network-manager/+question/4630)

---

