---
title: "Can't ping windows machines"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by jjascarm on 2008-05-19
Hi, I can't ping the windows machines that a connected via a router to my ubuntu machine, but I can ping the ubuntu machine from windows. 

The windows machine have the IP addresses 192.168.1.5, and 192.168.1.101
The Ubuntu machine is 192.168.1.100

The output of the route command is:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

```
and the output of the ifconfig command is :
```
eth0      Link encap:Ethernet  HWaddr 00:09:5b:1b:6a:79  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fe1b:6a79/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15698 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14691 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13900479 (13.2 MB)  TX bytes:2445433 (2.3 MB)
          Interrupt:17 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:02:44:72:57:cb  
          inet addr:192.168.1.21  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:44ff:fe72:57cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:259 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:46098 (45.0 KB)
          Interrupt:20 Base address:0x9800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2153 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:108274 (105.7 KB)  TX bytes:108274 (105.7 KB)

```

I can access the internet ok though
Thanks for any help...

---

### Post by ivze on 2008-05-19
Looks like it is forbidden to response to pings on the windows box.

---

### Post by Iowan on 2008-05-19
I'm kinda surprised it works to have two NICS in the same subnet.
(... or maybe it doesn't.)

---

### Post by jjascarm on 2008-05-19
It works in windows with this setup so I would presume that it would also work in Linux

---

### Post by |{urse on 2008-05-19
Just for diagnostic purposes go to [www.showmyip.com](www.showmyip.com) on your windows machine and ping its real ip from ubuntu nto see if it gives you an ack.

By the way, I'm sure you know not to but just in case DO NOT post your real ip here

it also may be helpful to paste the output of 

ROUTE PRINT

from your windows box.

again, please change the real ip when u paste it up.

---

### Post by jjascarm on 2008-05-20
I followed your instructions, and I CAN ping the my real IP Address.

The output from the route print command in windows was:
```
===========================================================================
Interface List
  9 ...00 19 7e 5f b1 68 ...... Atheros AR5007EG Wireless Network Adapter
  8 ...00 1b 24 2c fe c6 ...... Marvell Yukon 88E8038 PCI-E Fast Ethernet Contro
ller
  1 ........................... Software Loopback Interface 1
 11 ...02 00 54 55 4e 01 ...... Teredo Tunneling Pseudo-Interface
 10 ...00 00 00 00 00 00 00 e0  6TO4 Adapter
 20 ...00 00 00 00 00 00 00 e0  Microsoft ISATAP Adapter
 19 ...00 00 00 00 00 00 00 e0  isatap.{FF5A3C4B-CC76-48D0-972B-F571E6E529AF}
===========================================================================

IPv4 Route Table
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0      192.168.1.1    192.168.1.101     20
        127.0.0.0        255.0.0.0         On-link         127.0.0.1    306
        127.0.0.1  255.255.255.255         On-link         127.0.0.1    306
  127.255.255.255  255.255.255.255         On-link         127.0.0.1    306
      192.168.1.0    255.255.255.0         On-link     192.168.1.101    276
    192.168.1.101  255.255.255.255         On-link     192.168.1.101    276
    192.168.1.255  255.255.255.255         On-link     192.168.1.101    276
        224.0.0.0        240.0.0.0         On-link         127.0.0.1    306
        224.0.0.0        240.0.0.0         On-link     192.168.1.101    276
  255.255.255.255  255.255.255.255         On-link         127.0.0.1    306
  255.255.255.255  255.255.255.255         On-link     192.168.1.101    276
