---
title: "Operation not perminated :S"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by qbox on 2008-01-21
Hi  to all.
Im in a lan and i have a local ip 172.18.10.10. before I connect to internet with pppoe i can ping computer in my LAN. i can make ping to my another computer 172.18.10.11.
If I connect to internet with pppoe, in ifconfig configuration I have ppp0 connection but I cant ping computers in my lan. I receive this output.

qbox@qbox:~$ ping 172.18.10.11
PING 172.18.10.11 (172.18.10.11) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 172.18.10.67 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4009ms
qbox@qbox:~$ 

before I make pppoe connection everything is working fine.
Please tell me what to do.

---

### Post by qbox on 2008-01-28
Thanks to all who not answered. :popcorn:

The problem was in IPTABLE 
firewall disabled ping operations and other access tools.
I do this
$ sudo iptables-save > /home/qbox/firewall.rules

# iptables -X
# iptables -t nat -F
# iptables -t nat -X
# iptables -t mangle -F
# iptables -t mangle -X
# iptables -P INPUT ACCEPT
# iptables -P FORWARD ACCEPT
# iptables -P OUTPUT ACCEPT

dont worry if that show you error. Just keep going.

If you want your firewall back 

# iptables-restore < /home/qbox/firewall.rules

:guitar:

---

