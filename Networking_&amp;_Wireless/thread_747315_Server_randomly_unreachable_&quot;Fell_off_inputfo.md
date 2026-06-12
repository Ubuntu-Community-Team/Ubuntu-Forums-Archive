---
title: "Server randomly unreachable &quot;Fell off input/forward chain&quot;"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by chrilleh on 2008-04-06
I'm having some problems with a server which is unreachable at (seems to be) random times. At these  times it is not reachable through ping, ssh or anything else. It seems to be unreachable more oftan that it is reachable. The only strange thing i found in some logs is the following but I don´t know what would be the reason or if that even is the problem.

Despite these ingoing problems there seems to be no problem with outgoing traffic because my parents are using this server as router and the have confirmed that their internet is working OK.

As firewall-script I'm using "Ubuntu-firewall" ([http://rob.pectol.coma/content/view/2/1/](http://rob.pectol.coma/content/view/2/1/)) and It should at least not be a port related problem because the traffic (ping, ssh, openvpn etc) is working at some times.

Do you think the following syslog errors could be related to this problem? Any ideas on what could be causing that the server is reachable sometimes but mostly not?

Thanks.


In the syslog I have log messages of this kind:

[code]
Apr  6 19:10:38 servername kernel: [5261383.028442] Fell off input chain: IN=eth2 OUT= MAC= SRC=xxx.xxx.xxx.xxx DST=224.0.0.251 LEN=68 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=48
Apr  6 19:10:39 servername kernel: [5261384.027621] Fell off input chain: IN=eth2 OUT= MAC= SRC=xxx.xxx.xxx.xxx DST=224.0.0.251 LEN=68 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=48
Apr  6 19:10:41 servername kernel: [5261386.036033] Fell off input chain: IN=eth2 OUT= MAC= SRC=xxx.xxx.xxx.xxx DST=224.0.0.251 LEN=68 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=48
Apr  6 19:11:52 servername kernel: [5261456.780403] Fell off input chain: IN=eth2 OUT= MAC= SRC=xxx.xxx.xxx.xxx DST=224.0.0.251 LEN=68 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=48
Apr  6 19:11:53 servername kernel: [5261457.789581] Fell off input chain: IN=eth2 OUT= MAC= SRC=xxx.xxx.xxx.xxx DST=224.0.0.251 LEN=68 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=48

...


Apr  6 18:37:39 servername kernel: [5259405.026201] Fell off input chain: IN=eth2 OUT= MAC=00:50:8d:f7:d9:fa:00:0e:d6:e6:e4:00:08:00 SRC=201.70.12.211 DST=xxx.xxx.xxx.xxx LEN=40 TOS=0x00 PREC=0x00 TTL=89 ID=256 PROTO=TCP SPT=6000 DPT=1433 WINDOW=16384 RES=0x00 SYN URGP=0
Apr  6 18:39:01 servername /USR/SBIN/CRON[1053]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr  6 18:39:10 servername kernel: [5259496.627481] Fell off input chain: IN=eth2 OUT= MAC=00:50:8d:f7:d9:fa:00:0f:35:72:18:00:08:00 SRC=84.198.212.132 DST=xxx.xxx.xxx.xxx LEN=48 TOS=0x00 PREC=0x00 TTL=102 ID=28832 DF PROTO=TCP SPT=3102 DPT=2968 WINDOW=64240 RES=0x00 SYN URGP=0
Apr  6 18:39:13 servername kernel: [5259499.607325] Fell off input chain: IN=eth2 OUT= MAC=00:50:8d:f7:d9:fa:00:0f:35:72:18:00:08:00 SRC=84.198.212.132 DST=xxx.xxx.xxx.xxx LEN=48 TOS=0x00 PREC=0x00 TTL=102 ID=29434 DF PROTO=TCP SPT=3102 DPT=2968 WINDOW=64240 RES=0x00 SYN URGP=0
Apr  6 18:39:19 servername kernel: [5259505.646397] Fell off input chain: IN=eth2 OUT= MAC=00:50:8d:f7:d9:fa:00:0f:35:72:18:00:08:00 SRC=84.198.212.132 DST=xxx.xxx.xxx.xxx LEN=48 TOS=0x00 PREC=0x00 TTL=102 ID=30228 DF PROTO=TCP SPT=3102 DPT=2968 WINDOW=64240 RES=0x00 SYN URGP=0
Apr  6 18:46:07 servername kernel: [5259913.022982] Fell off input chain: IN=eth2 OUT= MAC=00:50:8d:f7:d9:fa:00:0f:35:72:18:00:08:00 SRC=84.109.35.223 DST=xxx.xxx.xxx.xxx LEN=48 TOS=0x00 PREC=0x00 TTL=101 ID=1390 DF PROTO=TCP SPT=4767 DPT=2967 WINDOW=65535 RES=0x00 SYN URGP=0
Apr  6 18:46:10 servername kernel: [5259916.096899] Fell off input chain: IN=eth2 OUT= MAC=00:50:8d:f7:d9:fa:00:0f:35:72:18:00:08:00 SRC=84.109.35.223 DST=xxx.xxx.xxx.xxx LEN=48 TOS=0x00 PREC=0x00 TTL=101 ID=1875 DF PROTO=TCP SPT=4767 DPT=2967 WINDOW=65535 RES=0x00 SYN URGP=0
 
