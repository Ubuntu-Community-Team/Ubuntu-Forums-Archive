---
title: "samba network problem"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by arju305 on 2010-10-24
Guys i cannot access my ubuntu shared file from windows 7 machine. but accessing 7 from ubuntu is possible.

 I am having a problem with samba.
firstly i installed it :
$sudo apt-get install samba
$sudo apt-get install system-config-samba
then i restarted the server.
from administrator-> samba i customized it for access to every one.
I found that.
from my ubuntu, I could access windows 7
but from windows 7 I cannot access ubuntu.
need your help.
Thanking you in advance.
*************************************

arjan@arjan-MS-7514:~$ testparm -sp
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[Myshare]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Pictures]"
Processing section "[Downloads]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = Ubuntu Server
    security = SHARE
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

[Myshare]
    comment = Myshare
    path = /myshare
    read only = No
    guest ok = Yes

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Pictures]
    path = /home/arjan/Pictures
    read only = No
    guest ok = Yes

[Downloads]
    path = /home/arjan/Downloads
    read only = No
    guest ok = Yes



**************************************************  ******************
[music]
path=/home/arjan/Music
comment=
usershare_acl=Everyone:F,
guest_ok=y

[sharing]
path=/home/arjan/Pictures/sharing
comment=
usershare_acl=Everyone:F,
guest_ok=y
*****************************************

Thanking you in advance.

---

### Post by luvshines on 2010-10-24
So you are able to start your own thread, Congrats !! :lolflag:

Have you tried accessing your Ubuntu shares from the Ubuntu machine itself (through nautilus) ??

Also make sure no firewall rules on Ubuntu are blocking the required ports
```
sudo ufw status
sudo iptables -L

```

Also, for Windows 7, people generally set this in local policies, security options
```
Network security: LAN Manager authentication level 
Send LM & NTLM responses 

Minimum session security for NTLM SSP 
Disable Require 128-bit encryption 
```

---

### Post by arju305 on 2010-10-24
> **luvshines said:**
> So you are able to start your own thread, Congrats !! :lolflag:

Have you tried accessing your Ubuntu shares from the Ubuntu machine itself (through nautilus) ??

Also make sure no firewall rules on Ubuntu are blocking the required ports
```
sudo ufw status
sudo iptables -L

```Also, for Windows 7, people generally set this in local policies, security options
```
Network security: LAN Manager authentication level 
Send LM & NTLM responses 

Minimum session security for NTLM SSP 
Disable Require 128-bit encryption 
```


arjan@arjan-MS-7514:~$ sudo ufw status
[sudo] password for arjan: 
Status: inactive
*************************
arjan@arjan-MS-7514:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
****************************************
arjan@arjan-MS-7514:~$ smbtree
Enter arjan's password: 
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
*******************************************

when ever i share a file in ubuntu.... it will be seen my windows 7....... it shows the directory of the shared folder and when ever i double click it.....
it gives an error ->
windows cannot access \\arjan\music
check the spelling of the name.......

waiting for you reply...........
(and yes. i now know how to start a thread...ehhe)

---

### Post by luvshines on 2010-10-24
I would suggest change the security parameter in smb.conf to default:
```
security = user
## Then restart the server and give it a try
sudo service smbd restart

```

---

### Post by arju305 on 2010-10-24
> **luvshines said:**
> I would suggest change the security parameter in smb.conf to default:
```
security = user
## Then restart the server and give it a try
sudo service smbd restart

```
It didnt work.
Even nautilus cannot open the shared file in ubuntu machine.
Unable to mount location. 
failed to mount windows share
Waiting for your valuable reply............

---

### Post by arju305 on 2010-10-24
> **arju305 said:**
> It didnt work.
Even nautilus cannot open the shared file in ubuntu machine.
Unable to mount location. 
failed to mount windows share
Waiting for your valuable reply............

hi luvshines.....
I am not understanding the problem.
If i create a folder outside home and share it by modifying smb.conf file.... then my windows machine can recognize it and access it.
But if i create it inside home then it will be recognized but not accessed.

---

### Post by luvshines on 2010-10-25
> **arju305 said:**
> hi luvshines.....
I am not understanding the problem.
If i create a folder outside home and share it by modifying smb.conf file.... then my windows machine can recognize it and access it.
But if i create it inside home then it will be recognized but not accessed.

When you create a folder in home, which user are you using to connect to the share ?
Assuming that /home/arjan is being owned by arjan user, if you use any other user to connect to the share(guest included), make sure that each of the directory in the shared paths is having a permission of 0755 atleast

---

### Post by d3v1150m471c on 2010-10-25
my /etc/samba/smb.conf additions:
```

[Music]
comment = Shared Music
path = /home/d3v11/Music
read only = yes
available = yes
browseable = yes
public = yes
writable = no
guest ok = yes


[Downloads]
comment = Shared Downloads
path = /home/d3v11/Downloads
read only = yes
available = yes
browseable = yes
public = yes
writable = no
guest ok = yes

```my samba works fine with these settings. check the permissions "apply to enclosed folders" when altered.

you may also need to install nautilus-share
```

sudo apt-get nautilus-share

```

---

