---
title: "ufw and local port forwarding"
date: 2013-10-06
forum: Networking &amp; Wireless
---

### Post by Tyndarus on 2013-10-06
Hello,

I'm new to ufw and I'd like to add a rule to iptables nat table to port forward ssh-server request on 178.119.***.***:22*** (my ubuntu box) to localhost:22

I know it's possible to make the ssh-server listen to a different port that the default port 22, but I'd like to do this with iptables because certain other ip's must be allowed to use the default port, while it should be blocked for public access.

On Thread: UFW and Port Forwarding ([http://ubuntuforums.org/showthread.php?t=833844](http://ubuntuforums.org/showthread.php?t=833844)) I've read one should add lines in /etc/ufw/before.rules:
*nat
:PREROUTING - [0:0]
# My DNAT rules
-A PREROUTING -i <iface> -p tcp --dport <port> -j DNAT --to-destination <addr>
-A PREROUTING -i <iface> -p udp --dport <port> -j DNAT --to-destination <addr>
COMMIT

I've added this using 
<iface> = eth0 || <iface> = lo
<port> = 22***
<addr> = 127.0.0.1 || <addr> = localhost

Then disable ufw, enable ufw and /etc/init.d/networking restart...

Now sudo iptables -L -v -t nat gives me:
Chain PREROUTING (policy ACCEPT 2 packets, 714 bytes)
 pkts bytes target prot opt in out source   destination         
    0     0 DNAT   tcp  --  eth0 any anywhere anywhere    tcp dpt:22*** to:127.0.0.1:22
    0     0 DNAT   udp  --  eth0 any anywhere anywhere    udp dpt:22*** to:127.0.0.1:22

But yet, ssh doesn't work and when I check the ports, eg. on 
canyouseeme.org or similar ones, I don't get anything...

I'm quite new to all this networking, I know the basics regarding iptables 
and several of the networking config files.

Any suggestions?

kind regards,
Dieter

---

### Post by 7182818 on 2013-10-08
Can you verify that the ssh packets are making it to your server?  You can do this by running tcpdump on eth0 and attempting to ssh in.  If you can't see the packets coming in, some possible issues are that you are behind a firewall or router that isn't set up to do port forwarding.  If you can, verify that your ssh server is listening on the loopback interface by trying to ssh to 127.0.0.1 from your server.  If both of those working then you might want to double check that you have forwarding turned on ([http://unix.stackexchange.com/questions/14056/what-is-kernel-ip-forwarding](http://unix.stackexchange.com/questions/14056/what-is-kernel-ip-forwarding))

If none of that works, post back and we can go from there.  :)

---

