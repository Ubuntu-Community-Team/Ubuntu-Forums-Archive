---
title: "UFW/gUFW"
date: 2013-10-25
forum: Networking &amp; Wireless
---

### Post by Azyx on 2013-10-25
Hey.
I have trie to understand UFW/gUFW and locking here: [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

I can't understand the ruleset a bit down on the page:

```
sudo ufw status

Firewall loaded

To                         Action  From
--                         ------  ----
22:tcp                     DENY    192.168.0.1
22:udp                     DENY    192.168.0.1
22:tcp                     DENY    192.168.0.7
22:udp                     DENY    192.168.0.7
22:tcp                     ALLOW   192.168.0.0/24
22:udp                     ALLOW   192.168.0.0/24
```

Does this mean that 192.168.0.0/24 (submask 192.168.0.1-192.168.0.254)  are allowed, except 192.168.0.1 and 192.168.0.7 for udp/tcp on port 22? Does the order of the rules have any meaning?

/Cheers

---

### Post by Toz on 2013-10-25
From the ufw manpage ("man ufw" or [here]("http://manpages.ubuntu.com/manpages/precise/man8/ufw.8.html")):
> Rule ordering is important and the first  match  wins.  Therefore  when
       adding rules, add the more specific rules first with more general rules
       later.

..."first match wins". So yes, the order of the rules is important. 192.168.0.1 and 192.168.0.7 are denied while the others in the 192.168.0.0/24 subnet are allowed.

---

### Post by Azyx on 2013-10-25
Thanx. Maybe I need to learn how to read man-pages :)

By the way, my /-partition with 24 GB, nearly get full, on a few minutes( system warned me). I have tried to find what filled up when I started log on ufw, and find that ufw.log and kernel.log  nearly 'explode' with 6-7 GB on a few minutes.
How can a log expand so quickly and how do I remove the logged information?

---

### Post by Toz on 2013-10-25
> **Azyx said:**
> By the way, my /-partition with 24 GB, nearly get full, on a few minutes( system warned me). I have tried to find what filled up when I started log on ufw, and find that ufw.log and kernel.log  nearly 'explode' with 6-7 GB on a few minutes.
How can a log expand so quickly and how do I remove the logged information?
Sounds like you might have full ufw logging enabled.

To check your current logging level:
```
sudo ufw status verbose
```

And to adjust the log level:
```
sudo ufw logging LEVEL
```
...where LEVEL is one of:
>        **off**    disables ufw managed logging

       **low**    logs all blocked packets not matching the default  policy  (with
              rate limiting), as well as packets matching logged rules

       **medium** log level low, plus all allowed packets not matching the default
              policy, all INVALID  packets,  and  all  new  connections.   All
              logging is done with rate limiting.

       **high**   log  level medium (without rate limiting), plus all packets with
              rate limiting

       **full**   log level high without rate limiting

Try adjusting the logging level (or turning it off) to see the effect that is has on log file.

---

### Post by Azyx on 2013-10-25
I truned it off as soon a the system warned me that the 25GB bit /-partition being filled up :( Made a reboot and after a while this messaged turned up :(

I don't know how I can remove all message from UFW. It's not only ufw.log that 'exploded' :( I had  around 7-8 GB in my root-partition before...

---

### Post by Toz on 2013-10-25
If you want to empty out the ufw.log file, try:
```
echo "" | sudo tee /var/log/ufw.log
```

---

### Post by Azyx on 2013-10-25
just as suspected approx 2GB dissapeared :( Now the root-partition is 19GB instead of 9 before...and have now  3 GB left instead of 1GB :(

---

### Post by Azyx on 2013-10-25
just as suspected approx 2GB dissapeared :( Now the root-partition is 19GB instead of approx 9GB before...and have now  3 GB left instead of 1GB :(

I maybe could make a new post and headline, or make a new install?

---

### Post by Azyx on 2013-11-10
I have now turned off loging and trie to make a rules that allow every traffic on my local 8192.168.0.0/24 subnet. 

i have tried find any guide on intenet and thogt i find a way. The problem was that udp was not allowed and I tried to add that according to input box in the picture. As I understand it, IF I want a portrange i Should add tthe firt port after IP-address and the last port in the box below. But it does not work as you can see.

I have tried to find were the rules are stored and maybe edit there, but

```
nano /var/lib/ufw/user.rules
```

But there are no ufw-folder under lib in Ubuntu 12.04lts

[ATTACH=CONFIG]247719[/ATTACH]

What complicated it has being to set up a firewall without firestarter :(

---

### Post by Toz on 2013-11-10
See [this wiki article.]("https://help.ubuntu.com/community/UFW").

>  trie to make a rules that allow every traffic on my local 8192.168.0.0/24 subnet. 
How about:
```
sudo ufw allow from 192.168.0.0/24
```

> 
```
nano /var/lib/ufw/user.rules
```
But there are no ufw-folder under lib in Ubuntu 12.04lts
Have a look in /lib/ufw.

---

### Post by Azyx on 2013-11-10
sudo ufw allow from 192.168.0.0/24-->
viewed in gUFW
     To          Action                 From
Anywhere        Allow in            192.180.0.0/24

Does all traffic from anywhere be allowed now? 

Is this as I asked for, all traffic allowed within the subnet, but I want a port-range. Does traffic to andfrom outside get stopped?

Thanks for the new placement of /lib/ufw :)

---

