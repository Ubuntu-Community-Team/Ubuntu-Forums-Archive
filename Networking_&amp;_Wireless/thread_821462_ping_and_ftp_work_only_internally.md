---
title: "ping and ftp work only internally"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by PatricioLearner on 2008-06-07
I am trying to learn ftp. This is where I am:
1) Already installed vsftpd
2) FTP from my vista-laptop to my ubuntu-ftp-sever using my internal IP.
3) Found my external IP, configure wireless modem to route the ftp requests to the ubuntu-ftp-server
4) FTP from my vista-laptop to my unbuntu-ftp-sever using my EXTERNAL IP while still connect to my internal network.

The problem: I cannot access my ftp server from outside my private network.  Actually I cannot even ping my external IP address when I am outside my private network. In case it helps I have a Linksys connected to a cable modem.
I am very new to networking so please forgive me if I am asking the obvious. 

Outside:
>ping 98.212.xx.xxx
no answer from 98.212.xx.xxx

Inside:
>ping 98.212.xx.xx
PING 98.212.xx.xxx (98.212.xx.xxx) 56(84) bytes of data.
64 bytes from 98.212.xx.xxx: icmp_seq=1 ttl=64 time=0.452 ms


$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.723 m

Thanks!

---

