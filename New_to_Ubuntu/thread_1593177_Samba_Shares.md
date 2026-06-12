---
title: "Samba Shares"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by Randy Wells on 2010-10-11
Just installed an external hdd on my Ubuntu 10.04 system.  Got it working with the help of the Forums.  :P

Now I need to add it as a share on Samba.  I already have a Samba share on the system.  I tried adding the folder in the new hdd in smb.conf.  

I first placed it under **[share]** in smb.conf where the original share was entered, but that only allowed me to see the new hdd. When I made an additional entry for my ext. hdd folder; **[wdshare]** I only saw the original share.
 
Is there any way that I can get access to both locations with Samba?

Thanx,

Randy

---

### Post by Morbius1 on 2010-10-11
Why not post the output of the following commands so we can all see what's up:
```
net usershare info
``````
testparm -s
```

---

### Post by Randy Wells on 2010-10-11
> **Morbius1 said:**
> Why not post the output of the following commands so we can all see what's up:
```
net usershare info
``````
testparm -s
```

Thanks for the reply...

"net usershare info" comes up with nothing.

"testparm -s" does give me a lengthy output, but I can't remember how to pipe it to a text file so I can post a copy. :confused:

Could you give an old dog a hint on how to generate a file from the output so I can post it.  Sorry, but my UNIX/Linux command line skills are 10 years rusty.

Thanks,
Randy

---

### Post by Morbius1 on 2010-10-11
It shouldn't be that long of an output. You should be able to "Edit > Select all" in the terminal and just copy and paste. But to answer your question:
```
testparm -s > smb.txt
```
It will then be in your home directory

---

### Post by Randy Wells on 2010-10-11
> **Morbius1 said:**
> It shouldn't be that long of an output. You should be able to "Edit > Select all" in the terminal and just copy and paste. But to answer your question:
```
testparm -s > smb.txt
```
It will then be in your home directory

Morbius1,

Thanks for the tip!  Here's the listing.  I don't have kde or gnome installed.  I'm trying to force myself to get back some ability at the command line (like to old days). 

It only shows one user.  How do I get it to allow other users to access the share(s)?

```
[global]
    server string = %h server (Samba, Ubuntu)
    security = SHARE
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
    create mask = 0775

[Share]
    comment = WDEXT Share
    path = /media/wd1tb_ext/wdshare
    valid users = sherri
    read only = No
    create mask = 0755
    guest ok = Yes

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

```

Thanx,

Randy

---

### Post by Morbius1 on 2010-10-11
I only see one share:
> [Share]
    comment = WDEXT Share
    path = /media/wd1tb_ext/wdshare
    valid users = sherri
    read only = No
    create mask = 0755
    guest ok = Yes
Assuming it's not an NTFS formatted drive that's automounted when turned on then the only user that has access is sherri. You can add other users just by adding more names:
> valid users = sherri, john, alvin

---

### Post by Randy Wells on 2010-10-11
Mobius1,

Thanks again!  I thought that I should be able to concatenate users on the "valid users" line but wasn't sure about the delimiter.

Yes, for now there is only one share.  I tried to add another but it didn't work.  I quoted it out in **smb.conf** until I could figure out the problem.  Do all the shares get listed under the "[Share]" heading?  Or, do you have to add other shares under other heading names?

Thanx,

Randy

---

### Post by Morbius1 on 2010-10-11
>  Do all the shares get listed under the "[Share]" heading?  Or, do you have to add other shares under other heading names?

Each share has it's own heading and it's own path and authentication parameters.

---

### Post by Randy Wells on 2010-10-12
Morbius1,

Thanks again.  I had put the second share under a second heading before and it didn't work.  BUT... this time it worked like a charm.  :)

We can mark this problem SOLVED!

I really appreciate your help.  You've been great. \\:D/

Randy

---

