---
title: "Samba help"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by greazy on 2009-08-21
Hello.

I'm having troubles with my Samba setup and my requirements are these:
1.  authentication using UNIX usernames (not samba)
2.  protected share directory accessible by only two users
3.  read-only access for one user, read/write for second user.
4.  not public
5.  not interested in printer shares
6.  both users will be sitting on  MS XP machines

I'm using Ubuntu 8.04 with all samba packages installed.

My setup is so that my scanner can send PDF scans to an FTP directory (already configured and working) then allow for a windows user to go in and read the pdf the scanner ftp'ed there.  With my current configuration I'm able to see the files, but I cannot read them  (access denied).

Here is my samba smb.conf file, condensed showing only active configuration portions (minimal comments):

> 
[global]

   workgroup = WORKGROUP
   server string = Server A
   dns proxy = no

#### Debugging/Accounting ####
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

####### Authentication #######
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user

############ Misc ############
   socket options = TCP_NODELAY
   usershare allow guests = yes


[scans]
comment = Scanned directory
path = /home/transferred/scans
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no




---

### Post by jonabyte on 2009-08-21
looks like you are missing the "valid user=" line in your share section.

---

### Post by greazy on 2009-08-21
I added:  

valid user = user1 user2

restarted samba:
sudo /etc/init.d/samba restart

went into a windows box, refreshed the explorer window and tried to map the directory using my user1 and it's UNIX password.

RESULT:
still cannot connect.  As before, it keeps prompting me for the user/pswd to access this share.

Another idea?

---

### Post by freebeer on 2009-08-21
Have you added the users to your linux box running samba?  Seems to me that you have to do that as well.

---

### Post by Iowan on 2009-08-21
I've been wrong before (frequently), but authentication may require Samba usernames (or different **security=** setting).

---

### Post by Linux000 on 2009-08-21
Is there an option to log on anonymously, if so that might be the problem, also there may be more than one server found in windows, if you click on WORKGROUP. Also, if you have a spare computer to use as the server try FreeNAS.

---

### Post by jonabyte on 2009-08-23
> **greazy said:**
> I added:  

valid user = user1 user2

restarted samba:
sudo /etc/init.d/samba restart

went into a windows box, refreshed the explorer window and tried to map the directory using my user1 and it's UNIX password.

RESULT:
still cannot connect.  As before, it keeps prompting me for the user/pswd to access this share.

Another idea?

Try this, even though you want to use the machine username, your conf file is saying you are using samba user/passwords.

```

# smbpasswd -a user1

```

---

### Post by greazy on 2009-08-24
Thanks everyone.  Still no solution

**freebeer**:  users are added on machine.  No issue there.
**Linux000**:  I'm not interested in anonymous login.  I want security

**jonabyte**:  I tried your smbpasswd-w user1.  I then restarted, still no go.  Very strange...

> Try this, even though you want to use the machine username, your conf file is saying you are using samba user/passwords.where in my config does it state that I am using Samba usr/psd's?
how do I change this?

---

### Post by greazy on 2009-08-25
UPDATE:

So I can remotely connect using my user1 login after restarting my windows box (probably using old user/pswd like Guest or something).
This said, I still don't have permissions to access the files!  I can see them, but I can't pull them down to a local share, like my windows desktop.

Permissions....help?

---

### Post by jonabyte on 2009-08-26
yes it is permissions, use groups for samba shares (I found this the easiest way) and then add the users to the groups.

---

### Post by wizard10000 on 2009-08-26
> **greazy said:**
> Hello.

I'm having troubles with my Samba setup and my requirements are these:
1.  authentication using UNIX usernames (not samba)
2.  protected share directory accessible by only two users
3.  read-only access for one user, read/write for second user.
4.  not public
5.  not interested in printer shares
6.  both users will be sitting on  MS XP machines

I'm using Ubuntu 8.04 with all samba packages installed.

