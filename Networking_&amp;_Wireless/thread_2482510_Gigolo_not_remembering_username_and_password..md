---
title: "Gigolo not remembering username and password."
date: 2023-01-02
forum: Networking &amp; Wireless
---

### Post by actavis on 2023-01-02
Gigolo not remembering username and password.,it says allways remember loggin userpasswords.
But it doesnt remember it.
What to do?

---

### Post by TheFu on 2023-01-02
Can you use a different protocol than whatever you are using?  

Perhaps something that is ssh-based?  With ssh, you can use ssh-keys and never be prompted for credentials at connection time after the first time.  There must be 20-50 ssh-based tools.  sftp, scp, rsync, ssh, sshfs just to name a few.  Setting up keys is 2 commands, 1 time for the first remote system and 1 command for all the others, if using the same keys.

A system-to-system file access method that doesn't depend on the user credentials at all, is NFS.  This is usually a little faster and makes remote storage available for all users, based on the Unix file/directory permissions.  NFS is mainly for secured LAN use, but with more complex configuration, Kerberos server-to-server with AES encryption can be used, but I've never set that up. sftp, scp, rsync, sshfs have always been so much easier to use going over the internet.

Of course, of the storage being accessed is only CIFS then you have little choice but to use it.  If you mount it using the fstab or autofs, then you don't need to deal with gigolo.  Yes, it should work, but when it doesn't, there are alternatives.  Best to say exactly which DE and which release of Ubuntu is being use, since things change from release to release.  I can't help with gigolo. Haven't used it in about a decade, but others probably can.  Please don't make people guess the important details.

---

### Post by actavis on 2023-01-02
First I must say that Im a newbe on this.
I have gigolo in the start up folder  soo when I boot it asks for username and password.
And there are 3 alternatives,the oneI i use says: never forget the pass user.
But the next time -i boot it still asks for user and password.

---

