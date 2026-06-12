---
title: "Samba Issues"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by li_diver on 2011-02-27
A few weeks ago I created a share, and was able to get my Windows workstation to connect to it.  Last weekend, it stopped working.  I know that I let Ubuntu install some software upgrades. but I didn't see any that should impact this.

I can ping my Ws from my laptop and vice-versa, but when I try to connect from windows it won't connect.  It acts as though I had typed an incorrect password, but I am certain I didn't.  I hope someone can give me some ideas on how to resolve this. 

I am using Ubuntu 10.10.  The Windows laptop is running XP.

---

### Post by Jogga484 on 2011-02-27
Have you enabled a firewall on the Ubuntu machine? 

[INDENT] *"[I] The module for netbios-ns (UDP port 137) is not loaded by default. You must turn it on for Samba to penetrate the ufw firewall"*[/I]
[/INDENT] 
If this is not the case, perhaps a Windows update has changed your security settings?

---

### Post by li_diver on 2011-02-27
No, If firewall is not enabled by default, I did not enable it (although, I guess I should).  Highly unlikely it has anything to do with Windows settings.  I don't even have auto updates turned on on that machine.

---

### Post by Morbius1 on 2011-02-27
Please post the output of the following commands:
```
net usershare info --long
```
```
testparm -s
```

---

### Post by li_diver on 2011-02-27
Interesting.  The command output is:

net usershare info --long

info_fn: file /var/lib/samba/usershares/l is not a well formed usershare file.
info_fn: Error was Path is not a directory.

Actually, I am sharing my Windows (this machine dual boots) drive, and the share is set up as the entire drive.

root@RJAWS:/home/rich# testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[l]"
Loaded services file OK.
Server role: ROLE_STANDALONE
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

[l]
    path = /media/FantomHD
    valid users = rich
    browseable = No

Does this help?

---

### Post by Morbius1 on 2011-02-27
There's a couple of issues here.

There are two ways to use samba to share folders and you are using both methods apparently at the same time on the same target folder.

This is a Samba Classic-share:
> [l]
    path = /media/FantomHD
    valid users = rich
    browseable = NoBut you also have an error message from the other method called Usershare or Nautilus-share:
> info_fn: file /var/lib/samba/usershares/l is not a well formed usershare file.
info_fn: Error was Path is not a directory.That error implies that the target directory does not exist. Did you try to share /media/FantomHD through nautilus? If so it would appear that FantomHD is not mounted.

I'm a big fan of Nautilus-share but in this case I would get rid of the share. You can go into Nautilus and right-click > Sharing Options on that folder and just "unshare" it.

That will leave you with the Classic share and you may have a problem with the "valid users = rich" line depending on how you set up the password because of a package that ubuntu slipped into the latest install named: libpam-smbpass. 

If you created an smbpasswd for rich that does not match your login password ( BTW, this is what every user should do - you don't want an smbpasswd = login password ) libpam-smbpass will override the smbpasswd with the login password.

If this is the case then you have two choices:
- Login into the remote share with rich's login password.
- Remove libpam-smbpass:
```
sudo apt-get remove libpam-smbpass
```I remove it on my own system since I can't figure out any circumstance where that would be a desirable feature.

---

### Post by li_diver on 2011-03-01
Thanks Morbius, That gives me something to start with at least.  I am away from my system right now, and won't be able to try anything until Friday, but I will look into it then.
 
I believe I do have 2 different shares of the same thing, at one point the share justseemed to "unshare"  itself, so I think I tried both ways.
 
I think your second point may be the issue, though, since everything did work until the last upgrade, altthough, I was using my login password as my share password, so if I'm reading that right it should still have worked.  In any case, I will try removing that package and see what happens.
 
Thanks again.

---

