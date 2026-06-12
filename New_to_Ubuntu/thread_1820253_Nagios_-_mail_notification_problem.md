---
title: "Nagios - mail notification problem"
date: 2011-08-07
forum: New to Ubuntu
---

### Post by Jonakoudijs on 2011-08-07
I have a problem with my Nagios setup and I hope someone could help me. The system is up and running and works like a charm, besides the mail notification.

It are all new systems. so the nagios server is just new and only monitoring itself and a other webserver in the same network. I installed Postfix and tested from telnet 25 and I could send mail without a problem to my hotmail-account.

I got 2 problems with the mail:
 1. It doesn't send mail from Nagios.
 2. It says in the Current Users Service State (critical) on the local host that it has send a notification: [I]Last Notification:08-07-2011 18:08:33 (notification 2)
[/I] The weird thing is, that when I look at the Current Users Service State from the webserver on the Notifications page it says the following: *(Return code of 127 is out of bounds - plugin may be missing)*

I am using:

[LIST]
[*]Ubuntu Server 10.04
[*]Nagios v3.2.3
[*]Nagios Plugins v1.4.11
[*]Nagios NRPE v.2.12  (*same version on the Nagios Server as the Webserver*)
[/LIST]

---

### Post by Jonakoudijs on 2011-08-29
I reïnstalled everything. It works again now..

---

