---
title: "user permissions not working - must be a config error"
date: 2016-08-21
forum: Networking &amp; Wireless
---

### Post by kenz71 on 2016-08-21
Maybe I am making this more complicated than it needs to be - I suppose that can be said often for security.

Anyway - I have a series of directories that I can browse from the command line using Putty but using the same user ids from a Win10 box I can't access the same shares via Samba.  What am I doing wrong?

Here is the directory on the Ubuntu Server:
```

drwxrwxr-x 201 jenny g-dlna   204 Jul 16 10:14 Music
drwxrwx---   9 jenny g-adults  34 Jul 19 15:05 OurDocs
drwxrwx---   2 ken   g-adults   3 Aug 21 22:23 Test

```

When trying to browse the shares from Windows 10 useing either user name jenny or ken I get an error indicating "you don' t have permission to access \\UBUNTUSRV\Test"

If I chmod 777 the directory then the shares work - what the freak??? Is group permissions not working in Samba?

What I am running:
Samba version 4.3.9-Ubuntu for the server

Windows 10 on the client

It's got to be error 12 (12 inches from my screen i.e. user error!!)

---

### Post by TheFu on 2016-08-22
Samba doesn't usually care about Unix permissions. It runs as root, so access controls to files and directories are completely under the control of samba. There is a way to convince userids between Unix and Windows to become equated. I've never seen that used in the real world, but suspect lots of other people do use it.

So ... if you want more help, please post the output from **testparm**.  And thnks for using code tags - that helps a bunch.

BTW, I don't have any Win10 here, so if there is anything funny about that OS related to network sharing, it will be impossible for me to help.

Also - there is perhaps 0.0000000001% good reasons to ever use 777. In short, don't. Ever.  I can actually think of good reasons to use 707, but not 777. ;)

---

### Post by kenz71 on 2016-08-22
testparm results:

```



*** System restart required ***
Last login: Mon Aug 22 20:24:47 2016 from 192.168.1.55
ken@ubuntusrv:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Music]"
Processing section "[OurDocs]"
Processing section "[Test]"
Loaded services file OK.
Server role: ROLE_STANDALONE


Press enter to see a dump of your service definitions


# Global parameters
[global]
        server string = %h server (Samba, Ubuntu)
        server role = standalone server
        security = USER
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
        browseable = No



[Music]
        comment = Music
        path = /mnt/Tank/Music
        read only = No
        create mask = 0755




[OurDocs]
        comment = OurDocs
        path = /mnt/Tank/OurDocs
        admin users = @g-adults
        read only = No
        create mask = 0755




[Test]
        comment = Test
        path = /mnt/Tank/Test
        read only = No
        create mask = 0755
        guest ok = Yes



```



This scheme worked under NAS4Free's FreeBSD with a samba share. Of course that is a different flavor of 'nix.

Any thoughts or comments most welcome.

---

### Post by kenz71 on 2016-08-23
Googled for a few more hours and found the fix.

had to set the user passwords for samba via
```

sudo smbpasswd -a ken
```

So despite the documentation here [https://help.ubuntu.com/lts/serverguide/samba-fileprint-security.html#samba-user-security](https://help.ubuntu.com/lts/serverguide/samba-fileprint-security.html#samba-user-security) indicating, or how I interpreted at least, that the UNIX passwords will copy to Samba. Grrrrrr... but it now works

```

[COLOR=#333333][FONT=Ubuntu][h=2]Security = User[/h][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit][FONT=inherit]This section will reconfigure the Samba file and print server, from [File Server]("https://help.ubuntu.com/lts/serverguide/samba-fileserver.html") and [Print Server]("https://help.ubuntu.com/lts/serverguide/samba-printserver.html"), to require authentication.[/FONT]
[FONT=inherit]First, install the [FONT=inherit]*libpam-winbind*[/FONT] package which will sync the system users to the Samba user database:[/FONT]
[/FONT]
[/FONT][/COLOR]

```


So I relearned the important lesson - when it don't work RTFM. Still don't work, read ANOTHER Freaking Manual, still don't work have an adult beverage and try again after reading yet another Freaking Manual.

---

### Post by sudodus on 2016-08-23
Ask for membership of the team ***Ubuntu Wiki Editors*** [https://launchpad.net/~ubuntu-wiki-editors](https://launchpad.net/~ubuntu-wiki-editors) and you can edit the page [samba-user-security](https://help.ubuntu.com/lts/serverguide/samba-fileprint-security.html#samba-user-security) to include your experience. Alongside your description it would be good to add a link to the web site that helped you find the solution.

-o-

You can refer to me, and tell them what you want to do, when they ask why you want to be a member.

---

### Post by TheFu on 2016-08-23
There have been many times I wanted to modify the wiki, but the barrier to make changes seemed too high.

I've always had to set the userid+password initially for samba users, but it has been a long time since setting up any new users/samba and didn't know if that was still the situation.

Before seeing this as solved, I was thinking the "USER" vs "User" could be it. Never know when case will matter. Unix is case sensitive and mainly Windows-users forget that.

---

### Post by kenz71 on 2016-08-23
So does this mean if someone changes their password it will or WILL NOT be in sync between client, file system and Samba?

I'll have to test it out.  Also sounds like a good reason to setup Samba as a domain controller.  Although I tend to tinker with my server so that sometimes might prevent others from getting to their stuff - that would be "crossing the streams level bad" as they said in the *Original* Ghostbusters.

I'll do more research on domain controllers.

Also will work on editing the Ubuntu Wiki - thanks for the invite!

---

