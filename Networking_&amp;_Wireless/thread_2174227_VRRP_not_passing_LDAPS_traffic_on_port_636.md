---
title: "VRRP not passing LDAPS traffic on port 636"
date: 2013-09-13
forum: Networking &amp; Wireless
---

### Post by eric_speake2 on 2013-09-13
We are moving to an "cluster" of LDAP servers and I nee to be able to access them via port 636 for some of our applications.  I can connect and get certificate information from each node individually but I get a connection error 111 when I try the VRRP address.  Below is and example of the real_server:

real_server 172.17.xxx.xxx 669 {
            weight 100
                TCP_CHECK {
                    connect_port 669
                    connect_timeout 2
                }

        }

I have all three servers configure this way  Since it is ldap I do not believe I can use SSL_GET since there is no file on the LDAP protocol to check.  When I do a network capture it shows the VRRP instance sends back a reset ack.  I read that the above error means that the connection is not listening on that port.  Again I can connect to the nodes directly, but not the VRRP instance.

Thank you,
Eric

---

### Post by s-bodet on 2013-09-14
Hi,

not sure that would work by default.

A VRRP address is a very special address (there's no entry in /etc/network/interfaces for example).  As such, a VRRP address has no direct access to the TCP/IP stack of the host.  This is probably it sends a TCP RST...

As a side question...  What would be the benefit of ssh the address of the group ?  Because you potentially don't know which one of the servers you would connect to.  The only thing you know is that you are connected to the VRRP Master of the group...

Steve

---

### Post by The Cog on 2013-09-14
I think my first step would be to use the command **[FONT=Courier New]ip addr ls[/FONT]** to show the addresses on each machine. One of them should have the vrrp address as will as their own addresses. Then on that machone, use **[FONT=Courier New]netstat -lntpu[/FONT]** to see which addresses the ldap service is listening on. My guess is that the ldap server is binding to the normal address and not the vrrp address. I think you probably need to get the ldap server to bind to 0.0.0.0 which means all local addresses, because the vrrp address won't even be there when ldap starts.

---

### Post by eric_speake2 on 2013-09-16
Here is what I get on both LDAP servers.  The VRRP address appears on the loopback interface which is normal from what I have read.  In the ouput below both LDAP servers shows it listening on port 389 and 636 at IP address 0.0.0.0

Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:40429           0.0.0.0:*               LISTEN      668/rpc.statd
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      636/rpcbind
tcp        0      0 0.0.0.0:55282           0.0.0.0:*               LISTEN      869/eventlogd
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      548/sshd
tcp        0      0 0.0.0.0:636             0.0.0.0:*               LISTEN      1018/slapd
tcp        0      0 0.0.0.0:389             0.0.0.0:*               LISTEN      1018/slapd
tcp        0      0 0.0.0.0:135             0.0.0.0:*               LISTEN      863/dcerpcd
tcp6       0      0 :::111                  :::*                    LISTEN      636/rpcbind
tcp6       0      0 :::36884                :::*                    LISTEN      668/rpc.statd
tcp6       0      0 :::22                   :::*                    LISTEN      548/sshd
tcp6       0      0 :::636                  :::*                    LISTEN      1018/slapd
tcp6       0      0 :::389                  :::*                    LISTEN      1018/slapd
udp        0      0 0.0.0.0:810             0.0.0.0:*                           636/rpcbind
udp        0      0 127.0.0.1:844           0.0.0.0:*                           668/rpc.statd
udp        0      0 0.0.0.0:111             0.0.0.0:*                           636/rpcbind
udp        0      0 172.17.3.144:123        0.0.0.0:*                           1378/ntpd
udp        0      0 172.17.1.93:123         0.0.0.0:*                           1378/ntpd
udp        0      0 127.0.0.1:123           0.0.0.0:*                           1378/ntpd
udp        0      0 0.0.0.0:123             0.0.0.0:*                           1378/ntpd
udp        0      0 0.0.0.0:135             0.0.0.0:*                           863/dcerpcd
udp        0      0 0.0.0.0:51516           0.0.0.0:*                           668/rpc.statd
udp6       0      0 :::810                  :::*                                636/rpcbind
udp6       0      0 :::111                  :::*                                636/rpcbind
udp6       0      0 ::1:123                 :::*                                1378/ntpd
udp6       0      0 fe80::250:56ff:fea8:123 :::*                                1378/ntpd
udp6       0      0 :::123                  :::*                                1378/ntpd
udp6       0      0 :::35262                :::*                                668/rpc.statd

If I try TLS on port 389 I still get the same SSL handshake error.

---

### Post by eric_speake2 on 2013-09-16
We are doing High availability for ldap using openLDAP with a n-way multimaster setup.  It works on port 389 with no issues but when we try to connect on port 636 the VRRP is rejecting the traffic and not even passing it.  I did a packet capture on both servers and watch the trquests come in and get reset on port 636 but passed through on port 389.  Since it is LDAP and no file to check against for the SSL I don't think that I can use GET_SSL.

Thanks,
Eric

---

### Post by eric_speake2 on 2013-09-16
We are doing High availability for ldap using openLDAP with a n-way multimaster setup.  It works on port 389 with no issues but when we try to connect on port 636 the VRRP is rejecting the traffic and not even passing it.  I did a packet capture on both servers and watch the trquests come in and get reset on port 636 but passed through on port 389.  Since it is LDAP and no file to check against for the SSL I don't think that I can use GET_SSL.

Thanks,
Eric

---

### Post by eric_speake2 on 2013-09-20
I needed thicker glasses.  I had hit a wrong key on my 10-key pad and was trying to got to the wrong port number.  I thought computers were supposed to be smarter than we are.  :)

Thanks for the help though.  I picked up some good tips.

Eric

---

