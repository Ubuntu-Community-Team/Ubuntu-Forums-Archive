---
title: "Create limited user for SSH login"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by Foxtrot-1 on 2007-10-30
I have an Linux server with ssh connection how many friends want to connect to. But how do I create an account with no home dir, no rights, so the just can log in through the ssh, but dont have the permission to cd to path or read any files.
They shall just log in so they kan use the server as proxy, and they dont need to do anything on the server

Am I clear?
Sry for my english..

---

### Post by MrFSL on 2007-10-30
Read this recently perhaps it will help;

[http://www.howtoforge.com/chrooted_ssh_howto_debian](http://www.howtoforge.com/chrooted_ssh_howto_debian)

---

### Post by netztier on 2007-10-30
> **Foxtrot-1 said:**
> I have an Linux server with ssh connection how many friends want to connect to. But how do I create an account with no home dir, no rights, so the just can log in through the ssh, but dont have the permission to cd to path or read any files.
They shall just log in so they kan use the server as proxy, and they dont need to do anything on the server

Am I clear?


You should be able to achieve this (or some of this) by configuring their login shell as **/bin/false** instead of **/bin/bash** (see file** /etc/passwd**). Like this, they can still build an ssh connection to the system, but won't get a login shell. If you google for "restricted account" and "/bin/false", you might find the occasional HOWTO document about locked-down accounts. 

I am however not quite sure what will happen when they connect with an sftp or scp client - I have (as of yet) no idea if they can access directories even if their login shell is /bin/false

Another idea I've seen in use is this one: the user can do an interactive SSH session to the server, but all he can do is login with the old password and then change the password to a new one - nothing else. Once he's done it, the program ends and the user is logged out immediately. Probably this is done by setting **/usr/bin/passwd** instead of /bin/bash or/bin/false.

best regards

Marc

---

### Post by Foxtrot-1 on 2007-10-31
Thanks
I'll test it now, and I think it will work out;)

---

### Post by Foxtrot-1 on 2007-11-01
Something went wrong.
I created a user with path: /bin/false, but when I connected to the server through ssh it just logout because it have no path.

---

### Post by Zeosa on 2007-11-01
MrFSL Posted what you need ....As you've discovered, if you set their shell to false it won't allow logins. You want to set up a chroot environment for these users which will restrict their movements in the filesystem...(they will need home directories as well, but these are stored within the chroot env.)

If you're looking for something more geared to ubuntu (and alot easier to accomplish) there's a forum post about using jailkit to accomplish the same thing here: [http://ubuntuforums.org/showthread.php?t=248724](http://ubuntuforums.org/showthread.php?t=248724)

---

### Post by kevdog on 2007-11-01
Is chroot the same as jailing the user?   Any advantages of either method?  With chroot, the user may not be able to browse other directories beyond their home directory, however can they run executables.

---

