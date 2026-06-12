---
title: "Cannot access Network Windows Server from Ubuntu 16.04"
date: 2017-04-09
forum: Networking &amp; Wireless
---

### Post by parablazer on 2017-04-09
Hello everybody.
I have looked everywhere and to no avail. I am running Ubuntu 16.04 and I have a windows 7 pro server that I am trying to connect. my older mint 15 and 18 laptops can connect just fine but Ubuntu 16.04 is not having it. This is where I am at.
I have edited the smb.conf file and added "client use spnego = no"
This has gotten me to a login screen to access the server, however the server has password sharing turned off. 
I even went as far as to add a user on the server with the same name and password as my ubuntu machine but it just keeps asking me to login over and over and over and over without letting me in.

Please HALP.

Cheers

---

### Post by TheFu on 2017-04-10
Welcome to the forums.

It isn't clear. Where is the storage located?  The smb.conf file is for running a samba server on Linux. Don't think it has anything to do with accessing CIFS shares on other machines.

Also, I'm assuming you want CIFS access. Is that the protocol you want?  There are hundreds of different ways to "connect to Windows" - you could use telnet, ssh, ftp, http, ... please clarify. I'd rather not assume what you mean and be wrong.

---

### Post by Morbius1 on 2017-04-10
Running this command will show you how Samba interprets your smb.conf file:
```
testparm -s
```
By any chance do you have this line listed:
> encrypt passwords = no
If you do you will pretty much be in an infinite loop passing credentials to the WIn7 server. Change it to yes.

---

### Post by parablazer on 2017-04-17
Ok, I will try this tomorrow. Thank you

---

### Post by parablazer on 2017-04-17
> **TheFu said:**
> Welcome to the forums.  It isn't clear. Where is the storage located?  The smb.conf file is for running a samba server on Linux. Don't think it has anything to do with accessing CIFS shares on other machines.  Also, I'm assuming you want CIFS access. Is that the protocol you want?  There are hundreds of different ways to "connect to Windows" - you could use telnet, ssh, ftp, http, ... please clarify. I'd rather not assume what you mean and be wrong.  The drive is on another server computer on my network. My mint 17 computers can see it fine, but the Mint 18 is no dice.

---

### Post by parablazer on 2017-04-17
> **Morbius1 said:**
> Running this command will show you how Samba interprets your smb.conf file:
```
testparm -s
```
By any chance do you have this line listed:

If you do you will pretty much be in an infinite loop passing credentials to the WIn7 server. Change it to yes.

Here is the output. I have switched to Mint 18 but the same issue. 

[I]Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE[/I]

[I]# Global parameters
[global]
    server string = %h server (Samba, Ubuntu)
    server role = standalone server
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb


[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers[/I]

---

### Post by parablazer on 2017-04-17
Update, I got in. used a user on the server and it let me in. Ubuntu was not working but Mint is fine with it. THE FIX IS you have to have a user on the server to log in with. NOTE: this will not work with Ubuntu, maybe editing the smb.conf file might work as suggested, but mint just works.

---

### Post by TheFu on 2017-04-17
> **parablazer said:**
> The drive is on another server computer on my network. My mint 17 computers can see it fine, but the Mint 18 is no dice.

Still not 100% clear.

Is the storage on a Windows server that you are trying to access using the CIFS protocol?  If so, I don't believe the smb.conf file has anything to do with that.

Try using the IP address, not the hostname. How does that work?
Also, the credentials for the connection must be those from the remote system, not your local Ubuntu ones, if they don't match.
Try using a different program - which program are you trying to use now?  Some file browser?  If you are using nautilus, try thunar or caja.

Is it really CIFS you are trying to use or some other protocol? That isn't clear yet.

Checking the log files is normally the first step. May need/want to enable more detailed logging, if the defaults don't show what is happening.  For example, when troubleshooting ssh connections, asking for more "verbosity" is helpful - just use **ssh -vvv** to get 3x more details about the connection attempt/failure/success.  Most client tools have some method to turn up the detail. Usually a --verbose or -debug or -vvv or some other option that is spelled out in the manpage for the command.  There is an smbclient command, for example.   The manpage for it says: [-d debuglevel] ... 
```
       -d|--debuglevel=level
           level is an integer from 0 to 10. The default value if this
           parameter is not specified is 1.

           The higher this value, the more detail will be logged to the log
           files about the activities of the server. At level 0, only critical
           errors and serious warnings will be logged. Level 1 is a reasonable
           level for day-to-day running - it generates a small amount of
           information about operations carried out.

           Levels above 1 will generate considerable amounts of log data, and
           should only be used when investigating a problem. Levels above 3
           are designed for use only by developers and generate HUGE amounts
           of log data, most of which is extremely cryptic.

           Note that specifying this parameter here will override the log
           level parameter in the smb.conf file.

```

So, it appears the smb.conf file **is** used in some way by some SMB/CIFS clients. Interesting.

---

