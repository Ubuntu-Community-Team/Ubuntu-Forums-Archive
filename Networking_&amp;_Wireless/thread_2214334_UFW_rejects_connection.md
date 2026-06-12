---
title: "UFW rejects connection"
date: 2014-03-31
forum: Networking &amp; Wireless
---

### Post by ivo_liondov on 2014-03-31
I configured ufw to work by default on REJECT everything and allowed certain applications. The output of ```
ufw status verbose
```is  this: ```
9091/tcp (Transmission-web) on eht0 ALLOW IN    192.168.0.0/24
``` However attempting to access port 9091 from 192.168.0.2 produces the following output on ufw's log: ```
Mar 31 21:00:07 lilith kernel: [  199.346987] [UFW BLOCK] IN=eth0 OUT= MAC=60:xx:xx:xx:xx SRC=192.168.0.2 DST=192.168.0.11 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=8887 DF PROTO=TCP SPT=4514 DPT=9091 WINDOW=8192 RES=0x00 SYN URGP=0
``` The same happens when attempting to access Samba/Cifs service, I am unable to use them. 


What simple thing am I missing?
Thanks all.

---

### Post by tomearp on 2014-04-02
Did you copy/paste the output from ufw status verbose?

One thing that appears wrong is it refers to eht0, which I guess should probably be eth0.

---

### Post by ivo_liondov on 2014-04-06
Should be eth0 not eht0! That is what I ment by something silly being missed! Thanks tomearp! Everything works as it should now.

---

