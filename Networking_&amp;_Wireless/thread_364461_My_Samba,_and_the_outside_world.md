---
title: "My Samba, and the outside world"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by dhice on 2007-02-18
Hi all, first time poster.

Basically what I am trying to do is be able to use Samba with my LAN to share a specific folder and it's contents. 

I can do this by going to other computers in my LAN and typing the IP address to my server, but I want to allow my friends and family to be able to use this fileserver remotely with the username and passwords I assign them.  My current setup is  Modem => Router => Server and I plan to have the DMZ enabled on my server, and create a firewall on ubuntu.  

Unfortunately, I do not have a static IP, so I was wondering if there is a way to set up a host name that automatically routes to my server.

I am fairly new to ubuntu, but I have managed pretty well through tutorials and such, but haven't ran across any tutorials for my specific situation.

Thank you for any help I receive.

:lol:

---

### Post by koenn on 2007-02-18
> Unfortunately, I do not have a static IP, so I was wondering if there is a way to set up a host name that automatically routes to my server.

[http://www.dyndns.com/services/dns/dyndns/](http://www.dyndns.com/services/dns/dyndns/)

---

### Post by dhice on 2007-02-18
Ok I now have a domain name that suits my needs, but how do I get that domain name working correctly with Samba so that when my users type in the domain, it will be treated like a file share over the net?

---

### Post by koenn on 2007-02-18
same as always - 
your samba shares should be visible as //server.domain.zz/share  (or with \\ ...\.... from WIndows)

how to actually go about it, depends on the file browser. With Nautilus, it would probably be easiest to go Places : Connect to a server

Note that, although it's technically possible to share files over the internet using Samba, it is highly recommended you use a secure protocol, such as ssh, and apply the security measures you mentioned (firewall, dmz, ...)

---

### Post by RandomJoe on 2007-02-18
I would also strongly suggest you use a more secure / Internet-savvy method of remotely accessing files.

If you really want to use SMB shares, then at least set up a VPN or SSH tunnel between the computers and share over that.  OpenVPN is quite handy for this, and is much easier to set up than most VPN alternatives.  (And also works well on Linux, Win, Mac, etc.)  An SSH tunnel would be relatively simple too, I think, although it's been quite a while since I messed with them.

Aside from security, I have found that SMB shares are S-L-O-W across the net!  A LAN has plenty of bandwidth to chew up, but most net connections aren't so roomy.  Browsing directories can be painful, especially when a folder has many files in it.

If you just want to have a single shared folder for people do dump/retrieve things, then perhaps an 'sftp' (Secure FTP) server would be one possibility.  I'm a CLI junkie, so I can't really tell you what other methods would have good graphical interfaces.  It's faster (for me) to do things like that in textmode.

---

### Post by RandomJoe on 2007-02-18
And I supposed the standard warning would be useful:

Since you mention this is a dynamic IP, I would assume that your Terms of Service probably state you aren't allowed to run servers.  For low-volume use, they probably won't say anything (but they could!), but if your friends/family start hitting your site heavily you may find your connection shut off one day.

Which reminds me of another point - in an attempt to stem the tide of worms and such, many ISPs are now blocking well-known ports, including those used by SMB/CIFS.  So you may not be able to use that protocol directly over the net anyway.  (I don't know if you can tell Windows to use a different port or not...)  OpenVPN and SSH servers can be told to use any port you want, so can still be set up unless your ISP blocks ALL ports.  (Which I haven't yet seen myself.)

---

### Post by dmizer on 2007-02-18
yeah ... samba ... bad idea for opening things up to the world.

you're better off with something built for the web.  http, or ftp, or even better sftp.  please think security when exposing yourself and your files to the net.  you will find yourself hacked in no time because it doesn't matter how secure linux is if you have that security turned off (as with opening samba to the net).

there's a very decent howto for setting up an ftp server in my sig.

---

### Post by dhice on 2007-02-18
Ok, now seeing the mistake I was trying to make with samba I have a question for you guys/gals.  I would like for yall to give a suggestion for my setup after hearing all of my goals / needs.



1. All of my home computers can share this folder. (Server being linux, the others being Windows)
2. This folder has read/write capabilities to all specified users.
3. Allow access remotely.
4. Remote access thats easy to use, so that novice computer users can login and use efficantly.

At this point I'm thinking keeping samba set up to the particular share folder for the home network, as it's easy to setup/use.  And maybe a ftp using the Dyn DNS site for the domain to connect to the outside world?  The only questions I have about the FTP is what would be an easy to use way for my users to access?


Thanks for all the help everyone

---

### Post by PartickThistle on 2007-02-18
FTP would probably be the best way for you to go since you can mount FTP shares in both Linux and Windows and they'll act like regular folders, albeit slow ones.  FTP is also a bit faster than SFTP.

It's advisable to put it on a different port as you'll get numerous break-in attempts from hack-bots which are trained on port 21.

---

### Post by dhice on 2007-02-18
I dont think I'm setting this up right.... heres my config file for the proftpd

ServerType standalone
DefaultServer on
Umask 022
ServerName "DNS"
ServerIdent on "My FTPD"
ServerAdmin [email]dhice@mchsi.com[/email]
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
User nobody
Group network_users
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
  Allow User: my user names

  DenyALL
</Limit>

<Anonymous /home/network>
User username
Group network_users
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
AllowOverwrite off
<Limit RETR LIST NLST MDTM SIZE STAT CWD XCWD PWD XPWD CDUP XCUP>
 AllowAll
</Limit>
<Limit DELE APPE STOR STOU SITE_CHMOD SITE_CHGRP RNFR RNTO MKD XMKD RMD XRMD>
 DenyAll
</Limit>
</Anonymous>

<Anonymous /home/network>
User cpressnell
Group network_users
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
AllowOverwrite off
<Limit RETR LIST NLST MDTM SIZE STAT CWD XCWD PWD XPWD CDUP XCUP>
 AllowAll
</Limit>
<Limit DELE APPE STOR STOU SITE_CHMOD SITE_CHGRP RNFR RNTO MKD XMKD RMD XRMD>
 DenyAll
</Limit>
</Anonymous>

<Anonymous /home/network>
User epressnell
Group network_users
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
AllowOverwrite off
<Limit RETR LIST NLST MDTM SIZE STAT CWD XCWD PWD XPWD CDUP XCUP>
 AllowAll
</Limit>
<Limit DELE APPE STOR STOU SITE_CHMOD SITE_CHGRP RNFR RNTO MKD XMKD RMD XRMD>
 DenyAll
</Limit>
</Anonymous>

<Anonymous /home/network>
User ghice
Group network_users
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
AllowOverwrite off
<Limit RETR LIST NLST MDTM SIZE STAT CWD XCWD PWD XPWD CDUP XCUP>
 AllowAll
</Limit>
<Limit DELE APPE STOR STOU SITE_CHMOD SITE_CHGRP RNFR RNTO MKD XMKD RMD XRMD>
 DenyAll
</Limit>
</Anonymous>

<Anonymous /home/network>
User chice
Group network_users
AnonRequirePassword off
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
<Limit LIST NLST  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Anonymous>

<Anonymous /home/network>
User shice
Group network_users
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
AllowOverwrite off
<Limit RETR LIST NLST MDTM SIZE STAT CWD XCWD PWD XPWD CDUP XCUP>
 AllowAll
</Limit>
<Limit DELE APPE STOR STOU SITE_CHMOD SITE_CHGRP RNFR RNTO MKD XMKD RMD XRMD>
 DenyAll
</Limit>
</Anonymous>

<Anonymous /home/network>
User dhice
Group network_users
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
AllowOverwrite off
<Limit RETR LIST NLST MDTM SIZE STAT CWD XCWD PWD XPWD CDUP XCUP>
 AllowAll
</Limit>
<Limit DELE APPE STOR STOU SITE_CHMOD SITE_CHGRP RNFR RNTO MKD XMKD RMD XRMD>
 DenyAll
</Limit>
</Anonymous>

<VirtualHost Unspecified>
Port 65535
ServerName "Unspecified"
ServerIdent on "Unspecified"
PassivePorts 49152 65534
#MasqueradeAddress None
ServerAdmin [email]Admin@this.doma[/email]in
Umask 022
TimesGMT off
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
User nobody
Group network_users
DirFakeUser on nobody
DirFakeGroup on nobody
DefaultTransferMode binary
AllowForeignAddress on
DeleteAbortedStores off
AllowRetrieveRestart on
AllowStoreRestart on
TransferRate RETR 30
TransferRate STOR 50
TransferRate STOU 50
TransferRate APPE 50
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gproftpd/gproftpd/gproftpd.pem
</IfModule>
<Limit LOGIN>
  DenyAll
</Limit>
</VirtualHost>

---

