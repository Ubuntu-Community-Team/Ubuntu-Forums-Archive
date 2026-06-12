---
title: "PPP connection problems"
date: 2015-03-27
forum: Networking &amp; Wireless
---

### Post by sridhar4 on 2015-03-27
Hello,

I am trying to use PPTP.  On the server side (centOS) I followed this guide [http://freehostinganswers.com/blog/how-to-install-your-own-vpn-server-in-5-mins-pptp-on-centos-redhat-and-ubuntu/](http://freehostinganswers.com/blog/how-to-install-your-own-vpn-server-in-5-mins-pptp-on-centos-redhat-and-ubuntu/)

On the client side (ubuntu), I am able to create a VPN connection using network-manager.  It connects successfully, but my internet connection is not there.  I cannot connect to yahoo.com or google.com or anything on the internet.

Here is my ifconfig output:
eth0      Link encap:Ethernet  HWaddr d8:9d:67:7c:3e:10  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:357055 (357.0 KB)  TX bytes:357055 (357.0 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.0.101  P-t-P:192.168.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1400  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:94 (94.0 B)  TX bytes:3884 (3.8 KB)

wlan0     Link encap:Ethernet  HWaddr 9c:2a:70:1c:33:f9  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9e2a:70ff:fe1c:33f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5020 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3285433 (3.2 MB)  TX bytes:767790 (767.7 KB)

Here is my route -n output:
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 ppp0
192.168.0.1     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
203.169.204.151 192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
203.169.204.151 192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0

I have spent several hours on this and have not found a solution.  Any help appreciated.  Also, if you require further info, please let me know.

Thanks in advance.

---

### Post by SeijiSensei on 2015-03-27
Can you connect if you use an IP address rather than the site's hostname?  Try [https://63.117.14.26/](https://63.117.14.26/) and see if google.com appears.  If so, you have a problem with name service.

---

### Post by sridhar4 on 2015-03-27
Thanks for the reply.  I tried the IP address and it couldnt get to google.

---

### Post by sridhar4 on 2015-03-27
Also, below is the log I get on the client side on successful connection to the VPN

Mar 28 05:21:57.901 pppd[12074]: Plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.

 Mar 28 05:21:58.122 pppd[12074]: pppd 2.4.5 started by root, uid 0

 Mar 28 05:21:58.122 pppd[12074]: Using interface ppp0

 Mar 28 05:21:58.122 pppd[12074]: Connect: ppp0 <--> /dev/pts/11

 Mar 28 05:21:58.874 pppd[12074]: CHAP authentication succeeded

 Mar 28 05:21:58.965 pppd[12074]: MPPE 128-bit stateless compression enabled

 Mar 28 05:21:59.163 pppd[12074]: local  IP address 192.168.0.101

 Mar 28 05:21:59.163 pppd[12074]: remote IP address 192.168.0.1

 Mar 28 05:21:59.163 pppd[12074]: primary   DNS address 8.8.8.8

 Mar 28 05:21:59.164 pppd[12074]: secondary DNS address 4.4.4.4

---

### Post by sridhar4 on 2015-03-28
Getting the following error messages in syslog:

Mar 28 23:19:22 sridhar-HP-1000-Notebook-PC NetworkManager[884]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Mar 28 23:19:25 sridhar-HP-1000-Notebook-PC ntpdate[6126]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Mar 28 23:19:25 sridhar-HP-1000-Notebook-PC ntpdate[6126]: no servers can be used, exiting
Mar 28 23:20:01 sridhar-HP-1000-Notebook-PC CRON[6153]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)

---

### Post by sridhar4 on 2015-03-29
Here is the Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
192.168.0.1     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
203.169.204.151 192.168.0.1     255.255.255.255 UGH   0      0        0 wlan0
203.169.204.151 192.168.0.1     255.255.255.255 UGH   0      0        0 wlan0

---

### Post by sridhar4 on 2015-03-31
SOLVED:

I am not sure exactly how it got solved.  But here is  what happened: I asked the VPS admin to turn on TUN/ TAP.  They did so,  but disabled the PPP.  Then I asked them to enable both.  When they did  so, my PPTP suddenly started working.  I almost fell off the chair when  google showed up (I live in China where the government blocks such bad  influences to protect me)  

For those who may be going down this  path: most instructions written on the web are for a dedicated server.   If you are on a VPS, you have to ask the admins to turn on stuff.  Its  quite possible they turned on some other things when they realized I was  trying to do a VPN.

Anyway, lots of frustration, learned a lot, finally got there - phew.

---

