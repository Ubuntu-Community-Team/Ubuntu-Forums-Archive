---
title: "how do you prevent always getting prompted for ssh passphrase"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by chris.olsen on 2008-05-02
I have copied my id_rsa.pub key to the server and put it in it's authorized_keys file. After logging in one the server's key is saved into the local machine's known_hosts file.  Unfortunately, I still get prompted for the local passphrase when logging in via ssh to the server.

What am I missing to get around having to type the passphrase all the time?  The local machine is really a backup server and to allow the backups be automated I can't have the passphrase prompt popping up all the time.

** My normal development machine has no problem logging in without entering the passphrase once the server's key is placed within the knows_hosts file.

Thanks for the help.

---

### Post by RDouglasC on 2008-05-05
Check the permissions on the .ssh folder, if you copied it, then it may not be secure enough so you'll be prompted for the password. It should be:
drwx------  2 root root 4096 May  1 14:39 .ssh

---

### Post by chris.olsen on 2008-05-06
The issue was that I entered a passphrase when creating the ssh key.  I don't remember ever not creating one, but supposedly on my other machine that works I guess I didn't.

It works fine now.

---

