---
title: "Need Help Executing commands inside of Bash Script"
date: 2021-01-31
forum: Networking &amp; Wireless
---

### Post by twistedknee on 2021-01-31
Hello all - Scripting n00b here. I'm setting up the UFW and I have a file with about 80,000 commands I need to run. I figured I would just loop through the file and execute the commands, but I'm have an issue doing it. Need some help. Here's what I built so far:

SetupUFW.sh
```

#!/bin/bash
while read p; do
  echo "$p"
done < BlockList.txt

```

BlockList.txt (80,000 lines that look like this:)
```

sudo ufw deny from 1.0.1.0/24
sudo ufw deny from 1.0.2.0/23
sudo ufw deny from 1.0.8.0/21

```

As you can see, I'm trying to loop through the file called BlockList.txt as I have already built it with the commands necessary. How can I loop through each line and execute the lines? Any help you can provide would be appreciated.

---

### Post by TheFu on 2021-01-31
ufw can't handle this.
iptables can't handle this.

If you have more than a few hundred rules, use ipset.

But so you see I'm right, just run the BlockList.txt file, directly.
```
chmod +x /path/to/BlockList.txt
/path/to/BlockList.txt
```
Give it 10 minutes to run.  Maybe more.

ipset will use 1 firewall rule for all the subnets, but match that single rule extremely efficiently.
There are a number of how-to guides.

---

### Post by TheFu on 2021-01-31
Would be smarter to only have 1 sudo too.  Remove it from every command in the script, call the script:
```
sudo /path/to/BlockList.txt
```

spawning an extra process for every line is bad. That's what sudo does.

---

### Post by twistedknee on 2021-01-31
Thank you! This is definitely a better way to go. I found a great tutorial online for how to implement. Thank you so much for your suggestion!

Tutorial Link: [How to block IP addresses from a country using IPset - IP2Location.com]("https://blog.ip2location.com/knowledge-base/how-to-block-ip-addresses-from-a-country-using-ipset/#:~:text=How%20to%20block%20IP%20addresses%20from%20a%20country,permission%20to%20blockcountry.sh%20and%20run%20it.%20More%20items")

> **TheFu said:**
> ufw can't handle this.
iptables can't handle this.

If you have more than a few hundred rules, use ipset.

But so you see I'm right, just run the BlockList.txt file, directly.
```
chmod +x /path/to/BlockList.txt
/path/to/BlockList.txt
```
Give it 10 minutes to run.  Maybe more.

ipset will use 1 firewall rule for all the subnets, but match that single rule extremely efficiently.
There are a number of how-to guides.

---

### Post by SeijiSensei on 2021-02-01
I run custom iptables scripts. I put the banned addresses in a file, then use some code like this:
```

EVIL=$(cat /path/to/banned/list)
for h in $EVIL
do
    /sbin/iptables -A INPUT -j REJECT -s $h
done

```
This is usually among the first commands I run in the firewalling script since we just want to drop any packets from these hosts before moving on to any other rules.

---

### Post by TheFu on 2021-02-01
When the number of rules becomes large and many are really just 1 rule, just with hundreds or thousands of subnet matches, using ipset is exponentially more efficient.
```
-A INPUT --match set --match-set countryblock  src --jump DROP
```

The OP has 80K rules.  I only have 6900:
```
$ wc -l /etc/ipset.up.rules
6926 /etc/ipset.up.rules
```

Somewhere around 200, it was noticeably slower both to load and while running.
Put in the single ipset "match-set" and the performance improvements are great.

---

