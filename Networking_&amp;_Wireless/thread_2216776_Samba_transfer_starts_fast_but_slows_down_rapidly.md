---
title: "Samba transfer starts fast but slows down rapidly"
date: 2014-04-13
forum: Networking &amp; Wireless
---

### Post by spacecakes on 2014-04-13
Hi, i have a problem with samba where iam transferring a file, its starts at 100mb/sec and declines to about 30mb/sec. Reads are usually fine (~100mb/sec) but when i try to write to the samba server (ubuntu 12.04) from my desktop (win7) the problem occurs. Both boxes have intel nics and have good enough hardware to reach gbit link speeds. This is my smb.conf:

[global]
name resolve order = lmhosts bcast host
printing = bsd
printcap name = /dev/null
load printers = no
workgroup = workgroup


[accounts]
path = /home/spacecakes/raid
valid users = spacecakes
public = no
writable = yes

i have tried various different options here, such as [COLOR=#000000][FONT=Ubuntu Mono]socket options = TCP_NODELAY IPTOS_LOWDELAY and [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]write raw = yes among a lot of other ones.

any ides? the ubuntu box is a vm with vmxnet3 on a esxi box, the desktop is standalone, but the problem even occurs when i try to transfer files to the ubuntu vm guest from a win7 vm guest on the same vswitch.[/FONT][/COLOR]

---

### Post by spacecakes on 2014-05-19
iam pulling my hair on this one, still no progress :/. Transfer starts at 100mb/sec and then it stalls and suddenly its down to 60mb/sec and then stalls, and its down to 40mb/sec and so on it continues until the transfer is done, any ides guys?

ibm m1015 it mode along with ST3000DM001 drives raided with mdadm raid6, might there be a problem with the drive settings? because ive had the same problem with the same raid array in a totally diffrent box.

---

### Post by spacecakes on 2014-05-24
does anyone have any ide? would really appreciate some help!

---

