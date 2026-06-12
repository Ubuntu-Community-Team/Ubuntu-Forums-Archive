---
title: "[SOLVED] 7.10 upgrade has blocked all of my ports"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by otakuj462 on 2007-12-08
I just upgraded to Kubuntu 7.10 from Kubuntu 7.04. I have never run a firewall on my computer before, but for some reason, ever since the upgrade, all of the ports that I would normally have had services listening on (sshd and ICMP are two), are now closed. I can no longer ping or ssh into my machine, even though the services are running. Even worse, the python debuggers for Pydev and Wing IDE are no longer working, as they require an open socket on localhost to listen on! When I try to start the debugger in either of them, they just hang. 
Here is the output of nmap:
```

jacob@jacob-laptop:~/Desktop$ nmap -P0 127.0.0.1

Starting Nmap 4.20 ( http://insecure.org ) at 2007-12-08 20:23 EST
All 1697 scanned ports on localhost (127.0.0.1) are filtered

Nmap finished: 1 IP address (1 host up) scanned in 351.141 seconds

```
It certainly appears as though a firewall was deployed on my machine during the 7.10 upgrade, perhaps in order to make my machine "secure by default." Could someone please confirm or deny this theory, or perhaps explain what might be going on?
Please let me know. Thanks.

Jake

Update:
I just checked my iptables

```

jacob@jacob-laptop:~/Desktop$ sudo iptables --list
[sudo] password for jacob:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```
Seemingly no rules in place. So what could be blocking these ports?

2nd Update:

I am able to ping/ssh into my computer from another computer on the network. It appears that I am blocked only when my computer attempts to connect to itself. What on earth could cause this behavior?

---

### Post by atlfalcons866 on 2007-12-08
install firestarter to configure your ports

> sudo apt-get install firestarter

---

### Post by Lostincyberspace on 2007-12-09
Thanks for this thread it is very helpful It is hard to  figure out how the ports work in ubuntu.

---

### Post by gombadi on 2007-12-09
First - firestarter would be of limited use. The iptables command shows no firewall so configuring one will not help much.

Second have a look around your machine to see how it is currently configured.

Show us the results of the following commands from the command line -

```

sudo netstat -plntu
ifconfig -a
route -n
sudo iptables -vnL
sudo iptables -t nat -vnL
telnet 127.0.0.1 22



```

netstat command shows what ports your system is currently listening on -
p - show process using the port
l - show listening ports
n - show in numeric mode
t - show tcp ports
u - show udp ports

ifconfig -a - show all network interfaces on the machine. Does it have a lo (loopback) interface?

route -n - show where your system will send packets

iptables commands - Just because I like to see the whole firewall :-)

telnet - see what happens when you try and connect. connection refused, timeout etc.

With this extra information we may be able to track down the problem.

---

### Post by otakuj462 on 2007-12-09
@gombadi:

```

jacob@jacob-laptop:~/apps/f-prot$ netstat -plntu
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:65447           0.0.0.0:*               LISTEN     13845/wish
tcp        0      0 0.0.0.0:8010            0.0.0.0:*               LISTEN     13523/kopete
tcp        0      0 0.0.0.0:6891            0.0.0.0:*               LISTEN     13845/wish
tcp        0      0 0.0.0.0:6892            0.0.0.0:*               LISTEN     13845/wish
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN     -
tcp        0      0 0.0.0.0:8888            0.0.0.0:*               LISTEN     -
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     -
tcp        0      0 0.0.0.0:63486           0.0.0.0:*               LISTEN     7606/skype
tcp6       0      0 :::21                   :::*                    LISTEN     -
tcp6       0      0 :::22                   :::*                    LISTEN     -
tcp6       0      0 :::25                   :::*                    LISTEN     -
udp        0      0 0.0.0.0:32768           0.0.0.0:*                          -
udp        0      0 127.0.0.1:32769         0.0.0.0:*                          7606/skype
udp        0      0 0.0.0.0:68              0.0.0.0:*                          -
udp        0      0 0.0.0.0:8010            0.0.0.0:*                          13523/kopete
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          -
udp        0      0 0.0.0.0:63486           0.0.0.0:*                          7606/skype
jacob@jacob-laptop:~/apps/f-prot$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:14:22:A9:6C:29
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19

eth1      Link encap:Ethernet  HWaddr 00:16:CE:46:E6:AB
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe46:e6ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:352570 errors:0 dropped:0 overruns:0 frame:0
          TX packets:266220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:330125609 (314.8 MB)  TX bytes:44702855 (42.6 MB)
          Interrupt:18 Memory:dfbfe000-dfc00000

eth0:avah Link encap:Ethernet  HWaddr 00:14:22:A9:6C:29
          inet addr:169.254.4.209  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19

lo        Link encap:Local Loopback
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

jacob@jacob-laptop:~/apps/f-prot$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0
jacob@jacob-laptop:~/apps/f-prot$ sudo iptables -vnL
[sudo] password for jacob:
Chain INPUT (policy ACCEPT 665K packets, 468M bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 431K packets, 66M bytes)
 pkts bytes target     prot opt in     out     source               destination
jacob@jacob-laptop:~/apps/f-prot$ sudo iptables -t nat -vnL
Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
jacob@jacob-laptop:~/apps/f-prot$ telnet 127.0.0.1 22
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection timed out

```

