---
title: "Very weird SMTP Issue"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by sakkara on 2008-04-12
Hi,
I am running Ubuntu server, with console only.  I have an iptables rule that PREROUTES port 25 to our email server.  From the internet however, this is not working.

I can telnet [Email Server] 25 from within our networ, no worries.
However the iptables rule for some reason doesn't get picked up.

If I change the iptables PREROUTE rule (to say 26 pointing to [Email Server]:25, works like a dream).
I have also confirmed that 110 (using the exact same rule) works like a dream.

iptables -L only shows the rules I have made, nothing else for SMTP.

netstat doesn't show anything binding to 25 or listening on 25.

I can confirm that my isp is not blocking any ports in or out.

I can confirm that no tcpwrappers are in force, with both the hosts.allow and hosts.deny files being empty.

I am really struggling to find out what the issue is.  I suspect there is something else picking up the port 25 packet before it hits the iptables rule, but I can't be sure.  Could someone please shed some light on what is going on with port 25?

Thank you!

---

### Post by jakev383 on 2008-04-12
Give us some of the output, specifically 'iptables -L' and 'netstat -an'

---

### Post by superprash2003 on 2008-04-12
you can try this [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/) to make sure the port is successfully opened or not!

---

### Post by sakkara on 2008-04-12
I can confirm that the port is open, and is picked up on the port scanner.

iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
LOG        0    --  anywhere             anywhere            limit: avg 15/min burst 5 LOG level debug 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:953 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:953 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:3128 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:8000 
           tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
logdropinternetinput  0    --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh flags:FIN,SYN,RST,ACK/SYN 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:webmin 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:webmin 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ntp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ntp 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:nameserver 
logdroplaninput  0    --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:www 
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ntp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ntp 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ldap 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ldaps 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:50000 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:50001 
logdropdmzinput  0    --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
LOG        0    --  anywhere             anywhere            limit: avg 15/min burst 5 LOG level debug 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:953 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:953 
ACCEPT     tcp  --  anywhere             172.17.100.5        tcp dpt:smtp 
ACCEPT     tcp  --  anywhere             172.17.100.5        tcp dpt:pop3 
           tcp  --  anywhere             anywhere            tcp dpt:https 
ACCEPT     tcp  --  10.1.0.0/24          anywhere            tcp dpt:2179 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             10.1.0.0/24         tcp dpt:postgresql 
ACCEPT     tcp  --  anywhere             10.1.0.0/24         tcp dpt:5433 
logdropinternetforward  0    --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             anywhere            
ACCEPT     tcp  --  10.1.0.0/24          anywhere            tcp dpt:microsoft-ds 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:pop3 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:433 
ACCEPT     tcp  --  anywhere             10.1.0.0/24         tcp dpt:2179 
ACCEPT     tcp  --  anywhere             10.1.0.0/24         tcp dpt:postgresql 
ACCEPT     tcp  --  anywhere             10.1.0.0/24         tcp dpt:5433 
logdroplanforward  0    --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             10.1.0.0/24         tcp dpt:microsoft-ds 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:pop3 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:smtp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     tcp  --  10.1.0.0/24          anywhere            tcp dpt:2179 
ACCEPT     tcp  --  anywhere             10.1.0.0/24         tcp dpt:postgresql 
ACCEPT     tcp  --  anywhere             10.1.0.0/24         tcp dpt:5433 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
logdropdmzforward  0    --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
LOG        0    --  anywhere             anywhere            limit: avg 15/min burst 5 LOG level debug 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:953 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:953 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:8000 
           tcp  --  anywhere             anywhere            tcp dpt:https 
           tcp  --  anywhere             anywhere            tcp dpt:www 
logdropinternetoutput  0    --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ntp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ntp 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:nameserver 
logdroplanoutput  0    --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ntp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ntp 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ldap 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ldaps 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:50000 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:50001 
logdropdmzoutput  0    --  anywhere             anywhere            

Chain logdropdmzforward (1 references)
target     prot opt source               destination         
LOG        0    --  anywhere             anywhere            LOG level alert prefix `DROPPED DMZ FORWARD: ' 
DROP       0    --  anywhere             anywhere            

Chain logdropdmzinput (1 references)
target     prot opt source               destination         
LOG        0    --  anywhere             anywhere            LOG level alert prefix `DROPPED DMZ INPUT: ' 
DROP       0    --  anywhere             anywhere            

Chain logdropdmzoutput (1 references)
target     prot opt source               destination         
LOG        0    --  anywhere             anywhere            LOG level alert prefix `DROPPED DMZ OUTPUT: ' 
DROP       0    --  anywhere             anywhere            

Chain logdropinternetforward (1 references)
target     prot opt source               destination         
LOG        0    --  anywhere             anywhere            LOG level alert prefix `DROPPED INTERNET FORWARD: ' 
DROP       0    --  anywhere             anywhere            

