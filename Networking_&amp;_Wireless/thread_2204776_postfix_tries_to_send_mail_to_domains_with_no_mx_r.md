---
title: "postfix tries to send mail to domains with no mx record"
date: 2014-02-10
forum: Networking &amp; Wireless
---

### Post by Peter_Klaffehn on 2014-02-10
Hi,

today i noticed an unexpected behaviour. This mail is lingering in the outbound queue on my mailserver:

54086E032F  10413683 Fri Feb  7 14:04:21  [EMAIL="some.user@my.domain"]some.user@my.domain[/EMAIL]
(lost connection with apple.de[17.149.160.31] while receiving the initial server greeting)
                                         [EMAIL="presse@apple.de"]presse@apple.de[/EMAIL]

Searching the postfix log i found out that postfix tries to deliver this email with no effort:

Feb 10 13:20:08 mx-50 postfix/qmgr[17611]: 54086E032F: from=<[EMAIL="some.user@my.domain"]some.user@my.domain[/EMAIL]>, size=10413683, nrcpt=1 (queue active)
Feb 10 13:21:22 mx-50 postfix/smtp[17651]: 54086E032F: lost connection with apple.de[17.172.224.31] while receiving the initial server greeting
Feb 10 13:22:37 mx-50 postfix/smtp[17651]: 54086E032F: lost connection with apple.de[17.178.96.17] while receiving the initial server greeting
Feb 10 13:23:52 mx-50 postfix/smtp[17651]: 54086E032F: to=<[EMAIL="presse@apple.de"]presse@apple.de[/EMAIL]>, relay=apple.de[17.149.160.31]:25, delay=256771, delays=256547/0/225/0, dsn=4.4.2, status=deferred (lost connection with apple.de[17.149.160.31] while receiving the initial server greeting)
Feb 10 14:35:08 mx-50 postfix/qmgr[6779]: 54086E032F: from=<[EMAIL="some.user@my.domain"]some.user@my.domain[/EMAIL]>, size=10413683, nrcpt=1 (queue active)
Feb 10 14:36:22 mx-50 postfix/smtp[4114]: 54086E032F: lost connection with apple.de[17.178.96.17] while receiving the initial server greeting
Feb 10 14:37:37 mx-50 postfix/smtp[4114]: 54086E032F: lost connection with apple.de[17.172.224.31] while receiving the initial server greeting
Feb 10 14:38:52 mx-50 postfix/smtp[4114]: 54086E032F: to=<[EMAIL="presse@apple.de"]presse@apple.de[/EMAIL]>, relay=apple.de[17.149.160.31]:25, delay=261272, delays=261047/0/225/0, dsn=4.4.2, status=deferred (lost connection with apple.de[17.149.160.31] while receiving the initial server greeting)
          
Now the strange thing. There is no mx record for apple.de:

[EMAIL="root@mx-50"]root@mx-50[/EMAIL]:~# host -t mx apple.de
apple.de has no MX record

So how could postfix determine the mxer for this Domain? Apparently postfix uses the a records:

[EMAIL="root@mx-50"]root@mx-50[/EMAIL]:~# host -t a apple.de
apple.de has address 17.178.96.17
apple.de has address 17.149.160.31
apple.de has address 17.172.224.31

Why? these Feature is off by Default and not activated on my mailserver:

[EMAIL="root@mx-50"]root@mx-50[/EMAIL]:~# postconf -d | grep ignore_mx_lookup_error
ignore_mx_lookup_error = no

[EMAIL="root@mx-50"]root@mx-50[/EMAIL]:~# postconf -n | grep ignore_mx_lookup_error
[EMAIL="root@mx-50"]root@mx-50[/EMAIL]:~# [no Output]

How can i turn this off?

TIA, Peter

---

