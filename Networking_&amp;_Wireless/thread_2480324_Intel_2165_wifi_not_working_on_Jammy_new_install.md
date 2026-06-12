---
title: "Intel 2165 wifi not working on Jammy new install"
date: 2022-10-26
forum: Networking &amp; Wireless
---

### Post by johnaaronrose on 2022-10-26
Apologies; the title should say 3165 not 2165.
Intel 3165 chip  wifi does not work on jammy new install. Ubuntu's Network   Manager never manages to connect to it. I've tried  the purge of the backport iwlwifi module but that didn't  help. I  followed the instructions elsewhere to give diagnostics.  They are at [https://pastebin.ubuntu.com/p/6tgVfYkmFj/](https://pastebin.ubuntu.com/p/6tgVfYkmFj/)

 Some more info:
 admin@Server:~$ lspci -nnk | grep 3165 
02:00.0 Network controller [0280]: Intel Corporation Wireless 3165  [8086:3165] (rev 81) Subsystem: Intel Corporation Dual Band Wireless AC  3165 [8086:4010] 
admin@Server:~$ rfkill list all
0: hci0: Bluetooth Soft blocked: yes Hard blocked: no
1: hci1: Bluetooth Soft blocked: yes Hard blocked: no 
2: phy0: Wireless LAN Soft blocked: no Hard blocked: no &#8211;
 Not dual boot. BTW Computer is an old Intel NUC.

I've tried changing /etc/modprobe.d/wifihacks.conf to conform with [https://bugzilla.kernel.org/show_bug.cgi?id=207409](https://bugzilla.kernel.org/show_bug.cgi?id=207409) but wifi still does not work.
admin@Server:~$ cat /etc/modprobe.d/wifihacks.conf
options iwlwifi swcrypt=0
options iwlwifi power_save=0
options iwlmvm power_scheme=1
options iwlwifi uapsd_disable=1

BTW I've reported this at [https://bugs.launchpad.net/ubuntu/+s...x/+bug/1993890]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1993890")

---

