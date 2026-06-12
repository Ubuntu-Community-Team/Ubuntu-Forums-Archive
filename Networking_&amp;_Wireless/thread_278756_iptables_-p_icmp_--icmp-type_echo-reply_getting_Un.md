---
title: "iptables -p icmp --icmp-type echo-reply getting Unknown arg type  error"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by allbut666 on 2006-10-16
uname provides:

  Linux tpt40 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux


The command
 iptables -A INPUT -p icmp ! --icmp-type echo-reply -j DROP
generates the following error message
 iptables v1.3.5: Unknown arg `--icmp-type'
 Try `iptables -h' or 'iptables --help' for more information.

This command works on an earlier version of iptables running under Dapper
with iptables v1.3.3.

Anybody know what gives?

---

### Post by jbogarin on 2006-10-18
Hi,

I'm getting exactly that error in a different environment.
Linux 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux
I'm running edgy.

iptables -A INPUT --proto icmp --icmp-type echo-reply -j ACCEPT
iptables v1.3.5: Unknown arg `--icmp-type'
Try `iptables -h' or 'iptables --help' for more information.


I reinstalled iptables and nothing happened.
Is that a bug o a problem with libipt_icmp.so?
Thanks
Jose B

---

### Post by allbut666 on 2006-10-19
It is mentioned in the bug database bug #66106

Status is Confirmed - Importance is Undecided...

---

### Post by jbogarin on 2006-10-20
thanks for your response.

Jose B

---

### Post by compudaze on 2006-10-21
I'm having this problem too..

I switched from debian to ubuntu and now my shorewall configurations don't work because of this.

---

