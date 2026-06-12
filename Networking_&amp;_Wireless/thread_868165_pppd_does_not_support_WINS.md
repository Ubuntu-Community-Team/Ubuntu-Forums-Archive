---
title: "pppd does not support WINS"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by yusufk on 2008-07-23
Hi,

I use pppd to dial up using a Huawei E220 modem.

I get the following:

```
CONNECT
Connected.
If the following ppp negotiations fail,
try restarting the phone.

Serial connection established.
using channel 7
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
Warning - secret file /etc/ppp/pap-secrets has world and/or group access
sent [LCP ConfReq id=0x1 <asyncmap 0xa0000> <magic 0xd8e7deb9>]
rcvd [LCP ConfReq id=0xd <asyncmap 0x0> <auth chap MD5> <magic 0xcea68c> <pcomp> <accomp>]
sent [LCP ConfRej id=0xd <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0xa0000> <magic 0xd8e7deb9>]
rcvd [LCP ConfReq id=0xe <asyncmap 0x0> <auth chap MD5> <magic 0xcea68c>]
sent [LCP ConfAck id=0xe <asyncmap 0x0> <auth chap MD5> <magic 0xcea68c>]
rcvd [LCP DiscReq id=0xf magic=0xcea68c]
rcvd [CHAP Challenge id=0x1 <fea521fc044819053801c7be606521fb>, name = "UMTS_CHAP_SRVR"]
sent [CHAP Response id=0x1 <4f297caa17d64fd9ebf3c4432fee7ff0>, name = "myname"]
rcvd [CHAP Success id=0x1 ""]
CHAP authentication succeeded
CHAP authentication succeeded
sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfNak id=0x1 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
IPCP: timeout sending Config-Requests
sent [LCP TermReq id=0x2 "No network protocols running"]
sent [LCP TermReq id=0x3 "No network protocols running"]
Connection terminated.

Sending break to the modem

PDP context detached
Serial link disconnected.
Modem hangup

```

Looks like WINS messages are not being handled?

There is mention of a patch here: 

[http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg419204.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg419204.html)
and here:
[http://osdir.com/ml/linux.ppp/2007-11/msg00006.html](http://osdir.com/ml/linux.ppp/2007-11/msg00006.html)

---

### Post by PinkFloyd102489 on 2008-07-23
Install the "winbind" package and then add "wins" to /etc/nsswitch.conf.


```
sudo apt-get install winbind
```

Then open the /etc/nssswitch.conf file. Insert "wins" (no quotes) directly before "dns" on the hosts line. For example:

```
hosts:          files dns wins mdns
```

---

### Post by dmizer on 2008-07-23
> **PinkFloyd102489 said:**
> Install the "winbind" package and then add "wins" to /etc/nsswitch.conf.


```
sudo apt-get install winbind
```

Then open the /etc/nssswitch.conf file. Insert "wins" (no quotes) directly before "dns" on the hosts line. For example:

```
hosts:          files dns wins mdns
```
first of all, the file is /etc/nsswitch.conf (you have one too many 's' in the file name)

the order matters in /etc/nsswitch.conf

it should be:
```
hosts:          files [COLOR="Red"]wins dns[/COLOR] mdns
```
that way wins gets resolved before dns.

---

### Post by PinkFloyd102489 on 2008-07-23
Yeah I was thinking wins before dns, then I just copied it from my server, which is backwards. :-P

---

### Post by kaaino on 2008-10-02
I am experiencing the same problem with the modem E169G, however I have tested your solution with Network manager 0.7 but it does not work.

Do you have any other suggestion?

Thanks

---

### Post by yusufk on 2009-12-23
Try adding the DNS servers manually in Network manager. These may be specific to your operator or try public DNS servers like Googles: 8.8.8.8, 8.8.4.4

---

### Post by alexfish on 2009-12-23
> **kaaino said:**
> I am experiencing the same problem with the modem E169G, however I have tested your solution with Network manager 0.7 but it does not work.

Do you have any other suggestion?

Thanks

Hi

This Guide  Here  May Help

[COLOR=Navy]Ubuntu Linux On The Move[/COLOR]

[http://ubuntuforums.org/showthread.php?t=1331317&page=2](http://ubuntuforums.org/showthread.php?t=1331317&page=2)

---

