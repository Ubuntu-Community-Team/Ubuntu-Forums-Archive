---
title: "Cannot see shared folders on Ubuntu Server 22.04 with Windows 10"
date: 2023-01-02
forum: Networking &amp; Wireless
---

### Post by Curt_Smock on 2023-01-02
I went through this on another server using Ubuntu 14.04 LTS a few years ago and thought that I could set up my new server similarly. Boy was I wrong!

I installed Ubuntu Server and then Desktop 22.04 LTS on a server re-build using a hardware RAID 5 storage solution. I was able to get the server up and operating except for the sharing portion.

Here is the output of Testparm of the Smb.conf file.

```
testparm
Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Weak crypto is allowed

Server role: ROLE_STANDALONE

Press enter to see a dump of your service definitions

# Global parameters
[global]
    bind interfaces only = Yes
    client max protocol = SMB3
    client min protocol = SMB2
    interfaces = lo eno1
    log file = /var/log/samba/log.%m
    logging = file
    map to guest = Bad User
    max log size = 1000
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    security = USER
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    smb ports = 445
    unix password sync = Yes
    usershare allow guests = Yes
    wins support = Yes
    idmap config * : backend = tdb


[printers]
    browseable = No
    comment = All Printers
    create mask = 0700
    path = /var/spool/samba
    printable = Yes


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


[Public]
    comment = Public Directory
    force create mode = 0777
    force directory mode = 0777
    guest ok = Yes
    guest only = Yes
    path = /home/serveradmin/shared/public
    read only = No


[Data]
    comment = Data Directory
    force create mode = 0777
    force directory mode = 0777
    guest ok = Yes
    guest only = Yes
    path = /home/serveradmin/shared/data
    read only = No
```

Here is the output of netusershare:

```
net usershare info --long
[Public]
path=/home/serveradmin/Shared/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Data]
path=/home/serveradmin/Shared/Data
comment=
usershare_acl=Everyone:F,
guest_ok=y
```

I'm still able to ping this server from my windows laptop so I know that it can be seen...not sure what else I should be trying/installing?

Oh, by the way, I also installed WSDD and Avahi-Daemon.

TheArchitect

---

### Post by Curt_Smock on 2023-01-02
I am able to see the shared folders in the network part of Windows File Explorer once I shared the "Home" directory, but I still cannot access the folders.

---

### Post by Morbius1 on 2023-01-03
Ubuntu changed the default permissions on user's home directories from 755 to 750.

The owner of the home directory can traverse his own home directory to access what is within it but no one else can.

Options:

[1] Set the home directory back to what it was:
```
chmod o+rx $HOME 
```
[2] ***Or*** at least set it so others can traverse the directory:
```
chmod o+x $HOME
```
[3] ***Or*** Since all of your shares allow guest access you could also use "force user" to make - for your samba shares - all client users appear to be you:

Edit /etc/samba/smb.conf and in the [global] section - like right under the workgroup = WORKGROUP line add:
```
force user = serveradmin
```
Then restart smbd:
```
sudo service smbd restart
```

---

### Post by Curt_Smock on 2023-01-03
Thanks Morbius1! I was hoping to attract your attention...I'll try the first option and go from there. Should I reboot the server and the Windows machine after these changes, or is simply restarting the SMDB service sufficient?

---

### Post by Curt_Smock on 2023-01-03
Morbius -

I tried the first option and then option #3 and restarted smdb service...

```
testparm
Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Weak crypto is allowed

Server role: ROLE_STANDALONE

Press enter to see a dump of your service definitions

# Global parameters
[global]
    bind interfaces only = Yes
    client max protocol = SMB3
    client min protocol = SMB2
    interfaces = lo eno1
    log file = /var/log/samba/log.%m
    logging = file
    map to guest = Bad User
    max log size = 1000
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    smb ports = 445
    unix password sync = Yes
    usershare allow guests = Yes
    wins support = Yes
    idmap config * : backend = tdb
    force user = serveradmin


[printers]
    browseable = No
    comment = All Printers
    create mask = 0700
    path = /var/spool/samba
    printable = Yes


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


[public]
    comment = Public Directory
    force create mode = 0750
    force directory mode = 0750
    guest ok = Yes
    guest only = Yes
    path = /home/serveradmin/shared/public
    read only = No


[data]
    comment = Data Directory
    force create mode = 0750
    force directory mode = 0750
    guest ok = Yes
    guest only = Yes
    path = /home/serveradmin/shared/data
    read only = No
serveradmin@fs2:~$ sudo service smbd restart
```

Unfortunately I still get the following error in Windows 10...weird because I can see the folders I just cannot open them up. Any ideas?

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291519&stc=1[/IMG]

---

