---
title: "How do I share a folder and all subfolders on my network?"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by ausairman on 2011-06-25
Hi everyone,

I tried sharing my music folder on my network, which seems to work, but for some reason I can only access that folder, not subfolders. How can I just share everything in a folder with guests, so that anyone on the network can download all files and subfolders without having to log in or change permissions or do something fancy?

---

### Post by abybaddi on 2011-06-25
Change the permission of the folder and check the box to apply to sub-folders and then share it via samba.

---

### Post by ausairman on 2011-06-25
Ok thanks. Is there any way of doing this without editing files? I mean like in windows where you right-click on a folder, click share and then it's shared?

---

### Post by Paqman on 2011-06-25
> **ausairman said:**
> I mean like in windows where you right-click on a folder, click share and then it's shared?

Same on Ubuntu. Right click > Sharing options.

---

### Post by ausairman on 2011-06-25
Yeah, but that doesn't actually work, at least it didn't for me. All it did was let me browse the contents of that folder, I couldn't go into any of the subfolders... Is there something else I should have done?

I tried the samba thing and followed some instructions but that of course didn't work either - I think you really need an indepth understand of linux to use that program...

---

### Post by Paqman on 2011-06-25
> **ausairman said:**
> Yeah, but that doesn't actually work, at least it didn't for me. All it did was let me browse the contents of that folder, I couldn't go into any of the subfolders... Is there something else I should have done?


Did you check the permissions like abybaddi suggested? Right click > Properties > Permissions. I can't say exactly what you'd need to set it to to work, you may need allow everybody read/write/execute permissions.

---

### Post by ausairman on 2011-06-25
I tried that, restarted, and now the ubuntu machine isn't even appearing in the network list... Any suggestions?

---

### Post by Morbius1 on 2011-06-25
You made too may references to using samba without telling us what method of samba you are using. Please post the output of the following commands:
```
testparm -s
``````
net usershare info --long
```You can probably resolve this with a "force user = your-user-name" line in the samba config file but it's best to see how you are configured first.

---

### Post by ausairman on 2011-06-25
```
arman@arman-XPS-M1530:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Global parameter guest account found in service section!
Processing section "[Guest share]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    interfaces = lo, ethl
    bind interfaces only = Yes
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

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Guest share]
    comment = Guest access share
    path = /home/arman/music
    guest ok = Yes
arman@arman-XPS-M1530:~$ net usershare info --long
[music]
path=/home/arman/Music
comment=
usershare_acl=Everyone:F,
guest_ok=y
```

---

### Post by Morbius1 on 2011-06-25
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section:
```
 force user = arman
```Save smb.conf, exit gedit, and back in the terminal restart samba:
```
sudo service smbd restart
```Every time you restart samba  the network has a fit so you need to wait a few minutes - yes minutes - for things to settle down before you can see if the remote user can access the share.

[COLOR=Blue]**EDIT:**[/COLOR] You might want to get rid of these two lines while you're in there:
> interfaces = lo, ethl
    bind interfaces only = Yes

---

### Post by ausairman on 2011-06-25
Great, that worked, thanks. Do you mind explaining what that did?

---

### Post by Morbius1 on 2011-06-25
I just used the path of least resistance.

"force user" will convert the remote user to you as far as those shares are concerned. I'm guessing you have no problem accessing /home/arman/Music as "arman" when you are accessing that box directly so if you convert your remote users to you problem solved.

---

