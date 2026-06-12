---
title: "iptables ping LAN computers using name"
date: 2015-03-22
forum: Networking &amp; Wireless
---

### Post by VamPikmin on 2015-03-22
Hi 
I have an ubuntu server 14

I have iptables set up, icmp is allowed for all local ip addresses

I can ping my server using name and ip address however from the server I can only ping other devices by using ip

If i flush the rules I can ping from the server by name

My local ip range 192.168.1.1-255
Any thoughts?

rules.v4

```


:OUTPUT ACCEPT

-A INPUT -p udp -s 192.168.1.0/24 --dport 137 -m state --state NEW,ESTABLISHED -j ACCEPT
-A INPUT -p udp -s 192.168.1.0/24 --dport 138 -m state --state NEW,ESTABLISHED -j ACCEPT
-A INPUT -p tcp -s 192.168.1.0/24 --dport 139 -m state --state NEW,ESTABLISHED -j ACCEPT
-A INPUT -p tcp -s 192.168.1.0/24 --dport 445 -m state --state NEW,ESTABLISHED -j ACCEPT

-A OUTPUT -s 192.168.1.0/24 -p icmp -j ACCEPT
-A INPUT -s 192.168.1.0/24 -p icmp -j ACCEPT


```

---

### Post by The Cog on 2015-03-22
You need to allow your server to do use DNS to look up the names to get the associated IP address. DNS uses UDP port 53 so you need to allow that out. And allow the replies back in.

I also see that you are allowing 4 protocols incoming, but no allowing any reply to those back out. 

It is always a good idea to allow RELATED,ESTABLISHED in both directions. That way, once an initial packet is allowed to create a connection, you don't have to explicitly allow responses in the other direction.

---

### Post by VamPikmin on 2015-03-22
Thanks Cog,
Will check when I get home. I'm pretty sure that 53 is allowed on INPUT but will add all the OUTPUT chains like you suggested
I thought wins was what is used when finding out names on the local network not DNS (I have added wins to /etc/nsswitch.conf)

---

### Post by VamPikmin on 2015-03-23
Still no luck,

When I set port 137 to log I see activity every time I try to ping using name but still can't work out why not working
Mar 23 20:50:33 Server kernel: [16102.957589] IN= OUT=eth0 SRC=192.168.1.2 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=40790 DF PROTO=UDP SPT=52198 DPT=137 LEN=58
Mar 23 20:50:33 Server kernel: [16102.957616] IN=eth0 OUT= MAC= SRC=192.168.12 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=40790 DF PROTO=UDP SPT=52198 DPT=137 LEN=58

---

### Post by The Cog on 2015-03-23
My next step would be to open the firewall and use tcpdump to capture a succesful ping - then look at the preceding packets to see how the name got resolved.
This command should get tcpdump printing out the packets going in and out:
```
sudo tcpdump -np
```

---