```

I notice at one stage when I tried to ping my windows PC from Ubuntu that it was using the wrong IP to ping from - ie it was using 192.168.1.21 whcih is only connected to my media extender. It should have been using 192.168.100 but now when I run ping it doesn't show which IP it is pinging from. Perhaps it would help if I could disable the second network card. Can someone please tell me how to do this?

Thanks for your help

---

### Post by mothbitten on 2008-05-20
I think it may have to do with this line in your 'route' output:

> 192.168.1.0     *               255.255.255.0   U     0      0        0 eth1

I am no expert, but I think that says to use eth1 for all traffic to the 192.168.1.0 network, which would be a problem. Did you put that line in manually?

---

### Post by jjascarm on 2008-05-20
> **mothbitten said:**
> I think it may have to do with this line in your 'route' output:



I am no expert, but I think that says to use eth1 for all traffic to the 192.168.1.0 network, which would be a problem. Did you put that line in manually?

No I didn't put that in...how do I change it to Eth0?

---

### Post by mothbitten on 2008-05-21
Well, that seems odd, but I think the command would be (and note that this is just a change of the running state, and any changes will disappear if you reboot):

```
sudo route del -net 192.168.1.0 netmask 255.255.255.0 dev eth1
```

If that fixes it, that is good. if it screws things up worse, reboot.

---

### Post by jjascarm on 2008-05-21
> **mothbitten said:**
> Well, that seems odd, but I think the command would be (and note that this is just a change of the running state, and any changes will disappear if you reboot):

```
sudo route del -net 192.168.1.0 netmask 255.255.255.0 dev eth1
```

If that fixes it, that is good. if it screws things up worse, reboot.

I did as you suggested and it doesn't seem to have amde any difference, here is the output from ROUTE after I typed your suggested code into terminal:
```


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

```
I tried to ping, and it still doesn't work...

---

### Post by infosys on 2008-05-21
Gotta remember to check the simple stuff, is the windows firewall off? Or set to allow pings? It will prevent pings.

Also, are you able to ping everything upto the windows machine, ie. the fa port on the router?

---

### Post by jjascarm on 2008-05-21
> **infosys said:**
> Gotta remember to check the simple stuff, is the windows firewall off? Or set to allow pings? It will prevent pings.

Also, are you able to ping everything upto the windows machine, ie. the fa port on the router?

:) OK - I turned off my 'bitdefender anti-virus' firewall in windows and turned on the 'Windows XP' firewall and now I can ping from--to unbuntu--windows.

I still can't see the windows machines in places|network though. This is something to do with Samba configuration isn't it? Here is my Samba.conf file
```

[global]
netbios name = Samba
server string = Home Linux/Windows Network
workgroup = mshome
security = user
hosts allow = 192.168.1.1
interfaces = eth0 127.0.0.1/8 192.168.1.1.24 
remote announce = 192.168.1.1
remote browse sync = 192.168.1.1
printcap name = /etc/printcap
load printers = yes
cups options = raw
printing = cups
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
null passwords = no
username level = 8
password level = 8
encrypt passwords = yes
unix password sync = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = no
domain master = no
preferred master = no
domain logons = no
os level = 33
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
time server = no
name resolve order = wins lmhosts bcast
wins support = no
wins server = 
wins proxy = no
dns proxy = no
preserve case = yes
short preserve case = yes
client use spnego = no
client signing = no
client schannel = no
server signing = no
server schannel = no
nt pipe support = yes
nt status support = yes
allow trusted domains = no
obey pam restrictions = yes
enable spoolss = yes
client plaintext auth = no
disable netbios = no
follow symlinks = no
update encrypted = yes
pam password change = no
passwd chat timeout = 120
hostname lookups = no
username map = /etc/samba/smbusers
smb passwd file = /etc/samba/smbpasswd
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
add group script = /usr/sbin/groupadd '%g'
delete user script = /usr/sbin/userdel '%u'
delete user from group script = /usr/sbin/userdel '%u' '%g'
delete group script = /usr/sbin/groupdel '%g'
add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
machine password timeout = 120
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /dev/null
winbind use default domain = yes
winbind separator = @
winbind cache time = 360
winbind trusted domains only = yes
winbind nested groups = no
winbind nss info = no
winbind refresh tickets = no
winbind offline logon = no

[homes]
comment = Home Directories
path = /home
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no

[netlogon]
comment = Network Logon Service
path = /home/netlogon
read only = no
available = yes
browseable = yes
writable = no
guest ok = no
public = no
printable = no
share modes = no
locking = no

[profiles]
comment = User Profiles
path = /var/samba/profiles
read only = no
available = yes
browseable = no
writable = yes
guest ok = no
public = no
printable = no
locking = no
create mode = 0600
directory mask = 0700

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = no
guest ok = no
public = no
printable = yes
share modes = no
locking = no

[pdf-documents]
path = /home/pdf-documents
comment = Converted PDF Documents
available = yes
browseable = yes
writeable = yes
guest ok = yes

[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
guest ok = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gsambadpdf %s %u
lpq command =
lprm command =

```

---

