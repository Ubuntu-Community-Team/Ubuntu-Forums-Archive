---
title: "FTP-server with dchp dynamic IP"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by galileo100584 on 2007-05-21
I have a linux box with ubuntu. It will be nice to setup it up as a ftp-server, If found out how!
I get my IP from a DHCP (always: 81.191.137.121) and my network cable is plugged in to the wall, no modem or router. I live in a apartment-complex, Where every apartment can plug in and go on line.
Is it possible to setup up a FTP-server, with just a LAN connection and DHCP?
(No modem, router, or static IP)

Thanks for the help! 

Her is my gproftpd configuration:



ServerType standalone
DefaultServer on
Umask 022
ServerName "81.191.137.121"
ServerIdent on "leo"
ServerAdmin galileo100584hotmail.com
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49152 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
User guest
Group guest
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress on
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 30
TransferRate STOR 40
TransferRate STOU 40
TransferRate APPE 40
SystemLog /var/log/secure
RequireValidShell off
#gp_random_username_length 6
#gp_random_password_length 6
#gp_randomize_case lower
#gp_useradd_homedir_path /var/ftp
#gp_useradd_upload_path /upload
#gp_html_path /var/www/ftp.htm
#gp_welcome_name welcome.msg
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol TLSv1
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gproftpd/gproftpd.pem
</IfModule>
<Limit LOGIN>
AllowUser guest
DenyALL
</Limit>

<Anonymous >
User guest
Group guest
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
<Limit LIST NLST RETR PWD XPWD SIZE STAT CWD XCWD CDUP XCUP >
AllowAll
</Limit>
<Limit STOR STOU APPE RNFR RNTO DELE MKD XMKD SITE_MKDIR RMD XRMD SITE_RMDIR SITE SITE_CHMOD SITE_CHGRP MTDM >
DenyAll
</Limit>
</Anonymous>

---

### Post by Jussi Kukkonen on 2007-05-21
> **galileo100584 said:**
> Is it possible to setup up a FTP-server, with just a LAN connection and DHCP?

Sure, but the question you want to ask is this: Can the client connect to your server? In your setup I'd assume it's not possible (from outside the building network at least). If you are behind a NAT as I assume (i.e. your external IP is different from the one you have inside the network), making it work would require network admin assistance...

---

