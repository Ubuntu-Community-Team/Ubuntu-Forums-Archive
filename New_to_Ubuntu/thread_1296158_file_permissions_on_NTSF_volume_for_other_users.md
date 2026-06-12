---
title: "file permissions on NTSF volume for other users"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by danklaf777 on 2009-10-20
Hi
I'm a new user on Kubuntu 9.0.4 (only a week - I don't know much)
I've created another user for my teenagers. But this user cannot access my NTSF files ("my documents" on Win XP) on my other hard drive. error message says that the user name is unknown from sudo. :(
They can access it only when I go on my own session, and with Dolphin I enter my password, then return on their session.:mad:
Is there an easy way to give them access to that hard drive with their own password (but only to that drive. In fact it is complete other partition of my windows hard drive). without always having to go to my own session. 
Note that I don't know how to use the Konsole terminal yet.

Thanks

Dan

---

### Post by gareththegeek on 2009-10-20
Put the following command into the command prompt to list the contents of the sudoers file:
```
cat /etc/sudoers
```
and post what comes out..

The sudoers file lists which users can use the sudo command. Is the problem user account in there?

---

### Post by uncle-c on 2009-10-20
I'm not sure if the same applies to Ubuntu 9.04 but my own experience with 8.10 suggests that you can access a XP shared folder without a password provided "Advanced Security" for XP folders has not been set . As you are trying to share your personal folder i.e "My Documents" your password will always be asked for. What you can do is to create a separate folder on XP and place all shareable files in there and make this file shareable. If you see an "Advanced Security" option then you can add the windows users that you want to have read , write or execute permissions in this directory. Now when someone on Ubuntu tries to connect to this share he/she will be asked for a user / passwd - this  must be the XP user and the xp password.

If you do not want to make a separate shareable directory and are happy to share "My Documents" then you can set this to share and in Advanced Security / share settings just add the windows users that you would like to have permission to rwx the directory.

---

### Post by danklaf777 on 2009-10-20
I went in the Konsole
Tried "cat /etc/sudoers
It says that I don't have permission (sorry if message is unclear. I have to translate error message from french)

---

### Post by danklaf777 on 2009-10-20
> **gareththegeek said:**
> Put the following command into the command prompt to list the contents of the sudoers file:
```
cat /etc/sudoers
```and post what comes out..

The sudoers file lists which users can use the sudo command. Is the problem user account in there?

 went in the Konsole
Tried "cat /etc/sudoers
It says that I don't have permission (sorry if message is unclear. I have to translate error message from french)

---

### Post by danklaf777 on 2009-10-20
> **gareththegeek said:**
> Put the following command into the command prompt to list the contents of the sudoers file:
```
cat /etc/sudoers
```and post what comes out..

The sudoers file lists which users can use the sudo command. Is the problem user account in there?

Finaly got it

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

---

### Post by bodhi.zazen on 2009-10-20
Ownership and permissions on ntfs partitions are set at the time of mounting.

While yes you can add your daughter to the admin group, giving her root access, this is overkill and using root power to avoid learning how to configure your system.

There are two options.

The first is to unmount the partition and edit /etc/fstab :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

There are examples on that link for NTFS partition.

If you want a gui tool, use ntfs-config or pysdm, both are in the repositories.

[http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)

---

### Post by danklaf777 on 2009-10-22
Great ! Thank you. This will surely help

---

