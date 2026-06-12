---
title: "[ssh]Can't connect to LAN PC managed by NAT"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by jsatubnutufroums on 2007-11-25
Hi, everyones:
Consider the following flow:
```
WAN PC(140.92.xxx.1) <--> NAT Server(140.92.xxx.2) <--> LAN PC(192.168.1.2)
```
I want to remotely login to LAN PC from WAN PC with SSH. I have already install SSH server on LAN PC and set up the DNAT setting:
```
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 22 -j DNAT --to 192.168.1.2:22
```
But it isn't work!!! Is this connection possible??? or What shall I do???

---

### Post by elctb on 2007-11-26
I usually do that with port forwarding. You need to also install the ssh server in the NAT Server and make sure you can ssh to it from WAN PC and that then you can ssh into LAN PC form the NAT Server.

Then you configure the NAT Server to forward the traffic to LAN PC:

. Choose a port between 1024-65535, something like 12345.
. Execute the following command on WAN PC:
```
ssh -l <your-login-name> -N -L 12345:LAN-PC:22 NAT-Server
```
. To regain the shell, you can do the following:
```
CTRL-z
bg
```

Now to login to LAN-PC from WAN-PC you do:
```
ssh -X -p 12345 localhost

```

If you need more information, read about ssh port forwarding.

---

### Post by jsatubnutufroums on 2007-11-26
Thank you.:KS

---

