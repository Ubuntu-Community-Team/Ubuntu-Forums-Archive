---
title: "Ubuntu Server 20.10: DNS not working"
date: 2021-04-30
forum: Networking &amp; Wireless
---

### Post by pelgrim on 2021-04-30
I have Ubuntu 20.10 server, with working internet.
pinging addresses work, but DNS not.
I can not update/upgrade ubuntu anymore.
One of the things I need to do with this server is sending out emails.

I spent one day searching on the internet for this, but no solution seems to work for me.

/etc/netplan/50-cloud-init.yaml
```
# This is the network config written by 'subiquity'
network:
  ethernets:
    enp5s0:
      dhcp4: true
    enp4s0:
      addresses:
        - 192.168.0.1/24
  version: 2
```

dig google.com
```
; <<>> DiG 9.16.1-Ubuntu <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 24409
;; flags: qr rd ra; QUERY: 0, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; Query time: 3 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Fri Apr 30 17:25:30 UTC 2021
;; MSG SIZE  rcvd: 12

```

dig @8.8.8.8 [www.google.com](www.google.com)
```
; <<>> DiG 9.16.1-Ubuntu <<>> @8.8.8.8 www.google.com
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 42034
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;www.google.com.			IN	A

;; ANSWER SECTION:
www.google.com.		135	IN	A	172.217.17.68

;; Query time: 11 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Fri Apr 30 17:28:42 UTC 2021
;; MSG SIZE  rcvd: 59

```

resolvectl query [www.google.com](www.google.com)
```
www.google.com: 142.250.179.196                -- link: enp5s0

-- Information acquired via protocol DNS in 13.6ms.
-- Data is authenticated: no

```

/etc/resolv.conf
```
# ............

nameserver 127.0.0.53
options edns0 trust-ad
search telenet.be

```

after trying just about anything I get now this result, before Current DNS Server entry was not present.
systemd-resolve --status | grep Current
```
      Current Scopes: DNS          
  Current DNS Server: 8.8.8.8      
      Current Scopes: none

```

appreciate any help.

---

### Post by TheFu on 2021-04-30
```
# This is the network config written by 'subiquity'
network:
  version: 2
  [COLOR="#0000FF"]renderer: networkd[/COLOR]
  ethernets:
    enp5s0:
      [COLOR="#0000FF"]dhcp4: false
      dhcp6: false
[/COLOR]    enp4s0:
      addresses:
        - 192.168.0.[COLOR="#0000FF"]1[/COLOR]/24
[COLOR="#0000FF"]       dhcp4: false
       dhcp6: false[/COLOR]
       gateway4: [COLOR="#0000FF"]{your gateway IP}[/COLOR]
[COLOR="#0000FF"]       nameservers:
         addresses: [ "8.8.8.8", "1.1.1.1" ][/COLOR]

```
I really think this: 192.168.0.[COLOR="#FF0000"]1[/COLOR]/24 is incorrect.  .1 is almost always the gateway IP. Check that.

Run
```
sudo netplan generate
sudo netplan apply --debug
```

---

### Post by pelgrim on 2021-05-01
TheFu, thank you for your reaction.

enp5s0 is the network to internet
enp5s0:
      dhcp4: true

is needed, it goes directly to the internet provider.

everything defined under enp4s0 is not relevant,
this is for the local network, which is out of scope of this question.

This server needs to connect to smtp.gmail.com to send out emails
and needs to find the ubuntu servers for updates, both through enp5s0.
When I replace smtp.gmail.com with an ip address, things work, but that's only a short-term solution.

The lan pc I have connected to enp4s0 is also running ubuntu and has no problems with dns, it can update ubuntu for example without any problem.

---

### Post by TheFu on 2021-05-01
Simplify and test.  Get 1 working first.

---

### Post by pelgrim on 2021-05-02
ok ...
that means you also don't know I assume.

I hope this is picked up by someone.

---

### Post by TheFu on 2021-05-02
Here, we never have all the facts and have to make reasonable assumptions.  For example, I didn't assume this was a router. I assumed it was a server that happened to be connected to multiple networks.

In my post, there is enough to get both NICs working. Just put the gateway and nameservers where they are needed. Also, don't forget to add the renderer.  I remember my first 20.04 server install didn't have networking work at all. Seemed fairly odd to me that the installer didn't get 20 lines of simple substitution correct. After the .1 release, I thought it all started working.
I do a few things different than the defaults, like I point directly at my internal DNS and don't run a caching DNS locally. resolvconf and systemd-resolved weren't working for me, and they aren't necessary on LANs with DNS already there. Basically, they are trying to fix a problem that we don't have here ... except when the fix breaks.

---

### Post by pelgrim on 2021-05-02
hi,

for those that can benefit from it, I finally found something that worked.

Indeed, I should have told that this server also worked as a router.
My mistake.

Now, this is what I performed to get DNS for the server working:

sudo nano etcsystemd/resolved.conf
```
DNSStubListener=no
```

systemctl stop systemd-resolved
sudo rm etc/resolv.conf
echo nameserver 8.8.8.8 | sudo tee /etc/resolv.conf

and bingo, I can
ping [www.google.com](www.google.com)

---

### Post by TheFu on 2021-05-02
Ok. Let's look at post #7 above.

The OP is stopping systemd-resolved, so editing the config file has ZERO effect. I think *etcsystemd/resolved.conf* is a typo. We all make them. I might have made some below:

The correct way to do this is:
Setup a temporary /etc/resolv.conf.new file - and add the lines after the sudoedit command
$ sudoedit /etc/resolv.conf.new
```
 nameserver 8.8.8.8
 nameserver 8.8.4.4
```

If you want more privacy, but fast nameservers, use these:
```
 nameserver 1.1.1.1
 nameserver 1.0.0.1
```

We always want at least 2 DNS servers. 

Next, disable systemd-resolved forever.  Be certain you "mask" systemd-resolved, so it will work forever.
```
sudo systemctl stop systemd-resolved.service
sudo systemctl mask systemd-resolved.service
```

And quickly, remove the existing /etc/resolv.conf (link/file/whatever) and move the new one into place.
```
sudo rm /etc/resolv.conf
sudo  mv  /etc/resolv.conf.new  /etc/resolv.conf
```
Do this quickly - copy/paste would be best. Sudo may be configured to check which system it is on DNS issues could make it so that sudo doesn't work. We are trying to minimize the chance that the sudo cache expires.

**This is probably incorrect:**
```
sudo nano etcsystemd/resolved.conf
```
Whenever editing system files, it is safest to use sudoedit for a multitude of reasons. Plus, we can use any editor we like, safely - even GUI editors - if we are on a system that supports GUIs.

---

