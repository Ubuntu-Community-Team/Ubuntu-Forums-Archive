---
title: "FTP server problem - please help."
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by lover_of_sc on 2008-03-24
Hi there,

I started a tread previously, but no one had an answer to my problem? Could someone please have a look at below tread and see if you know whats gone wrong. 

[http://ubuntuforums.org/showthread.php?t=733648](http://ubuntuforums.org/showthread.php?t=733648)

best regards
anders

---

### Post by TheWizzard on 2008-03-24
please post /etc/proftpd.conf

here are some sites i used to configure my ftp-server:
[http://archiv.debianhowto.de/en/proftpd/c_proftpd.html](http://archiv.debianhowto.de/en/proftpd/c_proftpd.html) 
[http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-ConfigFile.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-ConfigFile.html) 
[http://gentoo-wiki.com/HOWTO_ProFTPD](http://gentoo-wiki.com/HOWTO_ProFTPD) 
[http://www.ubuntuforums.org/showthread.php?t=79588](http://www.ubuntuforums.org/showthread.php?t=79588)

---

### Post by lover_of_sc on 2008-03-25
This is my proftpd.conf mate

# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias anders userftp

ServerName "Anders haXXor FTP"
ServerType standalone
DeferWelcome on

MultilineRFC2228 on
DefaultServer on
ShowSymlinks off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir .message
ListOptions "-l"

RequireValidShell off

TimeoutLogin 20

RootLogin off

# It's better for debug to create log files
ExtendedLog /var/log/ftp.log
TransferLog /var/log/xferlog
SystemLog /var/log/syslog.log

#DenyFilter \*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port 1980

# To prevent DoS attacks, set the maximum number of child processes
# to 30. If you need to allow more than 30 concurrent connections
# at once, simply increase this value. Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User nobody
Group nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask 022 022

PersistentPasswd off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent on "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/ftp

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts 5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/ftp>
Umask 022 022
AllowOverwrite off
<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
DenyAll
</Limit>
</Directory>

<Directory /home/ftp/download/*>
Umask 022 022
AllowOverwrite off
<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
DenyAll
</Limit>
</Directory>

<Directory> /home/ftp/upload/>
Umask 022 022
AllowOverwrite on
<Limit READ RMD DELE>
DenyAll
</Limit>

<Limit STOR CWD MKD>
AllowAll
</Limit>
</Directory>

---

### Post by TheWizzard on 2008-03-25
mmm, looks different than mine. 
you have no use and group specified. 


> # Set the user and group that the server normally runs at.
User nobody
Group nogroup

---

