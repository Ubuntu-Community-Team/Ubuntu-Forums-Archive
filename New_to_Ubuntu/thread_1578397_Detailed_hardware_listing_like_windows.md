---
title: "Detailed hardware listing like windows"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by g_ramesh on 2010-09-20
Hi

we are using RHEL 3.4.6-3 ( RHEL ES Release 4 Nahant update), kernel version - 2.6.9-55.ELsmp. What is ELsmp means?

In windows we can go to device manager and view what all are installed (see attached thumbnail)
In the above linux machine please tell me some program where I can do the same thing to know the hardware installed.

I tried lspci -vb, dmidecode, and seen some files in /proc directory, lshw etc, but none of them gave me a satisfactory answer.
Is there any other way?

---

### Post by lykeion on 2010-09-20
Sorry but I can't help you here since I've no experience with Red Hat whatsoever.

Google got me this:

ELsmp is the multiprocessor kernel

Apparently Hardware Browser and Device Manager applications should be accessible via the System Administration menu, see _[here]("http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/en-US/System_Administration_Guide/s1-sysinfo-hardware.html")_

---

