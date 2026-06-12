---
title: "Multiple Static IPs on one NIC Ubuntu Server 16.04"
date: 2017-10-17
forum: Networking &amp; Wireless
---

### Post by patdundee on 2017-10-17
Hi
I have been trawling the internet for ages. So far I have not found any info that will allow me to assign multiple Ips to one network card.

My current config runs Public IPs and is set as shown 

    > auto lo enp17s0
    iface lo inet loopback

    iface enp17s0 inet static
        address 109.xxx.xxx.xxx/27
        gateway 109.xxx.xxx.xxx
        broadcast 109.xxx.xxx.xxx
        network 109.xxx.xxx.xxx
        dns-nameservers 8.8.8.8 109.xxx.xxx.xxx 109.xxx.xxx.xxx

I need to add 4 more IP address's in the same /27 range

Does anyone know how this can be acheived correctly. It was a lot easier in Server 14.04 :)

---

### Post by patdundee on 2017-10-17
I seem to have found an answer to my issue and have added 3 more IPs and  also sorted out the dns servers not being set. See new config below  with dns nameservers remmed out

> auto lo enp17s0
    iface lo inet loopback

    iface enp17s0 inet static
        address 109.xxx.xxx.xxx/27
        gateway 109.xxx.xxx.xxx
        broadcast 109.xxx.xxx.xxx
        network 109.xxx.xxx.xxx
        #dns-nameservers 8.8.8.8 109.xxx.xxx.xxx 109.xxx.xxx.xxx

iface enp17s0 inet static
        address 109.xxx.xxx.xxx/27

iface enp17s0 inet static
        address 109.xxx.xxx.xxx/27

iface enp17s0 inet static
        address 109.xxx.xxx.xxx/27

iface enp17s0 inet static
        address 109.xxx.xxx.xxx/27

I have managed to get the dns nameservers added into the resolv.conf

However when i run this command to reset the network (without losing the ssh session)

> ifdown enp17s0 && ifup enp17s0

I get the following reply 

> RTNETLINK answers: Cannot assign requested address
RTNETLINK answers: Cannot assign requested address
RTNETLINK answers: Cannot assign requested address

But all IPs are accepted and respond to ping from internal and external outside the network. 
Reboot the system and i still get a reply from internal and external outside the network

Curious as to why RTNETLINK says it cannot assign requested address for the 3 new ones when they are in fact assigned

---