### Post by VamPikmin on 2015-03-24
With iptables flushed
 192.168.1.9 Ubuntu server
 192.168.1.2 Windows 7 Desktop

 16:16:43.647460 IP 192.168.1.9 > 192.168.1.2: ICMP echo request, id 1717, seq 5, length 64
 16:16:43.649187 IP 192.168.1.2 > 192.168.1.9: ICMP echo reply, id 1717, seq 5, length 64
 16:16:43.864572 IP 192.168.1.2.49382 > 192.168.1.9.22: Flags [.], ack 961, win 16281, length 0
 16:16:44.264635 IP 192.168.1.2.49335 > 192.168.1.9.22: Flags [.], ack 8080, win 16425, length 0
 16:16:44.649316 IP 192.168.1.9 > 192.168.1.2: ICMP echo request, id 1717, seq 6, length 64
 16:16:44.650482 IP 192.168.1.2 > 192.168.1.9: ICMP echo reply, id 1717, seq 6, length 64
 16:16:45.264738 IP 192.168.1.2.49335 > 192.168.1.9.22: Flags [.], ack 8736, win 16261, length 0
 16:16:45.650613 IP 192.168.1.9 > 192.168.1.2: ICMP echo request, id 1717, seq 7, length 64
 16:16:45.652926 IP 192.168.1.2 > 192.168.1.9: ICMP echo reply, id 1717, seq 7, length 64
 16:16:45.864622 IP 192.168.1.2.49382 > 192.168.1.9.22: Flags [.], ack 1249, win 16209, length 0

 With iptables enabled when not working

 16:18:43.603372 IP 192.168.1.9.39667 > 192.168.1.255.137: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
 16:18:43.606133 IP 192.168.1.2.137 > 192.168.1.9.39667: NBT UDP PACKET(137): QUERY; POSITIVE; RESPONSE; UNICAST
 16:18:43.775085 IP 192.168.1.2.49382 > 192.168.1.9.22: Flags [.], ack 1664, win 16317, length 0
 16:18:43.854031 IP 192.168.1.9.22 > 192.168.1.2.49382: Flags [P.], seq 1664:1744, ack 321, win 271, length 80
 16:18:43.856734 IP 192.168.1.9.22 > 192.168.1.2.49382: Flags [P.], seq 1744:1840, ack 321, win 271, length 96
 16:18:43.865065 IP 192.168.1.2.49382 > 192.168.1.9.22: Flags [.], ack 1840, win 16273, length 0
 16:18:44.038192 IP 192.168.1.13.7776 > 255.255.255.255.7776: UDP, length 15
 16:18:44.088303 IP 192.168.1.9.22 > 192.168.1.2.49335: Flags [.], seq 10192:11652, ack 161, win 271, length 1460
 16:18:44.088322 IP 192.168.1.9.22 > 192.168.1.2.49335: Flags [P.], seq 11652:12048, ack 161, win 271, length 396
 16:18:44.095107 IP 192.168.1.2.49335 > 192.168.1.9.22: Flags [.], ack 12048, win 16425, length 0
 16:18:45.089350 IP 192.168.1.9.22 > 192.168.1.2.49335: Flags [P.], seq 12048:12432, ack 161, win 271, length 384
 16:18:45.288418 IP 192.168.1.13.7776 > 255.255.255.255.7776: UDP, length 8
 16:18:45.305208 IP 192.168.1.2.49335 > 192.168.1.9.22: Flags [.], ack 12432, win 16329, length 0
 16:18:46.090457 IP 192.168.1.9.22 > 192.168.1.2.49335: Flags [P.], seq 12432:12784, ack 161, win 271, length 352
 16:18:46.305148 IP 192.168.1.2.49335 > 192.168.1.9.22: Flags [.], ack 12784, win 16241, length 0
 16:18:46.539062 IP 192.168.1.13.7776 > 255.255.255.255.7776: UDP, length 16
 16:18:46.583175 IP 192.168.1.2.49382 > 192.168.1.9.22: Flags [P.], seq 321:385, ack 1840, win 16273, length 64
 16:18:46.583644 IP 192.168.1.9.22 > 192.168.1.2.49382: Flags [P.], seq 1840:1904, ack 385, win 271, length 64
 16:18:46.583796 IP 192.168.1.9.22 > 192.168.1.2.49382: Flags [P.], seq 1904:1968, ack 385, win 271, length 64
 16:18:46.584159 IP 192.168.1.9.22 > 192.168.1.2.49382: Flags [P.], seq 1968:2064, ack 385, win 271, length 96
 16:18:46.595203 IP 192.168.1.2.49382 > 192.168.1.9.22: Flags [.], ack 1968, win 16241, length 0
 16:18:46.795205 IP 192.168.1.2.49382 > 192.168.1.9.22: Flags [.], ack 2064, win 16217, length 0
 16:18:47.091671 IP 192.168.1.9.22 > 192.168.1.2.49335: Flags [P.], seq 12784:13776, ack 161, win 271, length 992

 I ended up allowing all on Local LAN 
 -A INPUT -s 192.168.1.0/24 -j ACCEPT
 and it started working

