---
title: "Ubuntu is messing up my FTP connection"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by fatsheep on 2007-07-26
I tried connecting to my FTP on [www.gfboards.net](www.gfboards.net) through FileZilla and gFTP but they kept on timing out and disconnecting after only a few minutes of connection.  I do not use a firewall by the way.  Here is the result of my traceroute on Ubuntu:

```
fatsheep:~$  traceroute www.gfboards.net
traceroute to gfboards.net (208.109.181.15 ), 30 hops max, 52 byte packets
 1  192.168.0.1 (192.168.0.1)  0.167 ms  0.158 ms  0.122 ms
 2  74-133-184-1.dhcp.insightbb.com (74.133.184.1)  7.870 ms  8.136 ms  6.990 ms
 3  74-128-19-201.dhcp.insightbb.com (74.128.19.201 )  7.854 ms  7.087 ms  7.002 ms
 4  74.128.8.233 (74.128.8.233)  9.053 ms  7.367 ms  7.498 ms
 5  sl-gw25-atl-10-0.sprintlink.net (144.232.212.249)  36.697 ms  37.871 ms  35.297 ms
 6  sl-bb23-atl-6-0.sprintlink.net ( 144.232.22.9)  43.617 ms  40.009 ms  41.431 ms
 7  144.232.9.86 (144.232.9.86)  35.628 ms  34.595 ms  35.629 ms
 8  atl-core-02.inet.qwest.net (205.171.21.170)  42.426 ms  35.870 ms  38.246 ms
 9  * * *
10  phv-edge-03.inet.qwest.net ( 205.171.12.110)  74.928 ms  76.028 ms  74.228 ms
11  206.80.195.186 (206.80.195.186)  74.075 ms  75.324 ms  74.233 ms
12  ip-208-109-112-142.ip.secureserver.net (208.109.112.142)  76.384 ms  75.757 ms  74.778 ms
13  ip-216-69-188-33.ip.secureserver.net (216.69.188.33)  74.901 ms  76.884 ms  77.713 ms
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *
```

I'm not very familiar with this type of stuff but Godaddy customer support told me that it was either a router or an ISP problem and that the connection times out right after it leaves my local computer.  My ISP told me it times out right after it leaves their servers.  So I tried bypassing the router and connecting directly but that didn't work as I didn't get any internet at all.  

So then I reconnected the router and went on **Windows** and the FTP works fine!  Here is the output of tracert on XP:

```


Tracing route to gfboards.net [208.109.181.15]
over a maximum of 30 hops:
C:\Documents and Settings\Fatsheep>tracert www.gfboards.net
  1    <1 ms    <1 ms    <1 ms  192.168.0.1
  2     8 ms    11 ms    12 ms  74-133-184-1.dhcp.insightbb.com [74.133.184.1]
  3     8 ms     9 ms     9 ms  74-128-19-201.dhcp.insightbb.com [74.128.19.201]

  4    21 ms     9 ms     9 ms  74.128.8.233
  5    40 ms    40 ms    41 ms  sl-gw25-atl-10-0.sprintlink.net [144.232.212.249
]
  6    40 ms    42 ms    40 ms  sl-bb23-atl-6-0.sprintlink.net [144.232.22.9]
  7    36 ms    42 ms    37 ms  144.232.9.86
  8    34 ms    35 ms    40 ms  atl-core-02.inet.qwest.net [205.171.21.170]
  9     *        *        *     Request timed out.
 10    78 ms    78 ms    76 ms  phv-edge-03.inet.qwest.net [205.171.12.102]
 11    75 ms    76 ms    79 ms  206.80.195.186
 12    77 ms    76 ms    75 ms  ip-208-109-112-142.ip.secureserver.net [208.109.
112.142]
 13    79 ms    79 ms    79 ms  ip-216-69-188-33.ip.secureserver.net [216.69.188
.33]
 14    77 ms    76 ms    76 ms  www.gfboards.net [208.109.181.15]
 15    76 ms    76 ms    77 ms  www.gfboards.net [208.109.181.15]

Trace complete.

```

Now I want to know what Ubuntu is doing (or not doing) that is messing up the FTP connection.  I love Ubuntu but until I get this resolved I will have to log onto Windows to work on my website.  

Any advice would be greatly appreciated.

---

### Post by apjone on 2007-07-26
not sure bout filezilla but gftp dis-connects after 3 mins of inactivity.

---

### Post by fatsheep on 2007-07-27
> **apjone said:**
> not sure bout filezilla but gftp dis-connects after 3 mins of inactivity.

Well it's not just that.  It's messing up my uploads.  When I connect with FileZilla it appears to work fine but when I upload it won't be able to connect to the server and the files won't get uploaded even though FileZilla says they do.  I tried connecting directly to the modem and Ubuntu still has this problem while Windows does not.  I can show more traceroute and tracert output if that would be helpful.

---

