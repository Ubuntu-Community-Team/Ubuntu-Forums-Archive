---
title: "Need IPTABLES rules explanation about OpenVPN set up"
date: 2019-09-18
forum: Networking &amp; Wireless
---

### Post by Grigoriy on 2019-09-18
Hello!
                          I've got Ubuntu 16.04 and OpenVPN installed  and seems to be working fine. But when I check firewall rules using  "sudo ufw status", then I see this:

```
Status: active

To                         Action      From
--                         ------      ----
80                         ALLOW       Anywhere                  
443                        ALLOW       Anywhere                  
53                         ALLOW       Anywhere                  
465                        ALLOW       Anywhere                  
25                         ALLOW       Anywhere                  
110                        ALLOW       Anywhere                  
995                        ALLOW       Anywhere                  
143                        ALLOW       Anywhere                  
993                        ALLOW       Anywhere                  
10025                      ALLOW       Anywhere                  
10024                      ALLOW       Anywhere                  
80 (v6)                    ALLOW       Anywhere (v6)             
443 (v6)                   ALLOW       Anywhere (v6)             
53 (v6)                    ALLOW       Anywhere (v6)             
465 (v6)                   ALLOW       Anywhere (v6)             
25 (v6)                    ALLOW       Anywhere (v6)             
110 (v6)                   ALLOW       Anywhere (v6)             
995 (v6)                   ALLOW       Anywhere (v6)             
143 (v6)                   ALLOW       Anywhere (v6)             
993 (v6)                   ALLOW       Anywhere (v6)             
10025 (v6)                 ALLOW       Anywhere (v6)             
10024 (v6)                 ALLOW       Anywhere (v6)  

```

Port 1194 isn't mentioned at all! But I use  netstat command "root@mail:~# netstat -anlp |grep 1194" I get this:

```
udp        0      0 0.0.0.0:1194            0.0.0.0:*                           1142/openvpn    

```

Also I have this file, created by the OpenVPN script here /etc/systemd/system/openvpn-iptables.service and I see this in it:

```
[Unit]
Before=network.target
[Service]
Type=oneshot
ExecStart=/sbin/iptables -t nat -A POSTROUTING -s 10.8.0.0/24 ! -d 10.8.0.0/24 -j SNAT --to xx.249.16.253
ExecStart=/sbin/iptables -I INPUT -p udp --dport 1194 -j ACCEPT
ExecStart=/sbin/iptables -I FORWARD -s 10.8.0.0/24 -j ACCEPT
ExecStart=/sbin/iptables -I FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
ExecStop=/sbin/iptables -t nat -D POSTROUTING -s 10.8.0.0/24 ! -d 10.8.0.0/24 -j SNAT --to xx.249.16.253
ExecStop=/sbin/iptables -D INPUT -p udp --dport 1194 -j ACCEPT
ExecStop=/sbin/iptables -D FORWARD -s 10.8.0.0/24 -j ACCEPT
ExecStop=/sbin/iptables -D FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
RemainAfterExit=yes
[Install]
WantedBy=multi-user.target

```


                          So my question is... if port 1194 is open** (is it?)** with these IPTABLES rules, then why I don't see it in ufw status?

---

### Post by SeijiSensei on 2019-09-19
Try
```
sudo /sbin/iptables -L -nv
```

See it there?

---

### Post by Grigoriy on 2019-09-19
```
Chain INPUT (policy DROP)
target     prot opt source               destination         
f2b-sasl   tcp  --  0.0.0.0/0            0.0.0.0/0            multiport dports 25,465,587,143,220,993,110,995
f2b-apache-multiport  tcp  --  0.0.0.0/0            0.0.0.0/0            multiport dports 80,443
f2b-apache  tcp  --  0.0.0.0/0            0.0.0.0/0            multiport dports 80,443
f2b-ssh    tcp  --  0.0.0.0/0            0.0.0.0/0            multiport dports 22
f2b-postfix  tcp  --  0.0.0.0/0            0.0.0.0/0            multiport dports 25,465,587
f2b-apache-overflows  tcp  --  0.0.0.0/0            0.0.0.0/0            multiport dports 80,443
f2b-apache-noscript  tcp  --  0.0.0.0/0            0.0.0.0/0            multiport dports 80,443
f2b-sshd   tcp  --  0.0.0.0/0            0.0.0.0/0            multiport dports 22
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:1194
ufw-before-logging-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-track-input  all  --  0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
ACCEPT     all  --  10.8.0.0/24          0.0.0.0/0           
ufw-before-logging-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-track-forward  all  --  0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-track-output  all  --  0.0.0.0/0            0.0.0.0/0           

Chain f2b-apache (1 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           

Chain f2b-apache-multiport (1 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           

Chain f2b-apache-noscript (1 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           

Chain f2b-apache-overflows (1 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           

Chain f2b-postfix (1 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           

Chain f2b-sasl (1 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           

Chain f2b-ssh (1 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           

Chain f2b-sshd (1 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:137
ufw-skip-to-policy-input  udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:138
ufw-skip-to-policy-input  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:139
ufw-skip-to-policy-input  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:445
ufw-skip-to-policy-input  udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:67
ufw-skip-to-policy-input  udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:68
ufw-skip-to-policy-input  all  --  0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 3
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 4
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 11
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 12
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 8
ufw-user-forward  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
ufw-logging-deny  all  --  0.0.0.0/0            0.0.0.0/0            ctstate INVALID
DROP       all  --  0.0.0.0/0            0.0.0.0/0            ctstate INVALID
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 3
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 4
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 11
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 12
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 8
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp spt:67 dpt:68
ufw-not-local  all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     udp  --  0.0.0.0/0            224.0.0.251          udp dpt:5353
ACCEPT     udp  --  0.0.0.0/0            239.255.255.250      udp dpt:1900
ufw-user-input  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
ufw-user-output  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW ALLOW] "

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0            ctstate INVALID limit: avg 3/min burst 10
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type LOCAL
RETURN     all  --  0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type MULTICAST
RETURN     all  --  0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST
ufw-logging-deny  all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-track-forward (1 references)
target     prot opt source               destination         

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            ctstate NEW
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            ctstate NEW

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:80
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:80
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:443
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:443
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:53
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:53
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:465
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:465
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:25
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:25
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:110
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:110
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:995
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:995
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:143
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:143
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:993
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:993
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:10025
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:10025
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:10024
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:10024

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 5 LOG flags 0 level 4 prefix "[UFW LIMIT BLOCK] "
REJECT     all  --  0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           

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

### Post by Grigoriy on 2019-09-19
It's probably this line that matters?

ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:1194

So does it mean that port 1194 udp is open for OpenVPN outside of UFW control?

---

### Post by The Cog on 2019-09-19
> **Grigoriy said:**
> It's probably this line that matters?

ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:1194

So does it mean that port 1194 udp is open for OpenVPN outside of UFW control?
Yes. As you have discovered, it is opened by the script that runs as OpenVPN comes up. And some NAT rules are added too.

Remember, ufw is just a tool for simplifying configuration of iptables. Other tools go directly to iptables to do their own thing as well. virt-manager and I guess failtoban do too. 
Sshguard even has the brains to use nftables instead of iptables if that's what's being used on the host - something that others have yet to figure out.
Fortunately, conflicts between different apps are rare, and they just do their own thing unaware of each other's existence.

---

### Post by Grigoriy on 2019-09-20
I see... Okay, thank you!

---

