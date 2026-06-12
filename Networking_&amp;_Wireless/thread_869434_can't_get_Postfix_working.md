---
title: "can't get Postfix working"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by grandsatrap on 2008-07-24
I am trying to install Postfix. All I need is to be able to send email out from my Ubuntu computer. My computer is behind a router and an ADSL modem. My Windows computers have no trouble sending an receiving email.

I tried following 
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix) but it has all sorts of SASL and TLS stuff that I don't know what it is and surely don't need.

I am now trying to follow [http://flurdy.com/docs/postfix/index.html#config-simple-mta](http://flurdy.com/docs/postfix/index.html#config-simple-mta)

Here is what I have:
1. ps -ef | grep postfix
root     13052     1  0 Jul06 ?        00:00:00 /usr/lib/postfix/master
postfix  23626 13052  0 20:17 ?        00:00:00 pickup -l -t fifo -u -c
postfix  23627 13052  0 20:17 ?        00:00:00 qmgr -l -t fifo -u
satrap    23709 23535  0 20:26 pts/0    00:00:00 grep postfix

2. telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.

** NOTE: Postfix seems to be running from PS -EF, but nothing shows up when I do the TELNET LOCALHOST 25.

Please help.

---

### Post by BigbobOz on 2008-08-04
Not sure I've got the same problem but I don't seem to get any further either.

my mail.log reports
warning: SASL: Connect to private/auth-client failed: Permission Denied
fatal: no SASL authentication mechanisms

before that I postfix complain I didn't have an auth-client folder, so created one and now it complains it doesn't have permission to access it.

What does your log say? (var/log/mail.log)

Thanks

Rob

---

### Post by grandsatrap on 2008-08-04
Have a look at [http://ubuntuforums.org/showthread.php?t=873741](http://ubuntuforums.org/showthread.php?t=873741)

I put a copy of my mail.cf file there and part of my var/log/mail

It should help you out. Especially my notes about how I set up the mail.cf file. It only send email out (and can't do it to the domain that I am in). Maybe one day I'll fix that, but for now it is doing what I need it to.

(Feel free to ask for more detail -- but I am goign away for 2 weeks)

---

