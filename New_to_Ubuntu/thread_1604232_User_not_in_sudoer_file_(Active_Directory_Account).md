---
title: "User not in sudoer file (Active Directory Account)"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by ace0022 on 2010-10-23
Hi all,

I have been trying to add my ubuntu 10.04 to my Windows 2008 Server R2 Active Directory to access my shares and files.  I have managed so far to add it the machine to Active Directory with LikeWise-Open but when I try to access any share, ubuntu says cannot retrieve shares from windows network.  So I sound this [https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently) and ran into a different problem.  When I try to sudo anything I get user not in sudoer file.  I have tried to add my active directory user name into the sudoer file by adding domainname\username to both the admin and the sudo sections but once I log in to the ubuntu with my active directory account, I still can't access the sudo feature.

Any help guys would be awesome!

---

### Post by ace0022 on 2010-10-24
bump...  :confused:

---

### Post by ace0022 on 2010-10-24
After some trial and error, I was able to solve it.  Hope this helps someone else...

(This is assuming you already have it joined to AD, if not use this link [http://www.likewise.com/resources/documentation_library/manuals/open/likewise-open-54-guide.html#id2993474](http://www.likewise.com/resources/documentation_library/manuals/open/likewise-open-54-guide.html#id2993474))

To add an Active Directory to a sudoers file do the following:

First log in "local" to the ubuntu workstation.

Open a terminal and type "sudo -i"

Enter Password

Type "visudo"

Go to where it says "%sudo" right under it make a space and type "%domainname\\activedirectoryOU ALL=(ALL) ALL"

Once done click "CTRL+X" to save changes.

When it confirms, clear the ".tmp" from the end of the save file.

Now log in with your domain credentials and launch a terminal to test it.

---

