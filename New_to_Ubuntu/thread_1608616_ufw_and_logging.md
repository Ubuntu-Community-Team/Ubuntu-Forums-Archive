---
title: "ufw and logging"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-10-29
okay what am i doing wrong i want to show the logging report


ray@ray-desktop:~$ ufw -- show ARG
Invalid syntax


show ARG                        show firewall report


tks

---

### Post by cariboo on 2010-10-29
The different ARG's are:

[list]
[*] raw
[*] builtins
[*] before-rules
[*] user-rules
[*] after-rules
[*] logging-rules
[*] listening
[/list]

So the command would look like this:

```
sudo ufw show user-rules
```

The output of the above command will look something like this:

```
IPV4 (user):
Chain ufw-user-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-user-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-user-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-user-limit-accept (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-user-limit (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 5 LOG flags 0 level 4 prefix `[UFW LIMIT BLOCK] ' 
       0        0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable
```

**Note**: I just enabled ufw, I haven't set any rules.

---

### Post by rburkartjo on 2010-10-30
thank you car

---

