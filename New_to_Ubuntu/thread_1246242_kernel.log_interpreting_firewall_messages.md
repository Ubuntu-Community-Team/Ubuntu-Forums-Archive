---
title: "kernel.log: interpreting firewall messages?"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by minsf on 2009-08-21
hi,
i need help interpreting firewall (iptables) messages in my kernel.log
```
Aug 21 10:03:01 minsf-laptop kernel: [140240.297207] Inbound IN=wlan0 OUT= MAC=**:**:**:**:**:**:??:??:??:??:??:??:08:00 SRC=85.31.186.33 DST=192.168.0.1 LEN=626 TOS=0x00 PREC=0x20 TTL=48 ID=26305 DF PROTO=TCP SPT=80 DPT=58253 WINDOW=63874 RES=0x00 ACK PSH URGP=0 
```
where the *s are the mac address of my wireless card, and the ?s are the mac address of my router.
in particular, i can see that my machine was hit from an outside source, and i would like to confirm that the packet was blocked by the firewall. what part of the above says what happened to the packet? (or is there another place where i can get that info?)

---

### Post by minsf on 2009-08-22
bump
appreciate your help :)

---

