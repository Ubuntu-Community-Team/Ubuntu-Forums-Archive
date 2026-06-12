---
title: "Can changing dns servers solve connections to vk.com?"
date: 2014-03-27
forum: Networking &amp; Wireless
---

### Post by fangorn2 on 2014-03-27
Hello.

I recently installed Ubuntu 12.04 LTS.
I mainly use Internet to connect to some social network and make use of their features.  
For instance I often watch videos, movies mostly, stored in the social network vk.com.

However if I try to load any of these videos these are the messages I receive from my two browsers:

Firefox can't establish a connection to the server at vk.com.
Oops! Google Chrome could not connect to vk.com

I found an old thread by a user with the same problem.
It seems that he solved it changing dns server. Can this be the right solution?

[http://ubuntuforums.org/showthread.php?t=2070869](http://ubuntuforums.org/showthread.php?t=2070869)


I tried to ping vk.com ip address:

~$ ping -c 1 87.240.131.120
PING 87.240.131.120 (87.240.131.120) 56(84) bytes of data.
64 bytes from 87.240.131.120: icmp_req=1 ttl=55 time=112 ms

--- 87.240.131.120 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 112.095/112.095/112.095/0.000 ms

I was able to connect to vk.com through the following website:
[http://unblocksit.es/unblock/vk.com/](http://unblocksit.es/unblock/vk.com/)


I am wondering, if I am on the right way, what DNS servers would suggest.
With windows I use Comodo's dns servers.

I looked for explanation about how to change dns in Ubuntu and found the following thread:

[http://ubuntuforums.org/showthread.php?t=2078398](http://ubuntuforums.org/showthread.php?t=2078398)

Network manager did not show up when I called it with the following commands:

sudo /etc/init.d/network-manager stop
sudo /etc/init.d/network-manager start


Researches in Dash Home were unsussesful.


As I have uhderstood, instead of editing /etc/resolv.conf I should instead edit /etc/network/interfaces.

Here's my /etc/network/interfaces:

auto lo
iface lo inet loopback

What am I supposed to do? Delete the previous two lines and write the following ones or keep the previous and add the following?

auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 156.154.70.22 156.154.71.22

The machine I use is a desktop computer connected to the Internet through a router (192.168.1.1)

Many thanks in advance for any help.

---

### Post by oldos2er on 2014-03-27
Moved to Networking & Wireless.

---

### Post by buzzingrobot on 2014-03-27
In systems using DHCP connections with an ISP, you can usually change nameservers by right-clicking the network applet icon in the panel, selecting "Edit Connections", highlighting the connection, clicking "Edit", clicking the "IPv4" tab, changing "Method:" to "Automatic (DHCP) addresses only", and then entering a comma-delimited string of new nameserver addresses in the field below.  Click "Save" and close out and the change will take affect in a moment or two. You may see a "Disconnect" followed by "Connect..." notification.

---

### Post by fangorn2 on 2014-03-28
Thanks buzzingrobot. It works. 
So it is true that for those who cannot connect to vk.com it is necessary to change nameservers :p

I am wondering what file has been edited. I had a look at /etc/network/interfaces and it has not changed.

---