Chain logdropinternetinput (1 references)
target     prot opt source               destination         
LOG        0    --  anywhere             anywhere            LOG level alert prefix `DROPPED INTERNET INPUT: ' 
DROP       0    --  anywhere             anywhere            

Chain logdropinternetoutput (1 references)
target     prot opt source               destination         
LOG        0    --  anywhere             anywhere            LOG level alert prefix `DROPPED INTERNET OUTPUT: ' 
DROP       0    --  anywhere             anywhere            

Chain logdroplanforward (1 references)
target     prot opt source               destination         
LOG        0    --  anywhere             anywhere            LOG level alert prefix `DROPPED LAN FORWARD: ' 
DROP       0    --  anywhere             anywhere            

Chain logdroplaninput (1 references)
target     prot opt source               destination         
LOG        0    --  anywhere             anywhere            LOG level alert prefix `DROPPED LAN INPUT: ' 
DROP       0    --  anywhere             anywhere            

Chain logdroplanoutput (1 references)
target     prot opt source               destination         
LOG        0    --  anywhere             anywhere            LOG level alert prefix `DROPPED LAN OUTPUT: ' 
DROP       0    --  anywhere             anywhere            


netstat -an
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:8000            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     
tcp        0      0 169.254.7.41:53         0.0.0.0:*               LISTEN     
tcp        0      0 124.178.229.94:53       0.0.0.0:*               LISTEN     
tcp        0      0 10.1.0.1:53             0.0.0.0:*               LISTEN     
tcp        0      0 10.0.0.2:53             0.0.0.0:*               LISTEN     
tcp        0      0 172.17.100.100:53       0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN     
tcp        0      0 172.17.100.100:3128     0.0.0.0:*               LISTEN     
tcp        0      0 10.1.0.1:3128           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN     
tcp        1      0 172.17.100.100:42144    172.17.100.3:80         CLOSE_WAIT 
tcp        1      0 172.17.100.100:42145    172.17.100.3:80         CLOSE_WAIT 
tcp        0      0 10.1.0.1:3128           10.1.0.80:1425          FIN_WAIT2  
tcp6       0      0 :::53                   :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0     52 ::ffff:10.1.0.1:22      ::ffff:10.1.0.80:1398   ESTABLISHED
udp        0      0 0.0.0.0:32776           0.0.0.0:*                          
udp        0      0 0.0.0.0:32778           0.0.0.0:*                          
udp        0      0 0.0.0.0:32779           0.0.0.0:*                          
udp        0      0 0.0.0.0:10000           0.0.0.0:*                          
udp        0      0 169.254.7.41:53         0.0.0.0:*                          
udp        0      0 124.178.229.94:53       0.0.0.0:*                          
udp        0      0 10.1.0.1:53             0.0.0.0:*                          
udp        0      0 10.0.0.2:53             0.0.0.0:*                          
udp        0      0 172.17.100.100:53       0.0.0.0:*                          
udp        0      0 127.0.0.1:53            0.0.0.0:*                          
udp        0      0 0.0.0.0:3130            0.0.0.0:*                          
udp        0      0 0.0.0.0:67              0.0.0.0:*                          
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp6       0      0 :::32777                :::*                               
udp6       0      0 :::53                   :::*                               
raw        0      0 0.0.0.0:1               0.0.0.0:*               7          
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ACC ]     STREAM     LISTENING     15123    @/tmp/dbus-4SpoLDquGP
unix  2      [ ACC ]     STREAM     LISTENING     16650    /var/run/avahi-daemon/socket
unix  2      [ ]         DGRAM                    8486     @/com/ubuntu/upstart
unix  2      [ ]         DGRAM                    8604     @/org/kernel/udev/udevd
unix  15     [ ]         DGRAM                    14974    /dev/log
unix  2      [ ACC ]     STREAM     LISTENING     14735    /var/run/acpid.socket
unix  2      [ ]         DGRAM                    15152    @/org/freedesktop/hal/udev_event
unix  2      [ ACC ]     STREAM     LISTENING     15141    @/var/run/hald/dbus-IqXE9DTQhu
unix  2      [ ACC ]     STREAM     LISTENING     16842    /var/run/apache2/cgisock.5266
unix  2      [ ACC ]     STREAM     LISTENING     15064    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     15144    @/var/run/hald/dbus-Nxj3YxWL8F
unix  2      [ ]         DGRAM                    17932    
unix  3      [ ]         STREAM     CONNECTED     17929    
unix  3      [ ]         STREAM     CONNECTED     17928    
unix  2      [ ]         DGRAM                    17511    
unix  2      [ ]         DGRAM                    17492    
unix  2      [ ]         DGRAM                    17483    
unix  2      [ ]         DGRAM                    17471    
unix  2      [ ]         DGRAM                    16724    
unix  2      [ ]         DGRAM                    16685    
unix  3      [ ]         STREAM     CONNECTED     16662    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16661    
unix  2      [ ]         DGRAM                    16660    
unix  3      [ ]         STREAM     CONNECTED     16653    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16652    
unix  3      [ ]         STREAM     CONNECTED     16647    
unix  3      [ ]         STREAM     CONNECTED     16646    
unix  2      [ ]         DGRAM                    16644    
unix  3      [ ]         STREAM     CONNECTED     16612    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16611    
unix  2      [ ]         DGRAM                    16443    
unix  2      [ ]         DGRAM                    16368    
unix  3      [ ]         STREAM     CONNECTED     16344    @/var/run/hald/dbus-IqXE9DTQhu
unix  3      [ ]         STREAM     CONNECTED     16343    
unix  3      [ ]         STREAM     CONNECTED     16342    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16341    
unix  3      [ ]         STREAM     CONNECTED     15988    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     15987    
unix  3      [ ]         STREAM     CONNECTED     15978    @/var/run/hald/dbus-IqXE9DTQhu
unix  3      [ ]         STREAM     CONNECTED     15977    
unix  3      [ ]         STREAM     CONNECTED     15965    @/var/run/hald/dbus-IqXE9DTQhu
unix  3      [ ]         STREAM     CONNECTED     15578    
unix  3      [ ]         STREAM     CONNECTED     15147    @/var/run/hald/dbus-Nxj3YxWL8F
unix  3      [ ]         STREAM     CONNECTED     15146    
unix  3      [ ]         STREAM     CONNECTED     15143    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15142    
unix  3      [ ]         STREAM     CONNECTED     15130    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15129    
unix  3      [ ]         STREAM     CONNECTED     15128    @/tmp/dbus-4SpoLDquGP
unix  3      [ ]         STREAM     CONNECTED     15127    
unix  3      [ ]         STREAM     CONNECTED     15126    
unix  3      [ ]         STREAM     CONNECTED     15125    
unix  3      [ ]         STREAM     CONNECTED     15098    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15097    
unix  3      [ ]         STREAM     CONNECTED     15087    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15086    
unix  2      [ ]         DGRAM                    15082    
unix  3      [ ]         STREAM     CONNECTED     15067    
unix  3      [ ]         STREAM     CONNECTED     15066    
unix  2      [ ]         DGRAM                    15050    


Any ideas?

---

### Post by jakev383 on 2008-04-12
So I'm assuming you have a Ubuntu based firewall (of which the output is shown above). Or is the email server on the same machine?
What type of mail server?

---

### Post by sakkara on 2008-04-12
Correct I am running Ubuntu server, with iptables as the firewall.  The Email server is Exchange Server 2003, hosted on a seperate machine.

---

### Post by sakkara on 2008-04-13
bump

---

### Post by jakev383 on 2008-04-13
Not sure why it works when you move it to port 26 (as you said in your first post), but here's how I usually have to forward ports like that:
```

