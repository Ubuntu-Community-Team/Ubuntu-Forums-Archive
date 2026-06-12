---
title: "Temporary failure in name resolution"
date: 2018-05-08
forum: Networking &amp; Wireless
---

### Post by kevin.nelson on 2018-05-08
Hello all,

I'm setting up a ubuntu server on my network to use my local windows DNS server for name resolution (located at 192.168.40.20).  When I try to ping other machines on my network from the ubuntu server, I get  the following error: Temporary failure in name resolution.  This is true both if I try the qualified or full name.


I can dig other machines by specifying the name server like 

# dig @192.168.40.20 <hostname>

which works just fine, so the DNS server itself is working fine.  Also, every other machine on the network is using the DNS server and working just fine.


I've set up my /etc/netplan/50-cloud-init.yaml file as follows

network:
    version: 2
    ethernets:
        ens160:
        addresses: [192.168.40.6/24]
        gateway4: 192.168.40.1
        nameservers:
            addresses: [192.168.40.20]

and run sudo netplan apply (also I've rebooted)

when I run systemd-resolve --status I see the following

Global
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


Link 7 (idrac)
      Current Scopes: none
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: no
    DNSSEC supported: no


Link 2 (ens160)
      Current Scopes: DNS
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: no
    DNSSEC supported: no
         DNS Servers: 192.168.40.20



I'm not sure what I've got misconfigured.  Any help would be appreciated.

Thanks!
Kevin

---

### Post by papibe on 2018-05-08
Hi kevin.nelson. Welcome to forum ):P

Could you run these commands, and post back the results? (you can copy/paste the text)
```
apt policy netplan

ip address

ip route

cat /etc/network/interfaces

cat /etc/resolv.conf

cat /etc/nsswitch.conf 

nslookup ubuntu.com

dig ubuntuforums.org

ping 192.168.40.20
```
Regards.

---

