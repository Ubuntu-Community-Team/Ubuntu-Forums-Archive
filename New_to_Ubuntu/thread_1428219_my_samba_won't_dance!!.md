---
title: "my samba won't dance!!"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-03-12
I can't get samba to play nice with my moms computer which has the server on it.  I've been away for awhile (prison sucks)  In the past I had done and I had dolphin going to as a file browser. I download samba last nite and it was seeing the shares though i couldn't access them.  Now today I came in after parole (yeah i just sit in my house all day now) i couldn't even see what i saw last nite which wasn't much but i could at least see the icon when i went to places >> network.  I was wondering though she's running vista home premium on that desktop (yeah i know it sucks) do i need to put samba on that to get it to work? anyways i putting in the output of the testparm command from the shell to try and give a little more info. any advice is welcome at this point.  Oh yeah i don't know how to ping her computer i mean i know the ping command but i don't know why it won't work.  (the scan keeps timing out and i'm using the address that the router is saying is hers.

brad@brad-laptop:~$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

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
brad@brad-laptop:~$

---

### Post by bradmayne04 on 2010-03-14
i got it!!

sudo apt-get install winbind

good to go!!

---

