---
title: "Fresh 21.10 install cannot resolve .local hostnames"
date: 2022-02-09
forum: Networking &amp; Wireless
---

### Post by terrarum on 2022-02-09
I am having a hard time getting a fresh Kubuntu 21.10 install to access other machines on my network using hostname.local resolution.

 I have the following:
 
[LIST]
[*]Kubuntu 21.10 install named **jwork** - this is the problem machine 
[*]Ubuntu Server 20.04 install named **gimli** 
[*]Raspbian install named **plexpi** 
[/LIST]

 gimli and plexpi can ping **gimli.local**, **plexpi.local** and **jwork.local** and get a response.

 jwork gets no response from any of those, but does get a response from jwork.

 Related fact: Spotify on jwork cannot see any devices to cast to on my network. It could when I was on Manjaro before I switched to Kubuntu.

 Here are the contents of various files that I have worked out might be relevant:

 **/etc/resolv.conf**

 ```
nameserver 127.0.0.53
options edns0 trust-ad
search .
```
**/etc/systemd/resolved.conf**

 ```
[Resolve]
MulticastDNS=yes
LLMNR=yes
```
**/etc/nsswitch.conf**

 ```
passwd:         files systemd
group:          files systemd
shadow:         files
gshadow:        files

hosts:          files mdns4_minimal [NOTFOUND=return] dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```
[B]
libnss-mdns[/B] is installed

 **/etc/NetworkManager/conf.d/mdns.conf**

 ```
[connection]
connection.mdns=2
connection.llmnr=2
```
[B]
/etc/avahi/avahi-daemon.conf[/B]

 ```
[server]
domain-name=getoutoftheway
use-ipv4=yes
use-ipv6=yes
ratelimit-interval-usec=1000000
ratelimit-burst=1000

[wide-area]
enable-wide-area=yes

[publish]
publish-hinfo=no
publish-workstation=no
```

** avahi-daemon** is installed

 [B]resolvectl status
[/B]
```

 Global
       Protocols: +LLMNR +mDNS -DNSOverTLS DNSSEC=no/unsupported
resolv.conf mode: stub

Link 2 (enp7s0)
    Current Scopes: DNS LLMNR/IPv4 LLMNR/IPv6 mDNS/IPv4 mDNS/IPv6
         Protocols: +DefaultRoute +LLMNR +mDNS -DNSOverTLS DNSSEC=no/unsupported
Current DNS Server: 1.1.1.1
       DNS Servers: 1.1.1.1 1.0.0.1
```

For comparison, here’s gimli’s resolvectl status:

```

 Global
       LLMNR setting: no                  
MulticastDNS setting: no                  
  DNSOverTLS setting: no                  
      DNSSEC setting: no                  
    DNSSEC supported: no                  
          DNSSEC NTA: 10.in-addr.arpa     
                      ...more arpa addresses
                      corp                
                      d.f.ip6.arpa        
                      home                
                      internal            
                      intranet            
                      lan                 
                      local               
                      private             
                      test     

Link 3 (wlp2s0)
      Current Scopes: DNS    
DefaultRoute setting: yes    
       LLMNR setting: yes    
MulticastDNS setting: no     
  DNSOverTLS setting: no     
      DNSSEC setting: no     
    DNSSEC supported: no     
  Current DNS Server: 1.1.1.1
         DNS Servers: 1.1.1.1
                      1.0.0.1
```

So that’s a lot of information. Can anyone tell me what I need to do to get jwork to start resolving .local domains correctly?

 &#8203;

---

### Post by Morbius1 on 2022-02-09
I booted into a Kubuntu 21.10 install disk running in "Demo" mode and everything works for me.

I do have a question though. What is this all about:
> /etc/avahi/avahi-daemon.conf

Code:

[server]
**[COLOR="#FF0000"]domain-name=getoutoftheway[/COLOR]**

Why the change from the default .local? It doesn't explain your symptom as it only impacts others from pinging you with a hostname.local. It's just a curious change.

---

### Post by terrarum on 2022-02-09
I did not make that change, that's how I found that file. What should it be?

Edit: presumably .local since you said that's the default haha. I'll see if that does anything.

Edit 2: having set that to **domain-name=local** I can now ping **jwork.local** from jwork successfully. I still cannot ping **gimli.local** though.

---

### Post by terrarum on 2022-02-09
> **Morbius1 said:**
> I booted into a Kubuntu 21.10 install disk running in "Demo" mode and everything works for me.

Oh yes and thank you for this. If nothing else comes up I'll give that a try myself after work and see what the difference is.

---

### Post by terrarum on 2022-02-11
Booted into a Kubuntu live disk. Pinging gimli.local works, I couldn't see any notable configuration differences and that getoutoftheway value isn't there so I have to assume that I installed something weird or blindly copy pasted it and didn't notice. Clearly a layer 8 issue either way.

---

