---
title: "[SOLVED] Squid &amp;amp; DansGuardian Transparent Proxying"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by knichel on 2007-03-29
If you are experienced with squid and dansguardian and would not mind helping a newbie, please read on...

I have a new server in my classroom.  We use a wireless router for internet access. It does not seem to work well for access restrictions so I want to put my server "in-the-way" between the router and the internet connection...

wifi router ->(eth0)- server - (eth1)-> wall (internet)

The wall is our connection to the school network.  Eth1 gets an ip address on the 10.x.x.x network from the school dhcp server.  I figured I would give the eth0 a static ip address and connect it to the uplink of my wifi router.  I would then configure the router 

I wish to have my computers all go through the server so I can use dansguarding for content filtering and site blocking... and squid as a proxy.  I am new to this kind of stuff, so please be gentle.
[U][B]
The changes I made to the squid.conf file are...[/B][/U]
http_port 3128 # default
http_port 80 # I added

acl our_network src 192.168.6.0/24
http_access allow our_network

visible_hostname localhost

I left all else as is after install...

_**For DansGuardian I did ...**_
Added a couple of domains to the bannedsitelist.  

On the server, dansguardian is wokring (i cannot connect to a banned site).

(My server is currently connected to the router just like the other computers are)
However, from another computer in the room if I set the gateway to be my server and my server gateway is the router, I cannot connect to any site.  I don't get the dansguardian messages or anything.

I want all traffic to go through squid/dansguardian...  I just don't know how to make it happen.  Then I need to get any allowed traffic to go out the eth1 interface to the school network and out to the internet.

If you can help me understand this better and maybe offer some assistance, thank you.

I just thought of something... I am using the server for login authentication and doc's storage.  I should probably keep the server on the same network as the workstations, so that means I should keep it on one of the switchports of the router rather than the uplink?  Not really sure.


Mike

---

### Post by bmathis on 2007-04-16
you need to setup a firewall using iptables which can be a trivial task at first, but once you get the hang of it, it isnt too bad.

Heres a quick tutorial on the subject that is geared towards what youre trying to dl

[http://www.debian-administration.org/articles/71]("http://www.debian-administration.org/articles/71")

---

### Post by jonathan.lees on 2007-04-16
I used this site ([http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html](http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html)) to do exactly what you want to do, you can use their script, maybe you need to tweak it a little for your setup and you'll need to change port 3128 to your dansguardian port 8080. You don't need the http_port 80 in your squid.conf since iptables will redirect traffic from port 80 to 3128. Then you need to change the default gateway on your computers to the squid box.

---

### Post by knichel on 2007-04-17
Thanks to both for the reply.  I returned to work today and un-installed squid, dansguardian and iptables, just to get a clean start.
I read the how-to's and configured as follows...

Squid : 
installed and added
http_port 3128 transparent
visible_hostname myServer
acl myNet src 192.168.6.0/24
http_allow myNet

Dansguardian : 
added some addresses to the bannedsitelist
commented the line saying UNCONFIGURED
left other stuff alone

IPTables :
installed and added
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 8080

Here is where I stand...

From a workstation I have the gateway set as the squid,dg,iptables box.  If I set the proxy settings in the browser to the ip of the squid box port 8080, I can browse fine and the things I want blocked are blocked.  If I remove the proxy settings, then I cannot browse.  I do not get any entries in the squid/access.log file when I view with tail -f.

So, it appears that the proxy and filter are working fine.  Something must be missing/wrong with my iptables entries?

Any ideas?

Mike

---

### Post by Abhi Kalyan on 2007-08-30
The problem is you will have to set up NATing,
Please spt-get IPMASQ and DNsMAsQ!
Forgot the link with the whole procedure.
Will post in a while (2 hours max)

---

### Post by mokmoki on 2007-08-30
i have installed dansguardian just fine, everything's working...

but the problem is that when i restart dansguardian (sudo /etc/init.d/dansguardian restart), it seems that the process hangs...

i can stop dansguardian just fine (/etc/init.d/dansguardian stop works flawlessly), but when i try to start it again, it just says "Starting DansGuardian: dansguardian" and it stays there forever...

does anybody know why this is happening?

---

