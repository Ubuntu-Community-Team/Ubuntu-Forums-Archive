---
title: "How do I set IP range for UFW"
date: 2014-03-11
forum: Networking &amp; Wireless
---

### Post by p2bc on 2014-03-11
Trying to set a server for a small business. They allocated a set of ranges of IP addresses for different departments, and want to give departments access so by IP address.

So the accounting department is 10.0.1.30 to 10.0.1.60

I would like to make a UFW entry to demonstrate this without having to entre 30 entries manually.

```

sudo ufw deny from 10.0.1.1/24 to any port 631
sudo ufw allow from 10.0.1.30 to any port 631
sudo ufw allow from 10.0.1.31 to any port 631
sudo ufw allow from 10.0.1.32 to any port 631
...

```

Would love a simple one line entry that would cover the range I need like (although I know it does not work):

```

sudo ufw allow from 10.0.1.30-50 to any port 631

```

Any help would be appreciated.

---

### Post by tomearp on 2014-03-11
I don't think you can use IP ranges with ufw (if I'm wrong, no doubt someone will chime in!).

If you use iptables directly then you can use the iprange module, e.g.:
```
sudo iptables -A INPUT -p tcp --dport 631 -m iprange --src-range 10.0.1.30-10.0.1.60 -j ACCEPT
```

The order of rules is also important, once a rule matches then the packet is handled by that rule and no further processing occurs. 
To put it another way, your first rule to deny 10.0.1.1/24 to port 631 will match all addresses in the range 10.0.1.0 - 10.0.1.255. The subsequent rules will not get processed.

The [man page]("http://manpages.ubuntu.com/manpages/precise/en/man8/iptables.8.html") is worth a read, there are also lots of guides available on a popular search engine that should get you started.
The [community help wiki page]("https://help.ubuntu.com/community/IptablesHowTo") is also good.

---

### Post by houstonbofh on 2014-03-12
Can you change the ranges they picked?  Because this can be done with summery routes.  For example 10.0.1.1/29 is 10.0.1.1-7, and so on.

---

### Post by p2bc on 2014-03-12
@tomearp : I am not adverse to using iptables directly, it is more the lack of knowledge. Haven't played with them since my Fedora day way way ... way back when. But I could look into it. But I have to admit I am kinda partial to the "Uncomplicated" part of UFW.

@houstonbofh : Could you elaborate please. I am creating the infrastructure so I have some latitude as to its setup, I am just not sure what you mean. I found this [link]("http://wiki.xtronics.com/index.php/IP_Subnet_Masks"), and by that wouldn't "/27" because that would give me a group of 32 to chose from, but how does that limit some and not the others. It seems to be the right directions,I just don't fully understand how it works.

---

### Post by p2bc on 2014-03-12
Ok so if I am understanding this right.

```

sudo ufw allow from 10.0.1.32/27 to any port 631

```

Should give me what I am looking for.

Allow ip address from
10.0.1.32 to 10.0.1.64


??? Is this correct ???

---

### Post by p2bc on 2014-03-12
So I just went for it, because that is the way I roll, so dangerously. 

1.  I tried to print with UFW disabled - Worked was able to print. Setting base line.
2.  Enabled UFW and tried to print with not entries. Worked was able to print.
3.  Deny 'All'. Could not print.
4.  Allow certain IPs with: 
```
sudo ufw allow from 10.0.1.32/27 to any port 631
```

               Could not print since my IP was not in that range.
           5.  Manually changed IP to one within the allowed range. Could print.

 

Yea! I love it when things work.

Thanks for the collaboration. I did not know you could control the subnet mask like that. I thought it was a matter of syntax. Thanks for putting me onto the right path.


Happy Dance \\:D/

Another one solved.

---

### Post by houstonbofh on 2014-03-23
Sorry...  I only get on from time to time.

The slash notation is from CIDR, and it is also used to describe groups of IPs.  So, yes, your /27 was exctly what you needed.  Summery routes are also handy if you have more than one router and leased lines and IPsec VPNs, and MPLS networks...  (No need to understand all that)  You can lump several netowrks togeather and say "All of these guys are behind router number 3 over there."  I have a /23 summery route at home.  One /24 for my lan, and one /24 for my wireless...

---

