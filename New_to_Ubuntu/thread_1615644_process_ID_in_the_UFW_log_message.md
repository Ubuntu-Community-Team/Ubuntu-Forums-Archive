---
title: "process ID in the UFW log message"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by ramujinius on 2010-11-07
Hi 

Where is the process ID for which access is allowed/blocked by UFW in the ufw.log file?

Please let me know whether it is possible to log process id in log message using UFW when it is allowed or blocked.

In the below log messages, i am not able to find the process ID. I tried 1268 and ID=17977. Both numbers are not present in the system monitor process ID list

Log snippet

Nov  7 18:58:27 laptop kernel: [ 1268.182480] [UFW ALLOW] IN= OUT=eth1 SRC=192.168.3.2 DST=192.168.3.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=17977 DF PROTO=UDP SPT=47116 DPT=53 LEN=46 

Nov  7 18:58:27 laptop kernel: [ 1268.255874] [UFW ALLOW] IN= OUT=eth1 SRC=192.168.3.2 DST=117.121.249.253 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=3748 DF PROTO=TCP SPT=59081 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0

---

### Post by ramujinius on 2010-11-08
bump .

---

### Post by Hippytaff on 2010-11-08
I don't understand what your trying to do, but I'm guessing you've tried seraching the logs using grep or awk to find the process your looking for?

---

### Post by QLee on 2010-11-08
ramujinius, 

Like Hippytaff, I'm not sure what your goal would be.

Your first snippet is a DNS request.
Your second snippet is a http request to a site from the same computer that requested DNS.

Are you worried that something is trying to "phone home"?

---

### Post by ramujinius on 2010-11-12
No. Sorry for not making my question clear. 

I enabled UFW. I blocked the some incoming request using few rules. 

I just wanted to know which process is trying to access the port, from reading UFW log. But i don't know which part of the log is process ID. i wanted to get the "process from system monitor" using process ID

I hope things are clearer now

---

### Post by uRock on 2010-11-12
Every time a program runs, it will have a different process ID.

---

### Post by ramujinius on 2010-11-16
I know that process ID changes each time when a process is invoked. I am just looking for ID at particular instant (comparing ufw log and process monitor )

---

### Post by Hippytaff on 2010-11-16
Typing
```

pidof

```
or
```

top

```
Might return what your looking for? :-)

---

### Post by ramujinius on 2010-11-18
:-(

I knew that

Basically a log of firewall should have the information of process which is blocked when accessing the port. But just wanted to know the process id from ufw log which is blocked by UFW. 

:-(

---

### Post by ramujinius on 2010-11-21
bump

---

