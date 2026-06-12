---
title: "Iptables script cleanup help"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by Tom--d on 2008-11-04
Hello,

I need help to clean up this script.
Here it is:
```
#!/bin/bash
iptables -F INPUT
iptables -F OUTPUT
iptables -F FORWARD
iptables -A INPUT -j ACCEPT
iptables -A FORWARD -j ACCEPT
iptables -A OUTPUT -j ACCEPT
iptables -A INPUT -i eth0 -j ACCEPT
iptables -A INPUT -i wlan0 -j ACCEPT
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -A FORWARD -i wlan0 -o eth0
iptables -A FORWARD -o wlan0 -i eth0
```

Its for Xbox live. ICS. Anything wrong with it?


Also, one more thing. how can i stop network manager (0.7) making an auto eth0. I have made an Xbox but everytime I delete the auto eth0. it is re created at every startup!

Thanks.

---

### Post by nixscripter on 2008-11-04
Second question first:

> **Tom--d said:**
> 
how can i stop network manager (0.7) making an auto eth0. I have made an Xbox but everytime I delete the auto eth0. it is re created at every startup!

You can change **/etc/network/interfaces** to have it not be set up automatically. Instead of ```
iface eth0 auto
``` change it to ```
iface eth0 manual
``` and see if that helps.

First question: assuming you are doing IP masqerading, looks good, except you might want to set the chain policy instead of a "catch all rule" like -j ACCEPT. That can be done with the **-P** flag.

---

### Post by Tom--d on 2008-11-05
> **nixscripter said:**
> Second question first:



You can change **/etc/network/interfaces** to have it not be set up automatically. Instead of ```
iface eth0 auto
``` change it to ```
iface eth0 manual
``` and see if that helps.

First question: assuming you are doing IP masqerading, looks good, except you might want to set the chain policy instead of a "catch all rule" like -j ACCEPT. That can be done with the **-P** flag.

Thanks on the Network Manager.

I'm a newb at Iptables.

Why would I need the -P flag? (Please explain :) Im interested).

Also, that script will not make security issues?

---

### Post by nixscripter on 2008-11-05
The -P flag is chain policy. The policy is what to do (what target to use) if none of the rules match the packet. By default, it's ACCEPT; it's common for paranoid sys admins to change it to DROP.

If you have a rule which jumps to ACCEPT, and the chain policy is DROP, there is a tiny chance some clever packet will fail to match it and get dropped. If the script is assuming it has to set up iptables completely -- which is the smart thing to do -- then it would be a good idea to set the chain policy.

In other words, instead of your first three lines: ```
-A INPUT -j ACCEPT
``` use ```
-P INPUT ACCEPT
```

As for security, it depends on what kind of risks you're talking about. If you're just worried about people breaking in, it's pretty good (as good as the security of networking applications you run). If you're worried about Denial of Service or something more complicated, further steps could be taken.

If I knew more about what you were going to use it for, I might make more details suggestions. However, I would say -- based on just looking at it -- it should IP masquerading correctly.

---

### Post by Tom--d on 2008-11-05
With security all  I was wondering is...

since I want Iptables to accept everything which goes to the Xbox but not effect my internet on my Laptop. The only time I have iptables on is for xbox otherwise there is no firewall (since i have no server software etc). Nothing listening on ports (only bittorrent but thats rare and there is always traffic through that).

Basically, I only want iptables to ONLY give ICS. Nothing else.

Please correct me if im wrong as I'm only a beginner in security.


One more thing.
I need port 88 and 3074 opened for the Xbox 360. How do I open them in iptables JUST for Xbox. Do I need to forward them on my router manually as well? Any risks in that?

Last thing :P
When you said. "IP masqerading" in your first post.
I dont know what that does but it works and allows the connection but I heard its for dhcp not static ip. All my connections are static.

---

### Post by nixscripter on 2008-11-06
> **Tom--d said:**
> With security all  I was wondering is...

since I want Iptables to accept everything which goes to the Xbox but not effect my internet on my Laptop. The only time I have iptables on is for xbox otherwise there is no firewall (since i have no server software etc). Nothing listening on ports (only bittorrent but thats rare and there is always traffic through that).

Basically, I only want iptables to ONLY give ICS. Nothing else.

The script shown will forward have the Xbox recieve everything, and only allow TCP connections out of the laptop which it started. That sounds like what you want. The only thing you have to worry about is, for example, your Xbox being packet flooded (which seems unlikely to me), which requires far more drastic steps to fix.

> 
I need port 88 and 3074 opened for the Xbox 360. How do I open them in iptables JUST for Xbox. Do I need to forward them on my router manually as well? Any risks in that?

If you have a router in front of the Xbox, you will need to use port forwarding. That will route incoming connections to the Xbox, which it should accept. That shouldn't affect the laptop.

> 
When you said. "IP masqerading" in your first post.
I dont know what that does but it works and allows the connection but I heard its for dhcp not static ip. All my connections are static.

I simply meant bridging two networks at the Network level (IP addresses). Each interface belongs to a different network, in effect, and packets are forwarded between them if they are the right ones. Usually this is done in conjunction with DHCP, but doesn't have to be. Both interfaces could have their IPs assigned by someone else.

---

### Post by Tom--d on 2008-11-07
Thanks. But I know the xbox needs UDP as well on port 3074 for internet play. How will I go around this?

---

### Post by nixscripter on 2008-11-07
If you accept everything into the Xbox, it should just work. You're not telling it to drop anything with the script.

---

### Post by nixscripter on 2008-11-07
If you accept everything into the Xbox, it should just work. You're not telling it to drop anything with the script.

---

