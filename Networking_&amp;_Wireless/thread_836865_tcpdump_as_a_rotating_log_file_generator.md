---
title: "tcpdump as a rotating log file generator"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by nullvariable on 2008-06-21
I'm working with fresh install of Ubuntu 8.04 and I've been trying to find a way to use tcpdump (which is already installed) to create rotating logs of say every 24hrs or so filtering out a couple of IP addresses. Basically I want to see traffic on my network from PCs other than my main systems/servers. I'd then like to grab the files and read them on a different machine with WireShark. I'm also wondering if there's an easy way to setup some sort of alert that would send me an email when a new host is spotted, this is less important to me of course. I would imagine that this could all be accomplished with some bash scripts, I just need some suggestions or pointers ( :twisted: Googling various terms with what I want to do doesn't return anything I can work with).

Thanks!!

---

### Post by randomperson83 on 2008-09-10
Did you find a good solution to do this?

---

### Post by nullvariable on 2008-09-10
> **randomperson83 said:**
> Did you find a good solution to do this?

nope...never did :confused:

---

### Post by randomperson83 on 2008-09-10
If you look at the latest version of the tcpdump man page, apparently it supports rotating logfiles (using the -G option). 

[http://www.tcpdump.org/tcpdump_man.html](http://www.tcpdump.org/tcpdump_man.html)

Of course, the version there is newer than the one that Hardy provides (if you man tcpdump on Hardy, there is no -G option)... of course, I haven't used it yet, but that looks promising.

---

### Post by fwre01 on 2008-09-10
i know you can produce pcap files from tcpdump, that can be read into wireshark by using ```
sudo tcpdump -i eth0 -w /home/user/test2.pcap 
```

you could tie it down to as few or as many hosts as you want. but remember you will have to configure monitoring on your switch, unless you are using a hub **shudder**

becasue otherwise you will only see bcast/mcast traffic

---

### Post by randomperson83 on 2008-09-10
Yes, but that doesn't rotate the logs automatically.

---

### Post by fwre01 on 2008-09-10
did u want just the last 24hrs worth of traffic? becasue that wud be relatively easy in crontab

---

### Post by nullvariable on 2008-09-10
yeah...you could run a bash script to do the file rotation for you I suppose (its been a long time since I've tried that myself)

---

### Post by randomperson83 on 2008-09-10
Or use the new tcpdump option. :)

---

