---
title: "samba user restrictions"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by Ivan Perzan on 2007-02-09
Hi
got a small problem setting up a fileserver on ubuntu...
share on the machine with listed below Share Definitions ...
[fileserver]
    path = /fileserver
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0750
    directory mask = 0750

Setup 10 users on samba and added subfolders in /fileserver for their files. Subfolders have permissions 750. Now I need to enable in /fileserver/<Xuser>/XXX folder for others to be able to change/create content. I done it by manually changing permissions for XXX folder to 770. The thing is when an user changes the file or creates a new one in the XXX folder the permissions of the newly created or changed file are set to 750.
Any chance I can make some exception on the rules for /fileserver and allow users to change files in a specific XXX folder.
If I add new share definitions then they are seen outside users folder hierarchy

HEEELP :)

---

### Post by gradedcheese on 2007-02-10
On a slight tangent: if you want each user to have their own Samba share where they have full permissions (which I think is what you're doing), you can do this:

```

# make things more windows-friendly, if you want
logon drive = H:
logon script = scripts/logon.bat
logon path = \\your_server_name\profile\%U

[homes]
   comment = Home
   valid users = %S
   read only = no
   browsable = no
   vfs objects = recycle  #give them a recycle bin

[profile]
   comment = User profiles
   path = /home/samba/profiles
   valid users = %U
   create mode = 0600
   directory mode = 0700
   writable = yes
   browsable = no

```

This has an interesting effect: each user gets their real home directory, with the proper permissions they'd expect, and because %S and %U are used, any time you make a new user, they're all set automatically (no need to manage individual shares).  Add to this your general /fileserver share as an additional share (ie: what you already have) and you have yourself a nice and flexible file server :)

---

