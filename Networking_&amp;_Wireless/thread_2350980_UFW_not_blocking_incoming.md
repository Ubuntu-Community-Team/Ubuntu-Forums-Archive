---
title: "UFW not blocking incoming"
date: 2017-01-29
forum: Networking &amp; Wireless
---

### Post by Frank P on 2017-01-29
New install Ubuntu 16.04 LTS 

UFW status: active; logging: on (low) default: deny (incoming), allow (outgoing), disabled: routed, new profiles: skip

I can ping the IP and access the default apache page.

Suggestions as to why ufw is not working

Thanks

Frank

---

### Post by TheFu on 2017-01-30
Please post real output from the commands and log files. Humans are prone to misinterpreting output.
```
sudo ufw status
ifconfig -a
```
and ```

sudo iptables -L
```
Please use **code tags** so it is readable.

---

### Post by Frank P on 2017-01-30
Okay, here's the output
Thanks
Frank

```

Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

```

```

Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            
Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            
ufw-track-forward  all  --  anywhere             anywhere            
Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            
Chain ufw-after-forward (1 references)
target     prot opt source               destination         
Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-ns
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-dgm
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:netbios-ssn
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:microsoft-ds
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootps
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootpc
ufw-skip-to-policy-input  all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST
Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "
Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "
Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         
Chain ufw-after-output (1 references)
target     prot opt source               destination         
Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp source-quench
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ufw-user-forward  all  --  anywhere             anywhere            
Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ufw-logging-deny  all  --  anywhere             anywhere             ctstate INVALID
DROP       all  --  anywhere             anywhere             ctstate INVALID
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp source-quench
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ACCEPT     udp  --  anywhere             anywhere             udp spt:bootps dpt:bootpc
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             224.0.0.251          udp dpt:mdns
ACCEPT     udp  --  anywhere             239.255.255.250      udp dpt:1900
ufw-user-input  all  --  anywhere             anywhere            
Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         
Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         
Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         
Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ufw-user-output  all  --  anywhere             anywhere            
Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW ALLOW] "
Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere             ctstate INVALID limit: avg 3/min burst 10
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "
Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type LOCAL
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type MULTICAST
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST
ufw-logging-deny  all  --  anywhere             anywhere             limit: avg 3/min burst 10
DROP       all  --  anywhere             anywhere            
Chain ufw-reject-forward (1 references)
target     prot opt source               destination         
Chain ufw-reject-input (1 references)
target     prot opt source               destination         
Chain ufw-reject-output (1 references)
target     prot opt source               destination         
Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            
Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            
Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
Chain ufw-track-forward (1 references)
target     prot opt source               destination         
Chain ufw-track-input (1 references)
target     prot opt source               destination         
Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW
ACCEPT     udp  --  anywhere             anywhere             ctstate NEW
Chain ufw-user-forward (1 references)
target     prot opt source               destination         
Chain ufw-user-input (1 references)
target     prot opt source               destination         
Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 5 LOG level warning prefix "[UFW LIMIT BLOCK] "
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable
Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         
Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         
Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         
Chain ufw-user-output (1 references)
target     prot opt source               destination         


```

---

### Post by TheFu on 2017-01-30
log files?
ifconfig -a?

---

### Post by The Cog on 2017-01-30
Are you trying to test from the same machine or a different machine?

The output from **sudo iptables -L** does not give all the needed information. **sudo iptables-save -c** gives more info.

Please can you post the output of 
```
sudo iptables-save -c
```
then perform your connectivity tests, and then 
```
sudo iptables-save -c
```
for a second time. The change in the counter values will help figure out what is happening.

---

### Post by Frank P on 2017-01-31
I think there's something wrong with my installation. Now I'm getting a "temporary failure resolving ca.archive.ubuntu.com ......"
I'm going to reinstall.
Thanks
Frank

---

### Post by Frank P on 2017-02-01
I'm going to mark this solved - ufw was working correctly. The browser was returning a cached page when I tested after enabling the firewall.
Sorry for wasting your time
Thanks
Frank

---

### Post by The Cog on 2017-02-01
That's OK. You didn't know when you posted the problem.
Thanks for posting the "solution": people who've tried to help will not be left wondering, and others who find the thread later because they have similar problems will know to check for this.

---

### Post by TheFu on 2017-02-01
Always check the log files first.  If the logs don't show it, then it probably isn't happening.

---