I also ran f-prot virusscan, just because this is so strange:

```

jacob@jacob-laptop:~/apps/f-prot$ fpscan --adware --applications -a

F-PROT Antivirus version 6.2.1
FRISK Software International (C) Copyright 1989-2007

Engine version: 4.4.2.54
Virus signatures: 20071208172786fa464ca8af501a91f90c63c06fa95d
                  (/home/jacob/apps/f-prot/antivir.def)

Error: Can not open devicefile /dev/sda: Permission denied
Error: Can not open devicefile /dev/ram15: Permission denied
Error: Can not open devicefile /dev/ram14: Permission denied
Error: Can not open devicefile /dev/ram13: Permission denied
Error: Can not open devicefile /dev/ram12: Permission denied
Error: Can not open devicefile /dev/ram11: Permission denied
Error: Can not open devicefile /dev/ram10: Permission denied
Error: Can not open devicefile /dev/ram9: Permission denied
Error: Can not open devicefile /dev/ram8: Permission denied
Error: Can not open devicefile /dev/ram7: Permission denied
Error: Can not open devicefile /dev/ram6: Permission denied
Error: Can not open devicefile /dev/ram5: Permission denied
Error: Can not open devicefile /dev/ram4: Permission denied
Error: Can not open devicefile /dev/ram3: Permission denied
Error: Can not open devicefile /dev/ram2: Permission denied
Error: Can not open devicefile /dev/ram1: Permission denied
Error: Can not open devicefile /dev/ram0: Permission denied
[Error] <Can not open directory: Permission denied>     /var/run/sudo/
[Error] <Can not open directory: Permission denied>     /var/run/wpa_supplicant3/
[Not scanning] <Not a regular file or directory>        /var/run/wpa_supplicant-global3
[Error] <Can not open file: Permission denied>  /var/run/crond.reboot
[Error] <Can not open file: Permission denied>  /var/run/bluetoothd_address
[Not scanning] <Not a regular file or directory>        /var/run/sdp
[Not scanning] <Not a regular file or directory>        /var/run/avahi-daemon/socket
[Error] <Can not open file: Permission denied>  /var/run/tinyproxy.pid
[Error] <Can not open directory: Permission denied>     /var/run/exim4/
[Not scanning] <Not a regular file or directory>        /var/run/cups/cups.sock
[Error] <Can not open directory: Permission denied>     /var/run/cups/certs/
[Error] <Can not open file: Permission denied>  /var/run/xauth/A:0-LwNvts
[Not scanning] <Not a regular file or directory>        /var/run/xdmctl/dmctl-:0/socket
[Not scanning] <Not a regular file or directory>        /var/run/xdmctl/xdmctl-:0
[Error] <Can not open directory: Permission denied>     /var/run/xdmctl/dmctl/
[Not scanning] <Not a regular file or directory>        /var/run/xdmctl/xdmctl
[Not scanning] <Not a regular file or directory>        /var/run/NetworkManager/wpa_ctrl_6564-9
[Not scanning] <Not a regular file or directory>        /var/run/dbus/system_bus_socket
[Not scanning] <Not a regular file or directory>        /var/run/klogd/kmsg
[Not scanning] <Not a regular file or directory>        /var/run/acpid.socket
[Error] <Can not open file: Permission denied>  /var/backups/passwd.bak
[Error] <Can not open file: Permission denied>  /var/backups/group.bak
[Error] <Can not open file: Permission denied>  /var/backups/shadow.bak
[Error] <Can not open file: Permission denied>  /var/backups/gshadow.bak
[Error] <Can not open file: Permission denied>  /var/cache/apt/archives/lock
[Error] <Can not open file: Permission denied>  /var/cache/cups/remote.cache
[Error] <Can not open file: Permission denied>  /var/cache/cups/job.cache
[Error] <Can not open file: Permission denied>  /var/cache/debconf/passwords.dat
[Error] <Can not open directory: Permission denied>     /var/cache/beagle/.gnome2/
[Error] <Can not open directory: Permission denied>     /var/cache/setup-tool-backends/debug/
[Error] <Can not open directory: Permission denied>     /var/cache/setup-tool-backends/backup/
[Error] <Can not open file: Permission denied>  /var/lib/apt/lists/lock
[Error] <Can not open file: Permission denied>  /var/lib/aptitude/lock
[Error] <Can not open file: Permission denied>  /var/lib/dpkg/lock
[Error] <Can not open file: Permission denied>  /var/lib/dpkg/triggers/Lock
[Error] <Can not open file: Permission denied>  /var/lib/kdm/kdmsts
[Error] <Can not open directory: Permission denied>     /var/lib/slocate/
[Error] <Can not open file: Permission denied>  /var/lib/ucf/cache/:etc:texmf:texmf.cnf
[Error] <Can not open file: Permission denied>  /var/lib/urandom/random-seed
[Error] <Can not open directory: Permission denied>     /var/lib/tor/
[Error] <Can not open file: Permission denied>  /var/lib/bluetooth/00:13:10:5D:30:7D/linkkeys
[Error] <Can not open file: Permission denied>  /var/lib/avahi-autoipd/00:14:22:a9:6c:29
[Error] <Can not open file: Permission denied>  /var/lib/avahi-autoipd/00:16:ce:46:e6:ab
[Error] <Can not open file: Permission denied>  /var/lib/avahi-autoipd/00:02:6f:40:8f:86
[Error] <Can not open file: Permission denied>  /var/lib/tomcat5.5/conf.backup/tomcat-users.xml
[Error] <Can not open file: Permission denied>  /var/log/cups/cups-pdf_log
[Error] <Can not open file: Permission denied>  /var/log/installer/syslog
[Error] <Can not open file: Permission denied>  /var/log/installer/partman
[Error] <Can not open file: Permission denied>  /var/log/installer/version
[Error] <Can not open file: Permission denied>  /var/log/tinyproxy.log
[Error] <Can not open file: Permission denied>  /var/log/tinyproxy.log.3.gz
[Error] <Can not open file: Permission denied>  /var/log/tinyproxy.log.2.gz
[Error] <Can not open file: Permission denied>  /var/log/tinyproxy.log.4.gz
[Error] <Can not open file: Permission denied>  /var/log/tinyproxy.log.5.gz
[Error] <Can not open file: Permission denied>  /var/log/pure-ftpd/transfer.log
[Error] <Can not open file: Permission denied>  /var/log/tinyproxy.log.13.gz
[Error] <Can not open file: Permission denied>  /var/log/tinyproxy.log.6.gz
[Error] <Can not open file: Permission denied>  /var/log/tinyproxy.log.7.gz
[Error] <Can not open file: Permission denied>  /var/log/tinyproxy.log.8.gz
[Error] <Can not open file: Permission denied>  /var/log/tinyproxy.log.9.gz
[Error] <Can not open file: Permission denied>  /var/log/tinyproxy.log.12.gz
[Error] <Can not open file: Permission denied>  /var/log/tinyproxy.log.10.gz
[Error] <Can not open file: Permission denied>  /var/log/tinyproxy.log.11.gz
[Error] <Can not open file: Permission denied>  /var/log/tinyproxy.log.14.gz
[Not scanning] <Not a regular file or directory>        /var/log/tomcat5.5/catalina.out
[Error] <Can not open file: Permission denied>  /var/log/tomcat5.5/catalina.2007-12-01.log
[Error] <Can not open file: Permission denied>  /var/log/tomcat5.5/localhost.2007-12-01.log
[Error] <Can not open file: Permission denied>  /var/log/tomcat5.5/manager.2007-12-01.log
[Error] <Can not open file: Permission denied>  /var/log/tomcat5.5/admin.2007-12-01.log
[Error] <Can not open file: Permission denied>  /var/log/tomcat5.5/host-manager.2007-12-01.log
[Error] <Can not open file: Permission denied>  /var/log/tomcat5.5/catalina.2007-12-07.log
[Error] <Can not open file: Permission denied>  /var/log/tomcat5.5/localhost.2007-12-07.log
[Error] <Can not open file: Permission denied>  /var/log/tomcat5.5/manager.2007-12-07.log
[Error] <Can not open file: Permission denied>  /var/log/tomcat5.5/admin.2007-12-07.log
[Error] <Can not open file: Permission denied>  /var/log/tomcat5.5/host-manager.2007-12-07.log
[Error] <Can not open file: Permission denied>  /var/log/apt/term.log
[Error] <Can not open file: Permission denied>  /var/log/tinyproxy.log.1.gz
[Error] <Can not open file: Permission denied>  /var/spool/anacron/cron.daily
[Error] <Can not open file: Permission denied>  /var/spool/anacron/cron.weekly
[Error] <Can not open file: Permission denied>  /var/spool/anacron/cron.monthly
[Error] <Can not open directory: Permission denied>     /var/spool/cron/atjobs/
[Error] <Can not open directory: Permission denied>     /var/spool/cron/atspool/
[Error] <Can not open directory: Permission denied>     /var/spool/cron/crontabs/
[Error] <Can not open directory: Permission denied>     /var/spool/cups/
[Error] <Can not open directory: Permission denied>     /var/spool/exim4/
[Error] <Can not open directory: Permission denied>     /var/tmp/kdecache-root/
[Error] <Can not open file: Permission denied>  /var/crash/tomcat5.5.0.crash
[Error] <Can not open file: Permission denied>  /etc/X11/Xwrapper.config
[Error] <Can not open file: Permission denied>  /etc/apt/secring.gpg
[Error] <Can not open file: Permission denied>  /etc/apt/trustdb.gpg
[Error] <Can not open directory: Permission denied>     /etc/cups/ssl/
[Error] <Can not open file: Permission denied>  /etc/cups/printers.conf
[Error] <Can not open file: Permission denied>  /etc/cups/printers.conf.O
[Error] <Can not open file: Permission denied>  /etc/kde3/.kthemestylerc.lock
[Error] <Can not open file: Permission denied>  /etc/ppp/chap-secrets
[Error] <Can not open file: Permission denied>  /etc/ppp/pap-secrets
[Error] <Can not open file: Permission denied>  /etc/qt3/.qtrc.lock
[Error] <Can not open file: Permission denied>  /etc/qt3/.qt_plugins_3.3rc.lock
[Error] <Can not open file: Permission denied>  /etc/qt3/.kstylerc.lock
[Error] <Can not open file: Permission denied>  /etc/qt3/.polyesterstylerc.lock
[Error] <Can not open file: Permission denied>  /etc/security/opasswd
[Error] <Can not open file: Permission denied>  /etc/ssh/ssh_host_rsa_key
[Error] <Can not open file: Permission denied>  /etc/ssh/ssh_host_dsa_key
[Error] <Can not open directory: Permission denied>     /etc/ssl/private/
[Error] <Can not open file: Permission denied>  /etc/.pwd.lock
[Error] <Can not open file: Permission denied>  /etc/at.deny
[Error] <Can not open file: Permission denied>  /etc/group-
[Error] <Can not open file: Permission denied>  /etc/passwd-
[Error] <Can not open file: Permission denied>  /etc/sudoers
[Error] <Can not open file: Permission denied>  /etc/shadow-
[Error] <Can not open file: Permission denied>  /etc/gshadow-
[Error] <Can not open file: Permission denied>  /etc/shadow
[Error] <Can not open file: Permission denied>  /etc/gshadow
[Error] <Can not open file: Permission denied>  /etc/boinc-client/gui_rpc_auth.cfg
[Error] <Can not open file: Permission denied>  /etc/passwd.bak
[Error] <Can not open file: Permission denied>  /etc/shadow.bak
[Error] <Can not open file: Permission denied>  /etc/group.bak
[Error] <Can not open file: Permission denied>  /etc/gshadow.bak
[Error] <Can not open file: Permission denied>  /etc/mtab.fuselock
[Error] <Can not open directory: Permission denied>     /etc/ipsec.d/private/
[Error] <Can not open file: Permission denied>  /etc/ipsec.secrets
[Error] <Can not open file: Permission denied>  /etc/exim4/passwd.client
[Error] <Can not open file: Permission denied>  /etc/hsqldb/sqltool.rc
[Error] <Can not open file: Permission denied>  /home/jacob/.rnd
[Error] <Can not open file: Permission denied>  /home/jacob/documents/school/2007_summer/cse4344/homework/proj3/capture01
[Unscannable] <File is damaged> /home/jacob/.wine/drive_c/windows/temp/75d2.tmp
[Unscannable] <File is damaged> /home/jacob/.wine/drive_c/windows/temp/d530.tmp
[Unscannable] <Unknown format or compression method>    /home/jacob/.ies4linux/downloads/ie6/EN-US/HHUPD.CAB
[Unscannable] <File is damaged> /home/jacob/.ies4linux/downloads/ie6/EN-US/IE_S2.CAB->IE_2.CAB
[Unscannable] <File is damaged> /home/jacob/.ies4linux/downloads/ie6/EN-US/IE_S5.CAB->IE_5.CAB
[Unscannable] <File is damaged> /home/jacob/.ies4linux/downloads/ie6/EN-US/IE_S4.CAB->IE_4.CAB
[Unscannable] <File is damaged> /home/jacob/.ies4linux/downloads/ie6/EN-US/IE_S3.CAB->IE_3.CAB
[Unscannable] <File is damaged> /home/jacob/.ies4linux/downloads/ie6/EN-US/IE_S6.CAB->IE_6.CAB
[Not scanning] <Not a regular file or directory>        /home/jacob/beagle/socket
[Not scanning] <Not a regular file or directory>        /home/jacob/.beagle/socket
[Not scanning] <Not a regular file or directory>        /lib/udev/devices/net/tun
[Not scanning] <Not a regular file or directory>        /lib/udev/devices/console
[Not scanning] <Not a regular file or directory>        /lib/udev/devices/kmem
[Not scanning] <Not a regular file or directory>        /lib/udev/devices/loop0
[Not scanning] <Not a regular file or directory>        /lib/udev/devices/null
[Not scanning] <Not a regular file or directory>        /lib/udev/devices/ppp
[Error] <Can not open file: Permission denied>  /opt/cisco-vpnclient/bin/vpnclient
[Error] <Can not open file: Permission denied>  /opt/cisco-vpnclient/bin/cisco_cert_mgr
[Error] <Can not open file: Permission denied>  /opt/cisco-vpnclient/bin/ipseclog
[Error] <Can not open file: Permission denied>  /opt/cisco-vpnclient/bin/cvpnd
[Error] <Can not open directory: Permission denied>     /root/.kde/
[Error] <Can not open directory: Permission denied>     /root/.gnupg/
[Error] <Can not open file: Permission denied>  /root/.bash_history
[Error] <Can not open file: Permission denied>  /root/.mcop/random-seed
[Error] <Can not open file: Permission denied>  /root/.ICEauthority
[Error] <Can not open file: Permission denied>  /root/.mcoprc
[Error] <Can not open file: Permission denied>  /root/.Xauthority
[Error] <Can not open file: Permission denied>  /root/.xsession-errors
[Error] <Can not open file: Permission denied>  /root/.lesshst
[Error] <Can not open directory: Permission denied>     /root/.ssh/
[Error] <Can not open directory: Permission denied>     /root/.gnome2/
[Error] <Can not open directory: Permission denied>     /root/.google/
[Error] <Can not open directory: Permission denied>     /root/Desktop/
[Error] <Can not open directory: Permission denied>     /root/.local/
[Error] <Can not open directory: Permission denied>     /root/.amsn/
[Error] <Can not open directory: Permission denied>     /root/amsn_received/
[Error] <Can not open directory: Permission denied>     /root/.gconf/
[Error] <Can not open directory: Permission denied>     /root/.gconfd/
[Error] <Can not open directory: Permission denied>     /root/.gizmo/
[Error] <Can not open directory: Permission denied>     /root/.mozilla/
[Error] <Can not open directory: Permission denied>     /root/.gizmo-cache/
[Error] <Can not open directory: Permission denied>     /root/.Skype/
[Error] <Can not open directory: Permission denied>     /root/.gnome2_private/
[Error] <Can not open directory: Permission denied>     /root/.config/
[Error] <Can not open file: Permission denied>  /root/capture02
[Error] <Can not open file: Permission denied>  /root/capture03
[Not scanning] <Not a regular file or directory>        /tmp/.X11-unix/X0
[Not scanning] <Not a regular file or directory>        /tmp/.ICE-unix/dcop7469-1197157321
[Not scanning] <Not a regular file or directory>        /tmp/.ICE-unix/7480
[Not scanning] <Not a regular file or directory>        /tmp/ssh-xicjmm7380/agent.7380
[Not scanning] <Not a regular file or directory>        /tmp/ksocket-jacob/kdeinit__0
[Not scanning] <Not a regular file or directory>        /tmp/ksocket-jacob/kdeinit-:0
[Not scanning] <Not a regular file or directory>        /tmp/ksocket-jacob/klauncherLMs7wb.slave-socket
[Not scanning] <Not a regular file or directory>        /tmp/ksocket-jacob/jacob-laptop-1d54-475b2bdc
[Not scanning] <Not a regular file or directory>        /tmp/orbit-jacob/linc-1dd8-0-6a6ef8927809a
[Error] <Can not open directory: Permission denied>     /tmp/ksocket-root/
[Error] <Can not open directory: Permission denied>     /tmp/kde-root/
[Error] <Can not open directory: Permission denied>     /tmp/orbit-root/
[Error] <Can not open directory: Permission denied>     /tmp/gconfd-root/
[Error] <Can not open file: Permission denied>  /usr/lib/cups/backend/ipp
[Error] <Can not open file: Permission denied>  /usr/lib/cups/backend/http
[Error] <Can not open file: Permission denied>  /usr/lib/cups/backend/lpd
[Error] <Can not open file: Permission denied>  /usr/lib/cups/backend/cups-pdf
[Error] <Can not open file: Permission denied>  /usr/lib/cups/backend-available/ipp
[Error] <Can not open file: Permission denied>  /usr/lib/cups/backend-available/lpd
[Found possible virus] <Heuristic-90 (not disinfectable)>       /usr/lib/debug/usr/lib/firefox/firefox-bin
[Found possible virus] <Heuristic-90 (not disinfectable)>       /usr/lib/debug/usr/lib/firefox/regxpcom
[Found possible virus] <Heuristic-90 (not disinfectable)>       /usr/lib/debug/usr/lib/firefox/xpcshell
[Found possible virus] <Heuristic-90 (not disinfectable)>       /usr/lib/debug/usr/lib/firefox/xpicleanup
[Found possible virus] <Heuristic-90 (not disinfectable)>       /usr/lib/debug/usr/lib/firefox/xpidl
[Found possible virus] <Heuristic-90 (not disinfectable)>       /usr/lib/debug/usr/lib/firefox/xpt_dump
[Found possible virus] <Heuristic-90 (not disinfectable)>       /usr/lib/debug/usr/lib/firefox/xpt_link
[Found possible virus] <Heuristic-90 (not disinfectable)>       /usr/lib/debug/usr/lib/firefox/obscure-tool
[Found possible virus] <Heuristic-90 (not disinfectable)>       /usr/lib/debug/usr/bin/python2.5
[Error] <Can not open file: Permission denied>  /usr/share/keyrings/ubuntu-archive-removed-keys.gpg
[Error] <Can not open file: Permission denied>  /.bash_history


Results:

Files: 598820
Skipped files: 116
MBR/boot sectors checked: 1
Objects scanned: 2228906
Infected objects: 9
Files with errors: 7
Disinfected: 0

Running time: 771:33

```

Greatly appreciate the help. Please let me know what you think.
Thanks.

Jake

---

### Post by gombadi on 2007-12-09
Loopback interface has no IP address. It should be 127.0.0.1

Mine is 
```

lroger@dave:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:19:D1:70:FA:F4  
          inet addr:192.168.100.100  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe70:faf4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11851 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9868 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:13309762 (12.6 MB)  TX bytes:1536847 (1.4 MB)
          Base address:0x20c0 Memory:90300000-90320000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1284 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1284 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:578469 (564.9 KB)  TX bytes:578469 (564.9 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.133.1  Bcast:192.168.133.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.68.1  Bcast:172.16.68.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

Have a look at the /etc/network/interface file. For the lo interface it should be something like this -
```

lroger@dave:~$ cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.100.100
        netmask 255.255.255.0
        network 192.168.100.0
        broadcast 192.168.100.255
        gateway 192.168.100.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.100.1


```

---

### Post by otakuj462 on 2007-12-09
Got it. For some reason, /etc/network/interfaces didn't have a reference to loopback. I added it, and now everything is working fine again.
Thanks for you help!

Jake

---

