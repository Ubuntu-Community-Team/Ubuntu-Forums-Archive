---
title: "How to get connman working?"
date: 2018-01-27
forum: Networking &amp; Wireless
---

### Post by zeehaa on 2018-01-27
Is there any way to get connman working on Ubuntu 16.04.3?
After installing the OS, I tried to install connman.
(network-manager removed automatically)
If I try to start connmand (systemctl start connman) I get some error messages:

jJan 27 06:14:12 xxx connmand[5489]: Connection Manager version 1.21
Jan 27 06:14:12 xxx kernel: [ 1498.988417] audit: type=1130 audit(1517030052.657:521): pid=1 uid=0 auid=4294967295 ses=4294967295 msg='unit=connman comm="systemd" exe="/lib/systemd/systemd" hostname=? addr=? terminal=? res=success'
Jan 27 06:14:12 xxx kernel: [ 1498.995738] audit: type=1300 audit(1517030052.665:522): arch=c000003e syscall=54 success=yes exit=0 a0=9 a1=0 a2=40 a3=1e87300 items=0 ppid=1 pid=5489 auid=4294967295 uid=0 gid=0 euid=0 suid=0 fsuid=0 egid=0 sgid=0 fsgid=0 tty=(none) ses=4294967295 comm="connmand" exe="/usr/sbin/connmand" key=(null)
Jan 27 06:14:12 xxx kernel: [ 1498.998930] audit: type=1300 audit(1517030052.668:523): arch=c000003e syscall=54 success=yes exit=0 a0=9 a1=0 a2=40 a3=1e80c80 items=0 ppid=1 pid=5489 auid=4294967295 uid=0 gid=0 euid=0 suid=0 fsuid=0 egid=0 sgid=0 fsgid=0 tty=(none) ses=4294967295 comm="connmand" exe="/usr/sbin/connmand" key=(null)
Jan 27 06:14:12 xxx kernel: [ 1499.002387] audit: type=1300 audit(1517030052.672:524): arch=c000003e syscall=54 success=yes exit=0 a0=9 a1=0 a2=40 a3=1e833d0 items=0 ppid=1 pid=5489 auid=4294967295 uid=0 gid=0 euid=0 suid=0 fsuid=0 egid=0 sgid=0 fsgid=0 tty=(none) ses=4294967295 comm="connmand" exe="/usr/sbin/connmand" key=(null)
Jan 27 06:14:12 xxx connmand[5489]: Aborting (signal 11) [/usr/sbin/connmand]
Jan 27 06:14:12 xxx connmand[5489]: ++++++++ backtrace ++++++++
Jan 27 06:14:12 xxx connmand[5489]: +++++++++++++++++++++++++++
Jan 27 06:14:12 xxx systemd[1]: connman.service: Main process exited, code=exited, status=1/FAILURE
Jan 27 06:14:12 xxx systemd[1]: connman.service: Unit entered failed state.
Jan 27 06:14:12 xxx systemd[1]: connman.service: Failed with result 'exit-code'.
Jan 27 06:14:12 xxx systemd[1]: connman.service: Service hold-off time over, scheduling restart.



I can't find any documentation about installation of connman, except to issue "apt-get install connman"...
Could you help me?

---

