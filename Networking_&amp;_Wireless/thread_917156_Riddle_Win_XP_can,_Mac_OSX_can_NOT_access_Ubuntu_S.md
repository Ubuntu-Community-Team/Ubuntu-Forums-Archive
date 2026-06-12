---
title: "Riddle: Win XP can, Mac OSX can NOT access Ubuntu Samba"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by Big Head J on 2008-09-11
I've just switched my home file server from Slackware to Ubuntu HH and have spent the last day setting up Samba file sharing (kee-rist what a hassle).  I use a Win XP laptop (Spike) and a Mac Pro OSX Leopard (Richard) to access shared directories on my file server (Zeppo).

On Slackware, Samba was working fine for both machines, which have not changed.  Samba on Ubuntu is working fine for the Win XP machines - I can read and write files as with Slackware.  However, the Mac machine can not browse the shares, let alone write to them.

When I try to connect using Finder, I get prompted for a password and if I try to log in as 'Guest' the Mac says 'This file server does not allow Guest access'.  I can't log in with a username + password either, whereas the Win machine lets me in without even asking.

They're all on the same network.

The weird thing is that I *can* connect to the Samba server Zeppo from the Mac (Richard) using smbclient.  It doesn't ask for a password (or accepts a null password) and I can browse the shares and so on.

Why am I getting blocked using Mac Finder and NOT with smbclient?  The Mac can see and talk to the Samba server, but only with smbclient...  I would look more at the Mac side, but the same machine was working fine with the Slackware Samba just yesterday.

Could it be something to do with Ubuntus lack of root user (Slackware has one by default)?  

Any ideas on where to go to next?  I'm at my wits end!

Here's my smb.conf if that's any help.  I've used SWAT to configure it and there are some defaults in there which I don't understand, but don't seem to be related to my problem.

 
[global]
        workgroup = RASPBERRYJAM
        server string = %h server (Samba, Ubuntu)
        security = SHARE
        encrypt passwords = No
        passwd chat =
        client plaintext auth = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        ldap ssl = no
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d

[Private]
        comment = private
        path = /home/private
        read only = No
        create mask = 0777
        guest ok = Yes

[music]
        comment = Music Library
        path = /music/music
        read only = No
        create mask = 0777
        inherit permissions = Yes
        guest ok = Yes

Your suggestions/ help/ jokes greatly appreciated.

---

### Post by Big Head J on 2008-09-11
More investigations reveal that there's some weirdness going on with nmbd not finding the Mac on the network.  I tried nmblookup and it didn't see it.  I've added the following line to the smb.conf:

interfaces = ip.add.res.ofclient1 ip.add.res.ofclient2

Result: the Mac no longer asks for a password, but still does not connect, nor can I see the share in Finder.  The Win XP client can still see and write to the shares.

Will do more digging tomorrow.   In the meantime, if you can think of any likely places to look for clues, let me know.

---

### Post by Big Head J on 2008-09-12
It turns out that Mac OSX Leopard will NOT accept "encrypt passwords = no" on the Samba server.  It says "connection failed" no matter what user/ pass combination you put in.

For the Mac to access the Samba file share, (even if you have no password or Security = SHARE) you must set

encrypt passwords = yes

in the smb.conf file.  If you're using SWAT to configure Samba, there's an entry on the Globals page.

This is apparently an old problem, as documented here:
[http://www.macwindows.com/tiger.html#SMB1](http://www.macwindows.com/tiger.html#SMB1)

Here's my working smb.conf file, from which both WinXP SP2 and Mac OSX Leopard (10.5.4) can read/ write both shares:

[global]
        workgroup = BERRYJAM
        server string = %h server (Samba, Ubuntu)
        security = SHARE
        syslog = 0
        log file = /var/log/samba/sambadebug.log
        max log size = 1000
        usershare allow guests = Yes

[Private]
        comment = private
        path = /home/private
        read only = No
        guest ok = Yes

[music]
        comment = Music Library
        path = /music/music
        read only = No
        guest ok = Yes

I'm surprised so few others have had this problem.  Anyway, hope this info saves another poor soul from the hassle I've had!

P.S.  The nmbd post above is a red herring - couldn't be replicated this morning and probably wasn't related.

---

### Post by Whoopage on 2008-12-20
> **Big Head J said:**
> It turns out that Mac OSX Leopard will NOT accept "encrypt passwords = no" on the Samba server.  It says "connection failed" no matter what user/ pass combination you put in.

For the Mac to access the Samba file share, (even if you have no password or Security = SHARE) you must set

encrypt passwords = yes

in the smb.conf file.  If you're using SWAT to configure Samba, there's an entry on the Globals page.

This is apparently an old problem, as documented here:
[http://www.macwindows.com/tiger.html#SMB1](http://www.macwindows.com/tiger.html#SMB1)

Here's my working smb.conf file, from which both WinXP SP2 and Mac OSX Leopard (10.5.4) can read/ write both shares:

[global]
        workgroup = BERRYJAM
        server string = %h server (Samba, Ubuntu)
        security = SHARE
        syslog = 0
        log file = /var/log/samba/sambadebug.log
        max log size = 1000
        usershare allow guests = Yes

[Private]
        comment = private
        path = /home/private
        read only = No
        guest ok = Yes

[music]
        comment = Music Library
        path = /music/music
        read only = No
        guest ok = Yes

I'm surprised so few others have had this problem.  Anyway, hope this info saves another poor soul from the hassle I've had!

P.S.  The nmbd post above is a red herring - couldn't be replicated this morning and probably wasn't related.


You fixed my problem man - thanks for posting your solution.  Just wanted to let you know it payed off for someone else!

---

### Post by pseudorandomname on 2009-04-06
Thanks for this, you might also want to mention that this only seems to work when security = user on the linux box.  I would like to have security = user since share level security is technically deprecated, but I'll take what I can get.

---

### Post by mickey13 on 2009-05-01
The only way I can get this to work is if I set my home directory to 777.  Is there a way to do this with a permission level of 700?

---

### Post by inertial on 2009-08-08
Hey, I ran into this problem with Mac OSX10.5.8, and because I don't have access to the file server configuration (the samba server is a fairly un-configurable router) I had to take a more zen approach.

The Finder smb mounter can be controlled by the configuration file nsmb.conf. If you type 'man nsmb.conf' in the terminal you can read about how to set it up. Here's what I put in my nsmb.conf file, which I put in the directory ~/Library/Preferences/

[default]
minauth=none


This works because I think by default the smb mounting utility that Finder uses was trying to use a higher minimum level of authentication, and so it wasn't able to send plaintext authentication.

---

### Post by thockin on 2010-01-11
I have this same problem on Karmic now, but the nsmb trick does not seem to work (Mac OS 10.5.8).

Help?

---

