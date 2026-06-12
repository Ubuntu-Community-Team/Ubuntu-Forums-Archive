---
title: "Cannot assign requested address: Java error"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by robboguy on 2007-03-22
Hi all,

I'm having some problems working with sockets with Java and Ubuntu Edgy. I'm not sure what the problem is, but here is what I'm doing

Every time I try to bind a socket connection in Java I got
"Cannot assign requested address"

I tried this example code from my old good Java book:
[http://www.cadenhead.org/book/java-21-days/source/chapter17/NewFingerServer.java](http://www.cadenhead.org/book/java-21-days/source/chapter17/NewFingerServer.java)

this is the part of the sockets
[COLOR="Green"]           InetSocketAddress server = new InetSocketAddress(
                "localhost", 38991);
            ServerSocket socket = sockChannel.socket();
            socket.bind(server);[/COLOR]
and after the bind the error appears.

I've been trying to change the hostname, using the IP address and changing the port numbers but nothing seems to work. I tried in WinXP and it works, so I reduced the problem to something in my network configuration in Edgy.

My network/interfaces looks like this
[COLOR="Green"]#The loopback
auto lo
iface lo inet loopback

#The Ethernet
auto eth0
iface eth0 inet dhcp

#The wireless
auto eth1
iface eth1 inet dhcp[/COLOR]

and my hosts file looks like this
[COLOR="Green"]127.0.0.1 localhost
127.0.1.1 palantir

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts[/COLOR]

I've been googling around and apparently there was a problem with IPv6 but it was fixed in Mustang. I'm using the last Java 1.6.0 from Sun, configured the alternatives and everything, so I'm pretty sure the VM is working.

Has someone else had any problem like this? How can I deactivate IPv6? Is iptables blocking me or something? Maybe the programming is simply wrong (but it works in Win!!)? I think is something to do with the network configuration, but I'm not really good at networking so I can't tell. Any ideas?

Thanks :)

---

### Post by robboguy on 2007-03-25
OK I solved, for a reason loopback wasn't set up properly something like
ifconfig lo up
solve the problem :D

I just realised of it when I tried to ping localhost and it didn't work.

---

