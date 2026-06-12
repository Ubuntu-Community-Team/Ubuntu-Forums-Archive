---
title: "user not in the sudoers issue"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by hebebl on 2009-11-10
hi guys, 
all of a sudden my usual account lost its sudo privileges, then I visudoed the file and added: ```
username  ALL:(ALL) ALL 
```

Now I can use the sudo at the terminal but I cannot use it for any GNOME interface such as mounting, modifying users and groups etc. when trying to mount it asks for "password for root" instead of the usual account.

How do i bring my privileges back for the GNOME desktop? It is really annoying, somehow gnome does not see my account in the sudoers list. Thanks in advance.

---

### Post by albandy on 2009-11-10
You don't need to edit sudoers file, simply add your user to this groups:
adm
cdrom
plugdev
lpadmin
admin

your sudoers file should look like this:
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL



As you can see, the users in the admin group can use sudo.

---