$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -p tcp --dport 4569 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A PREROUTING -t nat -p tcp -d $EXTIP --dport 4569 -j DNAT --to 192.168.76.53:4569

```

4569 is for VoIP. $IPTABLES is the full path to the iptables command (/sbin/iptables on my RH machine). #EXTIF and $INTIF are my EXTernal and INTernal interface names.
Is the Ubuntu box the only thing between the Internet and your mail server? I've seen problems using PIX router/firewalls in the past with the fixup subsets.

---

### Post by sakkara on 2008-04-13
Yes the internet gateway using ppp0, using a normal modem to connect to the internet.  No other routers or firewalls are inbetween.  It doesn't seem to matter what port I change it too, it still works.  Every port except 25 unfortunately.

Any ideas why?

---

### Post by The Cog on 2008-04-13
Are you sure your ISP isn't blocking port 25? Can you confirm with tcpdump or wireshark that the connect requests are even arriving at your firewall?

P.S. 
You didn't post your forwarding rules. Try the command ```
iptables-save -c
```

---

### Post by sakkara on 2008-04-13
I can confirm that my isp is not blocking port 25, with the following command:-
```
tcpdump -i ppp0 'tcp port 25'
```
The iptables forward rules have been posted, under the heading Chain FORWARD (policy DROP).

This issue is amazingly frustrating!

Any ideas?

---

### Post by sakkara on 2008-04-13
Hi all,

First of all, sorry for wasting everyones time.  The test I was using was:-
```
telnet [external IP] 25
```

This turns out to be incorrect, because my home ISP (the one I was using to test it) was blocking incoming SMTP requests.
So basically my rule has been working all the time.

I am really sorry for wasting everyones time.

---

### Post by jakev383 on 2008-04-15
No problem. I glossed over that when you had said that you were sure that your ISP wasn't blocking the port but I was going to bring it back up.
I help develop a project called Qmailtoaster (doesn't run on Ubuntu, only RPM based distros) but we also use port 587 as a "submission" port to get around spam checks and it has been extremely successful for my roaming clients that travel and want to send email. I don't know of any ISPs that are blocking that port yet and even Earthlink is using it now.
Good luck!

---

