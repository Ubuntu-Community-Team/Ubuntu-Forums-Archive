---
title: "Internet connection problem with wifi xubuntu 20.0.4"
date: 2022-02-10
forum: Networking &amp; Wireless
---

### Post by iancoullie on 2022-02-10
I installed a fresh version xubuntu 20.0.4. My laptop connection is wifi not cable
All has been working fine with local network connections and internet on wifi
A software update availability popped up and I confirmed ok to update
Update completed no problem
I had a problem while working in windows 7 on virtualbox which caused me to reboot back into xubuntu
I could no longer access the internet but my local area network was still connected via wifi
I can ping 8.8.8.8
But not ping google.com

I checked resolv.conf which reads:
nameserver 127.0.0.53

I checked no-stub-resolve.conf and it reads the correct dns ip address for whichever wifi i connect to
I have 2 modems and a hot spot on my apple phone
They all work on windows systems

I checked my yaml file: 01-network-manager-all.yaml
which reads:

network
  version: 2
  renderer: NetworkManager

I have ready as many of the posts on this subject and there are a wide range of proposed solutions
and im not sure that it would be good to try these where they revolve around removing sym links to resolv.conf
and modifying the yaml file.

I think its a name resolution problem as when pinging google.com i get the reply : Temporary failure in name resolution
All the settings look correct. Not sure what to do next other then a re installation as a last resort

---

### Post by &amp;KyT$0P# on 2022-02-11
> **iancoullie said:**
> I checked resolv.conf which reads:
nameserver 127.0.0.53

I checked no-stub-resolve.conf and it reads the correct dns ip address for whichever wifi i connect to

Does running
```
resolvectl status
```
in Terminal also show the correct dns ip address?

---

### Post by slickymaster on 2022-02-11
*Thread moved to **Networking & Wireless**.*

---

### Post by iancoullie on 2022-02-11
Thanks for the reply

not sure what im looking at
The last bit of code is from the windows machine on the same network if its any help

```


ian@ianlinux:~$ resolvectl status
Global
       LLMNR setting: no                  
MulticastDNS setting: no                  
  DNSOverTLS setting: no                  
      DNSSEC setting: no                  
    DNSSEC supported: no                  
          DNSSEC NTA: 10.in-addr.arpa     
                      16.172.in-addr.arpa 
                      168.192.in-addr.arpa
                      17.172.in-addr.arpa 
                      18.172.in-addr.arpa 
                      19.172.in-addr.arpa 
                      20.172.in-addr.arpa 
                      21.172.in-addr.arpa 
                      22.172.in-addr.arpa 
                      23.172.in-addr.arpa 
                      24.172.in-addr.arpa 
                      25.172.in-addr.arpa 
                      26.172.in-addr.arpa 
                      27.172.in-addr.arpa 
                      28.172.in-addr.arpa 
                      29.172.in-addr.arpa 
                      30.172.in-addr.arpa 
                      31.172.in-addr.arpa 
                      corp                
                      d.f.ip6.arpa        
                      home                
                      internal            
                      intranet            
                      lan                 
                      local               
                      private             
                      test                

Link 3 (wlp3s0)
      Current Scopes: DNS          
DefaultRoute setting: yes          
       LLMNR setting: yes          
MulticastDNS setting: no           
  DNSOverTLS setting: no           
      DNSSEC setting: no           
    DNSSEC supported: no           
         DNS Servers: 192.168.1.254
          DNS Domain: ~.           
                      home         

Link 2 (enp2s0f1)
      Current Scopes: none
DefaultRoute setting: no  
       LLMNR setting: yes 
MulticastDNS setting: no  
  DNSOverTLS setting: no  
      DNSSEC setting: no  
    DNSSEC supported: no 

ian@ianlinux:~$ ping -c4 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_seq=1 ttl=64 time=41.5 ms
64 bytes from 192.168.1.254: icmp_seq=2 ttl=64 time=3.86 ms
64 bytes from 192.168.1.254: icmp_seq=3 ttl=64 time=3.45 ms
64 bytes from 192.168.1.254: icmp_seq=4 ttl=64 time=4.50 ms

--- 192.168.1.254 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3006ms
rtt min/avg/max/mdev = 3.447/13.329/41.517/16.278 ms
ian@ianlinux:~$ 

ian@ianlinux:~$ ping -c4 google.com
ping: google.com: Temporary failure in name resolution



Name:    Wi-Fi
Description:    Realtek RTL8723BE 802.11 bgn Wi-Fi Adapter
Physical address (MAC):    cc:b0:da:3c:bd:a9
Status:    Operational
Maximum transmission unit:    1500
Link speed (Receive/Transmit):    72/72 (Mbps)
DHCP enabled:    Yes
DHCP servers:    192.168.1.254
DHCP lease obtained:    &#8206;Saturday, &#8206;12 &#8206;February &#8206;2022 7:41:55 AM
DHCP lease expires:    &#8206;Sunday, &#8206;13 &#8206;February &#8206;2022 7:41:55 AM
IPv4 address:    192.168.1.70/24
IPv6 address:    fd58:d759:35b2:b600:8854:3c40:cde2:183c/64, fd58:d759:35b2:b600:9c6b:ba5c:592:ff52/128, fe80::8854:3c40:cde2:183c%14/64
Default gateway:    192.168.1.254
DNS servers:    fe80::1%14, 192.168.1.254, 192.168.1.254
DNS domain name:    home
DNS connection suffix:    home
Network name:    SPARK-Z2SYSA
Network category:    Private
Connectivity (IPv4/IPv6):    Connected to Internet / Connected to unknown network


```

