---
title: "Problems When Sharing Internet Connection With Vista"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by lichaoir on 2008-05-18
Hello, I've installed Ubuntu 8.04, and I've already connected to the internet throw dsl. This is my configuration in /etc/network/interfaces:

auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

auto eth1
iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0
gateway 192.168.0.1

I've executed these following commands:

echo 1 > /proc/sys/net/ipv4/ip_forward 
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

I've already configured Vista as the following:

address: 192.168.0.2
netmask: 255.255.255.0
gateway: 192.168.0.1

dns: same as Ubuntu's

All I want to do is to let Vista connect to internet through the dsl connection configured on Ubuntu. But now I've failed. What's wrong with my configuration? Please tell me.

Thanks for your discussion and answer!

---

### Post by SpaceTeddy on 2008-05-18
the setup looks correct. Masquerading is enabled on the correct device, the ip's are set and forwarding has been turned on. Your clients configuration seems to be correct too. 

So, here are my questions :)
do you have any firewall software installed on your computer (like firestarter) or can you please post the output of the following command :
```
sudo iptables -L -vnx
sudo iptables -L -vnx --table nat
```

on the windows, can you ping raw ip-addresses in the internet or does that not work either (google ip is 66.249.93.104) ?

have you check if ip_forwarding is really turned on ? you can check with
```
cat /proc/sys/net/ipv4/ip_forward
```

can your vista ping the server (192.168.0.1) ?

let's see if we can figure this out :)

---

### Post by lichaoir on 2008-05-18
OK, Thanks, I'll try and post the result back here.

---

### Post by lichaoir on 2008-05-19
Here's the output of "sudo iptables -L -vnx":

Chain INPUT (policy ACCEPT 3183 packets, 1267684 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 3116 packets, 266458 bytes)
    pkts      bytes target     prot opt in     out     source               destination   

Here's the output of "sudo iptables -L -vnx --table nat":

Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination  

I can't ping google's ip from Vista, but I can ping 192.168.0.1 from Vista.

And the result of "cat /proc/sys/net/ipv4/ip_forward" is 0.

So what's the problem? Please help. Thanks!

---

### Post by SpaceTeddy on 2008-05-19
> **lichaoir said:**
> Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

this is problem No.1. Your masquerading is not enabled. Otherwise your rule would show in the output of the POSTROUTING. But there is nothing to be seen. Make sure you ran the command
```
sudo iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
```
if in doubt, run it again and recheck that 
```
sudo iptables -L --table nat
```
then holds the proper line for the Masquerading

> **lichaoir said:**
> 
And the result of "cat /proc/sys/net/ipv4/ip_forward" is 0.

this is the second problem. 0 in this case means that ip_forwarding is not enabled. Try to run this command and then check again if a 1 comes back
```
sudo sysctl -w net.ipv4.ip_forward=1
```

that should do it... i think :)

hope it helps :)

PS: the fill tutorial on what to do and how to make these settings permanent can be found [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=713874")

---

### Post by lichaoir on 2008-05-19
I've executed "echo 1 > /proc/sys/net/ipv4/ip_forward", but Vista was still unconnected.

---

### Post by SpaceTeddy on 2008-05-19
that command cannot work on a normal ubuntu machine, as you have no rights to write to the /proc tree.
either run 
```
sudo "echo 1 > /proc/sys/net/ipv4/ip_forward"
```
which is the depreicated command, or use
```
sudo sysctl -w net.ipv4.ip_forward=1
```
which is the correct way of doing it. 

Also, the vista will only be able to connect to the internet if ip_forwarding is enabled AND the masquerading is set.

---

### Post by lichaoir on 2008-05-19
I've tried:
"sudo iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE"
"sudo sysctl -w net.ipv4.ip_forward=1"
and restarted both computer, but still don't work, why? Thanks!

---

### Post by tazmannusa on 2008-05-19
The program firestarter works pretty good for ICS and its simple to setup.
Tom

---

### Post by lichaoir on 2008-05-19
Finally! I've found the answer!

I've installed Firestarter, and it helped me solve the problem.

Now I've understood where I did wrong. My Ubuntu connects to internet throw ppp0 but not eth0!

Thanks for SpaceTeddy giving me so many advise, teaching me(an absolute newbie) a lot. Thanks for tazmannusa told me to install Firestart. Thanks!

---