### Post by kevin.nelson on 2018-05-09
Hi [COLOR=#000000]papibe, thanks for the response.

I've provided the results which you requested below.

Additionally, I noticed that if I manually add 192.168.40.20 as a nameserver to /etc/resolv.conf, name resolution works as expected.  However, the comments in the file say not to edit because the file is managed by systemd-resolved.  Therefore, I think my specific question becomes how to add a nameserver to systemd-resolved.  I thought this was done by configuring a nameserver in /etc/netplan/50-cloud-init.yaml, but that does not work.

```

# apt policy netplan

netplan:
  Installed: (none)
  Candidate: 1.10.1-5build1
  Version table:
     1.10.1-5build1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/universe amd64 Packages

```
```

# ip address


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: ens160: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 00:50:56:8f:44:e6 brd ff:ff:ff:ff:ff:ff
    inet 192.168.40.6/24 brd 192.168.40.255 scope global ens160
       valid_lft forever preferred_lft forever
    inet6 fe80::250:56ff:fe8f:44e6/64 scope link
       valid_lft forever preferred_lft forever
3: idrac: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 44:a8:42:10:6c:b1 brd ff:ff:ff:ff:ff:ff

```[/COLOR]
```
[COLOR=#000000]
# ip route

default via 192.168.40.1 dev ens160 proto static
192.168.40.0/24 dev ens160 proto kernel scope link src 192.168.40.6
[/COLOR]
```
```
[COLOR=#000000]
# cat /etc/network/interfaces

# ifupdown has been replaced by netplan(5) on this system.  See
# /etc/netplan for current configuration.
# To re-enable ifupdown on this system, you can run:
#    sudo apt install ifupdown
[/COLOR]
```
```
[COLOR=#000000]
# cat /etc/resolv.conf

# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "systemd-resolve --status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.


nameserver 127.0.0.53
[/COLOR]
```
```
[COLOR=#000000]
# cat /etc/nsswitch.conf

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.


passwd:         compat systemd
group:          compat systemd
shadow:         compat
gshadow:        files


hosts:          files dns
networks:       files


protocols:      db files
services:       db files
ethers:         db files
rpc:            db files


netgroup:       nis
[/COLOR]
```
```

# nslookup ubuntu.com

Server:         127.0.0.53
Address:        127.0.0.53#53


Non-authoritative answer:
Name:   ubuntu.com
Address: 91.189.94.40

```
```
[COLOR=#000000]
# dig ubuntuforums.com

[/COLOR] <<>> DiG 9.11.3-1ubuntu1-Ubuntu <<>> ubuntuforums.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 34584
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;ubuntuforums.com.              IN      A


;; ANSWER SECTION:
ubuntuforums.com.       598     IN      A       91.189.94.12
ubuntuforums.com.       598     IN      A       91.189.94.16


;; Query time: 162 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Wed May 09 14:05:14 UTC 2018
;; MSG SIZE  rcvd: 77

```
```
[COLOR=#000000]
# ping 192.168.40.20

[/COLOR]64 bytes from 192.168.40.20: icmp_seq=1 ttl=128 time=0.132 ms
64 bytes from 192.168.40.20: icmp_seq=2 ttl=128 time=0.101 ms
64 bytes from 192.168.40.20: icmp_seq=3 ttl=128 time=0.165 ms

--- 192.168.40.20 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2052ms
rtt min/avg/max/mdev = 0.101/0.132/0.165/0.029 ms

```
[COLOR=#000000]


[/COLOR]

---

### Post by papibe on 2018-05-09
Thanks.

Did you install netplan.io instead of netplan? Cloud you run this command?
```
apt policy netplan.io
```

127.0.0.53 in your resolv.conf makes me think you had NetworkManager installed. Is this a server edition or a desktop serving as a server?

If this is a server edition, it looks like systemd-resolved is conflicting with netplan. Try this:
```
 sudo systemctl disable systemd-resolved
```
and then reboot
```
sudo reboot
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by kevin.nelson on 2018-05-10
Hello,

Thanks for the response.

I was able to fix my problem by editing /etc/systemd/resolved.conf and adding the DNS server there.  I also had to add the local domain name that the DNS server is handling or it wouldn't resolve.  However, everything seems to work now.

To answer your question, this is ubuntu server addition.  The server is freshly installed with all the default packages.  It looks like netplan.io is installed instead of netplan (i'm not familiar with the differences).

Thank you for your help!

---

### Post by medikoo2 on 2018-08-22
> **papibe said:**
> If this is a server edition, it looks like systemd-resolved is conflicting with netplan. Try this:
```
 sudo systemctl disable systemd-resolved
```
and then reboot
```
sudo reboot
```
Hope it helps.

I've approached this issue when upgrading to 18 from 16, and disabling systemd-resolved as instructed above, solved the issue.

Thanks @papibe!

---

### Post by Drone4four on 2019-01-28
My Ubuntu 18.04 DigitalOcean droplet server is toast as of two days ago and I have no idea why or what changed. I first noticed the issue when my vhosts became inaccessible. Then I tried to ssh in from my localhost (with rsa keys in place) and the ssh session timed out completely. The only way I can access my server right now is from the QEMU web front end provided by DigitalOcean in my web browser.

Attached you can view the original apt errors I am trying to deal with.  

I would like to provide the output from **@papibe**’s suggested commands, but it appears there is no way for me to copy text from my web terminal emulator like I ordinarily would from a local gnome-terminal session. So I have taken screenshots of all my output so you folks can see. 

As suggested elsewhere, I tried temporarily turning off my firewall and running apt update and which didn’t fix the issue. I promptly turned my firewall back on.

What worked for **@medikoo2** (disabling systemd-resolved) didn’t work for me.

What else would you people recommend I try next?

---

### Post by Drone4four on 2019-01-28
By the way, a similar issue described over on DigitalOcean called, "[Apt-get update failing with unable to resolve error]("https://www.digitalocean.com/community/questions/apt-get-update-failing-with-unable-to-resolve-error")"

A veteran forum member there suggested:
```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update

```
This didn&#8217;t fix the issue

---

