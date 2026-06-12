---
title: "Login to Samba share"
date: 2024-05-28
forum: Networking &amp; Wireless
---

### Post by lydloke on 2024-05-28
I have got a NAS, which I from Kubuntu 22.04 logged in to thus:
sudo mount -t cifs //192.168.1.123/home /mnt/qnap -o uid=1000,iocharset=utf8,username="admin"
After installing Kubuntu 24.04 I am not able to log in. I get the usual prompt:
[FONT=monospace][COLOR=#000000]Password for admin@//192.168.1.123/home:
[/COLOR]but when I write the pe and press Enter I get the following message:
[/FONT][FONT=monospace][COLOR=#000000]mount error(2): No such file or directory [/COLOR]
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs) and kernel log messages (dmesg)
[/FONT][FONT=monospace]Running dmesg shows: 

[/FONT][FONT=monospace][COLOR=#18b218][ 2997.746224] [/COLOR][COLOR=#b26818]CIFS: [/COLOR][COLOR=#000000]Attempting to mount //192.168.1.123/home [/COLOR]
[COLOR=#18b218][ 2998.125481] [/COLOR][COLOR=#b26818]CIFS: [/COLOR][COLOR=#b21818]VFS:  BAD_NETWORK_NAME: \\192.168.1.123\home[/COLOR]
[COLOR=#18b218][ 2998.126803] [/COLOR][COLOR=#b26818]CIFS: [/COLOR][COLOR=#b21818]VFS: cifs_mount failed w/return code = -2[/COLOR]
[COLOR=#18b218][ 3008.352319] [/COLOR][COLOR=#000000]**[UFW BLOCK] IN=enp6s0 OUT= MAC=01:00:5e:00:00:01:5c:7b:5c:a6:03:34:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x10 PREC=0x80 TTL=1**[/COLOR]
 ID=34903 PROTO=2 
[COLOR=#18b218][ 3008.762224] [/COLOR][COLOR=#000000]**[UFW BLOCK] IN=enp6s0 OUT= MAC=01:00:5e:00:00:fb:00:08:9b:e2:ae:10:08:00 SRC=192.168.1.123 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 T**[/COLOR]
TL=1 ID=0 DF PROTO=2 
[COLOR=#18b218][ 3021.391562] [/COLOR][COLOR=#000000]**[UFW BLOCK] IN=enp6s0 OUT= MAC=01:00:5e:00:00:01:5c:7b:5c:a6:03:34:08:00 SRC=1.1.168.192 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1**[/COLOR]
 ID=63181 PROTO=ICMP TYPE=9 CODE=0 [/FONT][FONT=monospace]

I am able to log in to the NAS via the web interface though: 
[https://192.168.1.123/cgi-bin/](https://192.168.1.123/cgi-bin/)

[/FONT][FONT=monospace]What could be wrong? Has anything changed from 22.04 to 24.04? [/FONT][FONT=monospace]

[/FONT]

---

### Post by lydloke on 2024-05-31
Fixed. The error was that I had renamed "home" on the NAS to "back".

---

