---
title: "smbmount doesn't work like Samba?"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by FrozenFOXX on 2007-04-26
I'm currently having an issue with smbmount.  I have three directories on a central server that are set up to be accessed with read/write by members of an authorized group and readable by only two authorized users (though I'm thinking about changing it to readable by only the member of the authorized group).  On the central server all three directories are owned by root, have the authorized group, and the permissions are "drwxrwx---."

When I access them directly with Samba it works like you would expect.  Authorized user connects, authorized user is a member of the authorized group and thus can write changes to  everything in the directories.


The problem is when I use smbmount with a client machine's fstab in order to make it permanently mounted.  For the sake of simplicity I duplicated the parent directory structure (the three directories on the server are under /usr/local/share/ and on the client they are under /usr/local/share/ as well).  I even named them the same and used the same permissions, owner, and group settings, just left them empty for mounting purposes.


In my fstab I mount them as such:
//assault/Music /usr/local/share/Music smbfs credentials=/home/foxx/.smbpasswd,gid=staff,rw 0 0

The same follows for the other two directories.  For some reason even with the rw flag the directories don't have the permission set I gave them elsewhere instead changing to "drwxr-xr-x" which breaks the security model I've been trying to achieve.  To modify the files by Samba directly limits my accessibility since many programs do not recognize a smb:// stream.


Any ideas why on earth smbmount isn't working the same was as Samba?  Any fixes I can apply?  Or am I stuck with a broken smbmount? :(

---

### Post by FrozenFOXX on 2007-04-26
So, no ideas?

---

### Post by Unconscious on 2007-05-03
I have the same problem. I guess I'll seek a solution elsewhere.

---

### Post by Unconscious on 2007-05-03
Check out this thread at [http://www.linuxforums.org/forum/linux-newbie/57478-permissions-issues-windows-share-mounted-smbmount.html]("http://www.linuxforums.org/forum/linux-newbie/57478-permissions-issues-windows-share-mounted-smbmount.html")

---

