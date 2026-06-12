---
title: "Cannot Browse Samba Network. (Could, but can't now...)"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by raid517 on 2006-12-05
Hi I installed Kubuntu and on the whole it works OK.

However I appear to be unable to browse my network with it.

I have a Samba server located at192.168.1.77 and another located at 192.168.109. My main computer is located at 192.168.1.102.

I can ping both of my Samba servers, e.g.

```
PING 192.168.1.77 (192.168.1.77) 56(84) bytes of data.
64 bytes from 192.168.1.77: icmp_seq=1 ttl=64 time=58.1 ms
64 bytes from 192.168.1.77: icmp_seq=2 ttl=64 time=1.77 ms
64 bytes from 192.168.1.77: icmp_seq=3 ttl=64 time=1.79 ms
64 bytes from 192.168.1.77: icmp_seq=4 ttl=64 time=2.28 ms

--- 192.168.1.77 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
rtt min/avg/max/mdev = 1.775/16.008/58.180/24.348 ms$
```

And I do have the latest available Ubuntu samba client and server installed - so there appears to be no reason why I can't browse these shares. (They are not password protected BTW - since they are not computers - one is a modified Xbox and the other is a Linux based WifI media player)

Can anyone suggest what the issue might be?

So to be clear.

I have a Linux based Desktop PC, a laptop running Kubuntu, a Linux based NAS wireless router running an internal version of Linux which has a 320GB storage drive attached and an 'iPod like' media player type device, via the the 2 supplied USB 2.0 ports on the router - and finally I have a modifies Xbox running XBMC and also Linux.

All of these (except for my laptop) are part of a workgroup called (for example) MYHOME. I don't want to confuse you too much however, as I have up until yesterday - for several weeks, been browsing my network from my laptop without issue using KDE Konqueror - which simply uses the syntax smb://192.168.1.67 (to say for example to browse my NAS storage devices).

Also the shares are not 'mounted' as I hadn't quite got around to doing that and I wasn't sure how - although I now get the impression that the samba client that enables me to browse shares is simply no longer working. (The only thing that changed is that I did some updating last night and installed some officially sanctioned Kubuntu updates (there is a little 'updates' icon in the Kubuntu system tray, which alerts you to when Ubuntu release critical/important updates so I simply did as it recommended I do and installed these updates (although I have no idea what they were now).

I don't use any non officially sanctioned mirrors or anything like that to install software packages - and indeed I have made no significant changes or installed any software on my own for some time.

All I can say is that it worked until yesterday evening - and today it does not. Which is really frustrating TBH - as Linux without Samba for me (given that some of my network can only use SAMBA) is like having to live without a right arm or leg. (Only possibly less practical). Samba for sharing files and steaming media across my network is one of the main reasons I use Linux - because it has always been so robust and flexible - far more so the case indeed, than in Microsoft Windows. Of all the things to go wrong in terms of computing having to live without.

PS

OH and BTW, I have tried just rebooting too.

---

### Post by raid517 on 2006-12-05
I don't know if it makes any difference - but here is my Samba.conf

```
[global]
server string = Laptop
hosts allow = 127. 192.168.0.
printcap name = /etc/printcap
printing = cups
cups options = raw
guest account = avahi
log file = /var/log/samba/samba.log
max log size = 1000
username level = 8
password level = 8
username map = /etc/samba/smbusers
add user script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M %u
unix password sync = yes
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*UNIX*password* %n\n *ReType*new*UNIX*password* %n\n *passwd:*all*authentication*tokens*updated*successfully*\n
socket options = TCP_NODELAY SO_SNDBUF=8192 SO_RCVBUF=8192 
interfaces = 127.0.0.1/8 192.168.0.0/24
remote browse sync = 192.168.0.255
remote announce = 192.168.0.255
local master = no
os level = 33
domain master = no
preferred master = no
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
name resolve order = wins lmhosts bcast
dns proxy = no
preserve case = no
;  short preserve case = no
;  default case = lower
;  case sensitive = no
winbind use default domain = yes
winbind uid = 16777216-33554431
winbind gid = 16777216-33554431
template shell = /dev/null
security = share
restrict anonymous = no
workgroup = myhome
max protocol = NT
ldap ssl = No
server signing = Auto

[homes]
comment = Home Directories
path = /home
read only = no
share modes = no
locking = no
guest account =
case sensitive = no
guest ok = yes
msdfs proxy = no

[netlogon]
comment = Network Logon Service
path = /home/netlogon
share modes = no
locking = no
guest account =
case sensitive = no
guest ok = yes
msdfs proxy = no

[profiles]
comment = User Profiles
path = /home/profiles
read only = no
browseable = no
locking = no
create mask = 0600
directory mask = 0700

[printers]
comment = All Printers
path = /var/spool/samba
printable = yes
share modes = no
locking = no
```

As I said this only appears to be relevant if I am sharing any files from my laptop on the rest of the network - which I am not. I am simply using (or was using) the samba client to browse files on my network.

It may be worth noting that all of my devices are connected to each other via a combo router/wireless access point, which is located at 192.169.1.1.

---

