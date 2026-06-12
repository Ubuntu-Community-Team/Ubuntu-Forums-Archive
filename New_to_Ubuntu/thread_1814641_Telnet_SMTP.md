---
title: "Telnet SMTP"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by °-° on 2011-07-29
I'm trying to send an e-mail via telnet but it just just says "Trying xx.xxx.xxx.xxx..." but I don't receive any error messages even after 10 minutes. Anyone know why this is?

---

### Post by hreichgott on 2011-07-29
1. Are you connected to the Internet?
2. Are you able to contact the host with ping? Try "ping [hostname]"

---

### Post by °-° on 2011-07-29
Yes, I'm connected to the internet and I can contact the host with ping. You use port 25 right?

---

### Post by °-° on 2011-07-31
Anyone?:(

---

### Post by haqking on 2011-07-31
> **°-° said:**
> Anyone?:(

perhaps it does not accept telent connections.

Just cause the ip is live and its a smtp server it doesnt necesarrily allow telnet or even if ti did it might not accept the SMTP commands.

but i take it your format is:

telnet

telnet> open x.x.x.x

---

### Post by °-° on 2011-07-31
Yes and this includes multiple mail servers.. I can't connect to any of them!!

---

### Post by haqking on 2011-07-31
> **°-° said:**
> Yes and this includes multiple mail servers.. I can't connect to any of them!!


upload a screen dump of commands issued and it waiting

---

### Post by uRock on 2011-07-31
Sounds like the firewall is silently dropping the packets.

---

### Post by °-° on 2011-07-31
[IMG]file:///home/steve/Desktop/telnet.png[/IMG]

Not much to it. It'll sit there for a long time before it says it's timed out.

---

### Post by haqking on 2011-07-31
> **°-° said:**
> [IMG]file:///home/steve/Desktop/telnet.png[/IMG]

Not much to it. It'll sit there for a long time before it says it's timed out.


mm well works fine for me.

have you tried the ip address to eliminate resolution issues though i doubt it is that.

---

### Post by °-° on 2011-07-31
@uRock How can I check to make sure?

@haqking That's the arping command right?

---

### Post by e79 on 2011-07-31
```
ping <Domain Name>
```(ex : ping [www.google.com]("http://www.google.ca"))

This should return you the IP address for the given domain name (the server responsible for it will answer with a 'pong' reply).

As **uRock** mentionned, it is most probably a firewall (in your LAN that is) dropping the packet. Do you administer it yourself (router, firewall etc) ? You could then check if you could add a more permissive rule for your tests.

---

### Post by °-° on 2011-07-31
I have no problems pinging any mail servers, they all respond. How do I add a more permissive rule??

---

### Post by uRock on 2011-07-31
> **°-° said:**
> I have no problems pinging any mail servers, they all respond. How do I add a more permissive rule??

I think it is gmail's server blocking telnet, as I have the same issue in this attempt.```
rabbit@ronnie-desktop:~$ ping smtp.gmail.com -c 3
PING gmail-smtp-msa.l.google.com (74.125.127.109) 56(84) bytes of data.
64 bytes from pz-in-f109.1e100.net (74.125.127.109): icmp_seq=1 ttl=53 time=58.5 ms
64 bytes from pz-in-f109.1e100.net (74.125.127.109): icmp_seq=2 ttl=53 time=48.5 ms
64 bytes from pz-in-f109.1e100.net (74.125.127.109): icmp_seq=3 ttl=53 time=47.2 ms

--- gmail-smtp-msa.l.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 47.251/51.449/58.595/5.085 ms
rabbit@ronnie-desktop:~$ telnet
telnet> open smtp.gmail.com 25
Trying 74.125.127.109...
telnet: Unable to connect to remote host: Connection timed out
telnet> ^C
rabbit@ronnie-desktop:~$ 

```

---

### Post by haqking on 2011-07-31
> **uRock said:**
> I think it is gmail's server blocking telnet, as I have the same issue in this attempt.```
rabbit@ronnie-desktop:~$ ping smtp.gmail.com -c 3
PING gmail-smtp-msa.l.google.com (74.125.127.109) 56(84) bytes of data.
64 bytes from pz-in-f109.1e100.net (74.125.127.109): icmp_seq=1 ttl=53 time=58.5 ms
64 bytes from pz-in-f109.1e100.net (74.125.127.109): icmp_seq=2 ttl=53 time=48.5 ms
64 bytes from pz-in-f109.1e100.net (74.125.127.109): icmp_seq=3 ttl=53 time=47.2 ms

--- gmail-smtp-msa.l.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 47.251/51.449/58.595/5.085 ms
rabbit@ronnie-desktop:~$ telnet
telnet> open smtp.gmail.com 25
Trying 74.125.127.109...
telnet: Unable to connect to remote host: Connection timed out
telnet> ^C
rabbit@ronnie-desktop:~$ 

```


i can telnet to gmail fine using exaclty same method he posted in his screen dump.

i connect perfectly everytime though i am connecting to a different IP as when i resolve it resolves to 209.85.143.109

---

### Post by °-° on 2011-07-31
I figured it out! Use port 587:P

---

### Post by haqking on 2011-07-31
actually i can telnet fine to both.

see attachment.

---

