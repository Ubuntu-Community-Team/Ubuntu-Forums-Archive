---
title: "iptables --add-set is not working"
date: 2021-06-25
forum: Networking &amp; Wireless
---

### Post by atlantakid on 2021-06-25
I am trying to take advantage of iptset and iptables-extensions for my iptables.  I have the following the first statement works but the next one gives me an error, the man pages of iptables-extensions says I have --add-set feature but I am getting the following error.

I am trying to set a honeypot trap for port 25 which I do not have a service behind it and catch IP addresses automatically and block them in later statements.

My ipset version is: "ipset v7.5, protocol version: 7" and my OS version is "Ubuntu 20.04.2 LTS"

This code works.
```
sudo iptables -A INPUT   -m set --match-set aa_block_network src -j LOG_DROP
```

But the iptables statement below does not work!  Can you please advise.

```
sudo ipset --create honeypot_trap hash:ip hashsize 4096 maxelem 8192
sudo iptables -A INPUT -p tcp --dport 25  --add-set honeypot_trap src -j SET
iptables v1.8.4 (legacy): unknown option "--add-set"
Try `iptables -h' or 'iptables --help' for more information.
Or below has the same issue
sudo iptables -A INPUT -p tcp --dport 25  -m set --add-set honeypot_trap src -j SET

```

---

### Post by TheFu on 2021-06-25
I won't pretend to be an expert.

I don't use 
```
--add-set
```
.  I use 
```
--match set --match-set honeypot_trap
```

Followed a how-to guide from Linux.com or some Linux magazine article.
Also, I don't append the rules. I insert them at the top, since anything I deem bad enough to be in an ipset needs to be handled before anything else. Period. But our uses appear to be different. 

Inside my saved iptables file, it looks like this:
```
-A INPUT --match set --match-set countryblock  src --jump DROP
```

In my setup, countryblock has to exist and be filled PRIOR to iptables starting. Getting that working took longer than I care to admit.

---

### Post by Doug S on 2021-06-30
Did you get your issue figured out? Out of interest, I tried it and it seems to work.

Here is my test iptables rule set script:

```
doug@s19:~/iptables$ cat add-set.sh
#!/bin/sh
#
# add-set.sh 2021.06.29
#       experiment with add-set
#       see also: https://ubuntuforums.org/showthread.php?t=2464167
#       currently on s19.
#

# The location of the iptables program
#
IPTABLES=/sbin/iptables

# Set some stuff
#
EXTIF="enp3s0"
UNIVERSE="0.0.0.0/0"
EXTIP="192.168.111.136"

# Clearing any previous configuration
# and setting policies

echo clearing main tables
iptables -P INPUT ACCEPT
iptables -F INPUT
iptables -P OUTPUT ACCEPT
iptables -F OUTPUT
iptables -P FORWARD ACCEPT
iptables -F FORWARD

echo clearing nat tables
iptables -t nat -P INPUT ACCEPT
iptables -t nat -F INPUT
iptables -t nat -P OUTPUT ACCEPT
iptables -t nat -F OUTPUT
iptables -t nat -P FORWARD ACCEPT
iptables -t nat -F FORWARD
iptables -t nat -P PREROUTING ACCEPT
iptables -t nat -F PREROUTING

# Otherwise, I can not seem to delete it later on

echo delete chains main
iptables -X
echo delete chains nat
iptables -t nat -X

# Clear the counters

iptables -Z
iptables -t nat -Z

# Restore ipset stuff
#

echo "  Restoring any ipset lists.."

# Flush any existing lists.
# I wonder if I actually need to do this.
# Yes.
# broken. Hack seems to be sleeps
#
echo "  ipset: flush and destroy china..."
ipset flush jail
sleep 1
ipset destroy jail
ipset restore --file /home/doug/iptables/doug.ipset

$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# for this testing use the telent port as the get into jail port
#
$IPTABLES -A INPUT -p tcp --dport 23 -d $EXTIP -j SET --add-set jail src

# now check jail birds list
#
$IPTABLES -A INPUT -m set --match-set jail src -j DROP
```

Here is a current inquiry:

```
doug@s19:~/iptables$ sudo iptables -xvnL
Chain INPUT (policy ACCEPT 4771 packets, 507326 bytes)
    pkts      bytes target     prot opt in     out     source               destination
    3261  5556228 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
       7      420 SET        tcp  --  *      *       0.0.0.0/0            192.168.111.136      tcp dpt:23 add-set jail src
     334    31146 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0            match-set jail src

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 2817 packets, 10867155 bytes)
    pkts      bytes target     prot opt in     out     source               destination
```

Here is the current jail list:

```
doug@s19:~/iptables$ sudo ipset list jail
Name: jail
Type: hash:ip
Revision: 4
Header: family inet hashsize 1024 maxelem 65536
Size in memory: 248
References: 2
Number of entries: 1
Members:
192.168.111.1
```

And I created it with:

```
doug@s19:~/iptables$ sudo ipset create jail hash:ip
doug@s19:~/iptables$ sudo ipset save --file doug.ipset
```

---

### Post by TheFu on 2021-06-30
Doug, you probably want to use subnets, not IPs, if this is something you are serious about.  There are different types of hashes for each.

ipset has a test feature.
```
sudo ipset test jail 123.149.82.245
```
Useful with large sets, so duplicates aren't added - well - they will be refused, but nobody likes seeing errors.

---

### Post by Doug S on 2021-06-30
> **TheFu said:**
> Doug, you probably want to use subnets, not IPs, if this is something you are serious about.Yes, agreed and Thank you. For this test, I was just trying to do similar to the OP. For my real country related stuff, I use subnets.

> **TheFu said:**
> ipset has a test feature.
```
sudo ipset test jail 123.149.82.245
```
Useful with large sets, so duplicates aren't added - well - they will be refused, but nobody likes seeing errors.I did not know, thank you.

---

### Post by TheFu on 2021-06-30
> **Doug S said:**
>  I did not know, thank you.

The only reason I learned this was due to LE certs failing to renew beginning about 18 months ago when they mandated multiple validation locations around the world.  In the end, their servers kept jumping around as to be unpredictable (for me), so every 2.5 months, I disabled all my IPsets for the 8 minutes it takes to renew all the certs.  There are other solutions, like manually doing the DNS TXT record, but that's much more hassle with my DNS provider and it isn't worth my effort to automate.  Whereas I have the drop ipsets, do stand alone certs, then do webapp certs 100% all automated.  Only took about 3 tries to get correct. ;)  Hard to troubleshoot a script that gets run once every 2.5 months. ;)

---

