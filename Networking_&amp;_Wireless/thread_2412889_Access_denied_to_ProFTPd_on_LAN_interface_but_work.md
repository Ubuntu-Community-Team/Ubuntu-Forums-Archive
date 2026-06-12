---
title: "Access denied to ProFTPd on LAN interface but works on Wifi"
date: 2019-02-18
forum: Networking &amp; Wireless
---

### Post by fangji on 2019-02-18
[COLOR=#242729][FONT=Arial]I am having this super weird access denied issue on my home FTP server. The symptom is I can only access it through the wireless interface. When disabling the Wifi, and use ethernet, I got access denied.

[/FONT][/COLOR]```

LibNcFTP 3.2.5 (January 17, 2011) compiled for linux-x86_64-glibc2.21                                                                   
Uname: Linux|Korhal|4.4.0-87-generic|#110-Ubuntu SMP Tue Jul 18 12:55:35 UTC 2017|x86_64
Contents of /etc/debian_version:
  stretch/sid
Contents of /etc/issue:
  Ubuntu 16.04.3 LTS \n \l
Glibc: 2.23 (stable)
Remote server is running ProFTPD.


ProFTPD 1.3.4d Server (foxnfish FTP Server) [::ffff:192.168.1.134]
220: ProFTPD 1.3.4d Server (foxnfish FTP Server) [::ffff:192.168.1.134]                                                                 
Connected to 192.168.1.134.
Cmd: USER ji


Password requested by 192.168.1.134 for user "ji".


    Password required for ji


Password: ********
331: Password required for ji
Cmd: PASS xxxxxxxx
530: Access denied
Access denied
Cmd: QUIT
221: Goodbye.
Could not open host foxnfish: username and/or password was not accepted for login.

```[COLOR=#242729][FONT=Arial]

Output of my ifconfig

[/FONT][/COLOR]```

enp0s25   Link encap:Ethernet  HWaddr 00:1c:25:78:d5:06  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: **** Scope:Link
          inet6 addr: **** Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29531724 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4256164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42081203522 (42.0 GB)  TX bytes:851356778 (851.3 MB)
          Interrupt:20 Memory:fe200000-fe220000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:198 errors:0 dropped:0 overruns:0 frame:0
          TX packets:198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:16160 (16.1 KB)  TX bytes:16160 (16.1 KB)


wls3      Link encap:Ethernet  HWaddr 00:1f:3b:04:58:59  
          inet addr:192.168.1.143  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: **** Scope:Global
          inet6 addr: **** Scope:Link
          inet6 addr: ****/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:303586 errors:0 dropped:0 overruns:0 frame:0
          TX packets:157656 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:452487811 (452.4 MB)  TX bytes:15696186 (15.6 MB)

```[COLOR=#242729][FONT=Arial]

proftd.conf
[/FONT][/COLOR]```

ServerName "foxnfish FTP Server"
ServerType standalone
DefaultServer on
DefaultAddress foxnfish
UseIPv6 on
Port 21
User nobody
Group nogroup
Umask 000 000
SyslogFacility ftp
MultilineRFC2228 off
DisplayLogin /var/run/proftpd/proftpd.motd
DeferWelcome off
TimeoutIdle 600
TimeoutLogin 300
TimeoutNoTransfer 300
TimeoutStalled 3600
MaxInstances none
MaxClients 5
MaxConnectionsPerHost 10
MaxLoginAttempts  1
DefaultTransferMode ascii
IdentLookups off
UseReverseDNS off


<Limit LOGIN>
  AllowGroup ftp
  DenyAll
</Limit>


<Global>
  RequireValidShell off
  DefaultRoot ~ !wheel
  AllowOverwrite on
  DeleteAbortedStores off
  TimesGMT off
</Global>


<IfModule mod_ban.c>
  BanEngine off
  BanControlsACLs all allow group wheel
  BanLog /var/log/proftpd/ban.log
  BanMessage Host %a has been banned
  BanTable /var/run/proftpd/ban.tab
</IfModule>


<IfModule mod_delay.c>
  DelayEngine on
  DelayTable "/var/run/proftpd/proftpd.delay"
</IfModule>


<IfModule mod_wrap.c>
  TCPAccessFiles /etc/hosts.allow /etc/hosts.deny
  TCPAccessSyslogLevels info warn
  TCPServiceName ftpd
</ifModule>    

```[COLOR=#242729][FONT=Arial]

[/FONT][/COLOR]/etc/hosts.allow 
```

#ftpd  : xxx.xxx.xxx.xxx : deny
#sshd : .example.com : deny
#in.tftpd : xxx.xxx.xxx.xxx : deny
#bsnmpd : xxx.xxx.xxx.xxx : deny
ALL : ALL : allow

```

/etc/hosts.deny is empty
[COLOR=#242729][FONT=Arial]
What could possibly be wrong?[/FONT][/COLOR]

---

### Post by fangji on 2019-02-19
Thanks @wurtel for the hint. I checked the proftpD's configuration file and noticed there are two files named hosts.allow and hosts.deny. Although the contents of these two files looks very innocent. 


/etc/hosts.allow
```
#ftpd  : xxx.xxx.xxx.xxx : deny
#sshd : .example.com : deny
#in.tftpd : xxx.xxx.xxx.xxx : deny
#bsnmpd : xxx.xxx.xxx.xxx : deny
ALL : ALL : allow
```


/etc/hosts.deny is empty


When I further check the server logs and noticed these error logs.
```
Feb 18 21:51:55 foxnfish proftpd[19657]: 192.168.1.134 (192.168.1.2[192.168.1.2]) - mod_wrap/1.2.4: using access files: /etc/hosts.allow, /etc/hosts.deny 
Feb 18 21:51:55 foxnfish proftpd[19657]: 192.168.1.134 (192.168.1.2[192.168.1.2]) - mod_wrap/1.2.4: refused connection from ::ffff:192.168.1.2 
Feb 18 21:54:15 foxnfish proftpd[19659]: 192.168.1.134 (192.168.1.146[192.168.1.146]) - mod_wrap/1.2.4: using access files: /etc/hosts.allow, /etc/hosts.deny 
Feb 18 21:54:15 foxnfish proftpd[19659]: 192.168.1.134 (192.168.1.146[192.168.1.146]) - mod_wrap/1.2.4: allowed connection from iMac.xxx.xxx.xxx.net 
```


So for my wireless connection, my source address is resolved in the format of local domain host. But when connecting from the ethernet, my source address is some weird IP. I guess it didn't match the hosts.allow


Since this is an embedded Nas4Free build, I really can't modify the hosts.allow file. The quick solution is to turn off the proftpd_modwrap_enable entirely.


For people who is using proftpD on Nas4Free, you can turn off this module by setting the proftpd_modwrap_enable to NO in `System|Advanced|rc.conf`

---

