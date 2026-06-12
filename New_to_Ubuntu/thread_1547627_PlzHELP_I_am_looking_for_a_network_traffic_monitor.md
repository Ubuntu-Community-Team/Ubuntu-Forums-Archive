---
title: "PlzHELP: I am looking for a network traffic monitor"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by fremantle on 2010-08-07
I looked all over the net and failed to find one for linux. It has to be similar to netlimiter in windows... it MUST have

[LIST]
[*]list of incoming and out going network connections
[*]with ip addresses
[*]also it should list running programs which are using the internet with incoming and outgoing transfers (also ips)
[/LIST]

any help guys???

---

### Post by bodhi.zazen on 2010-08-07
Wireshark

From the command line you can use

```
netstat -ntulp
```

Or lsof

```
lsof -i -n -P
```

There are other options as well, ntop for example.

see also

[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)

[http://www.walkernews.net/2007/05/27/linux-commands-to-check-network-connection/](http://www.walkernews.net/2007/05/27/linux-commands-to-check-network-connection/)

---

### Post by The Cog on 2010-08-07
For looking at what connections are going on, I rather like **iftop** (command line) and **etherape**. For real detail - looking at packet contents, wireshark. But I'm not aware of any monitor that will also tell you which running program is using the network.

---

### Post by neoargon on 2010-08-07
> **fremantle said:**
> I looked all over the net and failed to find one for linux. It has to be similar to netlimiter in windows... it MUST have

[LIST]
[*]list of incoming and out going network connections
[*]with ip addresses
[*]also it should list running programs which are using the internet with incoming and outgoing transfers (also ips)
[/LIST]

any help guys???

the software named knemo will help you . It's in repository

---

### Post by HermanAB on 2010-08-07
Read the man pages of ntop, tcpdump and wireshark.

---

### Post by Paddy Landau on 2010-08-07
I once was recommended both [wireshark]("apt:wireshark") and [darkstat]("apt:darkstat"). See [explanation]("http://www.debianadmin.com/network-traffic-analyzer-for-your-ubuntu-system.html").

---

