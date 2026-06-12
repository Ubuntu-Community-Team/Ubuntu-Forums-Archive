---
title: "IP tables Permission Denied! Atempting to share internet conection."
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by rick3878894 on 2008-08-24
Howdy. I am working on trying to allow one computer to go through my other nic (eth1) and out into the internet with via my WIFI (eth2).

So I have finally got a handle on how to do this.

I set the client and eth1 (on the internet connected box) to static IP addresses so as to avoid working with DHCP.

Then I started playing with my IP tables. I don't really know what most of it means I am Copy Pasting from a walk through. 

I got this far:
```
xess@xess-desktop:~$ sudo iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
xess@xess-desktop:~$ echo 1 > /proc/sys/net/ipv4/ip_forward
bash: /proc/sys/net/ipv4/ip_forward: Permission denied
xess@xess-desktop:~$ sudo echo 1 > /proc/sys/net/ipv4/ip_forward
bash: /proc/sys/net/ipv4/ip_forward: Permission denied
xess@xess-desktop:~$ iptables-save > /etc/iptables.rules
bash: /etc/iptables.rules: Permission denied
xess@xess-desktop:~$ sudo iptables-save > /etc/iptables.rules
bash: /etc/iptables.rules: Permission denied

```

I know I made it so far... Any way my question is why do I not have permission? How do I fix this?
 
In spite of all this I still have no desire for Windows...

---

### Post by SpaceTeddy on 2008-08-24
you need to execute those commands as root. If you run something like the echo commands (which are obsolete and should not be used anymore) then you need to do so as root. Since you are also using bash output redirection this is better done in a proper root console than via sudo... here are some examples


> sudo su
iptables -P FORWARD ACCEPT
iptables -A POSTROUTING --table nat -o eth1 -j MASQUERADE
sysctl -w net.ipv4.ip_forward=1

that should do what you are trying to do. ALso, pleae notice the first line in the quote - it makes you root. So these commands will also work in root consoles (as they are missing the sudo infront on purpose).

hope it helps :)

---

### Post by rick3878894 on 2008-08-24
Well I can write now and get it save but I can only see as far as the wifi card when pinging from work station. I still can't connect to the router or the internet for that matter.

---

### Post by SpaceTeddy on 2008-08-25
mhm... has your client the right default gateway as well as a correct dns ?
Also, i suspect on the machine in question the internet is working ?
Can you post the ip configuration of your server/router as well as your clients for further debugging ?

thanks

---

### Post by Iowan on 2008-08-27
Late, as usual...
Have you seen [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing")?

---

### Post by rick3878894 on 2008-09-17
Thanks folks. I just built a router for it that plugs into a switch. Simple and effective

---

