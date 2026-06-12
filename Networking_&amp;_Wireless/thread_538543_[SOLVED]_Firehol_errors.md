---
title: "[SOLVED] Firehol errors"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by ushills on 2007-08-30
I am having a few problems with Firehol on my PC, this morning I lost internet conectivity and when I tried to restart fire hol using

```
Sudo /etc/init.d/firehol restart
```

I got the following errors,  I have not changed my firehol.conf file


```
sudo /etc/init.d/firehol start
 * Starting Firewall 
firehol                                                    

--------------------------------------------------------------------------------
ERROR   : # 1.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 23 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world -p tcp -m state '' 
--state NEW \! --syn -j pr_world_nosyn
OUTPUT  :




--------------------------------------------------------------------------------
ERROR   : # 2.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 24 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_all_c1 -m state '' 
--state NEW\,ESTABLISHED -j ACCEPT
OUTPUT  :




--------------------------------------------------------------------------------
ERROR   : # 3.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 24 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_all_c1 -m state '' 
--state ESTABLISHED -j ACCEPT
OUTPUT  :




--------------------------------------------------------------------------------
ERROR   : # 4.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 24 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_irc_c2 -p tcp --sport 
32768:61000 --dport 6667 -m state '' --state NEW\,ESTABLISHED -j ACCEPT
OUTPUT  :




--------------------------------------------------------------------------------
ERROR   : # 5.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 24 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_irc_c2 -p tcp --sport 
6667 --dport 32768:61000 -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT  :




--------------------------------------------------------------------------------
ERROR   : # 6.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 24 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_ftp_c3 -p tcp --sport 
32768:61000 --dport ftp -m state '' --state NEW\,ESTABLISHED -j ACCEPT
OUTPUT  :




--------------------------------------------------------------------------------
ERROR   : # 7.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 24 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_ftp_c3 -p tcp --sport ftp 
--dport 32768:61000 -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT  :




--------------------------------------------------------------------------------
ERROR   : # 8.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 24 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_ftp_c3 -p tcp --sport 
ftp-data --dport 32768:61000 -m state '' --state ESTABLISHED\,RELATED -j 
ACCEPT
OUTPUT  :




--------------------------------------------------------------------------------
ERROR   : # 9.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 24 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_ftp_c3 -p tcp --sport 
32768:61000 --dport ftp-data -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT  :




--------------------------------------------------------------------------------
ERROR   : # 10.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 24 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_ftp_c3 -p tcp --sport 
32768:61000 --dport 1000:65535 -m state '' --state ESTABLISHED\,RELATED 
-j ACCEPT
OUTPUT  :




--------------------------------------------------------------------------------
ERROR   : # 11.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 24 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_ftp_c3 -p tcp --sport 
1000:65535 --dport 32768:61000 -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT  :




--------------------------------------------------------------------------------
ERROR   : # 12.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 25 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_cups_s4 -p tcp --sport 
1000:65535 --dport 631 -m state '' --state NEW\,ESTABLISHED -j ACCEPT
OUTPUT  :




--------------------------------------------------------------------------------
ERROR   : # 13.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 25 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_cups_s4 -p tcp --sport 
631 --dport 1000:65535 -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT  :




--------------------------------------------------------------------------------
ERROR   : # 14.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 25 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_cups_s4 -p tcp --sport 
631 --dport 631 -m state '' --state NEW\,ESTABLISHED -j ACCEPT
OUTPUT  :




--------------------------------------------------------------------------------
ERROR   : # 15.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 25 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_cups_s4 -p tcp --sport 
631 --dport 631 -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT  :




--------------------------------------------------------------------------------
ERROR   : # 16.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 25 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_cups_s4 -p udp --sport 
1000:65535 --dport 631 -m state '' --state NEW\,ESTABLISHED -j ACCEPT
OUTPUT  :




--------------------------------------------------------------------------------
ERROR   : # 17.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 25 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_cups_s4 -p udp --sport 
631 --dport 1000:65535 -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT  :




--------------------------------------------------------------------------------
ERROR   : # 18.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 25 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_cups_s4 -p udp --sport 
631 --dport 631 -m state '' --state NEW\,ESTABLISHED -j ACCEPT
OUTPUT  :




--------------------------------------------------------------------------------
ERROR   : # 19.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 25 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_cups_s4 -p udp --sport 
631 --dport 631 -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT  :




--------------------------------------------------------------------------------
ERROR   : # 20.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 26 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world_ssh_s5 -p tcp --sport 
1000:65535 --dport 22 -m state '' --state NEW\,ESTABLISHED -j ACCEPT
OUTPUT  :




--------------------------------------------------------------------------------
ERROR   : # 21.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 26 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_ssh_s5 -p tcp --sport 22 
--dport 1000:65535 -m state '' --state ESTABLISHED -j ACCEPT
OUTPUT  :




--------------------------------------------------------------------------------
ERROR   : # 22.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world -m state '' --state 
RELATED -j ACCEPT
OUTPUT  :




--------------------------------------------------------------------------------
ERROR   : # 23.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world -m state '' --state 
RELATED -j ACCEPT
OUTPUT  :




--------------------------------------------------------------------------------
ERROR   : # 24.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A INPUT -m state '' --state RELATED 
-j ACCEPT
OUTPUT  :




--------------------------------------------------------------------------------
ERROR   : # 25.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A OUTPUT -m state '' --state RELATED 
-j ACCEPT
OUTPUT  :




--------------------------------------------------------------------------------
ERROR   : # 26.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A FORWARD -m state '' --state 
RELATED -j ACCEPT
OUTPUT  :
```


Below is my Firehol.conf file

```
#
# $Id: client-all.conf,v 1.2 2002/12/31 15:44:34 ktsaou Exp $
#
# This configuration file will allow all requests originating from the
# local machine to be send through all network interfaces.
#
# No requests are allowed to come from the network. The host will be
# completely stealthed! It will not respond to anything, and it will
# not be pingable, although it will be able to originate anything
# (even pings to other hosts).
#

version 5
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP

transparent_squid 8080 "nobody root"

#transparent_squid 8080 "ian root"

# Accept all client traffic on any interface
interface any world
policy drop
protection strong
client all accept
server cups accept
server ssh accept
#server webcache accept

```

---

### Post by ushills on 2007-08-31
Solved it with the following from another post

```

sudo su
sed 's/%q/%b/g' /lib/firehol/firehol > TMPFILE && mv TMPFILE /lib/firehol/firehol
chmod 744 /lib/firehol/firehol
```

---

### Post by scrooge_74 on 2007-09-11
which thread?

---

### Post by ruibernardo on 2007-09-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/firehol/+bug/78017](https://bugs.launchpad.net/ubuntu/+source/firehol/+bug/78017) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				scrooge_74, this is a known bug of the Firehol package in Feisty. Check the [23rd comment]("https://bugs.launchpad.net/ubuntu/+source/firehol/+bug/78017/comments/23").

---

### Post by scrooge_74 on 2007-09-12
Thanks, in the mean time I did as you said and got the kid's PC up and running with Dansguardian

---

