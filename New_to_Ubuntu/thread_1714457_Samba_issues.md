---
title: "Samba issues"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by Willye on 2011-03-25
Hi all, i'm trying to configure samba and thus see the shared ubuntu directories from windows and see the windows share folders from ubuntu, i  used gadmin-samba  and samba server configuration, but i cannot see nothing ....... any ideas ???  
my ubuntu version is 10.04

---

### Post by Willye on 2011-03-28
some ideas ?

---

### Post by mastablasta on 2011-03-28
do you have your folder marked as shared? for example public folder in home.
right click it and share it. in windows the folder also needs to be marked as shared in order to see it. 
 
check if you have all the necessary samba packages. i had issues in KDE and found that a package wasn't installed together with the rest.i think you need samba client packages.
You need at least: 
Samba
Samba Client

There is porbably another GTK netrworking package you might need. i am not sure. 
 
what windows are you using?

---

### Post by Morbius1 on 2011-03-28
This is more an FYI but gadmin-samba by design generates an incoherent mess of an /etc/samba/smb.conf that only Yoda and the Sith Lords can interpret. If you want to return your smb.conf back to it's factory fresh state: [http://ubuntuforums.org/showpost.php?p=9505697&postcount=13](http://ubuntuforums.org/showpost.php?p=9505697&postcount=13)

Setting it back to the default state won't necessarily fix your situation but at least it will give those wishing to help you something understandable to work with.

Just a thought.

---

### Post by Willye on 2011-03-28
I have copied again the smb.conf 
cp -a /usr/share/samba/smb.conf /etc/samba/
i shared a folder in linux and windows
change the next lines in smb.conf
encrypt passwords = true 
netbios name = ubuntubox
stop smbd
start smbd
from windows i cannot see the linux and from linux neither

what other thing can i do ?

---

### Post by Morbius1 on 2011-03-28
[1] Make usere the following services are running:
```
sudo service smbd status
sudo service nmbd status

```If not running start them:
```
sudo service smbd start
sudo service nmbd start
```[2] Don't browse to the share state the location explicitly by ip address from Windows:
```
\\192.168.0.100\share-name
```[COLOR=Blue]*changing the ip address and share-name to fit your circumstance*[/COLOR]
If all that does nothing then please post the output of the following commands from the Ubuntu box:
```
smbtree
net usershare info --long
testparm -s
```

---

### Post by Willye on 2011-03-28
the output:
```



C:\Documents and Settings\Administrator>\\9.172.223.71\videos
Logon failure: unknown user name or bad password.

/etc/samba> sudo service smbd status
smbd start/running, process 25826
/etc/samba> sudo service nmbd status
nmbd start/running, process 1315
/etc/samba> smbtree
Enter root's password:
session request to 9.172.222.25 failed (Called name not present)
WORKGROUP
        \\UBUNTUBOX                     ubuntu server (Samba, Ubuntu)
                \\UBUNTUBOX\videos
                \\UBUNTUBOX\IPC$                IPC Service (ubuntu server (Samba, Ubuntu))
                \\UBUNTUBOX\print$              Printer Drivers
        \\T400-SSD
cli_start_connection: failed to connect to T400-SSD<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
        \\PC-ZUGASTI                    ES2_87473
cli_start_connection: failed to connect to PC-ZUGASTI<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
        \\L3CNC6K-6474B84
cli_start_connection: failed to connect to L3CNC6K-6474B84<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
        \\L3ALD7F-7458AU2
ES_AVAM
session request to 9.172.220.217 failed (Called name not present)
session request to *SMBSERVER failed (Not listening on called name)
session request to ES2SP82116 failed (Not listening on called name)
session request to *SMBSERVER failed (Not listening on called name)

/etc/samba>  net usershare info --long
[videos]
path=/home/y87042/Videos
comment=
usershare_acl=Everyone:F,
guest_ok=y

/etc/samba> testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        netbios name = UBUNTUBOX
        server string = %h server (Samba, Ubuntu)
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

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No
        browsable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

```

---

### Post by Morbius1 on 2011-03-28
Confused by something. Private ip addresses for use in a LAN are of the form:
10.0.X
172.16.x
192.168.x

Your's do not fall in that range. Are you attempting to access a samba share from the internet itself?
> [videos]
path=/home/y87042/Videos
comment=
usershare_acl=Everyone:F,
guest_ok=yThat's a guest accessible share so I don't understand the error message that Windows is showing you:
> C:\Documents and Settings\Administrator>\\9.172.223.71\videos
Logon failure: unknown user name or bad password.Make sure the permissions on the target folder allow "guest" access:
```
 ls -dl /home/y87042/Videos
```Should come back with: drwxrwxrwx
And it's parents:
```
ls -dl /home/y87042
ls -dl /home
```All should come back with at least: drwxr-xr-x

---

### Post by Willye on 2011-03-30
next the output requested:

/home/y87042> ls -ld Videos/
drwxrwxrwx 2 y87042 y87042 4096 2011-01-25 18:19 Videos/
/home/y87042> ls -dl /home/y87042
drwxr-xr-x 52 y87042 y87042 4096 2011-03-30 10:05 /home/y87042
/home/y87042> ls -dl /home
drwxr-xr-x 14 root root 4096 2011-03-25 13:01 /home
/home/y87042>

from  windows: 

C:\Documents and Settings\Administrator>ping 9.172.223.71

Pinging 9.172.223.71 with 32 bytes of data:

Reply from 9.172.223.71: bytes=32 time=3ms TTL=61
Reply from 9.172.223.71: bytes=32 time=2ms TTL=61
Reply from 9.172.223.71: bytes=32 time=1ms TTL=61


ipconfig:
Ethernet adapter Local Area Connection:

      
        IP Address. . . . . . . . . . . . : 9.172.132.52
        Subnet Mask . . . . . . . . . . . : 255.255.255.128
        Default Gateway . . . . . . . . . : 9.172.132.1

Ethernet adapter Wireless Network Connection:

---

### Post by Willye on 2011-03-30
any ideas ???

---

