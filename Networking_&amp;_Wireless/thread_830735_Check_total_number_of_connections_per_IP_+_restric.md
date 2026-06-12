---
title: "Check total number of connections per IP + restrictions"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by danny_b85 on 2008-06-16
Hi all,

I have somewhat of a problem which I haven't been able to solve on my own so far so I want to ask anybody who's willing to help for some assistance.

I'm working on a server which gets overloaded from time to time on the networking part due to the large number of TCP/UDP connections and an IP ban is required from time.

Now I'm checking the number of connections on the server via the following command:
```
netstat -anp | grep 'tcp\|udp' | sed -n -e '/[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}/p' | awk '{print $5}' | sed 's/::ffff://' | cut -d: -f1 | sort | uniq -c | sort -n
```

Which gives me an output something like this:
```

     38 123.123.123.123
     42 123.123.123.124
     47 123.123.123.125
     49 123.123.123.126
     59 123.123.123.127
     68 123.123.123.128
     71 123.123.123.129

```

In the output the first column contains the number of simultaneous connections to the server from any one IP address. If I see more than 90 simultaneous connections from any IP, I ban it via:
```
csf -td IP
```

Right now I'm doing this manually but I want to automatize this via a script. What I've tried so far is this:

```
#!/bin/bash
VAR=`netstat -anp | grep 'tcp\|udp' | sed -n -e '/[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}/p' | awk '{print $5}' | sed 's/::ffff://' | cut -d: -f1 | sort | uniq -c | sort -n`
if [ $1 > 90 ]; then
for line in $VAR; do 
csf -td $2
done
fi
```

and:

```
#!/bin/bash
VAR=`netstat -anp | grep 'tcp\|udp' | sed -n -e '/[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}/p' | awk '{print $5}' | sed 's/::ffff://' | cut -d: -f1 | sort | uniq -c | sort -n > file`
while read file; do
if [ `cat file | awk '{print $1}'` > 90 ]; then
csf -td `cat file | awk '{print $2}'`
fi
done
```

So far I haven't had any luck with either of the two, my guess is that for the first script the $1 argument from the if statement doesn't take the the output from the above mentioned variable VAR, as for the second script I don't get why it doesn't work, theoretically the second script should have worked.

Does anyone have any ideas related to this, suggestions, maybe even another way of achieving the same goal?

Thank you in advance

---

