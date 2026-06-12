---
title: "ufw not working correctly"
date: 2013-12-08
forum: Networking &amp; Wireless
---

### Post by rmi2 on 2013-12-08
Hi,

I just enabled ufw on my Ubuntu 12.04.

```
[10:32:42] [~]
-> # ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
22                         ALLOW IN    Anywhere
443                        ALLOW IN    Anywhere
80                         ALLOW IN    Anywhere
64740                      ALLOW IN    Anywhere
64739                      ALLOW IN    Anywhere
25565                      ALLOW IN    Anywhere
8888                       ALLOW IN    Anywhere
64553                      ALLOW IN    Anywhere
Anywhere                   DENY IN     78.58.199.xxx
```

The last IP is one I want to ban (because it bruteforces my ssh and fail2ban doesn't catch him as he's delaying his retries). Unfortunatly, it doesn't work:

```
netstat -atnp
[..]
tcp        0      0 5.45.xx.xxx:22          78.58.199.xxx:60895     ESTABLISHED 30076/sshd: root
[..]
```

He is still able to connect. Did I configure anything wrong?

Greetings,
rmi

---

### Post by bashiergui on 2013-12-08
I believe it works like iptables. You have to put the deny first, then the allow below it. 

Is that guy really the only one that bruteforces ssh? It might make sense to deny all in and then allow from the IPs you know you'll use.

You could also move ssh to a nonstandard port to avoid the constant bruteforcing from the internet. For some reason the scripted scans don't seem to bother with nonstandard ports.

---

### Post by sammiev on 2013-12-08
I deny both in and out and then setup my rules for out only.

Status: active
Logging: on (low)
Default: deny (incoming), deny (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
80/tcp                     ALLOW OUT   Anywhere
443/tcp                    ALLOW OUT   Anywhere
25/tcp                     ALLOW OUT   Anywhere
110/tcp                    ALLOW OUT   Anywhere
143/tcp                    ALLOW OUT   Anywhere
67/udp                     ALLOW OUT   Anywhere
68/udp                     ALLOW OUT   Anywhere
123/udp                    ALLOW OUT   Anywhere
53                         ALLOW OUT   Anywhere
631                        ALLOW OUT   Anywhere
515                        ALLOW OUT   Anywhere
1194/udp                   ALLOW OUT   Anywhere

---

### Post by bashiergui on 2013-12-09
> **sammiev said:**
> I deny both in and out and then setup my rules for out only.
That would be awesome if rmi2 didn't want anyone including himself to connect to his servers. Not sure why you'd run a web & ssh server that *no one* could connect to.

Actually... Hang on. Are all those ports servers? 
                  22                 Ssh        
443                Web server    
80                  Web server    
64740             
64739             
25565                 
8888                     
64553

---

### Post by ub-newbie on 2013-12-13
rmi2, 
 It is my understanding the firewall rules are processed in order.  Since your first rule is to allow into port 22 from anywhere, that's the ballgame.
Try moving your deny rule to the top/first position.  You can see the rules numbers with "[FONT=Courier New]sudo ufw status numbered[/FONT]"
Then," [FONT=Courier New]sudo ufw insert 1 deny from 78.58.199.xx[/FONT]x"  (I think, I was following instructions from [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)  )

---

