---
title: "UFW rules and IPV6"
date: 2024-11-27
forum: Networking &amp; Wireless
---

### Post by georgesgiralt on 2024-11-27
Hi Guys,
Disclaimer : I'm too old to have learned IPV6 but was proficient at IPV4. 
I would like to set up an IPV6 UFW rule to allow ssh only from machines on my local network. All of them run Ubuntu 24.04.1 LTS fully updated.
I've put this rule in effect on my server where I want to log: 
      ```
 ufw allow from fe80::/64  to any port 22 proto tcp
```
But it is not working  because when I try to connect to my machine from another one in my local network :  
```
$ : ssh user@2a01:xxx:xxx:xxxx:xxx:xxx:xxxx:xx
The response is : 
sh: connect to host 2a01:xxx.............  port 22: Connection timed out
```
The server machine log has the entry : 
```
[UFW BLOCK] IN=wlan OUT= MAC=xxxxxxxxxx SRC=<client IPV6 addr> DST=<SRV IPV6 addr> LEN=80 TC=16 HOPLIMIT=64 FLOWLBL=608458 PROTO=TCP SPT=49960 DPT=22 WINDOW=64800 RES=0x00 SYN URGP=0
```
So, obviously, my ufw rule is not working...
I would be delighted to get all help you can give to me ! 
Thanks a lot in advance !

---

