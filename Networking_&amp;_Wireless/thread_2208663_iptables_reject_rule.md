---
title: "iptables reject rule"
date: 2014-03-01
forum: Networking &amp; Wireless
---

### Post by cylent on 2014-03-01
I have a program listening on port 9005.


The default  iptables has a reject rule which i cant figure out how to remove.


```
[root@localhost ~]# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     icmp --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:ssh
REJECT     all  --  anywhere             anywhere            reject-with icmp-host-prohibited
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:9005
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:9005
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:9005


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
REJECT     all  --  anywhere             anywhere            reject-with icmp-host-prohibited
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:9005


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```


with this set if i test for port 9005 it shows closed.


if i do:


```
iptables -F
```
then the port responds.


obviously this is bad as i dont want to cancel all the rules.


what to do?

---

### Post by untrustytahr on 2014-03-01
When you are entering the rules, enter the accept port 9005 before you put  in the reject rule.  Alternatively, if you have the reject in, you should use the -I to (insert by line number) instead of -A (append to end).

---

### Post by cylent on 2014-03-01
i cant modify the reject rule as its already in there.

what do you mean by -l ? where should that go in the line? example please?

---

### Post by untrustytahr on 2014-03-01
Do you have sudo access to change the firewall rules?  If so, how are you entering them?
sudo iptables -I INPUT 4   

would insert the rule as the 4th rule in the input table.

---

### Post by SeijiSensei on 2014-03-02
Before you do this, I recommend using the -v (verbose) option so you can see the interfaces involved.  Use "sudo iptables -L -nv".  (The -n switch avoids resolving addresses to host/network names.)  Without the interfaces, you can't really tell what a rule does.  For instance, people often freak out when the first rule in most firewalls appears to accept all traffic, as in your listing above.  As it turns out that rule typically applies only to the lo ("localhost") interface, but that fact is invisible without using the verbose switch.

Once you've seen the detailed rules, you can be more certain what to change.

---

### Post by The Cog on 2014-03-02
It might be easiest to do this to get an editable copy of the current rules:
```
sudo sh -c 'iptables-save > myrules'
```
Then edit that file by removing the reject line (or moving it further down the list) and then load the edited version back in as the new rules with this command:
```
sudo sh -c 'iptables-restore < myrules'
```

---