My setup is so that my scanner can send PDF scans to an FTP directory (already configured and working) then allow for a windows user to go in and read the pdf the scanner ftp'ed there.  With my current configuration I'm able to see the files, but I cannot read them  (access denied).

Here is my samba smb.conf file, condensed showing only active configuration portions (minimal comments):

Windows authentication will only send a Windows username.

---

### Post by greazy on 2009-08-27
thanks again jonabyte.

I've modified my smb.conf and added:
[B]directory mask = 0775
read list = scanner[/B]

Therefore my share definition is as follows:

> 
[scans]
comment = Scanned directory
path = /home/xxxx

[B]read list = scangroup
directory mask = 0775[/B]

available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
this group owns the path shown above in UNIX permissions.  Is there another way to define this?  a better way?


Wizard:
how do I send a unix username from a windows box?  I've tried authenticating by "user1" or "workgroup/user1".  Given that I specifically map my path in windows using a unix-only (and not windows valid) login I'm fairly certain its authenticating properly.

---

### Post by ayenack on 2009-08-27
Take a look at this lots of useful info on setting up SAMBA for both Ubuntu and Windows machines. Should be able to find the answers you need.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by wizard10000 on 2009-08-27
> **greazy said:**
> Wizard:
how do I send a unix username from a windows box?  I've tried authenticating by "user1" or "workgroup/user1".  Given that I specifically map my path in windows using a unix-only (and not windows valid) login I'm fairly certain its authenticating properly.

The only way I know of to do it is using a 'net use' command.  This might help a little -

```
c:\>net help use
The syntax of this command is:


NET USE
[devicename | *] [\\computername\sharename[\volume] [password | *]]
        [/USER:[domainname\]username]
        [/USER:[dotted domain name\]username]
        [/USER:[username@dotted domain name]
        [/SMARTCARD]
        [/SAVECRED]
        [[/DELETE] | [/PERSISTENT:{YES | NO}]]

NET USE {devicename | *} [password | *] /HOME

NET USE [/PERSISTENT:{YES | NO}]


NET USE connects a computer to a shared resource or disconnects a
computer from a shared resource. When used without options, it lists
the computer's connections.

devicename       Assigns a name to connect to the resource or specifies
                 the device to be disconnected. There are two kinds of
                 devicenames: disk drives (D: through Z:) and printers
                 (LPT1: through LPT3:). Type an asterisk instead of a
                 specific devicename to assign the next available
                 devicename.
\\computername   Is the name of the computer controlling the shared
                 resource. If the computername contains blank characters,
                 enclose the double backslash (\\) and the computername
                 in quotation marks (" "). The computername may be from
                 1 to 15 characters long.
\sharename       Is the network name of the shared resource.
\volume          Specifies a NetWare volume on the server. You must have
                 Client Services for Netware (Windows Workstations)
                 or Gateway Service for Netware (Windows Server)
                 installed and running to connect to NetWare servers.
password         Is the password needed to access the shared resource.
*                Produces a prompt for the password. The password is
                 not displayed when you type it at the password prompt.
/USER            Specifies a different username with which the connection
                 is made.
domainname       Specifies another domain. If domain is omitted,
                 the current logged on domain is used.
username         Specifies the username with which to logon.
/SMARTCARD       Specifies that the connection is to use credentials on
                 a smart card.
/SAVECRED        Specifies that the username and password are to be saved.
                 This switch is ignored unless the command prompts for username
                 and password.  This option is not available on Windows XP
                 Home Edition and will be ignored.
/HOME            Connects a user to their home directory.
/DELETE          Cancels a network connection and removes the connection
                 from the list of persistent connections.
/PERSISTENT      Controls the use of persistent network connections.
                 The default is the setting used last.
YES              Saves connections as they are made, and restores
                 them at next logon.
NO               Does not save the connection being made or subsequent
                 connections; existing connections will be restored at
                 next logon. Use the /DELETE switch to remove
                 persistent connections.
NET HELP command | MORE displays Help one screen at a time.
```

---

