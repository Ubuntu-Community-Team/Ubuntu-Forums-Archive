---
title: "problem with file sharing"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by s1wood on 2010-08-23
I now have Lucid Lynx running on my desktop and on my netbook and want to share files between them. I have gone through the terminal: 'shares-admin' and installed the services on my netbook and, with some difficulty, on my desktop. When I try to share a folder on the desktop I get this message:

'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running.

I have no idea where the "Everyone" comes from. How do I find out whether smbd is running?

Oh, and why is there no 'Shared files' icon in my System>Administration as I am told there should be? 

Any help would be appreciated.

Susan

---

### Post by Morbius1 on 2010-08-23
shares-admin no longer works.

You need the following package to create Samba Classic-shares:
```
system-config-samba
```
It should show up under System > Administration > Samba

---

### Post by egalvan on 2010-08-23
Simple Sharing should be workable...

 Post the output of these commands so we can see what method you are using and how you are using it:

Code:
 ```
 sudo net usershare info
  testparm -s

```


note...
Simple Sharing is as simple as right-clicking the folder you want to share and choosing "share options".

---

### Post by Confucius! on 2010-08-23
You will need to have samba and smbfs installed on both.
 
sudo apt-get install smbfs samba

---

### Post by s1wood on 2010-08-23
this is the response to the 'testparm -s' command

>Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
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
    path = /var/lib/samba/printers<

Hope it means something to you!

Susan

---

### Post by Morbius1 on 2010-08-23
Yep, that's the default smb.conf.

You've gotten a lot of responses here unfortunately they are all over the map. There are two completly different ways to create samba shares:

Nautilus-share: Nautilus > right-click a folder > Sharing Options
Classic-share: that's where ***system-config-samba ***is needed.

It's best not to use both methods at the same time. What method of sharing are you trying to use?

---

### Post by s1wood on 2010-08-23
I took the advice of Confucius and installed smfbs & samba on both machines. The netbook will now detect and read the desktop but not the other way round.

Susan
PS I have also found the shared folders file on the netbook.

---

### Post by s1wood on 2010-08-23
>What method of sharing are you trying to use?<

*I wish I knew!*

Anything that works, please. Preferably the simplest method that will work on both computers.

Susan

---

### Post by Morbius1 on 2010-08-23
Well you either used Nautilus or you used Samba from the menu but ....

Let's try it this way:
From the netbook, open a terminal and post the output of the following commands:

```
net usershare info
```[COLOR=Blue]*Note: there is no sudo in front of the net usershare info*[/COLOR]
```
testparm -s
```

[COLOR=Blue]EDIT: I reread your #7 post - including the "PS" - does that mean the issue is solved?[/COLOR]

---

### Post by s1wood on 2010-08-23
It is not quite solved till I can get the desktop - which is my main computer - to read the netbook (and the old Windows computer - which the netbook is doing).

So, this is what the desktop has to say

>susan@Carrera:~$ net usershare info
[brumaire]
path=/home/susan/BIOGRAPHY/Brumaire
comment=
usershare_acl=Everyone:F,
guest_ok=n

[nc current]
path=/home/susan/Documents/NC current
comment=
usershare_acl=Everyone:F,
guest_ok=n

info_fn: file /var/lib/samba/usershares/yr3  is not a well formed usershare file.
info_fn: Error was Path is not a directory.
susan@Carrera:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
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
susan@Carrera:~$ <

'Brumaire' and 'NC current' are the 2 folders I selected to share. 

Is this any help?

Susan

---

### Post by Morbius1 on 2010-08-23
> [brumaire]
 path=/home/susan/BIOGRAPHY/Brumaire
 comment=
 usershare_acl=Everyone:F,
[COLOR=Blue] guest_ok=n[/COLOR]
 
 [nc current]
 path=/home/susan/Documents/NC current
 comment=
 usershare_acl=Everyone:F,
 [COLOR=Blue]guest_ok=n[/COLOR]Just in case you want to know you're using Nautilus-share and the way you have them set up it's requiring a username and password to gain access.

Is this what you wanted or would you like it so anyone on the home network can have access?

If you want authentication you need to create users and passwords on the netbook corresponding to the remote users.

---

### Post by Morbius1 on 2010-08-23
Sorry misread your post again.
> It is not quite solved till I can get the desktop - which is my main  computer - to read the netbook (and the old Windows computer - which the  netbook is doing). ...So, this is what the desktop has to say Why are you showing me the desktop shares when the problem is the netbook shares. I asked for the output from the netbook. And where is this windows computer you're taking about?

This is a very confusing thread.

---

