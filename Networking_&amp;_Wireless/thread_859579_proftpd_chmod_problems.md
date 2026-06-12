---
title: "proftpd chmod problems"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by doomstone on 2008-07-14
I have set a ftp up on my ubuntu server for my web projects.
beta.aocdb.info
aocdb.info

My homepages are located in 
/var/www/aocdb.info/beta/
/var/www/aocdb.info/www/

I have this little problem, i can upload new files without any problems. but when i try to overwrite or delete a file i get promission denied.
I have tryed all i know about linux to fix it
"sudo chmod -R 777 /var/www/" but nothing i can come up with workes :(

This is my proftpd.conf
```
ServerType standalone
DefaultServer on
Umask 022
ServerName "0.0.0.0"
ServerIdent on "AoCdb.info"
ServerAdmin kasper@sogaard.us
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
DisplayLogin welcome.msg
User doomstone
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
  AllowUser aocdb
  AllowUser beta.aocdb
  DenyALL
</Limit>

<Anonymous /var/www/aocdb.info/www>
User aocdb
Group aocdb
AnonRequirePassword on
MaxClients 100 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SI$
 AllowAll
</Limit>
<Limit NOTHING >
 DenyAll
</Limit>
</Anonymous>

<Anonymous /var/www/aocdb.info/beta>
User aocdb
Group aocdb
AnonRequirePassword on
MaxClients 100 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SI$
 AllowAll
</Limit>
<Limit NOTHING >
 DenyAll
</Limit>
</Anonymous>

<Anonymous /var/www/aocdb.info/beta>
User beta.aocdb
Group aocdb
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
AllowOverwrite off
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SI$
 AllowAll
</Limit>
<Limit NOTHING >
 DenyAll
</Limit>
</Anonymous>
```

Any 1 who can point me in the right direction here?

---

### Post by superprash2003 on 2008-07-15
install gproftpd the gui for proftpd.. makes it easier to configure proftpd.. in the terminal type sudo apt-get install gproftpd

---

### Post by doomstone on 2008-07-16
> **superprash2003 said:**
> install gproftpd the gui for proftpd.. makes it easier to configure proftpd.. in the terminal type sudo apt-get install gproftpd

That is the way i have done it so far as you can see from the config file,

---

