---
title: "ubuntu sending packets to 224.0.0.251:5353"
date: 2021-03-23
forum: Networking &amp; Wireless
---

### Post by dave219 on 2021-03-23
hello guys:

why ubuntu keep sending out mDNS packets? but supposedly mDNS is not running. i checked my firewall logs:

```
Mar 17 23:43:27 <security.info> FW kernel: ipfw: 9999 Deny UDP 192.168.xx.xx:5353 224.0.0.251:5353 in via em0

user@home:~$ resolvectl status
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
      Current Scopes: none
DefaultRoute setting: no  
       LLMNR setting: yes 
MulticastDNS setting: no  
  DNSOverTLS setting: no  
      DNSSEC setting: no  
    DNSSEC supported: no  


Link 2 (enp0s25)
      Current Scopes: DNS           
DefaultRoute setting: yes           
       LLMNR setting: yes           
MulticastDNS setting: no            
  DNSOverTLS setting: no            
      DNSSEC setting: no            
    DNSSEC supported: no            
  Current DNS Server: 208.67.220.220
         DNS Servers: 208.67.220.220
                      8.8.4.4       
          DNS Domain: ~.
```

---

### Post by TheFu on 2021-03-23
a) when posting logs or terminal output, please wrap it in code-tags in these forums.  How to: [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)
b) Is **avahi** running?

---

### Post by Doug S on 2021-03-23
> **dave219 said:**
> Mar 17 23:43:27 <security.info> FW kernel: ipfw: 9999 Deny UDP 192.168.xx.xx:5353 224.0.0.251:5353 in via em0 Describe this log entry in more detail. What is "em0", as it is not in your other output. How do you know it is an Ubuntu computer sending those packets?

In the past approximately 11 days, there have been 57989 of those types of packets on my LAN, but none were from my Ubuntu test server.

---

### Post by TheFu on 2021-03-23
em0 is the NIC device name.

Where it comes from is clear by the source IP address. The OP just needs to find the device at that IP. With a well-managed network, every IP address is known and connected to a single, specific, device.  With a reverse DNS lookup (assuming a properly configured DNS on the LAN), it would be easy.  
```
host 192.168.22.23
```

In a loosey-goosey network, DHCP without any IP reservations is common - so manually checking each devices' current IP is one method.  May try the **arp** command to get a MAC-to-IP mapping. From a MAC lookup tool website, the NIC vendor for the device could be discovered ... which would intuitively lead to a specific type of device.

For example, arp returns a line like this:
```
hdhr5                    ether   00:18:dd:07:xx:xx   C                     ens3
```
here. There are 20 other lines returned too.  The hdhr5 tells me exactly which device it is, but my network is "well-managed". It could be an IP address instead which isn't exactly useful ... unless all I had was the IP and I wanted the MAC.  Taking the MAC, 00:18:dd:07:xx:xx, and visiting a MAC lookup website .... returns this:
MAC Address Lookup Result - 00:18:dd:07:xx:xx

```
00:18:DD
Silicondust Engineering Ltd
38 Lillington Road
Auckland    
 [nz - &#12491;&#12517;&#12540;&#12472;&#12540;&#12521;&#12531;&#12489;] NZ
```
Ah ... Silicondust that's a TV tuner.  I know exactly which device it is on my LAN.  

Lookup for  b8:27:eb: ... says: 
```
B8:27:EB
Raspberry Pi Foundation
Mitchell Wood House
Caldecote  Cambridgeshire  CB23 7NU
 [us - &#12450;&#12513;&#12522;&#12459;&#21512;&#34886;&#22269;] US
```
Ah - it is one of my Raspberry Pi computers.

 f0:4d:a2: ... 
```
F0:4D:A2
Dell Inc.
One Dell Way, MS RR5-45
Round Rock     78682
 [us - &#12450;&#12513;&#12522;&#12459;&#21512;&#34886;&#22269;] US
```
is for a Dell.  Since I have only 1 Dell computer powered, I know exactly which device it is.

Anyways, those are some examples.

---

