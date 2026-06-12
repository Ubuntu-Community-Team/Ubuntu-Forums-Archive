---
title: "Problem with vista and samba"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by aprillia99 on 2009-12-21
Ok ive checked all over and read tons of how to and followed step by step, and ive started over many times so this is where im at now.

I've installed samba and shared a folder in "my pictures" changed the workgroup to match my vista machine (using just workgroup) and jut from doing that i should be able to see it and acess the file on my windows machine from what ive read. I getting a error message and here is a screen shot of it      [http://tinypic.com/r/iw3h3q/6](http://tinypic.com/r/iw3h3q/6)

The blank desktop u see there is my ubuntu machine i belive but i get that error when i try to open it and ive tried mapping a network drive to it too but gotten a error as well

Anyone have any insight on my problem plz help and thx in advance :)

---

### Post by holastickboy on 2009-12-21
I recall seeing somewhere that it might have something to do with encryption of passwords and the way that Vista and Windows 7 handles them.  Could this be the problem?

---

### Post by aprillia99 on 2009-12-22
ive read about that and have changed what they said to change and still got the error, so from what ive tried, it did nothing anyone else have any ideas?

---

### Post by aprillia99 on 2009-12-22
Anyone have anymore ideas?

---

### Post by oldfred on 2009-12-22
In XP it was my firewall. Can you ping from each machine to the other?

---

### Post by Morbius1 on 2009-12-22
May we have some more information. Please post the output of the following commands:

Open **Terminal**
Type **net usershare info**
Type **sudo net usershare info**
Type [B]testparm -s

[/B]Also, does your Ubuntu box have a name?

---

### Post by aprillia99 on 2009-12-22
Ok ill post that info in about 5 min or so i just reinstalled samab and gonna try again and ill post the info for u 

ty

---

### Post by aprillia99 on 2009-12-22
Ok this is what i git from typing that info




kyle@kyle-Server-Ubuntu:~$ net usershare info
[hand]
path=/home/kyle/Pictures/hand
comment=
usershare_acl=Everyone:F
guest_ok=y

kyle@kyle-Server-Ubuntu:~$ sudo netshare info
sudo: netshare: command not found
kyle@kyle-Server-Ubuntu:~$ sudo net usershare info
kyle@kyle-Server-Ubuntu:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    passdb backend = tdbsam
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    invalid users = root

[homes]
    comment = Home Directories
    valid users = %S
    read only = No

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

---

### Post by aprillia99 on 2009-12-22
and yes i can ping from both machines... :-\

---

### Post by Morbius1 on 2009-12-22
I do believe that host name is too long. Has to be less than 15 characters for windows to be happy. I always thought Windows would truncate it but maybe not. By default if the netbios name is not specified in smb.conf samba will use the hostname.

Rather than change the host name ( which is difficult in Ubuntu and I always have to refer to my notes) try adding a netbios name to smb.conf:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

In the [COLOR=RoyalBlue][global][/COLOR] section add the following two lines:

[B]netbios name = kyle-server
force user = kyle[/B]

[COLOR=RoyalBlue]You can change kyle-server to something else, just keep it under 15 characters. The second line has nothing to do with this name length but I think part of your problem may be linux file permissions.[/COLOR]

Save the file and exit gedit.
Back in the terminal issue a **sudo service samba restart**

Wait a few minutes, and try to access the server again.

---

### Post by aprillia99 on 2009-12-22
u know i have spent over 12 hours tring all sorts of different parameter and aps and it was al because i was 3 letter to long and windows didnt like it, im about ready to jump off a bridge...  lol but thanks alot my friend :)

---

### Post by Morbius1 on 2009-12-22
Glad it worked. Somebody needs to write down all these rules :lol:

---

