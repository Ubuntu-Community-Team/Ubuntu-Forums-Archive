---
title: "aptitude resolving names to 1.0.0.0"
date: 2006-08-18
forum: Networking &amp; Wireless
---

### Post by thumper on 2006-08-18
](*,) Very frustrating problem.

Fairly simple dapper install on Sony Vaio SZ2XP.  

/etc/apt/sources.list
```

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```
Aptitude then fails to update as such:
```
root@slacko:/etc/apt# aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]
```
Sometimes ping resolves the ip address, sometimes it doesn't... If both resolve, then running aptitude works (for a brief while).
```
root@slacko:/etc/apt# ping archive.ubuntu.com
PING archive.ubuntu.com (82.211.81.182) 56(84) bytes of data.
64 bytes from archive.ubuntu.com (82.211.81.182): icmp_seq=1 ttl=47 time=12.6 ms
64 bytes from archive.ubuntu.com (82.211.81.182): icmp_seq=2 ttl=47 time=11.5 ms

--- archive.ubuntu.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1003ms
rtt min/avg/max/mdev = 11.565/12.094/12.624/0.540 ms
root@slacko:/etc/apt# ping security.ubuntu.com
PING security.ubuntu.com (1.0.0.0) 56(84) bytes of data.

--- security.ubuntu.com ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 5014ms

root@slacko:/etc/apt# ping security.ubuntu.com
```
The following things have been done to remove ipv6:
```
tim@slacko:/etc/modprobe.d$ grep ipv6 blacklist
# ipv6 isn't understood by the work router
blacklist ipv6
tim@slacko:/etc/modprobe.d$ grep off aliases
alias net-pf-10 off
alias ipv6 off
```
also, /etc/apt/apt.conf is empty.

After writing all this out I did the following:
```
root@slacko:/etc/apt# ping security.ubuntu.com
PING security.ubuntu.com (195.248.90.23) 56(84) bytes of data.
64 bytes from security.ubuntu.com (195.248.90.23): icmp_seq=1 ttl=48 time=12.5 ms
64 bytes from security.ubuntu.com (195.248.90.23): icmp_seq=2 ttl=48 time=10.7 ms
64 bytes from security.ubuntu.com (195.248.90.23): icmp_seq=3 ttl=48 time=10.3 ms

--- security.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2010ms
rtt min/avg/max/mdev = 10.301/11.194/12.529/0.961 ms
root@slacko:/etc/apt# ping archive.ubuntu.com
PING archive.ubuntu.com (82.211.81.182) 56(84) bytes of data.
64 bytes from archive.ubuntu.com (82.211.81.182): icmp_seq=1 ttl=47 time=11.4 ms

--- archive.ubuntu.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 11.420/11.420/11.420/0.000 ms
root@slacko:/etc/apt# aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://security.ubuntu.com dapper-security Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security Release
Get:3 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:4 http://archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://archive.ubuntu.com dapper Release
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Sources
Hit http://archive.ubuntu.com dapper-updates/main Packages
Get:5 http://archive.ubuntu.com dapper-updates/restricted Packages [14B]
Hit http://archive.ubuntu.com dapper-updates/main Sources
Get:6 http://archive.ubuntu.com dapper-updates/restricted Sources [14B]
Get:7 http://archive.ubuntu.com dapper-backports/main Packages [14B]
Get:8 http://archive.ubuntu.com dapper-backports/restricted Packages [14B]
Get:9 http://archive.ubuntu.com dapper-backports/universe Packages [14B]
Get:10 http://archive.ubuntu.com dapper-backports/multiverse Packages [14B]
Get:11 http://archive.ubuntu.com dapper-backports/main Sources [14B]
Get:12 http://archive.ubuntu.com dapper-backports/restricted Sources [14B]
Get:13 http://archive.ubuntu.com dapper-backports/universe Sources [14B]
Get:14 http://archive.ubuntu.com dapper-backports/multiverse Sources [14B]
Fetched 896B in 1s (894B/s)
Reading package lists... Done
root@slacko:/etc/apt#
```
If I don't do the pings, then aptitude still resolves to 1.0.0.0.

Help.

---

### Post by bakert on 2007-10-19
This might help:

[http://ubuntuforums.org/archive/index.php/t-367353.html](http://ubuntuforums.org/archive/index.php/t-367353.html)

---

