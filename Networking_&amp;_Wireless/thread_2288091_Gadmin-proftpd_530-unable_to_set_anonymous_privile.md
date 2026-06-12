---
title: "Gadmin-proftpd 530-unable to set anonymous privileges"
date: 2015-07-24
forum: Networking &amp; Wireless
---

### Post by Pascal_Paquin on 2015-07-24
A couple of days ago I had to re-install ubuntu on my computer, doing that I had to re-install all my applications.
One of these was gadmin-proftpd (I prefer to have a GUI interface).
I remember last year when I first install ubuntu I had a lot of problem setting up everything but it I was able to make it work.
Since yesterday I'm trying to make my ftp server to work with no luck.
I have try to login with firefox on my machine, and use Filezilla while at work and all I get is :

```

Statut :    Connexion à X.X.X.:21...
Statut :    Connexion établie, attente du message d'accueil...
Réponse :    220 MetalHead84
Commande :    USER MetalHead84
Réponse :    331 Password required for MetalHead84
Commande :    PASS ******
[B]Réponse :    530-Unable to set anonymous privileges.
Réponse :    530 Login incorrect.[/B]

```
(Sorry if it's in french, but I have put in bold the important part)

Also, here's my proftpd.conf : 
```

ServerType standalone
DefaultServer on
Umask 022
ServerName "192.168.0.105"
ServerIdent on "MetalHead84"
ServerAdmin myMail@mail.com
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49152 65534
#MasqueradeAddress 192.168.0.105
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
DisplayChdir .message
User metalhead84
Group root
DirFakeUser on nobody
DirFakeGroup on nobody
DefaultTransferMode binary
AllowForeignAddress off
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 220
TransferRate STOR 250
TransferRate STOU 250
TransferRate APPE 250
SystemLog /var/log/secure
RequireValidShell off
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol SSLv23
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gadmin-proftpd/certs/cert.pem
TLSRSACertificateKeyFile /etc/gadmin-proftpd/certs/key.pem
TLSCACertificateFile /etc/gadmin-proftpd/certs/cacert.pem
TLSRenegotiate required off
TLSOptions AllowClientRenegotiation
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
  AllowUser MetalHead84
  DenyALL
</Limit>

<Anonymous /media/metalhead84/MP3/sounds>
User MetalHead84
Group root
AnonRequirePassword on
MaxClients 10 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayChdir .msg
<Limit LOGIN>
Allow from All
Deny from all
</Limit>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit NOTHING >
 DenyAll
</Limit>
</Anonymous>


```

While driving to work, I start thinking that I should create a group for my ftp User, do you think it's the problem ?
Should I create a group call UserFtp ? Also should I create a user in ubuntu call MetalHead84 that is part of that group ? Or that doesn't change anything ?

---

