---
title: "Samba stopped working after ntfs-config"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by Totooch on 2011-02-19
Hi all,
I'll try to make it short. After a while I succeeded installing Samba4 and a share manager ("Samba" in the Ubuntu Software Center) and I got it working, even if just with "user" access type. I successfully accessed my shared directory from my mobile and I saw the shared folders in the Network directory.

Then I decided I wanted every internal hdd to automount on startup, so I installed ntfs-config as I read it was the right tool I could easily use. It installed correctly from the Ubuntu Software Center but it does not start once clicked. I gave up on this as I didin't really needed that but when I restarted the system Samba stopped working!

I can still find the server from my mobile but I can't access it anymore. Moreover I can no longer share directories via the sharing options, this is the related error message:
'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Memory allocation error.

I assumed the two facts were related after reading this post:
[http://art.ubuntuforums.org/showpost.php?p=10416995&postcount=178](http://art.ubuntuforums.org/showpost.php?p=10416995&postcount=178)

How can I reassign the original directory permission, as if it was a fresh installation?

I'm using Ubuntu 10.10, 64bit version. 

Thanks a lot!!!

---

### Post by Morbius1 on 2011-02-19
You are in uncharted waters I'm afraid. From the description in synaptic concerning Samba4:
> These packages contain snapshot versions of Samba 4, the next-generation version of Samba. These should be considered _experimental_, and should not be used in production.I don't think ntfs-config is the root of the problem since you couldn't get it to  run - which BTW is a good thing.

You could post your smb.conf by posting the output of the following command:
```
testparm -s
```It would be interesting to see if the "testparm" command still works in Samba4 and what kind of default smb.conf exists.

---

### Post by Totooch on 2011-02-19
Thanks for the quick reply, for some strange reason it works again! I did not use my pc the whole day...strange indeed!

I still need some help: I can't make it work in share mode, so that every device connected to the same wi-fi does not need username and password to access the server, any hints?

The command works ;) here are the results:

```
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
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

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[media]
    path = /media
    valid users = totooch
    read only = No

```

Thanks a lot!
Salvo

---

### Post by Morbius1 on 2011-02-19
I don't think I've ever seen anyone share /media before. Um ......

Let's take an exapmple of an external USB device formatted to NTFS. When it mounts it will mount with totooch as owner and permissions of 700. So you can do anything you want to it but nobody else can - including anyone on the network.

Having a "valid user" option in the share definition will work but then everyone has to login as you so change it to this:
> [media]
    path = /media
    **[COLOR=Blue]#[/COLOR]**valid users = totooch
    read only = No
[COLOR=Blue][B]guest ok = yes
force user = totooch[/B][/COLOR]I commented out the valid users line just in case you want to go back to it. The "guest ok" will allow guests to access the share without authentication and "force user" will convert all users to you. So if you can access it from your local machine everyone else should also.

---