---

### Post by &amp;KyT$0P# on 2022-02-11
It looks like systemd-resolved is picking up the correct dns server.  Could you please post the output from running this command in Terminal? -
```
dig ubuntu.com
```

If that doesn't successfully resolve ubuntu.com to any IP address(es), what about -
```
dig @192.168.1.254 ubuntu.com
```

---

### Post by iancoullie on 2022-02-11
Thanks here it is

```


ian@ianlinux:~$ dig ubunu.com

; <<>> DiG 9.16.1-Ubuntu <<>> ubunu.com
;; global options: +cmd
;; connection timed out; no servers could be reached

ian@ianlinux:~$ dig @192.168.1.254 ubuntu.com

; <<>> DiG 9.16.1-Ubuntu <<>> @192.168.1.254 ubuntu.com
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 57938
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;ubuntu.com.            IN    A

;; ANSWER SECTION:
ubuntu.com.        48    IN    A    185.125.190.21
ubuntu.com.        48    IN    A    91.189.88.180
ubuntu.com.        48    IN    A    185.125.190.20
ubuntu.com.        48    IN    A    91.189.88.181
ubuntu.com.        48    IN    A    185.125.190.29

;; Query time: 4 msec
;; SERVER: 192.168.1.254#53(192.168.1.254)
;; WHEN: Sun Feb 13 00:01:07 NZDT 2022
;; MSG SIZE  rcvd: 119

ian@ianlinux:~$ 

```

Regards Ian

---

### Post by &amp;KyT$0P# on 2022-02-11
Do you have a firewall on your Xubuntu system that's blocking access to systemd-resolved (127.0.0.53 UDP port 53) or the loopback interface?

---

### Post by iancoullie on 2022-02-11
Doesn't look like any firewall and port seems to be used by DNS

```

ian@ianlinux:~$ sudo ufw status
[sudo] password for ian: 
Status: inactive
ian@ianlinux:~$ lsof -i TCP:53
ian@ianlinux:~$ sudo lsof -i TCP:53
COMMAND   PID            USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
systemd-r 789 systemd-resolve   13u  IPv4  30972      0t0  TCP 127.0.0.53:domain (LISTEN)
ian@ianlinux:~$ 

```

Thanks for persevering

---

### Post by iancoullie on 2022-02-11
Sorry I think this tests the loopback interface
[code]
ian@ianlinux:~$ telnet 127.0.0.53 53
Trying 127.0.0.53...
Connected to 127.0.0.53.
Escape character is '^]'.
[/]

---

### Post by iancoullie on 2022-02-12
Sucumbed to re-install

---

