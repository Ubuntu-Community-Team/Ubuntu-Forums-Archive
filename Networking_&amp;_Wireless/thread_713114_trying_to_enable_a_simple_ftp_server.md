---
title: "trying to enable a simple ftp server"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by lime4x4 on 2008-03-02
here is a copy of my current config file all i want is simple access to one folder /media/sdc1/music/albums
i get the following error when trying to start the server

* Starting ftp server proftpd                                                                                                                                                                                                               - IPv4 getaddrinfo 'john-webbox' error: No address associated with hostname
 - warning: unable to determine IP address of 'john-webbox'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'

ServerType standalone
DefaultServer on
Umask 022
ServerName "192.168.1.23"
ServerIdent on "My FTPD"
ServerAdmin [email]Admin@this.domain.topd[/email]omain
IdentLookups on
UseReverseDNS on
Port 21
PassivePorts 49152 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress off
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
#gp_html_path /var/www/html/ftp.htm
#gp_welcome_name welcome.msg
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol TLSv1
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gproftpd/gproftpd.pem
</IfModule>
<IfModule mod_ratio.c>
Ratios off
SaveRatios off
RatioFile "/restricted/proftpd_ratios"
RatioTempFile "/restricted/proftpd_ratios_temp"
CwdRatioMsg "Please upload first!"
FileRatioErrMsg "FileRatio limit exceeded, upload something first..."
ByteRatioErrMsg "ByteRatio limit exceeded, upload something first..."
LeechRatioMsg "Your ratio is unlimited."
</IfModule>
<Limit LOGIN>
  AllowUser john
  DenyALL
</Limit>

<Anonymous /media/sdc1/music>
User john
Group john
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Anonymous>
  DenyALL
</Limit>

---

### Post by jeffus_il on 2008-03-02
If you have openssh installed, you can use sftp with no setup, you can use a client like filezilla and set up a sftp connection in the gui or use sftp from a terminal.

---

