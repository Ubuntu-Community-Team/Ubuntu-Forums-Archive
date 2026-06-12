---
title: "iptables REDIRECT"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by denver on 2007-04-29
Hello!


My iptables is a little rusty but ive been trying to redirect connections coming to a specific port, to another port on the same machine. Back when i needed this rule i used ( if im not mistaking ):

```
iptables -t nat -A PREROUTING -i ppp0 -p tcp --dport 2222 -j REDIRECT --to-port 22
```

to redirect all connections on 2222 to port 22. Also tried using:

```
 iptables -t nat -A PREROUTING -i ppp0 -p tcp --dport 2222 -j DNAT --to :22
```

but still no joy.( and im using the rule above )
```
root@denver:/home/gaby# telnet 86.123.243.27 2222
Trying 86.123.243.27...
telnet: Unable to connect to remote host: Connection refused
```

```
root@denver:/home/gaby# netstat -tapn | grep ssh
tcp6       0      0 :::22                   :::*                    LISTEN     7066/sshd
```

 Am i missing something? Some special voodoo i'm not aware of?

I'm using Ubuntu Feisty with default kernel.

Thanks in advance!

---

### Post by denver on 2007-04-29
Anyone?...any ideeas?

---

### Post by denver on 2007-04-30
I was trying to connect from my local machine to port 2222 but it apears that the corrent rule in that case would be:

```
 iptables -t nat -A OUTPUT -p tcp --dport 2222 -j DNAT --to :22
```

on the count that if the connection is initiated on the local machine, it does not go through PREROUTING. The rules above work perfectly from the outside.

---

