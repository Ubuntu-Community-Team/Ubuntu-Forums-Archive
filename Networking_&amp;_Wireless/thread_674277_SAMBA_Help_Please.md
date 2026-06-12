---
title: "SAMBA Help Please"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by BrentC on 2008-01-21
I've tried reading through the documentation, but 99% of it seems like it was written for people who already understand and mastered SAMBA.

Anyways, I have my SAMBA server setup with a working username that Windows XP can log into. My problem is as follows; the permissions for the folder I log into are not set properly. I tried setting the permissions to anything you can think of, even 777. Still a no-go. Any help would be extremely appreciated.

Here is my smb.conf:

```
[global]
        workgroup = HOME
	netbios name = SAMBA
        server string = Samba Server
        security = USER
        encrypt passwords = Yes
        log file = /var/log/samba/%m.log
        max log size = 0
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
        load printers = No
        os level = 65
        preferred master = True
        domain master = No
        dns proxy = No
        wins support = Yes
        hosts allow = 192.168.1. 127.
        printing = lprng

[data]
        comment = Stuff
        path = /home/samba
	valid users = brent
        read only = No
        create mask = 0777
        directory mask = 0777
        dos filemode = Yes
[homes]
	comment = Home Directories
	browseable = no
	writeable = yes
	create mask = 750
	directory mask = 750
```

EDIT: Here is the problem on the Windows client side; [http://img301.imageshack.us/img301/471/permissionsml2.jpg](http://img301.imageshack.us/img301/471/permissionsml2.jpg)

---

### Post by sujoy on 2008-01-21
you need to set 

browseable = yes

it is under [homes].................. that should do the work

---

### Post by BrentC on 2008-01-21
Nope, same problem as before except with \\Samba\home. I can't access the directory(ies) at all. Even with them set a 777.

EDIT: Let me further explain. I can access my directories now on the SAMBA server from the Windows client. I have no permission to write to the directory however. Even after setting the directory to 0777.

---

### Post by davemcl on 2008-01-21
I had been having the same problem as you and then went back and read that once you modify smb.conf it's a good idea to run testparm from a terminal while in that directory.  That showed me what was going to happen and when I pressed ENTER as instructed at the end of the listing it showed me that I had NOT set the parameter for read only correctly.  You might try that and good luck.  I'm only 1/3 of a page in the book ahead of you...

---

### Post by burbankmarc on 2008-01-21
whenever I have an issue like this it's due to not adding a smb password for the user via smbpasswd.

---

### Post by jonandrews on 2008-01-22
Have a look at the method I use to configure SAMBA in this Windows / Ubuntu networking guide:

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by BrentC on 2008-01-23
> **burbankmarc said:**
> whenever I have an issue like this it's due to not adding a smb password for the user via smbpasswd.
100% sure I have a correct user account and password set because I can connect to the SAMBA network with that said user and account on my Windows client.
> **jonandrews said:**
> Have a look at the method I use to configure SAMBA in this Windows / Ubuntu networking guide:

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)
I actually tried your guide first thing before I started modifying my smb.conf when I saw it in a thread, but I got this error:
"error accessing file:///*filepath/directoryhere*: Access denied."

This is when I realized I had to start manually editing the directory permissions myself because Nautilus obviously wasn't putting me in superuser mode even after entering my password to do so.
> **davemcl said:**
> I had been having the same problem as you and then went back and read that once you modify smb.conf it's a good idea to run testparm from a terminal while in that directory.  That showed me what was going to happen and when I pressed ENTER as instructed at the end of the listing it showed me that I had NOT set the parameter for read only correctly.  You might try that and good luck.  I'm only 1/3 of a page in the book ahead of you...
I'll double check everything tomorrow morning. I made sure to do this on the directories I planned to share on the server to the client and everything seemed to be in working order. As they say though, it never hurts to look twice. ;)

---

### Post by RawMustard on 2008-01-23
Did you try encrypt passwords = No   ?

---

