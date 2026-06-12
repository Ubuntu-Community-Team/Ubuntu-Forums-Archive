---
title: "Cannot write to Samba shares from Win7"
date: 2017-08-18
forum: Networking &amp; Wireless
---

### Post by accounts0 on 2017-08-18
I've shared dirs via Dolphin [1] after having done so in smb.conf [2] failed to allow shares to appear on the Windows side.


I use a startup script [3] when Windows starts, & when I share from in Dolphin it appears to work with the mapped drives appearing after it runs, but I can't write to them [4].


However if I use smb.conf to share the same, my net use script won't complete & I can't even get the shares to appear.


I have my smb.conf set with globals that seem right [5], my linux user is indeed in the @sambashare group, but something's wrong.




[1]:
[http://imgur.com/NAY0b2U](http://imgur.com/NAY0b2U)


[2]:
[http://sebsauvage.net/paste/?a09fb38d16935382#zbphg6fdLz4WUkDY8bHrnBtRyRk/6nI5J0ZE93hqPaE=](http://sebsauvage.net/paste/?a09fb38d16935382#zbphg6fdLz4WUkDY8bHrnBtRyRk/6nI5J0ZE93hqPaE=)


[3]:
[http://sebsauvage.net/paste/?78716a6de2f9f45d#lejIbdX/hi/zjzrl1vyN/J2zPvFgfJBvEWEJ8hBydnM=](http://sebsauvage.net/paste/?78716a6de2f9f45d#lejIbdX/hi/zjzrl1vyN/J2zPvFgfJBvEWEJ8hBydnM=)


[4]:
[http://imgur.com/J9WNWLM](http://imgur.com/J9WNWLM)


[5]:
[http://sebsauvage.net/paste/?ab6d68d8f8acb93f#j6n6MtdETLLbopEhRSV94yHYvxCbWJR+SRxtKwc6RNw=](http://sebsauvage.net/paste/?ab6d68d8f8acb93f#j6n6MtdETLLbopEhRSV94yHYvxCbWJR+SRxtKwc6RNw=)

---

### Post by Morbius1 on 2017-08-19
For one thing Samba is confused as to what you want.

** Run the following command and take a look at your [Desktop] share for example:
```
net usershare info --long
```
It will likely look something like this:
> [Desktop]
path=/home/cb/Desktop
comment=
usershare_acl=Everyone:R,Unix User\cb:F,
guest_ok=y
Now take a look at the share you created in smb.conf:
> [Desktop] 
path = /home/cb/Desktop 
valid users = @sambashare 
guest ok = no 
writable = yes 
browsable = yes

One ( the one you created in Dolphin which is called a Samba Usershare ) allows guest read only access and the other does not. 

** There is also no mention in your post if you added the cb user to the samba password database:
```
 sudo smbpasswd -a cb
```
Without that the cb user will not be accepted as a legitimate user by samba and will be treated as a "guest" user - read only permissions in the Usershare and no permissions at all in the Classic share ( the one in smb.conf ).

Get rid on one of these shares and add yourself to the samba password database.

---

### Post by accounts0 on 2017-08-19
So I did
```
sudo smbpasswd -a cb
```

And disabled sharing from inside Dolphin.

I have these entries at the end of smb.conf
```

[Desktop]
path = /home/cb/Desktop
valid users = @sambashare
guest ok = no
writable = yes
browsable = yes


[DS]
path = /mnt/DS/cb
valid users = @sambashare
guest ok = no
writable = yes
browsable = yes

```

Verified my user is in the required group
```
cb : cb adm cdrom sudo dip plugdev lxd sambashare
```

Now I get nothing when I run
```
net usershare info --long
```

And when I do ```
$ testparm -s
```
I get
```

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Desktop]"
Processing section "[DS]"
Loaded services file OK.                                                                                                                              
Server role: ROLE_STANDALONE                                                                                                                          
                                                                                                                                                      
# Global parameters                                                                                                                                   
[global]                                                                                                                                              
        workgroup = FUNKYSALAMANDER                                                                                                                   
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




[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers




[Desktop]
        path = /home/cb/Desktop
        valid users = @sambashare
        read only = No




[DS]
        path = /mnt/DS/cb
        valid users = @sambashare
        read only = No


```

And of course
```
[FONT=monospace][COLOR=#000000]$ sudo service smbd restart[/COLOR]
[/FONT]
```

None of which has made any difference in Windows, I still get 'Destination Folder Access Denied / You need permission to perform this action' errors trying to write.

---

### Post by Morbius1 on 2017-08-20
I see nothing wrong with your setup and I cannot reproduce your symptom.

It's unlikely that anyone in the sambashare group will actually be able to write to that share besides "cb" unless you also changed ownership of the Desktop folder allowing a group write and/or you did not encrypt your home folder but "cb" should have full access.

---

### Post by accounts0 on 2017-08-20
The startup script [1] specifies the user "cb" & the password entered via the
```

sudo smbpasswd -a cb

```
command, so AFAIK it should be working.

In KDE's "System Settings > Connectivity > Windows Shares" I have the Windows user/password set there. But I don't think that should make a difference here...



[1]:
[http://sebsauvage.net/paste/?78716a6de2f9f45d#lejIbdX/hi/zjzrl1vyN/J2zPvFgfJBvEWEJ8hBydnM=](http://sebsauvage.net/paste/?78716a6de2f9f45d#lejIbdX/hi/zjzrl1vyN/J2zPvFgfJBvEWEJ8hBydnM=)

---

### Post by gordintoronto on 2017-08-20
The end of my smb.conf is about printers; if I were to put something about shared folders there, I think it would be ignored.

---

### Post by accounts0 on 2017-08-21
> **gordintoronto said:**
> I think it would be ignored.

Having those entries there worked on KDE Neon, which is also Ubuntu 16.04. I would imagine that would work here as well. This also is part of why I'm so lost as to why it doesn't work in this case.

---

### Post by accounts0 on 2017-08-27
bump

---

### Post by accounts0 on 2017-10-31
Finally got it working using a fresh samba install & the instructions here:

[https://askubuntu.com/questions/820549/ubuntu-16-samba-server-with-windows-10-client-tutorial-howto](https://askubuntu.com/questions/820549/ubuntu-16-samba-server-with-windows-10-client-tutorial-howto)

---

