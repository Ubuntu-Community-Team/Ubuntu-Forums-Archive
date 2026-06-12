---
title: "Samba Problem"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by aharvey on 2007-07-31
Alrighty, ill start with what im trying to do

Im trying to join an ubuntu machine into a windows 2003 controlled domain for the express purpose of a file share server.

I can get the box joined to the domain without a problem, it lists all users and groups using wbinfo.

however, when trying to map the samba share with a windows xp machine through the domain i get a login windows which no username/pass will get through.

Any pointers would be great.

---

### Post by ugm6hr on 2007-07-31
The easiest way is to remove the need for a password to access the Samba share.  If you have security concerns re: this - then you can define the password with a command (but I can't remember how - smbpassword rings bells...)

Have a look at my signature link re: File sharing - specifically the bit that starts:
> I then edited /etc/samba/smb.conf (as root) (in Terminal: gksudo thunar and browse and double-click file), and added just one line immediately below the [global] entry, so this part looked like:

#======================= Global Settings =======================

[global]
[COLOR="Red"]security=share[/COLOR]
## Browsing/Identification ###


The **security=share** removes all samba passwords to access the Ubuntu shared folders.

PS: remember thunar=nautilus in Ubuntu.

---

### Post by aharvey on 2007-08-01
unfortunatlly,

This box will contain a multitude of shares, each directory having different read/write access by the win2003 group settings.

im praying i can get it to work seamlessly, just like mapping a share hosted on a windows machine with group permissions, no password or login required at all if they're already logged into the domain with the appropriate group permissions..

Im unsure if its even possible at this point, however, the samba share can be successfully mapped if i remove all valid user comments from the conf file, so im starting to think ive made a config error. 

wbinfo lists perfectly as ive said, will post the conf file from the ubuntu machine shortly.

---

### Post by aharvey on 2007-08-01
```

[global]

security = ads
realm = HEADOFFICE.DOMAIN.COM
password server = X.X.X.X
workgroup = HEADOFFICE
idmap uid = 10000-20000
idmap gid = 10000-20000
winbind enum users = yes
winbind enum groups = yes
template homedir = /home/%D/%U
template shell = /bin/bash
client use spnego = yes
client ntlmv2 auth = yes
encrypt passwords = yes
winbind use default domain = yes
restrict anonymous = 2
domain master = no
local master = no
preferred master = no
os level = 0

[homes]
   comment = Home Directories
   browseable = no
   valid users = %S
   writable = yes

[test]
comment = test share
path = /shares/test
read only = no
valid users = aharvey @Office



```

---

