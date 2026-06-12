---
title: "Ubuntu share strange on Windows"
date: 2020-11-08
forum: Networking &amp; Wireless
---

### Post by bearnie78 on 2020-11-08
[COLOR=#333333][FONT=UbuntuBeta]Hi all!

First things first, sorry for my english! :)

Maybe it's a lame question, but i'm new in the world of penguin, and I've been fighting it for three days.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuBeta]I have two PC.
On the first have Ubuntu 20.10 + KDE. Inside have some HDD mounted at /media.
In the Dolphin I shared them with Samba.
On the Ubuntu have two user. one for the ubuntu usage, and one for the Win share.
The Ubuntu main user's Home is also shared with the same method.
All two user have full permissions to all shared directories.
The second PC is Win10, where I would like to map them as network drives.
If I do it with the Win share username and password, the Win PC reach the Ubuntu user's Home directory, but just can read it.
And the other HDD-s just mapped, but can't open it.
If I do the same with the Ubuntu user's username and password, the Win PC can reach every folder and have full permission on them.
In the Dolphin I can't do more accurate the settings.
And in the smb.conf don't have the users and share points neither.
The Dolphin-samba and the "Samba"-samba is two diferent samba?

Thank in advance![/FONT][/COLOR]
[CENTER][COLOR=#333333][FONT=UbuntuBeta][/FONT][/COLOR][/CENTER]

---

### Post by Morbius1 on 2020-11-08
What would help is for you to post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by bearnie78 on 2020-11-09
[FONT=monospace]Here are the outputs:
testparm -s
```
[COLOR=#54FF54][B]
nas@BEARNIE-NAS[/B][/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ testparm -s[/COLOR]
Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]
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
        unix password sync = Yes
        usershare allow guests = Yes
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
[COLOR=#54FF54]**nas@BEARNIE-NAS**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$
[/COLOR]
```[COLOR=#000000]
[/COLOR]
net usershare info --long

[/FONT]```

[FONT=monospace][COLOR=#54FF54]**nas@BEARNIE-NAS**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ net usershare info --long[/COLOR]
[Movies]
path=/media/nas/Movies
comment=
usershare_acl=Everyone:R,Unix User\nas:F,
guest_ok=n

[Seeder]
path=/media/nas/Seeder
comment=
usershare_acl=Everyone:R,Unix User\nas:F,
guest_ok=n

[COLOR=#54FF54]**nas@BEARNIE-NAS**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ 
[/COLOR][/FONT]
```[FONT=monospace][COLOR=#000000]
[/COLOR]
I didn't known the last command.
Is it means the Dolphin made the shared folders data to an another place, not to the smb.conf?[/FONT]

---

### Post by Morbius1 on 2020-11-09
In order for any user to get to a folder - either locally or across the network - it has to go through the path to that folder. /media/nas blocks everyone from getting to the Movies and Seeder folders except "nas".

One way out of this is to make every network user appear to be "nas". You can do that in smb.conf by adding a line - right under the **workgroup = WORKGROUP** line that looks like this:
```
force user = nas
```
Then restart smbd:
```
sudo service smbd restart
```

The share definition will still restrict who can access the share but once samba lets them in everything they do will be as the user "nas"

> [FONT=monospace] Is it means the Dolphin made the shared folders data to an another place, not to the smb.conf?[/FONT]         

There are two ways to create a samba share. One is a Classic Share and that is done in smb.conf. The other is a Samba Usershare and that is normally done through the file manager. They are both samba shares but their share definitions are in different places.

---

