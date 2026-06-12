---
title: "Samba configure access rights"
date: 2015-12-30
forum: Networking &amp; Wireless
---

### Post by May_Masters on 2015-12-30
Hi all

I've setup a Samba Server ho host my Fotos and Vids. I've no problems accessing it via Win7, but now I want to attach my new Ubuntu box to it.
 The users I use on the servers do not exist within the Ubuntu System and shall never do.

So currently I'm mounting the CIFS share with "root" through the fstab.
But doing so, only root can save, delete move or rename any files. Not the "standard" users

So what I want is: All files should be treated a the server-user that runs the SMB process. 
When the share gets mounted you can copy, delete or move any file you like - like I can do with Windows atm.

Is it enough to disable the "Unix Extensions" on the server ?

---

### Post by bab1 on 2015-12-30
> **May_Masters said:**
> Hi all

I've setup a Samba Server ho host my Fotos and Vids. I've no problems accessing it via Win7, but now I want to attach my new Ubuntu box to it.

The users I use on the servers do not exist within the Ubuntu System and shall never do.

If I understand you correctly; you are saying that the user authenticated on the client does not exist on the server or as a Samba user.  If this is so, then the user is allowed access if the "map to guest = bad user" parameter is set.  The bad user is typically set to the user ***nobody*** and the primary group is ***nogroup***.  In addition the share has to be configured for guest access (e.g  guest ok = yes). > 

So currently I'm mounting the CIFS share with "root" through the fstab.
But doing so, only root can save, delete move or rename any files. Not the "standard" users

So what I want is: All files should be treated a the server-user that runs the SMB process.
[QUOTE]That would be the root user.  Looking at ps -ef we can see that```

[COLOR="#FF0000"]UID[/COLOR]        PID  PPID  C STIME TTY          TIME CMD
[COLOR="#FF0000"]root [/COLOR]      642     1  0 13:34 ?        00:00:00 smbd -F
[COLOR="#FF0000"]root[/COLOR]       668   642  0 13:34 ?        00:00:00 smbd -F

``` 

When the share gets mounted you can copy, delete or move any file you like - like I can do with Windows atm.
[/QUOTE]
You need to set the user/group ownership and permissions correctly.
> 

Is it enough to disable the "Unix Extensions" on the server ?
I can't see how that is relevant at this point.

In the end you will either have to set up the shares for guest sharing and live with the insecurities that come with that or add Linux users and Samba users so they can authenticate to the share.  The Samba client does not work exactly like the Windows client when accessing the Samba server.

---

### Post by Elishasmantle on 2015-12-31
Hello,

I tried all kinds of various articles and found these principles to be true:
The simpler and more global the easier to set-up and maintain as suggested above by Bab1.
Windows, MAC, Unix, Linux are all set-up differently and especially MS Windows and its type of Authentication.
So- Using Authentication on both the Linux side and Windows side in my noob experience was a very frustrating experience.

I used this article and it was working within 30 minutes:

[https://help.ubuntu.com/lts/serverguide/samba-fileserver.html](https://help.ubuntu.com/lts/serverguide/samba-fileserver.html)
I have a /srv/samba/share folder created that is a public share within my network at home.
It is accessed via a browser smb://<my-pc-name>/<share-folder-name>

My next addition will be to re-modify the smb.conf file again and add a private folder that would require a password using my ubuntu userid / passwd used for just myself.

If you end up with extra shares or shares you want or cannot delete, try this article to remove them.
[http://ubuntuforums.org/showthread.php?t=1083000](http://ubuntuforums.org/showthread.php?t=1083000)

Hope this may help some.

elishasmantle

---

### Post by May_Masters on 2015-12-31
Well a "ps -ef" shows me that the smbd is running as root
But I connect to the shares with the "smbuser". This UID exists as samba-user and Linux-User but only on the server.
However, this is my line from the fstab:
```
//192.168.0.11/media /storage/media cifs credentials=/root/.smbcredentials  0 0
```
(The .smbcredentials hold the user and password)

Now, I read that with Unix extensions enabled (or was it the other way around ?), only the user that mounts the share has the access rights as specified within the smb.conf (read/write in this case)
And that's exactly what's going on. As "root" I can modify files as I like and they're still owned by smbuser ...
If I disable them will any other user that uses this share be treated the same way ?

If this doesn't work - and I don't want to have the smbuser on my workstation - how can I use my std-users to "appear" as smbusers on the server - or is that not possible ?

---

### Post by SeijiSensei on 2015-12-31
One simple solution is to use the "force user" and "force group" options to Samba.  This tells it to use a specific Linux user account for all file transactions regardless of who is logged into Samba.  Create a user in Linux to own the shared directories, then set that user as the target in the "force" commands.

---

### Post by Elishasmantle on 2015-12-31
SeijiSnsei,

Just curious since I am new to linux. 
Is the way to do this to create a new user/group just for this purpose with all the desired access, rights, perms, etc... and then use the "force" commands to assign that user/group to the samba share?

---

### Post by SeijiSensei on 2015-12-31
That's my preferred approach.  You could also use your own account as long as it has full rights to the share.

---

### Post by May_Masters on 2016-01-01
Hm, but this stuff is already set ... 
```
[pictures]
    comment = pictures
        path = /raid_fs_1/pictures/
        username = smbuser
        force user = smbuser
        force group = smbgrp
        read only = No
        available = Yes
        browseable = yes
        guest ok = No
        create mask = 0644
        directory mask = 0755

```

---

### Post by May_Masters on 2016-01-02
Ok now.
I created the smbgrp on ly linux box and changed the maks to 0660 (and dir mask to 0770) on my Server.
Now it works :)

---

