---
title: "Help Troubleshooting Network Problem with 64-bit Hardy"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by jacoulter on 2008-09-16
Hi,

I installed Hardy 8.0.4 64-bit on a new box with an ASUS M2A-VM motherboard, AMD 64 Phenom CPU, and a built-in Realtek RTL8111/8168B NIC.  I am dual-booting with pre-installed Windows Vista 64-bit Basic Home Edition, which is working without any problems.

This machine is on a home LAN hard-wired into a Belkin N1 router which is connected to an Arris TM502G cable modem.  ISP is Cox Gulf Coast.

I have limited/restricted connectivity with the Internet.  I am able to connect to some sites, like [www.google.com](www.google.com), but I cannot connect to others such as this site, [www.ubuntuforums.org](www.ubuntuforums.org) with Firefox.  I am also unable to run apt-get update about 95% of the time.  Sometimes I am able to install/update with Synaptic Package Manager, sometimes it complains it cannot connect to [http://security.ubuntu.com](http://security.ubuntu.com).

I have an older machine running Hardy 8.0.4 32-bit and it rarely experiences these problems.  When it does I reset the Belkin router and the I get full connectivity again.

I researched this problem and found the following links relating to problems with the Realtek NIC and its pre-loaded r8169 driver:

[http://ph.ubuntuforums.com/showthread.php?t=799662]("http://ph.ubuntuforums.com/showthread.php?t=799662")

[http://www.jamesonwilliams.com/hardy-r8168.html]("http://www.jamesonwilliams.com/hardy-r8168.html")

[http://ubuntuforums.org/showthread.php?t=755002]("http://ubuntuforums.org/showthread.php?t=755002")

I followed the instructions updating the /etc/sysctl.conf file and compiling and loading the r8168 driver, but my network problems remain.

Following is some information on my system and it's behavior:

output of uname -a:

```
jacoulter@ubuntu64:~$ uname -a
Linux ubuntu64 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux
```

lspci for my NIC:

```
jacoulter@ubuntu64:~$ lspci | grep Real
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
```

lsmod for the Realtek driver:
```

jacoulter@ubuntu64:~$ lsmod | grep r8
r8168                  40720  0 
```

This is what a apt-get update looks like:
```

jacoulter@ubuntu64:~$ sudo apt-get update
Err http://security.ubuntu.com hardy-security Release.gpg                      
  Could not connect to security.ubuntu.com:80 (91.189.88.4), connection timed out
Err http://security.ubuntu.com hardy-security/main Translation-en_US           
  Unable to connect to security.ubuntu.com http:

<SNIP>

  Unable to connect to us.archive.ubuntu.com http: [IP: 91.167.0.4 80]
Reading package lists... Done                        
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Unable to connect to us.archive.ubuntu.com http: [IP: 91.167.0.4 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com http: [IP: 91.167.0.4 80]

<SNIP>

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
```

I can ping google:

```
jacoulter@ubuntu64:~$ ping www.google.com
PING www.l.google.com (64.233.169.103) 56(84) bytes of data.
64 bytes from yo-in-f103.google.com (64.233.169.103): icmp_seq=1 ttl=247 time=40.2 ms
64 bytes from yo-in-f103.google.com (64.233.169.103): icmp_seq=2 ttl=247 time=40.3 ms
64 bytes from yo-in-f103.google.com (64.233.169.103): icmp_seq=3 ttl=247 time=40.6 ms
64 bytes from yo-in-f103.google.com (64.233.169.103): icmp_seq=4 ttl=247 time=57.5 ms
64 bytes from yo-in-f103.google.com (64.233.169.103): icmp_seq=5 ttl=247 time=39.9 ms

--- www.l.google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4001ms
rtt min/avg/max/mdev = 39.944/43.761/57.584/6.915 ms
```

. . . but I can't ping us.archive.ubuntu.com:

```
jacoulter@ubuntu64:~$ ping us.archive.ubuntu.com
PING us.archive.ubuntu.com (91.167.0.4) 56(84) bytes of data.

--- us.archive.ubuntu.com ping statistics ---
64 packets transmitted, 0 received, 100% packet loss, time 63068ms
```

Hope somebody can help me troubleshoot and maybe fix this problem - really want to use Ubuntu instead of Vista, but right now Vista is working and Ubuntu isn't. . .

Thanks,

Jim

---

### Post by jacoulter on 2008-09-17
Bump

---

