---
title: "SAMBA Auth problem"
date: 2014-08-16
forum: Networking &amp; Wireless
---

### Post by andreas26 on 2014-08-16
Hi! After several minutes of troubleshooting (thats a joke ;)) without a solution... I'm in need of some help :)

I have two computers running Windows 8.1. Thing is, I can login to my shares without any problem. Told Windows to automount $home for each user.
Thing is, if I login with User2, and automount User2's $home in Windows, I cant access other shares, which that user does not have access to. Fair enough :) Problem is, if I do try to login with User1, which has access to a specific folder... IT WONT WORK!? So this is what I do:

Boot up Computer1, Login as User2. Auto-mount User2's $home.
Try to access \\sambaserver\disk2
Auth with User1
Fails.

Boot up Computer2, login as User1. Auto-mount User1's $home.
Try to access \\sambaserver\disk2
No auth required.
Success.


My smb.conf:
```

[global]        
        log file = /var/log/samba/log.%m
        read raw = no
        name resolve order = lmhosts host bcast
        write raw = no
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        obey pam restrictions = yes
        map to guest = bad user
        encrypt passwords = true
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        wins support = no
        dns proxy = no
        printing = bsd
        server string = %h server
        unix password sync = yes
        workgroup = WORKGROUP
        printcap name = /dev/null
        security = user
        syslog = 0
        panic action = /usr/share/samba/panic-action %d
        max log size = 1000
        pam password change = yes

[homes]
        create mask = 0700
        directory mask = 0700
        browseable = no
        writeable = yes
        valid users = %S
#       veto files = /.*/

[disk2]
        writeable = yes
        valid users = User1
        path = /disk2
        write list = User1

[media]
        public = yes
        path = /disk2/share/media
        write list = User1


```

I could of course add User2 to "valid users" for /disk2, but thats not a solution, thats a work-around :)

---

### Post by andreas26 on 2014-08-16
"Solution" was to disconnect User2's $home. After that I could login with User1... Windows, sigh. Cant handle two different credentials it seems. Funny thing, it was told in the error popup on the Windows station. I'll get back if I find a "hack" for it ;)

---

### Post by andreas26 on 2014-08-16
Found it! :) For anyone else with the same problem: [http://support.microsoft.com/kb/938120](http://support.microsoft.com/kb/938120) 
In short: I map the shared folder for User2 with the IP address. After that, I can access the other share for User1, by using the hostname instead of the IP address.

---