...

Apr  6 14:03:13 servername kernel: [5242953.369384] Fell off forward chain: IN=eth0 OUT=eth2 SRC=192.168.0.50 DST=213.244.185.10 LEN=40 TOS=0x00 PREC=0x00 TTL=127 ID=12074 DF PROTO=TCP SPT=49401 DPT=80 WINDOW=0 RES=0x00 ACK RST URGP=0
Apr  6 14:03:13 servername kernel: [5242953.369409] Fell off forward chain: IN=eth0 OUT=eth2 SRC=192.168.0.50 DST=75.126.17.155 LEN=40 TOS=0x00 PREC=0x00 TTL=127 ID=12075 DF PROTO=TCP SPT=49409 DPT=80 WINDOW=0 RES=0x00 ACK RST URGP=0
Apr  6 14:03:13 servername kernel: [5242953.369435] Fell off forward chain: IN=eth0 OUT=eth2 SRC=192.168.0.50 DST=88.221.39.180 LEN=40 TOS=0x00 PREC=0x00 TTL=127 ID=12076 DF PROTO=TCP SPT=49415 DPT=80 WINDOW=0 RES=0x00 ACK RST URGP=0
Apr  6 14:03:17 servername kernel: [5242956.524509] Fell off forward chain: IN=eth0 OUT=eth2 SRC=192.168.0.50 DST=38.118.213.25 LEN=40 TOS=0x00 PREC=0x00 TTL=127 ID=12178 DF PROTO=TCP SPT=49421 DPT=80 WINDOW=0 RES=0x00 ACK RST URGP=0
Apr  6 14:03:19 servername kernel: [5242959.035828] Fell off forward chain: IN=eth0 OUT=eth2 SRC=192.168.0.50 DST=38.118.213.25 LEN=40 TOS=0x00 PREC=0x00 TTL=127 ID=12195 DF PROTO=TCP SPT=49418 DPT=80 WINDOW=0 RES=0x00 ACK RST URGP=0
Apr  6 14:03:22 servername kernel: [5242961.557899] Fell off forward chain: IN=eth0 OUT=eth2 SRC=192.168.0.50 DST=38.118.213.25 LEN=40 TOS=0x00 PREC=0x00 TTL=127 ID=12214 DF PROTO=TCP SPT=49423 DPT=80 WINDOW=0 RES=0x00 ACK RST URGP=0
Apr  6 14:03:58 servername kernel: [5242997.890800] Fell off input chain: IN=eth2 OUT= MAC=00:50:8d:f7:d9:fa:00:0e:d6:e6:e4:00:08:00 SRC=208.122.51.40 DST=xxx.xxx.xxx.xxx LEN=45 TOS=0x00 PREC=0x00 TTL=44 ID=17231 DF PROTO=TCP SPT=80 DPT=49396 WINDOW=32850 RES=0x00 ACK PSH FIN URGP=0
Apr  6 14:04:00 servername kernel: [5242999.704230] Fell off input chain: IN=eth2 OUT= MAC=00:50:8d:f7:d9:fa:00:0f:35:72:18:00:08:00 SRC=84.58.69.104 DST=xxx.xxx.xxx.xxx LEN=64 TOS=0x00 PREC=0x00 TTL=26 ID=32563 DF PROTO=TCP SPT=3988 DPT=2967 WINDOW=53760 RES=0x00 SYN URGP=0

---

