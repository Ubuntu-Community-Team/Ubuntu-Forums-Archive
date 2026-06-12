---
title: "ubuntu 10.10 having SNMP issues?"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by CurryNoodles on 2011-02-08
Dear all,

I search through the internet and there is alot of post that saying ubuntu 10.10 is having snmpwalk issues, with MiB couldn't accept or something.

I really need to know SNMP is working on Ubuntu 10.10? else i will avoid from using this version.

Well... Anyone had successfully tried snmp on ubuntu 10.10 (or any desktop environment). please advise...

Million thanks in advance.:popcorn:

---

### Post by Arndt on 2011-02-09
> **CurryNoodles said:**
> Dear all,

I search through the internet and there is alot of post that saying ubuntu 10.10 is having snmpwalk issues, with MiB couldn't accept or something.

I really need to know SNMP is working on Ubuntu 10.10? else i will avoid from using this version.

Well... Anyone had successfully tried snmp on ubuntu 10.10 (or any desktop environment). please advise...

Million thanks in advance.:popcorn:

I didn't find a lot, but I found this, which seems to present both a problem and its solution. Is it what you mean?

[http://www.mail-archive.com/net-snmp-users@lists.sourceforge.net/msg26741.html](http://www.mail-archive.com/net-snmp-users@lists.sourceforge.net/msg26741.html)

---

### Post by CurryNoodles on 2011-02-09
[FONT=Verdana][SIZE=1]> **Arndt said:**
> I didn't find a lot, but I found this, which seems to present both a problem and its solution. Is it what you mean?

[http://www.mail-archive.com/net-snmp-users@lists.sourceforge.net/msg26741.html](http://www.mail-archive.com/net-snmp-users@lists.sourceforge.net/msg26741.html)[/SIZE][/FONT][SIZE=1]  [/SIZE][FONT=Verdana][SIZE=1]


Thanks for your reply Arndt.

however, i still need some help here

1) i can't find snmp.conf (which under /etc/snmp), am i lack of anything?
[/SIZE][/FONT][FONT=Verdana][SIZE=1]
2) I do not have any [FONT=monospace]"[/FONT]old net-snmp-5.3/mibs/* files" as that guy mentioned, where i can get it?
3) there is some files under ~$/usr/share/snmp/mibs# which looks looks "NET-SNMP-MIB.txt". how to use it?

Sorry about my language. Really need some advise. Thanks! *hugsss* :popcorn:
[/SIZE][/FONT]

---

### Post by Arndt on 2011-02-09
> **CurryNoodles said:**
> [FONT=Verdana][SIZE=1]


Thanks for your reply Arndt.

however, i still need some help here

1) i can't find snmp.conf (which under /etc/snmp), am i lack of anything?
[/SIZE][/FONT][FONT=Verdana][SIZE=1]
2) I do not have any [FONT=monospace]"[/FONT]old net-snmp-5.3/mibs/* files" as that guy mentioned, where i can get it?
3) there is some files under ~$/usr/share/snmp/mibs# which looks looks "NET-SNMP-MIB.txt". how to use it?

Sorry about my language. Really need some advise. Thanks! *hugsss* :popcorn:
[/SIZE][/FONT]

(What did you do to the fonts?)

I haven't actually used SNMP for several years, so now I'm only somewhat familiar with the concepts and nothing more. But it seems to me that 10.10 in itself shouldn't be a permanent obstacle for you.

Official MIB files should be somewhere at IETF. I remember they are also included in the smidump package.

---