Can you make sense of the tcpdump capture what port I would need to unblock to get it working?

Thanks again

---

### Post by The Cog on 2015-03-24
There is no name lookup at all in the trace where it works. I guess it had already resolved the name before your trace started, so I'm afraid there is nothing to learn there.

However, there is an NBT name query and response in the failing trace. Perhaps the response is being blocked?

What is the response when you try to ping by name?

---

### Post by VamPikmin on 2015-03-24
I will try and capture the working one again while it's looking up the name and compare

You said perhaps the response is being blocked, which to I agree as well
The line in bold, my Windows7 desktop is sending from udp port 137 to udp port 39667 which is not open in iptables, is my reasoning correct here?

16:18:43.603372 IP 192.168.1.9.39667 > 192.168.1.255.137: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
 **16:18:43.606133 IP 192.168.1.2.137 > 192.168.1.9.39667: NBT UDP PACKET(137): QUERY; POSITIVE; RESPONSE; UNICAST**
 16:18:43.775085 IP 192.168.1.2.49382 > 192.168.1.9.22: Flags [.], ack 1664, win 16317, length 0
 16:18:43.854031 IP 192.168.1.9.22 > 192.168.1.2.49382: Flags [P.], seq 1664:1744, ack 321, win 271, length 80
 16:18:43.856734 IP 192.168.1.9.22 > 192.168.1.2.49382: Flags [P.], seq 1744:1840, ack 321, win 271, length 96
 16:18:43.865065 IP 192.168.1.2.49382 > 192.168.1.9.22: Flags [.], ack 1840, win 16273, length 0
 16:18:44.038192 IP 192.168.1.13.7776 > 255.255.255.255.7776: UDP, length 15

You asked what the response is when I try to ping by name, the above log is when I try to ping by name, both are from my previous post

Thank you for your time :)

---

### Post by SeijiSensei on 2015-03-24
The entry in bold is a reply to the packet logged in the line above it.

---

### Post by VamPikmin on 2015-03-25
Yeah that part makes sense, just wanted to be sure about the ports. It appears that NetBIOS is using random udp ports for reply

Thanks for all your help!

IP 192.168.1.9.39807 > 192.168.1.100.53: 59657+ A? Windows7-PC. (26)
IP 192.168.1.100.53 > 192.168.1.9.39807: 59657 NXDomain 0/1/0 (101)
IP 192.168.1.9.52966 > 192.168.1.255.137: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
IP 192.168.1.2.137 > 192.168.1.9.52966: NBT UDP PACKET(137): QUERY; POSITIVE; RESPONSE; UNICAST
IP 192.168.1.9.36935 > 192.168.1.100.53: 38327+ PTR? 2.1.168.192.in-addr.arpa. (42)
IP 192.168.1.100.53 > 192.168.1.9.36935: 38327 1/2/0 PTR 192-168-1-2.XXXXXXX. (115)
IP 192.168.1.2.60069 > 239.255.255.250.1900: UDP, length 137

---

### Post by The Cog on 2015-03-25
> **VamPikmin said:**
> Yeah that part makes sense, just wanted to be sure about the ports. It appears that NetBIOS is using random udp ports for reply

Thanks for all your help!

IP 192.168.1.9.52966 > 192.168.1.255.137: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
IP 192.168.1.2.137 > 192.168.1.9.52966: NBT UDP PACKET(137): QUERY; POSITIVE; RESPONSE; UNICAST

No, it's the client that uses a random source port when making the request. It is very common for a client to use a randon free port when making an outgoing request/connection, although the server has to listen on a "well known port" number or course. The server just replies to the client on whichever port it has chosen for itself. This is why it's a good move to allow:
* outgoing to port 137, and
* incoming RELATED,ESTABLISHED.
The outgoing request establishes a "connection" in the firewall between the two end points that then allows the reply back in.

---

