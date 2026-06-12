---
title: "Feisty network very slow one way"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by pr0fess0r on 2007-04-29
Hi all

I have just installed Feisty server (called hobbiton, workgroup middleearth) on  Core 2 Duo machine with 2GB of RAM, ASUS P5B-VM motherboard (we're using it as a webserver in our office). Previously we had Windows 2003 Server running as our server.

I have another machine running Feisty Desktop (connected to out TV) and a couple of Macs - mine is a PowerMac G5, my business partner uses a Core Duo iMac 20". We're all connected via a US Robotics 9106 router.

Our problem, which I've seen some mentions of elsewhere, is that copying files from the server to another machine - either the feisty desktop, or one of the macs - is incredibly slow. A few kb/sec.

Copying files TO the server works no problem.

On the Feisty desktp machine I connect using CIFS in /etc/fstab

//hobbiton/wwwroot /home/media/Desktop/wwwroot cifs credentials=/etc/hobbiton.cred,domain=middleearth 0 0

On the Macs we just use the Network icon in Finder to connect to the server.

So I tried iperf to check speeds - regardless of which machine was server and which was client, between my Mac and the feisty server my speeds were 65-70Mbits/.sec


Copying files from the server using SSH (i.e. SSH hobbiton cat remote/file > /local/file) works very fast as well.

It's only when copying from mounted drives we have this one way slowdown problem.

On the server, here is my smb.conf (with all of the lines starting with # removed)

```


[global]
   workgroup = MIDDLEEARTH
   server string = %h server
;   wins support = no
;   wins server = w.x.y.z
   dns proxy = no
;   name resolve order = lmhosts host wins bcast
;   interfaces = 127.0.0.0/8 eth0
;   bind interfaces only = true
   log file = /var/log/samba/log.%m
   max log size = 1000
;   syslog only = no
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
;   guest account = nobody
   invalid users = root
;   unix password sync = no
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
;   pam password change = no
;   domain logons = yes
;   logon path = \\%N\profiles\%U
;   logon path = \\%N\%U\profile
;   logon drive = H:
;   logon home = \\%N\%U
;   logon script = logon.cmd
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
   load printers = yes
;   printing = bsd
;   printcap name = /etc/printcap
   printing = cups
   printcap name = cups
;   printer admin = @lpadmin
;   include = /home/samba/etc/smb.conf.%m
   socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=8192 SO_SNDBUF=8192
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
;   domain master = auto
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
;[homes]
;   comment = Home Directories
;   browseable = no
;   valid users = %S
;   writable = no
;   create mask = 0600
;   directory mask = 0700
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700
wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
;   write list = root, @ntadmin
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom
[client]
path = /media/client
valid users = administrator
read only = No
create mask = 0777
directory mask = 0777
available = yes
browsable = yes
public = yes
writable = yes
[finance]
path = /media/finance
valid users = administrator
read only = No
create mask = 0777
directory mask = 0777
available = yes
browsable = yes
public = yes
writable = yes
[wwwroot]
path = /var/www
valid users = administrator
read only = No
create mask = 0777
directory mask = 0777
available = yes
browsable = yes
public = yes
writable = yes


```

The only change I'd made was to socket options:
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=8192 SO_SNDBUF=8192

So this is a serious issue for us as we need to copy files and edit them and so on as this is our company's development web server.

Where could I start looking to diagnose this issue?

thanks in advance for any help

cheers

Lucas

---

### Post by MCMcButtah on 2007-04-30
I had a simial problem to this with a ASUS P5B-E motherboard which uses the Attansic ethernet chipset. There was a bug in the driver that caused horrible upload speeds. Your ASUS P5B-VM motherboard uses a Realtek so I am not sure if the problem is related. You didn't mention the hardware in your other fiesty machine so i figuered I would pass this along just in case.

---

### Post by pr0fess0r on 2007-04-30
Thanks. Not sure what the card is in the other Feisty machine but the problem occurs with all of the machines on our network - a mix of OS X, Feisty and XP which all have different network cards. The P5B-VM uses a Realtek® PCI-E Gigabit LAN controller.
But the fact that I can ssh files at max speed surely means it's a software prob not a hardware one?
I've heard mention of using CIFS instead of smbfs, how do I configure Samba on the server to use CIFS, and will this help?

cheers

---

### Post by pr0fess0r on 2007-05-08
This bug makes Feisty almost unusable, and other users are experiencing the same problem. Has there been any progress with resolving this?

---

### Post by pr0fess0r on 2007-05-09
Here's some more configuration info based onm what I've found on other posts.
I've disabled IPv6 by the way, to no avail.

```

ifconfig -a -v
eth0      Link encap:Ethernet  HWaddr 00:18:F3:06:61:AC  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:850 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1300 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:129501 (126.4 KiB)  TX bytes:1417073 (1.3 MiB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


```

```
dmesg |grep eth
[   20.392881] eth0: RTL8168b/8111b at 0xf8830000, 00:18:f3:06:61:ac, IRQ 17
[   28.188264] r8169: eth0: link up
[   28.188272] r8169: eth0: link up

```

```
ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:18:F3:06:61:AC  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:976 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1336 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:161981 (158.1 KiB)  TX bytes:1422131 (1.3 MiB)
          Interrupt:17 

```

```
cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.2
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 210.55.12.1 210.55.12.2

```

Any suggestions greatly appreicated. Taking 10-20 seconds to copy a 1MB file across a 100Mbps network is no fun!

cheers

---

### Post by pr0fess0r on 2007-05-09
SOLVED!
The onboard Realtek Gigabit Ethernet card was the culprit, well the drivers anyway.

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/112794](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/112794)

The advice was to compile the Official Realtek r1000 drivers for the RTL8168b/8111b onboard card, but I was too scared to do that, so I disabled the card and chucked a Realtek 8139 card in, configured, rebooted and I'm away!

So, there you go. Would have liked to use the funky onboard card, but maybe I'll wait till I can get a compiled driver or am confident enough to compile my own. Hope that helps someone.

---

### Post by galileux on 2007-05-15
Hi
> **pr0fess0r said:**
> SOLVED!
 I was too scared to do that, so I disabled the card and chucked a Realtek 8139 card in, configured, rebooted and I'm away!

I have the same issue, but I compiled the official r1000 drivers on the onboard card only to find that IT STILL DOESN'T WORK.

I'm going to get a separate PCI contoller and try with that.
How should I go about it?
Should I disable the onboard NIC from the BIOS?
How do I remove the r1000 driver and compile the other one?

Thanks

---

