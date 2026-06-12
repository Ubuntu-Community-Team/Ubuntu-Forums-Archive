---
title: "Can't get access to shared folder"
date: 2018-08-23
forum: Networking &amp; Wireless
---

### Post by gumbo64 on 2018-08-23
I am setting up a file server/backup server named "NAS" on an old  machine running Bodhi linux and I have to share some folders on the  server so they are accessible from the network.
  On the network, besides "NAS", I have one workstation "PC" running Ubuntu  14.04, one workstation "WIN" running Windows 7, and an Android TVBox.

  The shared folders on "NAS" should be accessed from the two  workstations. Ideally the shared folders should also be accessed by the Android TV  Box, but this is not so important. I guess if I manage to get access to  the shared folder(s) on NAS from the ubuntu WORKSTATION, I will also get  access to it from the TV BOX, as it easily connects to the shared  folders on the Ubuntu workstation.


  Bodhi is a very light distribution based on Ubuntu Xenial, but  it is VERY minimal. So minimal that even the basic networking packages  (such as Samba) were missing. I installed the necessary packages though, and I also installed  Nautilus, in the hope I could manage to share a network folder through  the file manager (same as I do in Ubuntu 14.04), but I can't get the  shared folder to work.

  If I search the network from the "PC" (Ubuntu 14.04) filemanager, NAS is  displayed among the resources, but when I try to connect I get a refused  connection error message .
  I followed about 10 different tutorials and been working two days on how to  configure the Samba Server on "NAS" but nothing seems to work for me, and I  can't get access to the shared folder.

  Here the result of smbclient run from the Ubuntu Workstation:

```
cg@PC:~$ /usr/bin/smbclient -L 192.168.0.102
WARNING: The "syslog" option is deprecated
Enter cg's password: 
Domain=[WORKGROUP] OS=[Windows 6.1] Server=[Samba 4.3.11-Ubuntu]

Sharename       Type      Comment
---------       ----      -------
print$          Disk      Printer Drivers
NAS_share       Disk      
IPC$            IPC       IPC Service (NAS server (Samba, Ubuntu))
Domain=[WORKGROUP] OS=[Windows 6.1] Server=[Samba 4.3.11-Ubuntu]

Server               Comment
---------            -------
NAS                  NAS server (Samba, Ubuntu)

Workgroup            Master
---------            -------
WORKGROUP            PC
```

I can see the shared folder on NAS (NAS_share) if I use the "connect to  server" interface on the Ubuntu file manager (smb://192.168.0.102), but I  can't access the folder since the password I set up in samba is not  recognized.... I'm sure about the username and password as I use the same on all  machines, and its the same I use to log into all the systems.

Here's some output about the current samba config on "NAS"

testparm -s

```
   cg@NAS:~$ testparm -s
  Load smb config files from /etc/samba/smb.conf
  rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
  WARNING: The "syslog" option is deprecated
  Processing section "[printers]"
  Processing section "[print$]"
  Processing section "[NAS_share]"
  Loaded services file OK.
  Server role: ROLE_STANDALONE

# Global parameters
    [global]
    server string = %h server (Samba, Ubuntu)
    server role = standalone server
    security = USER
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew
    \s*\spassword:                    
    * %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


[NAS_share]
    comment = NAS_share
    path = /home/cg/NAS_share
    valid users = @users
    force group = users
    group = users
    read only = No
    create mask = 0660
    directory mask = 0771
    directory mode = 0771
```


net usershare info --long

```
[NAS_share]
path=/home/cg/NAS_share
comment=
usershare_acl=Everyone:F,
guest_ok=y
```

---

### Post by Morbius1 on 2018-08-24
Is this the same question you marked as solved on AskUbuntu?

BTW, I had some free time and ran Bodhi and had a completely different experience than you did.

Note: Perhaps what I downloaded and how I'm running makes a difference: Bodhi-5.0.0-64.iso on a VirtualBox guest in a Live session - so I didn't actually install it.

** I installed samba.
** I created a samba guest share as the AskUbuntu post:
```
[Test]
path = /home/bodhi/Test
guest ok = yes
force user = bodhi
read only = No
```
Restarted the samba daemon:
```
sudo service smbd restart
```
And I could access it just fine from all my clients.

Another oddity from your last post is the use of **public = yes. **According to[B] man smb.conf :
[/B]> public

           This parameter is a synonym for guest ok.
"public" or "guest ok" should both work.

---

