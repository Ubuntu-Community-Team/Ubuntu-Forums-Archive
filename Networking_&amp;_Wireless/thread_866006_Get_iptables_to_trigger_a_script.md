---
title: "Get iptables to trigger a script"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by danielsbrewer on 2008-07-21
Is it possible to get iptables to run a script when a certain port is accessed?

The reason I want to do this is the following, I have two computers:
1) A router which is always on.
2) A rarely used web server that I would like to be asleep most of the time.

The router forwards all traffic coming in on say port 80 to the web server.  What I want is that when any traffic on port 80 comes into the router that it runs a script that wakes the web server.

Thanks

---

### Post by SpaceTeddy on 2008-07-21
yes and no. There is not easy solution to this - meaning there is no pre-defined and no pre-compiled module for iptables to do this (as far as i know at least). A quick google search showed the same result. 
However, since iptables does have the userspace hook, you could write that plugin yourself - scary, i know !

but that is the only solution i can think of at the moment. But maybe lightning strikes me during the night and i get a better idea (which i doubt)...

hope it helps :)

---

### Post by danielsbrewer on 2008-07-22
Thanks for confirming what I feared, and I am not sure if I am up to compiling a module myself.

How about this though for an idea.  Is there a way to log entry on a particular port?  If there is, and I think there is, then a script could monitor the log file and when the appropriate line comes up trigger a different script.  Does that sound feasible?

---

### Post by eentonig on 2008-07-22
You could approach this a lot easier. 

- Set up iptables to log port 80 requests to a specific logfile.
- Create a script that monitors (tail -f) that logfile and executes whatever you want when it sees connection attempts to tcp/80. (That's how I used to do port-knocking)

---

### Post by SpaceTeddy on 2008-07-22
would have been my idea too - just dead forward to the appropriate machine (even if it is off) and have a log run beforehand to write into some log file (you might need to mess with syslog or syslog-ng for that). Since the LOG target of iptables does not abort a packets chain run, the packet will still go to the server, but also leave a log entry in the appropriate file - Which you can then use to trigger something if that file is being monitored. 

Thinking about it further - you probably don't need syslog since you can specify a prefix for a log target, which you can then grep out.

Hope it helps :)

---

### Post by danielsbrewer on 2008-07-22
A bit lazy I know, but could you provide me with an example line for IPTABLES.  I can find plenty of stuff about logging dropped packets on the net, but not about logging all packets on a particular port.

---

### Post by SpaceTeddy on 2008-07-22
```
sudo iptables -I FORWARD -p tcp --dport 80 -d a.b.c.d -j LOG --log-prefix="TRIGGER ME NOW !!!"

```

 - change a.b.c.d to the ip of the server (internal)
 - change the "TRIGGER ME NOW !!!" to something more appropriate
 - make sure this line is in the list BEFORE the one acctually accepting the paket. 

cheers

---

### Post by danielsbrewer on 2008-07-28
> **eentonig said:**
> Create a script that monitors (tail -f) that logfile and executes whatever you want when it sees connection attempts to tcp/80. (That's how I used to do port-knocking)

I have been trying to do this, but without much luck.  I have found a way to do it in ksh but as I now want this part of the script to run on my router which only has busybox (ash shell).

Could you tell me how you do it?  It might give me a hint on the right way to go.

Thanks

---

### Post by danielsbrewer on 2008-07-29
```
tail -f some-logfile | awk '/some-pattern/ {system("*run-some-command*")}'
```

This seems to do the trick.  Got this from the unix forums.

---

