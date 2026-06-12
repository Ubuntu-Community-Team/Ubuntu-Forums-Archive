---
title: "No Internet Access over Port 80 Anymore"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by invisiblelunatic on 2008-01-04
Hello All!

I'm starting this thread because I haven't found one with a similar problem to the one I'm experiencing.

I'm using an almost freshly installed Kubuntu 7.10 on my laptop.

We have wireless internet access in my building. For the first month things were working fine, but then all of a sudden I can't access HTTP pages anymore. You try [http://www.gmail.com](http://www.gmail.com) in Konqueror and immediately "Could not connect to host www.gmail.com" appears. But if you try [https://www.gmail.com](https://www.gmail.com), everything runs smoothly.

I can't explain it because when I bring my work laptop home (Win XP), it has absolutely no problems accessing the internet.

I know this is vague, but what kind of software can block outgoing traffic on port 80? I'm trying to figure out what I installed. For sure I don't have Firestarter installed.


Thanks,
IL

---

### Post by metoor30 on 2008-01-04
The first thing that comes to mind is iptables -L and netstat -ant.  Can you post the output of these commands.  When something immediately comes up as unavailable, it is usually because it is blocked.

---

### Post by invisiblelunatic on 2008-01-04
> **metoor30 said:**
> The first thing that comes to mind is iptables -L and netstat -ant.  Can you post the output of these commands.  When something immediately comes up as unavailable, it is usually because it is blocked.

Here are the results.....

sudo iptables -L
```

Chain INPUT (policy ACCEPT)
target     prot  opt  source      destination

Chain FORWARD (policy ACCEPT)
target     prot  opt  source      destination

Chain OUTPUT (policy ACCEPT)
target     prot  opt  source      destination

```

netstat -ant
```

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address          Foreign Address     State
tcp              0           0  0.0.0.0:111            0.0.0.0:*                LISTEN
tcp              0           0  0.0.0.0:52374        0.0.0.0:*                LISTEN
tcp              0           0  127.0.0.1:631        0.0.0.0:*                LISTEN

```

---

### Post by metoor30 on 2008-01-04
Nothing there... Have you tried another browser?  Install firefox and see if that works.  If not, there is a package called tcptraceroute.  You can use this like traceroute on cisco, windows or linux equipment, but instead of icmp (ping) you can use it for tcp ports.  This would be helpful in finding where you are being blocked.  You can install it by sudo apt-get install tcptraceroute.

---

### Post by metoor30 on 2008-01-04
Also, try running 'telnet [www.google.com](www.google.com) 80' before installing tcptraceroute.

---

### Post by invisiblelunatic on 2008-01-04
> **metoor30 said:**
> Nothing there... Have you tried another browser?  Install firefox and see if that works.  If not, there is a package called tcptraceroute.  You can use this like traceroute on cisco, windows or linux equipment, but instead of icmp (ping) you can use it for tcp ports.  This would be helpful in finding where you are being blocked.  You can install it by sudo apt-get install tcptraceroute.

I've tried using firefox.
Immediately:
"Firefox can't establish a connection to the server at www.gmail.com."

Unfortunately I cannot use the package manager because of the same problem. I cannot connect.

telnet [www.google.com](www.google.com) 80
```

Trying 209.85.135.147...
Trying 209.85.135.99...
Trying 209.85.135.103...
Trying 209.85.135.104...
telnet: Unable to connect to remote host: Connection refused

```

Wait....does that mean it knows the IP addresses...but it cannot connect??

---

