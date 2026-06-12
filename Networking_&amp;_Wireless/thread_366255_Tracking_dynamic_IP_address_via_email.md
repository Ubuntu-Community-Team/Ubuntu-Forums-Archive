---
title: "Tracking dynamic IP address via email"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by jhhoward on 2007-02-20
I have a server box running Ubuntu Edgy Eft 6.10 connected to the internet behind a router. The router has port forwarding to allow for external connection to access the computer via SSH. This all works perfectly, as long as I have the WAN IP address of the computer. However, as I am on a cable connection I have a dynamic IP address that changed periodically. 

I would like to set up a script or write a daemon program to send an email to my account every time the WAN IP address changes. I am an experienced C/C++ programmer with some bash scripting experience so I believe this to be a fairly trivial task to undertake. My questions are as follows:
a) Is there a program/script that already does this job?
b) How do I access my WAN IP address? I can only seem to access the LAN address issued by the router.
c) Is there a linux command line tool which can be used to send an email?

Thanks in advance for replies
James

---

### Post by gborzi on 2007-02-20
Hello,
I'm not sure I understood completely your problem, but it looks like the one I had: an ubuntu box behind a NAT, that takes its internal IP address through DHCP, so that it may change after a reboot. I solved this problem with this script that sends me an email with the internal IP address: ```
#!/bin/sh

SERVER=<your smtp server here>
TOMAIL=<email address that will receive the message>

SERVEROK=`nslookup $SERVER|grep 'Address'|sed 1d|cut -f1 -d:`
ADDR=`ifconfig eth0|grep "inet addr"`

if [ $SERVEROK ]; then
   {
      echo HELO <something>
      echo MAIL FROM:<sender address>
      echo RCPT TO: $TOMAIL
      echo DATA
      echo Subject: amd64
      echo $ADDR
      echo .
      echo quit
   } | telnet $SERVER 25
  exit 0
else
  exit 1
fi

```
Note that this script won't work if your mail server doesn't allow telnet connections. The above script is executed some minutes after boot, through the following line in /etc/rc.local ```
echo /usr/local/sbin/addrmsg.sh|/usr/bin/at now + 5 minute
```
I think you can use the script, executing it from the program that changes your WAN connection.
As for your questions:
a) I don't know.
b) I don't understand this question. Aren't you able to do an ssh tunnel ?
c) mailx, it's in the repositories.

---

