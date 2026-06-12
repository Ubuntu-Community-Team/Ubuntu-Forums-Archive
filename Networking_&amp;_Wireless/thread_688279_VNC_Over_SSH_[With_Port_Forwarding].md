---
title: "VNC Over SSH [With Port Forwarding]"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by Naveen Chandran on 2008-02-05
Hi all!

I am trying to build an app of VNC over ssh...

I am confused abt this port forwarding thing...

Scenario:


Home PC     --     ADSLMODEM       --               Internet                --  ADSLMODEM         -- Office PC 


for both my home pc and office pc I have installed Ubuntu..  I have installed OpenSSH Server...

I am able to browse the Internet on both my PC's

I have assigned my Home PC 

IP address: 192.168.1.2
Gateway   : 192.168.1.1
My Public IP is 59.92.85.49 and is dynamic...



Similarly on my Office PC


IP address: 192.168.1.5
Gateway   : 192.168.1.1
My Public IP is 59.92.85.34 and is dynamic...


My ISP have all the ports open ... How do I do a NAT Traversal without modifying anything on the Modems using SSH? I need to tunnel vnc over ssh

How do I Port Forward? 
What is the advantage of reverse tunneling?

I have gone through the guides but I could not get what remote port means

Expecting your answers :-)

NC

---

### Post by Wharf Rat on 2008-02-05
If the host machine (the one you plan to control) has a dynamic IP how are you going to find it?

SOMEPLACE in your equation, you need to be able to find the host.  Do you have a domain name at the office?
 If not get one through Dyndns.org
They will keep track of your ip address as it changes dynamically.  

You then point the client to [email]mypc@myofficedomain.com[/email]  Or  [email]192.168.1.5@myofficedomain.com[/email]  and it should work.

Of course your office firewall needs to forward VNC over to the machine (192.168.1.5).

While I used a fixed ip for my office domain, I use VNC to control two windows machines from my Ubuntu laptop.

A bit sluggish and remote video never works, but it is still useful.

---

### Post by Naveen Chandran on 2008-02-05
Say, I know the Dynamic IP of my Office PC as well or I already have a DynDNS...

I need to use SSH ... I don't have access to the Modem/Router to forward the port.. I believe it is possible without access to the router by use of SSH port forwarding mechanism by NAT punching / Traversal...

I want to know abt the ssh options

     -L [bind_address:]port:host:hostport

and also about reverse tunneling thing...

---

