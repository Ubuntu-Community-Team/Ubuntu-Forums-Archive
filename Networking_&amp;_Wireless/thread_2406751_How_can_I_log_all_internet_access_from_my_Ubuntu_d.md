---
title: "How can I log all internet access from my Ubuntu desktop?"
date: 2018-11-25
forum: Networking &amp; Wireless
---

### Post by anjaanaadmi on 2018-11-25
Hi,
I would like to register all websites or IP addresses which had been accessed by all users from my Ubuntu desktop (installed on my PC at home). How can I access this feature? Or enable it to access some sort of log file?
Do such log files already exist? 

Please advise, many thanks.
Anjaan

---

### Post by SeijiSensei on 2018-11-25
There is no simple method for this. You can force all web traffic through the Squid proxy where it will be logged. Browse the web for "transparent Squid proxy" for help. This is a pretty complex task, especially if you want to track HTTPS traffic as well.

You can also use iptables if there is a Linux box between the users and the Internet. A rule like
```
/sbin/iptables -A INPUT -p tcp --dport 80 -j LOG
```
on a Linux router would log outbound HTTP requests.

If your just tracking usage on a single machine, adding the rules

```
/sbin/iptables -A OUTPUT -p tcp --dport 80 -j LOG
/sbin/iptables -A OUTPUT -p tcp --dport 443 -j LOG
```

might be sufficient.

You need to be comfortable with the command prompt for both of these and have a basic grasp of Internet protocols.

---

### Post by anjaanaadmi on 2018-11-26
Thanks for this.
I'm pretty comfortable with shell commands. 

Just curious, do I need to supply the location of the log file? Where would this get logged?

---

### Post by SeijiSensei on 2018-11-26
By default, Squid usually writes its own logs in /var/log/squid.  Traffic logged by iptables uses the kernel facility and probably appears in /var/log/kern.log.  (I don't use Squid on Ubuntu, but on RedHat/CentOS it appears in /var/log/kernel.)

Squid's entries are very detailed like this:

```
1543247786.387     58 10.10.10.10 TCP_CLIENT_REFRESH_MISS/200 42904 GET http://acroipm.adobe.com/10/rdr/ENU/win/nooem/none/message.zip - DIRECT/72.247.9.72 application/zip
```

There's a timestamp, duration of the request in milliseconds, the originating IP, the HTTP response received, the length of the object, the URL requested and method, the destination IP, and the file's mimetype.

---

### Post by anjaanaadmi on 2018-11-27
Because I'm tracking the internet access on a single Ubuntu machine (my desktop at home), I wanted to know where the logs would be stored for these commands you provided. I would prefer these commands to using SQUID.
[FONT=courier new][/FONT][SIZE=4][/SIZE][SIZE=3][FONT=courier new][B]/sbin/iptables -A OUTPUT -p tcp --dport 80 -j LOG
/sbin/iptables -A OUTPUT -p tcp --dport 443 -j LOG[/B]
[/FONT][/SIZE]
Thanks
Anjaan

---

### Post by SeijiSensei on 2018-11-27
As I said, they should be in /var/log/kern.log.  A typical entry looks like this:

```
Nov 27 00:08:08 rocky kernel: SSL_ALLOW_IN=eth1 OUT=eth0 SRC=10.10.10.10 DST=52.109.12.74 LEN=40 TOS=0x00 PREC=0x00 TT
L=126 ID=24263 DF PROTO=TCP SPT=63945 DPT=443 WINDOW=254 RES=0x00 ACK URGP=0 
```

This is an SSL request to 52.109.12.74.  The "SSL_ALLOW_IN" is a custom log prefix so we can easily distinguish among types of requests.  We have a number of different rules that permit or deny requests from various clients, and each is logged with a separate prefix.  You can add one with the "--log-prefix" parameter to iptables.  See [man iptables]("https://linux.die.net/man/8/iptables") for details.

---

### Post by anjaanaadmi on 2018-11-28
Got it!

Thanks!

---

