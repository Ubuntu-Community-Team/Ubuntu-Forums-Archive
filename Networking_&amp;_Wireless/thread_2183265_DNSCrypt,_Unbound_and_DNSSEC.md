---
title: "DNSCrypt, Unbound and DNSSEC"
date: 2013-10-24
forum: Networking &amp; Wireless
---

### Post by eon01 on 2013-10-24
[COLOR=#333333][FONT=Helvetica Neue]I would like to have an encrypted DNS queries + a DNS Cache + Domain Name System Security Extensions (DNSSEC) .[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue]I used this bash script to install DNSCrypt and I choosed to use dnscrypt.eu servers :[/FONT][/COLOR]
DNSCrypt.eu (no logs)

```
Holland
Server address:
176.56.237.171:443
Provider name
2.dnscrypt-cert.dnscrypt.eu
Public key
67C0:0F2C:21C5:5481:45DD:7CB4:6A27:1AF2:EB96:9931:40A3:09B6:2B8D:1653:1185:9C66
```
[COLOR=#333333][FONT=Helvetica Neue]I installed ( apt-get install unbound ) Unbound and my unbound.conf file contains :
[/FONT][/COLOR]```

#
# See the unbound.conf(5) man page.
#
# See /usr/share/doc/unbound/examples/unbound.conf for a commented
# reference config file.

server:
    # The following line will configure unbound to perform cryptographic
    # DNSSEC validation using the root trust anchor.
    auto-trust-anchor-file: "/var/lib/unbound/root.key"
server:
verbosity: 1
num-threads: 4                                                        
interface: 0.0.0.0
 do-ip4: yes
 do-udp: yes
 do-tcp: yes
 access-control: 192.168.0.0/24 allow                
 do-not-query-localhost: no
 chroot: ""       
 logfile: "/var/log/unbound.log"             
 use-syslog: no 
 hide-identity: yes
 hide-version: yes 
 harden-glue: yes
 harden-dnssec-stripped: yes
 use-caps-for-id: yes       
 private-domain: "localhost"      
 local-zone: "localhost." static
 local-data: "freebox.localhost. IN A 192.168.0.254"                                              
 local-data-ptr: "192.168.0.254 freebox.localhost"
python:
remote-control:
forward-zone:
  name: "."
  forward-addr: 127.0.0.1@40
```
[COLOR=#333333][FONT=Helvetica Neue]Like you see, I added this line to activate DNSSEC :[/FONT][/COLOR]
```
server:
    # The following line will configure unbound to perform cryptographic
    # DNSSEC validation using the root trust anchor.
    auto-trust-anchor-file: "/var/lib/unbound/root.key"
``` 
[COLOR=#333333][FONT=Helvetica Neue]Now, when I enter : sudo service unbound start This is the error that I get :[/FONT][/COLOR]
     ```
* Restarting recursive DNS server unbound
[1382606879] unbound[8878:0] error: bind: address already in use
[1382606879] unbound[8878:0] fatal error: could not open ports
```
[COLOR=#333333][FONT=Helvetica Neue]My question is of course about the error ! Also, is it useful to use DNSSEC in an ordinary laptop (not a DNS server) or it is just useful for DNS Servers ?[/FONT][/COLOR]

---

### Post by eon01 on 2013-10-24
[COLOR=#333333][FONT=Helvetica Neue]I found a solution : 

When typing[/FONT][/COLOR]
```
sudo lsof -nPi | grep \:53

```[COLOR=#333333][FONT=Helvetica Neue]I can see that bind is also listening on the same port :[/FONT][/COLOR]
```
TCP *:53 (LISTEN)

```[COLOR=#333333][FONT=Helvetica Neue]I made then a modification on /etc/unbound/unbound.conf by adding this line :[/FONT][/COLOR]
```
port:533

```[COLOR=#333333][FONT=Helvetica Neue]ps : The port number, default 53, on which the server responds to queries.[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]Another solution is to change the port of Bind from 53 to another.[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]I hope it will help others having the same problem.[/FONT][/COLOR]

---

### Post by ziga555 on 2013-12-17
Hello guys!

I am new at unbound and dns server and I need some help. I configured unbound server but it doesn't work correct.
Here is my config: [http://pastebin.com/LjuFsyKR](http://pastebin.com/LjuFsyKR)

And dig returning me this:
[http://pastebin.com/AuUrMAQx](http://pastebin.com/AuUrMAQx)

Looks like it is not returning SOA properly.

Thanks for help!

---

