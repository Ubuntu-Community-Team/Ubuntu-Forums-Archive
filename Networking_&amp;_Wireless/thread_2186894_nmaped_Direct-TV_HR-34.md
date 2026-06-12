---
title: "nmaped Direct-TV HR-34"
date: 2013-11-09
forum: Networking &amp; Wireless
---

### Post by craig-lafon on 2013-11-09
I was bored and ran nmap to my directtv box and wanted to share this information. Was somewhat surprised that it reported Linux Centos.
Its ironic that DirectTV doesnt support linux for the webshare streaming service...

Starting Nmap 6.00 ( [http://nmap.org](http://nmap.org) ) at 2013-11-09 14:11 CST
NSE: Loaded 93 scripts for scanning.
NSE: Script Pre-scanning.
Initiating ARP Ping Scan at 14:11
Scanning 192.168.10.106 [1 port]
Completed ARP Ping Scan at 14:11, 0.01s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 14:11
Completed Parallel DNS resolution of 1 host. at 14:11, 11.08s elapsed
Initiating SYN Stealth Scan at 14:11
Scanning 192.168.10.106 [1000 ports]
Discovered open port 8080/tcp on 192.168.10.106
Discovered open port 10010/tcp on 192.168.10.106
Discovered open port 9001/tcp on 192.168.10.106
Discovered open port 49152/tcp on 192.168.10.106
Discovered open port 9000/tcp on 192.168.10.106
Completed SYN Stealth Scan at 14:11, 4.26s elapsed (1000 total ports)
Initiating Service scan at 14:11
Scanning 5 services on 192.168.10.106
Completed Service scan at 14:12, 100.83s elapsed (5 services on 1 host)
Initiating OS detection (try #1) against 192.168.10.106
NSE: Script scanning 192.168.10.106.
Initiating NSE at 14:13
Completed NSE at 14:13, 30.01s elapsed
Nmap scan report for 192.168.10.106
Host is up (0.0046s latency).
Not shown: 988 filtered ports
PORT STATE SERVICE VERSION
6000/tcp closed X11
6001/tcp closed X11:1
6002/tcp closed X11:2
6003/tcp closed X11:3
6004/tcp closed X11:4
8080/tcp open http-proxy?
|_http-methods: No Allow or Public header in OPTIONS response (status code 405)
9000/tcp open http Web-Based Enterprise Management CIM serverOpenPegasus WBEM httpd
|_http-methods: No Allow or Public header in OPTIONS response (status code 501)
|_http-title: Site doesn't have a title (text/plain).
9001/tcp open tor-orport?
10000/tcp closed snet-sensor-mgmt
10010/tcp open rxapi?
49152/tcp open http Web-Based Enterprise Management CIM serverOpenPegasus WBEM httpd
|_http-methods: No Allow or Public header in OPTIONS response (status code 501)
49153/tcp closed unknown
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at [http://www.insecure.org/cgi-bin/servicefp-submit.cgi](http://www.insecure.org/cgi-bin/servicefp-submit.cgi) :
SF-Port8080-TCP:V=6.00%I=7%D=11/9%Time=527E96EC%P=i686-pc-linux-gnu%r(GetR
SF:equest,EF,"HTTP/1\.1\x20403\x20Forbidden\.\r\nContent-Type:\x20applicat
SF:ion/json;\x20charset=UTF-8\r\nDate:\x20Sat,\x209\x20Nov\x202013\x2020:1
SF:1:27\x20GMT\r\nConnection:\x20close\r\nContent-Length:\x2090\r\n\r\n{\"
SF:status\":\x20{\n\x20\x20\"code\":\x20403,\n\x20\x20\"commandResult\":\x
SF:201,\n\x20\x20\"msg\":\x20\"Forbidden\.\",\n\x20\x20\"query\":\x20\"/\"
SF:\n}}")%r(HTTPOptions,163,"HTTP/1\.1\x20405\x20Method\x20Not\x20Allowed\
SF:.\r\nContent-Type:\x20application/json;\x20charset=UTF-8\r\nDate:\x20Sa
SF:t,\x209\x20Nov\x202013\x2020:11:27\x20GMT\r\nConnection:\x20close\r\nCo
SF:ntent-Length:\x20142\r\nReason:\x20Only\x20HTTP\x20GET\x20or\x20POST\x2
SF:0methods\x20are\x20supported\.\r\n\r\n{\"status\":\x20{\n\x20\x20\"code
SF:\":\x20405,\n\x20\x20\"commandResult\":\x201,\n\x20\x20\"msg\":\x20\"Me
SF:thod\x20Not\x20Allowed\.Only\x20HTTP\x20GET\x20or\x20POST\x20methods\x2
SF:0are\x20supported\.\",\n\x20\x20\"query\":\x20\"\"\n}}")%r(RTSPRequest,
SF:163,"HTTP/1\.1\x20405\x20Method\x20Not\x20Allowed\.\r\nContent-Type:\x2
SF:0application/json;\x20charset=UTF-8\r\nDate:\x20Sat,\x209\x20Nov\x20201
SF:3\x2020:11:28\x20GMT\r\nConnection:\x20close\r\nContent-Length:\x20142\
SF:r\nReason:\x20Only\x20HTTP\x20GET\x20or\x20POST\x20methods\x20are\x20su
SF:pported\.\r\n\r\n{\"status\":\x20{\n\x20\x20\"code\":\x20405,\n\x20\x20
SF:\"commandResult\":\x201,\n\x20\x20\"msg\":\x20\"Method\x20Not\x20Allowe
SF:d\.Only\x20HTTP\x20GET\x20or\x20POST\x20methods\x20are\x20supported\.\"
SF:,\n\x20\x20\"query\":\x20\"\"\n}}")%r(FourOhFourRequest,13B,"HTTP/1\.1\
SF:x20404\x20Not\x20Found\.\r\nContent-Type:\x20application/json;\x20chars
SF:et=UTF-8\r\nDate:\x20Sat,\x209\x20Nov\x202013\x2020:11:28\x20GMT\r\nCon
SF:nection:\x20close\r\nContent-Length:\x20136\r\nReason:\x20Resource\x20n
SF:ot\x20found\.\r\n\r\n{\"status\":\x20{\n\x20\x20\"code\":\x20404,\n\x20
SF:\x20\"commandResult\":\x201,\n\x20\x20\"msg\":\x20\"Not\x20Found\.Resou
SF:rce\x20not\x20found\.\",\n\x20\x20\"query\":\x20\"/nice\x20ports,/Trini
SF:ty\.txt\.bak\"\n}}")%r(Socks5,163,"HTTP/1\.1\x20405\x20Method\x20Not\x2
SF:0Allowed\.\r\nContent-Type:\x20application/json;\x20charset=UTF-8\r\nDa
SF:te:\x20Sat,\x209\x20Nov\x202013\x2020:11:28\x20GMT\r\nConnection:\x20cl
SF:ose\r\nContent-Length:\x20142\r\nReason:\x20Only\x20HTTP\x20GET\x20or\x
SF:20POST\x20methods\x20are\x20supported\.\r\n\r\n{\"status\":\x20{\n\x20\
SF:x20\"code\":\x20405,\n\x20\x20\"commandResult\":\x201,\n\x20\x20\"msg\"
SF::\x20\"Method\x20Not\x20Allowed\.Only\x20HTTP\x20GET\x20or\x20POST\x20m
SF:ethods\x20are\x20supported\.\",\n\x20\x20\"query\":\x20\"\"\n}}");
MAC Address: 16:D4:FE:3F:15:7A (Pace plc)
Device type: general purpose
Running: Linux 2.6.X
OS CPE: cpe:/o:linux:kernel:2.6.18
OS details: Linux 2.6.18 (Centos 5.3), Linux 2.6.9 - 2.6.30
Uptime guess: 16.854 days (since Wed Oct 23 18:43:36 2013)
Network Distance: 1 hop
TCP Sequence Prediction: Difficulty=203 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:kernel

---

