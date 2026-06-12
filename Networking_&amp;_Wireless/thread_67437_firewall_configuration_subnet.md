---
title: "firewall configuration /subnet"
date: 2005-09-20
forum: Networking &amp; Wireless
---

### Post by [pl]ice on 2005-09-20
hi, i got 2 cards wlan0 at 192.168.1.5
  and eth0 at 192.168.2.5

problem is that firewall doesn't allow traffic from x.x.2. subnet when x.x.1.x is running, i got to turn the bugger off :( (firewall)  tried in firestarter with allowing all traffic through  x.x.2.x but didn't help.
can someone please tell me how to configure via iptables? I'm just starting to learn it from the book :D 
thanks!!!

---

### Post by Vardor on 2005-09-30
i don't think it's a problem with firewall. Did you enabled forwarding traffic beetween interfaces ???? 

Try this:

echo 1 > /proc/sys/net/ipv4/ip_forward

---

### Post by [pl]ice on 2005-09-30
cat  /proc/sys/net/ipv4/ip_forward
1

 ping sabro2
PING sabro2 (192.168.2.7) 56(84) bytes of data.
ping: sendmsg: Operation not permitted

 still nothing, but then when i swith cff firestarter, it's ok :(

---

### Post by cwaldbieser on 2005-10-02
[QUOTE='[pl]ice']cat  /proc/sys/net/ipv4/ip_forward
1
ping sabro2
PING sabro2 (192.168.2.7) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
still nothing, but then when i swith cff firestarter, it's ok :([/QUOTE]

I guess you'd have to examine the firewall settings then and see what's blocking the packets.  If you can't tell from the firestarter GUI, you can dump all the firewall rules for filtering out with:
```

$ sudo iptables -nL

```
If you are not sure how to interpret them, try posting them back here.  Auto generated rules tend to be a bit messier for humans to read, so it may take us a while to chew through them, though.

---

### Post by [pl]ice on 2005-10-02
um, i guess i can 'make' my own rules now, but i'm not sure if i have to include eg. nmap recognition for xmass scann, null scan etc. and can i do port rejection upon many connections? things like that top me playing with fwall. But once this below can be explained, then i'll just set it to standars + my stuff.
thanks



Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  203.161.127.1        0.0.0.0/0           tcp flags:!0x16/0x02 
ACCEPT     udp  --  203.161.127.1        0.0.0.0/0           
ACCEPT     tcp  --  203.153.224.41       0.0.0.0/0           tcp flags:!0x16/0x02 
ACCEPT     udp  --  203.153.224.41       0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
DROP       all  --  0.0.0.0/0            255.255.255.255     
DROP       all  --  0.0.0.0/0            192.168.1.255       
DROP       all  --  224.0.0.0/8          0.0.0.0/0           
DROP       all  --  0.0.0.0/0            224.0.0.0/8         
DROP       all  --  255.255.255.255      0.0.0.0/0           
DROP       all  --  0.0.0.0/0            0.0.0.0             
DROP       all  --  0.0.0.0/0            0.0.0.0/0           state INVALID 
LSI        all  -f  0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
INBOUND    all  --  0.0.0.0/0            0.0.0.0/0           
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.5          203.161.127.1       tcp dpt:53 
ACCEPT     udp  --  192.168.1.5          203.161.127.1       udp dpt:53 
ACCEPT     tcp  --  192.168.1.5          203.153.224.41      tcp dpt:53 
ACCEPT     udp  --  192.168.1.5          203.153.224.41      udp dpt:53 
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
DROP       all  --  224.0.0.0/8          0.0.0.0/0           
DROP       all  --  0.0.0.0/0            224.0.0.0/8         
DROP       all  --  255.255.255.255      0.0.0.0/0           
DROP       all  --  0.0.0.0/0            0.0.0.0             
DROP       all  --  0.0.0.0/0            0.0.0.0/0           state INVALID 
OUTBOUND   all  --  0.0.0.0/0            0.0.0.0/0           
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     all  --  192.168.2.7          0.0.0.0/0           
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:4660 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:4660 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:4663 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:4663 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:4661 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:4661 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:4664 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:4664 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:4662 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:4662 
LSI        all  --  0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x16/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x16/0x02 
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
LOG        icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0

---

### Post by cwaldbieser on 2005-10-02
[QUOTE='[pl]ice']
Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 
[/QUOTE]
This section is the relevant.  The FORWARD hook point is for when a packet enters your  system through one NIC and exits through another.  Note, that if you are trying to make the connection from the Ubuntu computer itself, you will need to look at the OUTPUT hook, as packets that originate on the host and exit through a NIC are intercepted there.

Your default policy here is to DROP any such packets that don't match a rule.  Looks like you are ACCEPTing ICMP traffic, but nothing else.  So everything else should fail.

You mentioned you were having trouble pinging, though.  It looks like the firewall should allow that.  That is a little bit of a puzzle.

Looks like you have LOGging turned on, though.  You should be able to use "dmesg" to see if your pings are being blocked by the firewall.  If it does, it should show you the source, destination, etc., and you can try to compare it to the rules you just printed out so you can see why it is getting blocked.

---

### Post by [pl]ice on 2005-10-03
hm, i'll change the accept rule to accept all, from that,

while the fwall is on, i can't do anyting with that subnet ,no connections of any type, 

yeh, will look through logs, capture some see what happens.
thnx

---

### Post by [pl]ice on 2005-10-12
hey, that seems to work:

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5
TCPMSS     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x06/0x02 TCPMSS clamp to PMTU
OUTBOUND   all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     tcp  --  0.0.0.0/0            192.168.2.0/24      state RELATED,ESTABLISHED
ACCEPT     udp  --  0.0.0.0/0            192.168.2.0/24      state RELATED,ESTABLISHED
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward'

actually firestater got that option 'share internet '  
i hope i did the right thing :/

---

