---
title: "Windows 10 not allowing access to shared folder"
date: 2023-05-17
forum: Networking &amp; Wireless
---

### Post by tinman456 on 2023-05-17
Hi guys, I'm having a seemingly intractable problem trying to access a shared folder (Public) from my Windows 10 laptop. I'm running the latest Ubuntu which I just downloaded and installed on another laptop. I'm getting to see the folder on
 my Win10 machine but I just cannot access it. Windows keeps saying:

"Windows cannot access \\IP_address\Public
You do not have permission to access <as above>. Contact your network administrator to request access"

I have searched and searched and searched some more and did all the recommended config changes to the Win OS that I could find with no luck whatsoever. Can anyone help me sole this?

Thanks in advance

---

### Post by Morbius1 on 2023-05-17
Insufficient information provided to answer the question.

Start with posting the output of the following commands from Ubuntu:
```
testparm -s
```
```
net usershare info --long
```
```
hostname
```

---

### Post by tinman456 on 2023-05-18
Hi Morbius, thanks for replying I'm new to all this stuff but here goes..

My output 
```
 testparm -s

Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Weak crypto is allowed

WARNING: The 'netbios name' is too long (max. 15 chars).

Server role: ROLE_STANDALONE

# Global parameters
[global]
    log file = /var/log/samba/log.%m
    logging = file
    map to guest = Bad User
    max log size = 1000
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    unix password sync = Yes
    usershare allow guests = Yes
    idmap config * : backend = tdb


[netlogon]
    comment = Network Logon Service
    guest ok = Yes
    path = /home/samba/netlogon


[profiles]
    browseable = No
    comment = Users profiles
    create mask = 0600
    directory mask = 0700
    path = /home/samba/profiles


[share]
    comment = Ubuntu File Server Share
    create mask = 0755
    guest ok = Yes
    path = /srv/samba/share
    read only = No


[printers]
    browseable = No
    comment = All Printers
    create mask = 0700
    path = /var/spool/samba
    printable = Yes


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
avh@avh-HP-G42-Notebook-PC:~$ 
----------------------------------------------------------------
[B]The net usershare info was:
[/B]
vh@avh-HP-G42-Notebook-PC:~$ net usershare info --long
info_fn: file /var/lib/samba/usershares/shared folder is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[Shared]
path=/home/avh/Shared
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Public]
path=/home/avh/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y
-------------------------------------------------
```

**Hostmane is: **avh-HP-G42-Notebook-PC

I sincerely hope you can do something to help me out - I'm at my wits end
Thanks

---

### Post by Morbius1 on 2023-05-18
You are using two different methods to share folders: The classic way in smb.conf and the File manager way using usershares.

The problem with the usershares is the path: /home/avh/Public. 

Ubuntu made some changes to the permissions on a user's home folder that permits only that user access to it's contents. The guest user isn't avh so it will never get access.

I think the safest thing to do is:

Go to /var/lib/samba/usershares and just delete the share definition file: Public

Then recreate that share definition in smb.conf this way:
```
[Public]
path = /home/avh/Public
read only = No
guest ok = Yes
force user = avh

```
Then restart smbd:
```
sudo service smbd restart
```

THe "guest" user will be converted to avh - for that one share - which will bypass the problem/

---

### Post by tinman456 on 2023-05-19
Well Morbius, it actually worked. You are the real real. I had not come  across anything like that in all my days of frustrated searching. Thank  you a whole lot. Now I can sleep again!

Now i have another one for you if you don't mind...I have a Linux driver  for my USB wireless network adapter and I cannot install it for love or  money. It came with a shell script that does not complete and ends with  an error 2 message that I still can't resolve. I do know the adapter is  compatible because it did work when I first installed Ubuntu  "alongside" my Windows but now as I have it on a dedicated HDD no luck.  Can you be of help there also?

I appreciate in advance, Anthony

---

### Post by Morbius1 on 2023-05-19
I think it would be best if you start a new topic with that question. Probably in the [Network & Wireless]("https://ubuntuforums.org/forumdisplay.php?f=336") section so those folks who are knowledgeable about these things can see it.
 
I don't know much about hardware issues.

---

### Post by tinman456 on 2023-05-19
Perfect advice. I will do so right now. Thanks again

---

