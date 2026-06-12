---
title: "SSH remote login issue"
date: 2023-10-29
forum: Networking &amp; Wireless
---

### Post by virtual163 on 2023-10-29
Unable to remotely log in to another system using a certificate
```
Welcome to Ubuntu 23.10 (GNU/Linux 6.5.0-10-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage


0 updates can be applied immediately.


Last login: Mon Oct 30 07:31:30 2023 from 10.10.10.88
mrchen@MrChen-Duet:~$ cd .ssh/
mrchen@MrChen-Duet:~/.ssh$ ll
total 32
drwx------  2 mrchen mrchen  119 Oct 30 07:28 ./
drwxr-x--- 21 mrchen mrchen 4096 Oct 30 07:28 ../
-rw-------  1 mrchen mrchen  738 Oct 17 08:19 authorized_keys
-rw-r--r--  1 mrchen mrchen 6467 Oct 29 20:59 config
-rw-------  1 mrchen mrchen 2320 Oct 30 06:38 known_hosts
-rw-------  1 mrchen mrchen 2098 Oct 29 21:27 known_hosts.old
-rw-------  1 mrchen mrchen 3434 Oct 29 21:17 Mr.Chen
-rw-r--r--  1 mrchen mrchen  738 Oct 30 07:28 Mr.Chen.pub
mrchen@MrChen-Duet:~/.ssh$ ssh-copy-id MrChen-T14 
/usr/bin/ssh-copy-id: ERROR: No identities found
mrchen@MrChen-Duet:~/.ssh$ ssh MrChen-T14 
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0644 for '/home/mrchen/.ssh/Mr.Chen.pub' are too open.
It is required that your private key files are NOT accessible by others.
This private key will be ignored.
Load key "/home/mrchen/.ssh/Mr.Chen.pub": bad permissions
mrchen@10.10.10.88's password: 
Permission denied, please try again.
mrchen@10.10.10.88's password: 
Permission denied, please try again.
mrchen@10.10.10.88's password: 
mrchen@10.10.10.88: Permission denied (publickey,password).
mrchen@MrChen-Duet:~/.ssh$ ssh -i Mr.Chen M
ModemManager  MrChen-Duet   MrChen-T14    
mrchen@MrChen-Duet:~/.ssh$ ssh -i Mr.Chen MrChen-T14 
Enter passphrase for key 'Mr.Chen': 
Welcome to Ubuntu 23.10 (GNU/Linux 6.5.0-10-generic x86_64)


 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage


0 updates can be applied immediately.


Last login: Mon Oct 30 07:30:40 2023 from 10.10.10.89
&#9484;&#9472;[mrchen@MrChen-T14]&#9472;[~]
&#9492;&#9472;&#9472;&#9596;$exit
logout
Connection to 10.10.10.88 closed.
mrchen@MrChen-Duet:~/.ssh$ ssh MrChen-T14 
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0644 for '/home/mrchen/.ssh/Mr.Chen.pub' are too open.
It is required that your private key files are NOT accessible by others.
This private key will be ignored.
Load key "/home/mrchen/.ssh/Mr.Chen.pub": bad permissions
mrchen@10.10.10.88's password: 
Welcome to Ubuntu 23.10 (GNU/Linux 6.5.0-10-generic x86_64)


 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage


0 updates can be applied immediately.


Last login: Mon Oct 30 07:52:21 2023 from 10.10.10.89
&#9484;&#9472;[mrchen@MrChen-T14]&#9472;[~]



```

---

### Post by TheFu on 2023-10-30
```
Load key "/home/mrchen/.ssh/Mr.Chen.pub": bad permissions
```

ssh is picky about permissions. They cannot be too open. Fix that or it will never work.  Generally, you should use **ssh-copy-id** to push the public key file from the client to the remote system. ssh-copy-id will ensure the correct file and directory permissions for the copied keys.

Your attempt to use ssh-copy-id failed. You need to fix that first.
From the client, looking at your file listing, it appears you didn't use the command correctly. I'd guess this is what you need:

```
ssh-copy-id       -i      ~/.ssh/Mr.Chen.pub      mrchen@MrChen-T14
```

If you aren't using a default key filename, then you'll want to setup a ~/.ssh/config file to use the specific identity file when connecting to the specific systems where that identity will work.  Or just use the default filenames.  To setup ssh-keys, here are the steps:

```
Step 1:  Run on the client as the normal user:
   $ ssh-keygen -t ed25519

Step 2:  Run from the client to the server:
   $ ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote

Step 3: Test that ssh works.  ssh into the remote system,
   $ ssh username@remote
```


id_ed25519 is a default ssh-key filename. There are some others, depending on the type of ssh-keys used.

---

### Post by virtual163 on 2023-10-30
These are the configurations of the two machines, the same. The normal system was upgraded from 23.04 liters, and the abnormal one was a newly installed brand new system, so I don't know what the reason is?
```
mrchen@MrChen-Duet:~/.ssh$ lltotal 32
drwx------  2 mrchen mrchen  119 Oct 30 07:28 ./
drwxr-x--- 21 mrchen mrchen 4096 Oct 31 06:59 ../
-rw-------  1 mrchen mrchen  738 Oct 17 08:19 authorized_keys
-rw-r--r--  1 mrchen mrchen 6467 Oct 29 20:59 config
-rw-------  1 mrchen mrchen 2320 Oct 30 06:38 known_hosts
-rw-------  1 mrchen mrchen 2098 Oct 29 21:27 known_hosts.old
-rw-------  1 mrchen mrchen 3434 Oct 29 21:17 Mr.Chen
-rw-r--r--  1 mrchen mrchen  738 Oct 30 07:28 Mr.Chen.pub
mrchen@MrChen-Duet:~/.ssh$ ssh-copy-id MrChen-T14 
/usr/bin/ssh-copy-id: ERROR: No identities found
mrchen@MrChen-Duet:~/.ssh$ 

```
```
&#9484;&#9472;[mrchen@MrChen-T14]&#9472;[~/.ssh]&#9492;&#9472;&#9472;&#9596;$ll
total 100
drwx------   2 mrchen mrchen    96 Oct 31 06:54 ./
drwxr-x---+ 38 mrchen mrchen  4096 Oct 31 07:00 ../
-rw-------   1 mrchen mrchen  2222 Oct 30 07:28 authorized_keys
-rw-r--r--   1 mrchen mrchen  6468 Oct 31 06:35 config
-rw-------   1 mrchen mrchen 76222 Oct 30 17:13 known_hosts
-rw-------   1 mrchen mrchen  3434 Jan  3  2022 Mr.Chen
-rw-r--r--   1 mrchen mrchen   737 Jan 24  2022 Mr.Chen.pub
&#9484;&#9472;[mrchen@MrChen-T14]&#9472;[~/.ssh]
&#9492;&#9472;&#9472;&#9596;$ssh-copy-id MrChen-Duet 
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed


/usr/bin/ssh-copy-id: WARNING: All keys were skipped because they already exist on the remote system.
		(if you think this is a mistake, you may want to use -f option)


&#9484;&#9472;[mrchen@MrChen-T14]&#9472;[~/.ssh]



```

---

### Post by TheFu on 2023-10-30
If you don't do what is suggested, nobody can help.

---

### Post by virtual163 on 2023-10-30
Thank you, but it's already done now

---

