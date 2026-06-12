---
title: "Certain web addresses time out- It's BACK"
date: 2021-10-01
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2021-10-01
I had a similar problem some months ago. I was unable to reach my bank's website from our LAN. any connection would time out. I worked on it for months with the bank and posted about it here. Eventually the problem disappeared. 

It's back now. I cannot access our bank site from inside our LAN. (except of one specific computer running 18.04 32 bit Ubuntu). Now I have discovered some additional websites I cannot reach, all of them are state government sites in different states. I can access all of them when using a cell network or from another location. I would likely never have discovered this if I hadn't need to check the status of various licenses. We have 4 Linux computers 3 are running 20.04 LTS), 5 Windows 10 computers and one Windows Server. 

I can do an nslookup on the sites, I can ping some of them both by name and by ipaddress but a trace route may time out or not. I've contacted our ISP (ATT) and they haven't been able to offer any help.

The sites I know about are:

[LIST]
[*]login.hancockwhitney.com
[*][www.myfloridalicense.com](www.myfloridalicense.com)
[*]lsbae.com
[*]arc.ohio.gov
[*][www.tn.gov](www.tn.gov)
[/LIST]

```
>nslookup login.hancockwhitney.com
Server:  dsldevice6.attlocal.net
Address:  2600:1700:3e6::1

Non-authoritative answer:
Name:    pv65z9.hancock.gslb.f5silverline.com
Address:  107.162.184.159
Aliases:  login.hancockwhitney.com
```

```
>ping login.hancockwhitney.com

Pinging pv65z9.hancock.gslb.f5silverline.com [107.162.184.159] with 32 bytes of data:
Reply from 107.162.184.159: bytes=32 time=28ms TTL=244
Reply from 107.162.184.159: bytes=32 time=28ms TTL=244
Reply from 107.162.184.159: bytes=32 time=28ms TTL=244
Reply from 107.162.184.159: bytes=32 time=28ms TTL=244

Ping statistics for 107.162.184.159:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 28ms, Maximum = 28ms, Average = 28ms

```
```
>ping  107.162.184.159

Pinging 107.162.184.159 with 32 bytes of data:
Reply from 107.162.184.159: bytes=32 time=28ms TTL=244
Reply from 107.162.184.159: bytes=32 time=28ms TTL=244
Reply from 107.162.184.159: bytes=32 time=27ms TTL=244
Reply from 107.162.184.159: bytes=32 time=28ms TTL=244

Ping statistics for 107.162.184.159:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 27ms, Maximum = 28ms, Average = 27ms
```

```
>tracert login.hancockwhitney.com

Tracing route to pv65z9.hancock.gslb.f5silverline.com [107.162.184.159]
over a maximum of 30 hops:

  1    <1 ms    <1 ms    <1 ms  dsldevice.attlocal.net [192.168.1.254]
  2     1 ms     1 ms    <1 ms  107-143-24-1.lightspeed.nworla.sbcglobal.net [107.143.24.1]
  3     1 ms     1 ms     1 ms  99.55.25.28
  4    14 ms    14 ms    14 ms  12.123.239.206
  5    16 ms    14 ms    14 ms  12.122.28.29
  6    19 ms    14 ms    14 ms  attga402igs.ip.att.net [12.122.117.121]
  7    44 ms    14 ms    12 ms  192.205.36.158
  8    13 ms    12 ms    13 ms  ae-6.r23.atlnga05.us.bb.gin.ntt.net [129.250.5.59]
  9    28 ms    28 ms    38 ms  ae-4.r25.asbnva02.us.bb.gin.ntt.net [129.250.4.165]
 10    29 ms    28 ms    31 ms  ae-1.a04.asbnva02.us.bb.gin.ntt.net [129.250.2.125]
 11    29 ms    28 ms    28 ms  ae-1.f5-networks.asbnva02.us.bb.gin.ntt.net [128.241.219.154]
 12    28 ms    27 ms    27 ms  107.162.79.1
 13    28 ms    28 ms    28 ms  107.162.184.159

Trace complete.
```

```
>nslookup www.myfloridalicense.com
Server:  dsldevice6.attlocal.net
Address:  2600:1700:3e6::1

Non-authoritative answer:
Name:    www.myfloridalicense.com
Address:  199.250.17.14
```


```
>ping  www.myfloridalicense.com

Pinging www.myfloridalicense.com [199.250.17.14] with 32 bytes of data:
Request timed out.
Request timed out.
Request timed out.
Request timed out.

Ping statistics for 199.250.17.14:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),
```

```
>ping 199.250.17.14

Pinging 199.250.17.14 with 32 bytes of data:
Request timed out.
Request timed out.
Request timed out.
Request timed out.

Ping statistics for 199.250.17.14:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),
```

```
>tracert www.myfloridalicense.com

Tracing route to www.myfloridalicense.com [199.250.17.14]
over a maximum of 30 hops:

  1    <1 ms     5 ms    <1 ms  dsldevice.attlocal.net [192.168.1.254]
  2     2 ms     1 ms     3 ms  107-143-24-1.lightspeed.nworla.sbcglobal.net [107.143.24.1]
  3     1 ms     1 ms     1 ms  99.55.25.28
  4    17 ms    19 ms    58 ms  12.123.239.206
  5    14 ms    14 ms    19 ms  12.122.28.29
  6    24 ms    22 ms    21 ms  attga402igs.ip.att.net [12.122.117.121]
  7    15 ms    17 ms    15 ms  4.68.62.225
  8    30 ms    38 ms    26 ms  ae-0-11.bar2.Tampa1.Level3.net [4.69.137.110]
  9    37 ms    31 ms    31 ms  4.34.132.222
 10     *        *        *     Request timed out.
 11     *        *        *     Request timed out.
 12     *        *        *     Request timed out.
 13     *        *        *     Request timed out.
 14     *        *        *     Request timed out.
 15     *        *        *     Request timed out.
 16     *        *        *     Request timed out.
 17     *        *        *     Request timed out.
 18     *        *        *     Request timed out.
 19     *        *        *     Request timed out.
 20     *        *        *     Request timed out.
 21     *        *        *     Request timed out.
 22     *        *        *     Request timed out.
 23     *        *        *     Request timed out.
 24     *        *        *     Request timed out.
 25     *        *        *     Request timed out.
 26     *        *        *     Request timed out.
 27     *        *        *     Request timed out.
 28     *        *        *     Request timed out.
 29     *        *        *     Request timed out.
 30     *        *        *     Request timed out.

Trace complete.
```

Any suggestions welcomed.

---

### Post by morrownr on 2021-10-04
It was reported last week that the certs of many web sites expired on the last day of the quarter. You are likely seeing the result.

---

### Post by rsteinmetz70112 on 2021-10-04
Thanks, but I'm skeptical. The problem started before the end of the month and continues. If the certificates were expired I'd expect to see an error related to the invalid certificate. I'm getting a time out - ERR_CONNECTION_TIMED_OUT. I can also access all of these sites utilizing another ISP.

---

