---
title: "Virtualbox - How can I share folders using Samba?"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by digital21c on 2007-05-24
Goal: I'd like my virtual WinXP (running as a guest OS under VirtualBox 1.3.8 )  to have read/write access to a partition on Feisty (host OS) using Samba instead of VirtualBox's built-in folder sharing system.  I'm suffering from [VirtualBox's shared folder bug (http://www.virtualbox.org/ticket/57)]("http://www.virtualbox.org/ticket/57").  A suggested work-around is to use Samba networking between the host and guest OSs.

Problem: From virtual WinXP, I can't see any samba services at all.  Windows explorer shows no local network.   Pings to the Feisty and the wireless router fail.  

Steps taken so far: I've installed Samba ( 3.0.24-2).  I've tried to set up smb.conf.  Workgroup names match between smb.conf and WinXP.  Samba seems to be running (sudo /etc/init.d/samba restart --> * Starting Samba daemons... [ OK ]).

Other: I'm using VirtualBox's NAT networking.  I'm the only user of this machine.  I'm happy to leave security until later.  My internet connection is via wireless router.  General internet access from Feisty and from (virtual) WinXP works well. I use local addresses in the range 172.16.1.x

What should I try next?

Here's my smb.conf:
```
[global]
workgroup = BRAHE
netbios name = GANDALF
security = SHARE
passdb backend = guest
domain master = no
wins support = yes

[data]
comment = Data
path = /media/data
read only = No
guest ok = Yes
```

From Feisty, 'ifconfig eth1' produces:
```
eth1      Link encap:Ethernet  HWaddr 00:19:D2:7A:9E:03  
          inet addr:172.16.1.12  Bcast:172.16.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe7a:9e03/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12214 errors:38 dropped:376 overruns:0 frame:0
          TX packets:9631 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16156835 (15.4 MiB)  TX bytes:1001920 (978.4 KiB)
          Interrupt:17 Base address:0x4000 Memory:efcff000-efcfffff 

```

From virtual WinXP, 'ipconfig' produces:
```
Windows IP Configuration
Ethernet adapter Local Area Connection:
        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 10.0.2.15
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 172.16.1.1
```

Thanks!

---

### Post by bodhi.zazen on 2007-05-25
You have to bridge you network card, then your windows guest will become a part of your local workgroup and get a local IP (172.16.1.xx)

Here is how : [http://doc.gwos.org/index.php/VirtualBox#Networking](http://doc.gwos.org/index.php/VirtualBox#Networking)

---

### Post by digital21c on 2007-05-27
bodhi.zazen,

Thanks for that information.  I'll work through those steps and try to figure out how it is all working.

I need to thank you for the information that you posted on ubuntuforums about USB devices and VirtualBox.   Your advice has  been very helpful!

Thanks again.

---

