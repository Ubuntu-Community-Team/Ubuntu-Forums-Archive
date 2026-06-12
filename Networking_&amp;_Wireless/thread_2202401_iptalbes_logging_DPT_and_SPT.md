---
title: "iptalbes logging DPT and SPT?"
date: 2014-01-29
forum: Networking &amp; Wireless
---

### Post by ant2ne on 2014-01-29
Basically, on my firewall I log some connections via iptables connections on port 80. Port 80 is NATed to a webserver inside my network. It is not PATed in that the web server answers on port 80 like a good webserver should.

```
iptables -A INPUT -i $_ethOUT -p tcp -m multiport --sport 80 -j LOG --log-prefix "[IPTABLES PORT 80 " --log-level info

```

And here is an example of an entry
```
Jan 28 23:01:29 fw kernel: [6342113.924061] [IPTABLES PORT 80 IN=eth1 OUT= MAC=00:e0:66:6a:c5:12:00:21:a0:fa:fa:d9:08:00 SRC=91.189.91.13 DST={MYIP} LEN=1500 TOS=0x00 PREC=0x00 TTL=50 ID=52913 DF PROTO=TCP SPT=80 DPT=55661 WINDOW=204 RES=0x00 ACK URGP=0 
```

What is confusing me is the SPT=80 and the DPT=55661. I assume that SPT is Source Port and DPT is Destination port. The webserver is answering on port 80. So how can the DPT and SPT not be the same? What is this strange DPT that shouldn't be doing anything. I understand if maybe I PATed the DPT to something else but I haven't.

I've tried goodling "iptalbes logging" and I don't find a good explanation of the logs that are generated. Just how to setup the logging.

---

### Post by ian-weisser on 2014-01-29
Your web server receives requests and replies to them on your server's port 80.

My browser does not use port 80 to make the requests nor to receive the responses. That would block my webserver, and would limit me to a single http connection at a time. So my browser opens a port for every request/response, and some of those many open ports can easily be in the 55661 range.

You can test this by opening a browser, then use netstat to see what ports the browser uses.

---

### Post by Doug S on 2014-01-29
I log new external connections to my web server, via:```
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p tcp -s $UNIVERSE -d $EXTIP --dport 80 -j LOG --log-prefix "NEW80:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p tcp -s $UNIVERSE -d $EXTIP --dport 80 -j ACCEPT
```However, and as you can see from my second line, I am not forwarding the packet. Your case might require such a rule in the FORWARD chain, similar to what I (temporarily) do for another server (but port 80 in your case):```
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -p tcp --dport 80 -d 192.168.111.112 -m state --state NEW -j LOG --log-prefix "PFNEW80:" --log-level info
```Where this is the corresponding PREROUTING rule (dport would be 80 for your case):```
$IPTABLES -t nat -A PREROUTING -p tcp -i $EXTIF --dport 8083 -j DNAT --to 192.168.111.112:80
```

---

### Post by ant2ne on 2014-01-29
Thanks guys. That explains it. And I will test out that FORWARDING firewall rule.

---

