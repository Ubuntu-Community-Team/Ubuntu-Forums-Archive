---
title: "Port Forwarding Ubuntu Server Blocked"
date: 2015-06-04
forum: Networking &amp; Wireless
---

### Post by wylieza on 2015-06-04
I am trying to run a Minecraft server off a laptop with Ubuntu Server on it.

I port forwarded everything on the router and I could not get it to be picked up as an open port. I wanted to see where the problem lies, so I port forwarded my windows laptop with a Minecraft server and the router port forwarded perfectly. _I have decided that because of this the problem must be caused by software on the Ubuntu laptop and not the router?_

Things I have done:
[LIST]
[*]Looked all over the web for help and guides
[*]The local IP addresses are static in both cases
[*]I make sure to restart my router after every change I attempt (I don't know what I haven't tried)
[*]I make sure that I always use my currant public IP (The one that updates after every router restart)
[*]I have tweaked and fiddled with UFW with no luck
[/LIST]

Does anyone have any idea as to what may be causing Ubuntu Server to block incoming requests?

Thanks in advance :)

---

### Post by houstonbofh on 2015-06-04
Checking with a different system is a good start,but not definitive.  Start the server on your Ubuntu box and see if it can connect locally.  When you are connected and playing, use "netstat" from the command line (I know, but it is the easiest way) to see what ports are being used.

```
netstat -a | grep 192.168.1.25
```
Use the client IP address in the command above.

---

### Post by wylieza on 2015-06-05
> **houstonbofh said:**
> Checking with a different system is a good start,but not definitive.  Start the server on your Ubuntu box and see if it can connect locally.  When you are connected and playing, use "netstat" from the command line (I know, but it is the easiest way) to see what ports are being used.

```
netstat -a | grep 192.168.1.25
```
Use the client IP address in the command above.


Alright so its all very confusing.... (Yes I'm new to port forwarding so ill need a bit of patience :P)


So I pick up two SSH sessions from my ip:

tcp        0      0 192.168.1.111:ssh       192.168.1.222:58027     ESTABLISHED
tcp        0     64 192.168.1.111:ssh       192.168.1.222:58132     ESTABLISHED

I am connected and in the Mincraft server locally and nothing is showing up??? 

Justing running netstat on its own brings up nothing that is related to 25565 (minecraft)

EDIT: The five lines above are related to the Ubuntu command line....
From windows I got:
  TCP    192.168.1.222:58027    192.168.1.111:ssh      ESTABLISHED
  TCP    192.168.1.222:58108    192.168.1.111:25565    ESTABLISHED
  TCP    192.168.1.222:58132    192.168.1.111:ssh      ESTABLISHED




(Ubuntu box is running off static 192.168.1.111 and my windows pc with putty is running off 12.168.1.222 (also static))

PS: All local connections work fine (SSH and the server)

Any more ideas, what to next/ Was I looking for the wrong thing maybe?

---

### Post by The Cog on 2015-06-05
Two things I can think of:
* minecraft is listening on a different port to the port you think
* the server doesn't have a default route back to the internet

Please can you post the output of these two commands. The first lists all ports listening for incoming connections and the second lists the routing table:
```
sudo netstat -lntup
route -n
```

---

### Post by wylieza on 2015-06-05
> **The Cog said:**
> Two things I can think of:
* minecraft is listening on a different port to the port you think
* the server doesn't have a default route back to the internet

Please can you post the output of these two commands. The first lists all ports listening for incoming connections and the second lists the routing table:
```
sudo netstat -lntup
route -n
```

sudo netstat -lntup

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      909/mysqld
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      805/sshd
tcp6       0      0 127.0.0.1:8005          :::*                    LISTEN      990/java
tcp6       0      0 :::8080                 :::*                    LISTEN      990/java
tcp6       0      0 :::80                   :::*                    LISTEN      936/apache2
tcp6       0      0 :::22                   :::*                    LISTEN      805/sshd
tcp6       0      0 192.168.1.111:25565     :::*                    LISTEN      3859/java

route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

---

### Post by The Cog on 2015-06-05
OK. Minecraft (java) is there listening on TCP port 25565.

However, you do not have a default route back to the internet. It can't send its replies to your internet callers.
Try this command to see if it fixes things temporarily (until reboot) but give the address of your router - I'm guessing it:
```
sudo ip route add default via 192.168.1.1
```

If you are using /etc/network/interfaces to set the static address, add this line:
```
     gateway 192.168.1.1
```

---

### Post by wylieza on 2015-06-05
> **The Cog said:**
> OK. Minecraft (java) is there listening on TCP port 25565.

However, you do not have a default route back to the internet. It can't send its replies to your intetrnet callers.
Try this command to see if it fixes things temporarily (until reboot) but give the address of your router - I'm guessing it:
```
sudo ip route add default via 192.168.1.1
```

If you are using /etc/network/interfaces to set the staic address, add this line:
```
     gateway 192.168.1.1
```


YES!

This appears to have worked....
The ip for gateway in the file seems to be wrong....

Just gonna finish double checking its 100%

Thanks for your help!

---

