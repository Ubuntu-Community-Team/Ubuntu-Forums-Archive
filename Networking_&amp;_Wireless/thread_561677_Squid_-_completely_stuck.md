---
title: "Squid - completely stuck"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by grandsatrap on 2007-09-27
I am having a terrible time trying to get squid proxyto work.   I have spent about 10 hours on it!
Main problems are indicated with ***
I have Ubuntu 6.06 LTS

Here is what is working:

1. I have set up my ASDL modem to do port forwarding (it calls it NAT rules)
    port 837 is forwarded to 192.168.1.7:3128    [my Linux machine]  [Why use the obvious 3128 - am I being too clever?]
    port  22 is forwarded to 192.168.1.7:22

2. I have set up my router to do port forwarding (it calls it Virtual Server).
   port 837 is forwarded to 192.168.1.7:3128  [both TCP and UDP]
   port  22 is forwarded to 192.168.1.7:22
*** I don't know if I need to do port forwarding on both the ASDL modem and the router.


3. I can ssh to my Linux  machine from INSIDE my home network

4. I can ssh to my Linux machine from OUTSIDE my home network

5. I can use the Squid proxy from INSIDE my home network. I just set my browser to use the proxy: 192.168.1.7 : 3128
   My squid.conf file is below.
   I have not used the http_accel options.

*** 6. I CANNOT get Squid to work at all from OUTSIDE my home network. I set my browser to use proxy 209.100.100.100 (in this message it is a fake IP) and port to 837

I have tried everything! 
In my /etc/hosts.allow file I have only used "ALL : ...." This means that it should apply to all protocols/programs. (i.e. both ssh and squid)

*** For some reason, my /etc/inetd.conf file has zero length!  There is nothing in it. I am sure that a few days ago, it was not empty. I looked back through my sudo command history and didn't see anywhere where I edited it. What do I do about it?

*** I would also like to be able to use SSH tunneling to browse the web from work, but I can't get it working even without tunneling. I want to tunnel to Linux from a laptop running Windows 98 SE and Firefox.

Important parts of my squid.conf file:
=========================================================
#Default:
http_port 3128

# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS

# Example rule allowing access from your local networks. Adapt
# to list your (internal) IP networks from where browsing should
# be allowed
#acl our_networks src 192.168.1.0/24 192.168.2.0/24
#http_access allow our_networks
acl localnet src 192.168.1.0/255.255.255.0
http_access allow localnet
# for testing
acl worknet srcdomain .uwo.ca
http_access allow worknet
# more testing
acl worknet2 srcdomain .tvdsb.on.ca
acl worknet3 src 209.100.100.100 [this is my IP from "whatismyip.com"]
http_access allow worknet2
http_access allow worknet3
http_access allow localhost

# And finally deny all other access to this proxy
#http_access deny all
# IN DESPERATION!!!
http_access allow  all
========================================================

Help, and thanks.

---

### Post by Maxtorm on 2007-09-29
It could be your specification of the allowed subnets. Squid uses /#ofbits notation, whereas you're using x.x.x.x notation. Try changing the 192 mask from 255.255.255.0 to /24 and add a /32 to the worknet3 mask. 

Also, remove the port forwarding from the modem. It should only be necessary on the router.

---

### Post by grandsatrap on 2007-10-01
Thanks for your help. It fixed the problem. I deleted the ASDL modem NAT routing info (and I also decided not to try and use the router to change from port 837 to port 3128). This seems to have fixed the problem,

Squid works fine with the 255.255.255.0 version of netmask.

Thanks again.

---

