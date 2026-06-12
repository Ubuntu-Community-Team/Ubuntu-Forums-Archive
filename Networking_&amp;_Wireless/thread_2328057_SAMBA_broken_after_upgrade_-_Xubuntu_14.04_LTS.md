---
title: "SAMBA broken after upgrade - Xubuntu 14.04 LTS"
date: 2016-06-16
forum: Networking &amp; Wireless
---

### Post by toddk63 on 2016-06-16
My SAMBA broke (Win 7 client can't see Linux shares) after a normal upgrade of Xubuntu 14.04. I have a stable version image before the upgrade that I can go back to.  I have put off the upgrade for a few months hoping the problem would resolve itself with new upgrades, but so far no luck.  The working SAMBA is 4.1.6 and it is being updated to 4.3.9 which does not work.  It seems that the new smb.conf is not loading.

 Here is the testparm of it:

------------------------------------------
:/etc/samba$ testparm -s smb.conf
Load smb config files from smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
WARNING: Ignoring invalid value 'server' for parameter 'security'
Error loading services.
--------------------------------------------

Here is the testparm of the original smb.conf that works

-----------------------------------------
:/etc/samba$ testparm -s smb.conf
Load smb config files from smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: Ignoring invalid value 'server' for parameter 'security'
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Share-A]"
Processing section "[Share-B]"
Processing section "[Share-C]"
Processing section "[Share-D]"
Loaded services file OK.
Server role: ROLE_STANDALONE
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
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Share-A]
    path = /mnt/Share-A
    valid users = User1, User2, User3
    read only = No

[Share-B]
    path = /mnt/Share-B
    valid users = User1, User2, User3
    read only = No

[Share-C]
    path = /mnt/Share-C
    valid users = User1, User2, User3
    read only = No

[Share-D]
    path = /mnt/Share-D
    valid users = User1, User2, User3
    read only = No
-------------------------------------------

What else do you need to help me?  Any ideas?

Thanks,

Todd K.

---

### Post by drifting on 2016-06-17
> **toddk63 said:**
> My SAMBA broke (Win 7 client can't see Linux shares) after a normal upgrade of Xubuntu 14.04. I have a stable version image before the upgrade that I can go back to.  I have put off the upgrade for a few months hoping the problem would resolve itself with new upgrades, but so far no luck.  The working SAMBA is 4.1.6 and it is being updated to 4.3.9 which does not work.  It seems that the new smb.conf is not loading.

 Todd K.

Truncated for clarity.


Same Problem, although the only difference is mine has a problem with Share security. Sorry for the me too, but this way it allows me to follow your thread. Have read up a few other threads and changed the share to user. What happens when you do a testparm -s   ? Does it throw any problems up? Mine actually does not, yet still cannot connect as it asks for username and password? Which don't work.

Regards D

---

### Post by Morbius1 on 2016-06-17
There is no such thing as "security = server"

Edit /etc/samba/smb.conf, find the line, and delete it. Then restart smbd:
```
 sudo service smbd restart
```

---

### Post by drifting on 2016-06-17
Not wishing to highjack Todds post, but that did not work for me.
Seem to have lost permissions? as the share shows, but cannot access them, says the username and password are wrong, which they are not?
Wished I understood this better :-(

---

### Post by Morbius1 on 2016-06-17
It didn't work for you because you have a different issue. If you want me to guess it would be that you didn't add your users to the samba password database:
```
sudo smbpasswd -a user-name
```
Anything other than legitimate security values in "security = " now results in samba stopping the process. Before it simply ignored it and set it to the default because it assumed the user was inebriated or using system-config-samba.

---

### Post by toddk63 on 2016-06-17
> **Morbius1 said:**
> 
Anything other than legitimate security values in "security = " now results in samba stopping the process. Before it simply ignored it and set it to the default because it assumed the user was inebriated or using system-config-samba.

Wow!  That confirms my suspicion.  I thought I had read sumat about "security" behaviour in the upgraded version.

<it assumed the user was inebriated or using system-config-samba>
The later is certainly true and the former, quite possibly.

I will try it when I get off work tonite.

Thanks,

Todd K.

---

### Post by toddk63 on 2016-06-17
> **Morbius1 said:**
> 
Anything other than legitimate security values in "security = " now results in samba stopping the process. Before it simply ignored it and set it to the default because it assumed the user was inebriated or using system-config-samba.

Yup, that did it!.  Commented out the "security = server" line and all is well.

Thanks for the quick turnaround,

Todd K.

---

