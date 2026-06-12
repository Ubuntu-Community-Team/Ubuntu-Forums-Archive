---
title: "VPN oddities"
date: 2023-08-02
forum: Networking &amp; Wireless
---

### Post by cauliflower on 2023-08-02
Hello,

VERSION="22.04.2 LTS (Jammy Jellyfish)"

I have an odd situation that I haven't been able to resolve. I use Linux regularly but I'm definitely a user not a sysadmin!

At work we have a VPN which allows us access to iLO on some of our  servers in our Data Centre. On my other devices once connected to the  VPN I can browse to the iLO GUI no problem. But on my Ubuntu desktop it  just times out. Weirdly tcptraceroute and telnet to port 443 seem to  work fine. Note I am connected to the same wireless network (and same  VPN) on all devices. When I check my IP address it looks like:


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 18:03:73xxx brd ff:ff:ff:ff:ff:ff
    altname enp0s25
3: wlxa09f10bef7e6: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether a0:9f:10xxx brd ff:ff:ff:ff:ff:ff
    inet 10.255.227.145/14 brd 10.255.255.255 scope global dynamic noprefixroute wlxa09f10bef7e6
       valid_lft 830sec preferred_lft 830sec
    inet 172.16.56.36/32 scope global wlxa09f10bef7e6
       valid_lft forever preferred_lft forever
    inet6 fe80::...<snip>/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

172.16.56.36/32 is the VPN IP. 10.255.227.145/14 is the wireless network I am connected to.
I can also successfully SSH to the iLO addresses from the Ubuntu desktop, though I had to add ssh-rsa,ssh-dss to the key types.
I feel  like this must be a FW problem as the iLO interfaces I'm trying  to access are all on the same VLAN. But what I don't understand is why  my other devices can connect to them fine.
It seems to be just browsing that is the issue.

Has anyone come across this kind of oddity before?

Guy

---

### Post by TheFu on 2023-08-02
I don't understand much of what you posted, but if you show the routing table AND posted here using the forum 'code-tags', others might be able to help.

```
alias iproute='ip route | column -t'
```
Is an alias I use to get a non-ugly routing table. The older command 'route -n' was much nicer.

BTW, there isn't just 1 sort of VPN, so to get effective help, you'll need to be clear which type of VPN is being used.  Large companies usually have some proprietary VPN software from a networking company like Cisco.  Smaller companies could use almost anything, but openvpn and wireguard would be the most popular.

I have no idea what iLO is.  Is that like a DRAC or RIBLO or IPMI server admin interface?  It is hard to know what is a "known" industry term and what your company uses. I get that.

---

