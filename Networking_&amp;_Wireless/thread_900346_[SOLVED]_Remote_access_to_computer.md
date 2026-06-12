---
title: "[SOLVED] Remote access to computer"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by wilson47 on 2008-08-25
Hi Guys,

I run Ubuntu 8.04 Desktop edition on my home desktop and will be studying in Germany next year and will only be able to bring my laptop. I would really like to set up my PC so that I can securely access my files and a shell. So, essentially, I would like to use ssh and scp (i think that should do). The finer points of the networking above me are a bit of a mystery. I was able to use ssh and scp through my local network (at least that is what i think), because my IP address from whatismyip.com returns something completely different from what i used to connect between my two computers. How do I go about setting this up? Do I need to figure out how to do this using something like no-ip.com? Can anybody provide me with more specific instructions on setting up my computer with no-ip.com or similar?

I know there are a bunch of tutorials and how-tos out there, but I still haven't found anything that works for me yet. If you don't feel like giving me a full run-down, any links would be greatly appreciated. 

Thanks very much!

---

### Post by wilson47 on 2008-08-25
So this is what I think I need to do from lots of searching... I'm at work so I won't be able to try until later tonight, so if you see an issue please let me know.

My computer that I want to access remotely is called glen-desktop, but for sake of argument, let us call it HOME; similarly, call my laptop LAPTOP. 

HOME goes through a router, and so is given a local IP address from the router. With HOME and LAPTOP on the local network, I was able to ssh and scp from LAPTOP to HOME using ssh USER@HOME after adding 
```
local-IP-address HOME 
```
into /etc/hosts.

Now the problem is that I want to get access when LAPTOP is not connected to the local network, but from anywhere. So I need to obtain the IP address of the router, I guess using whatismyip.com or something, then figure out what port I want LAPTOP to connect to HOME through and open up that port in the router by doing [http://router-IP-address](http://router-IP-address) on HOME. I should hopefully be able to find my way through there to open that up and forward the request on my router at a certain port to HOME. 

Hopefully once I get into my router configuration I should see what to do? I think I read that port 22 is default for ssh, but I can choose to use another port as long as I modify the .conf file. 

The above should let me be able to access HOME with LAPTOP when LAPTOP is not connected to the local network, I think... 

Then setting up my routers IP address with no-ip.com should give me a host-name that I can use instead of the IP address, and also set up a program that will update the IP address for my host-name when the IP address on my router changes. But this is only necessary if I can't check what IP address my router has at the time I want to connect, and the IP address were to change.

After that I need to worry about security, and from what I read, a good start is to use RSA or DSA public key encryption for ssh and to eliminate login with just a password. Also change the port, and for web browsing to use a SOCKS proxy and change the setting in firefox to do all lookups on HOME instead of whatever LAPTOP is directly connected to. 

Help? Suggestions? Thanks everyone...

---

### Post by Iowan on 2008-08-27
Have you seen this [VPN]("https://help.ubuntu.com/community/SSH_VPN") How-To?

---

### Post by wilson47 on 2008-12-28
My issue was that i needed to set up port forwarding with my router. It was pretty self explanatory when I accessed the router configuration.

---

