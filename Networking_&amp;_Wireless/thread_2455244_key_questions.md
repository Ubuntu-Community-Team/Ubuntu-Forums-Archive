---
title: "key questions"
date: 2020-12-15
forum: Networking &amp; Wireless
---

### Post by supertight on 2020-12-15
I want to connect to my Centos server from the Ubuntu shell on my windows 10 laptop.

I have the key in my users home directory. 
Where do I ```
cat >
``` the key to so its given on login? 

thank you!

---

### Post by TheFu on 2020-12-15
What sort of key?

If this is for ssh, it doesn't work that way. It is much easier once setup.  Find a guide for te exact key tpe an setup you are attempting. There must be 10 commonly used "keys."

---

### Post by supertight on 2020-12-15
> **TheFu said:**
> What sort of key?

If this is for ssh, it doesn't work that way. It is much easier once setup.  Find a guide for te exact key tpe an setup you are attempting. There must be 10 commonly used "keys."


I have a set of RSA keys I want to use.

I found the syntax for SFTP. When I pass 
```
sftp -i /home/user/id_rsa.pub username@server 
```
I get back
```
Load key "/home/user/id_rsa.pub": invalid format

```

---

### Post by TheFu on 2020-12-15
sftp uses ssh keys.
Find a how-to for ssh and use that.  The public ssh-key needs to be placed into a specific file, in a specific directory with specific permissions to work.

**sftp thefu@192.168.1.99** would be the command format, or just use any linux file manager and put sftp://thefu@192.168.1.99 into the URL.

---

### Post by supertight on 2020-12-15
> **TheFu said:**
> sftp uses ssh keys.
Find a how-to for ssh and use that.  The public ssh-key needs to be placed into a specific file, in a specific directory with specific permissions to work.

**sftp thefu@192.168.1.99** would be the command format, or just use any linux file manager and put sftp://thefu@192.168.1.99 into the URL.

RSA keys are ssh keys... I use this set of keys to ssh between centos servers regularly. 

Anyone else want to chime in with some actual help?

---

### Post by TheFu on 2020-12-15
Google found this: [https://ubuntu.com/tutorials/ssh-keygen-on-windows#1-overview](https://ubuntu.com/tutorials/ssh-keygen-on-windows#1-overview)

On Linux, these are the steps. RSA  generall considered less secure than ed25519 keys, but use whatever you want.
 
```
Step 1:  Run on the client as the normal user:
   $ ssh-keygen -t ed25519

Step 2:  Run from the client to the server:
   $ ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote
 The "username" is optional and not needed if the same between the
 client machine and remote server.
 "remote" can be a DNS name, IP address, some manually setup lookup
 inside the /etc/hosts or configured in the ~/.ssh/config file.

Step 3: Test that ssh works.  ssh into the remote system, 
   $ ssh username@remote
 All ssh-based connections between the client and server should now work
 just as easily.  ssh, sftp, scp, rsync, x2go, rdiff-backup, sshfs, and
  50 others regardless of the program.  Open a file manager like Caja,
 Thunar, whatever, Put sftp://username@remote/ into the URL. Hit <enter>.
```

That is it.

Sounds like the ssh-copy-id part is were the trouble is. In WSL, it should exist. Win10 has  a native ssh client now, but they didn't port ssh-copy-id.  ssh-keygen creates the private and public key files. Need to append the public key into the authorized_keys file in the ~/.ssh/ directory of the remote host. Lots of ways to accomplish that. I'd use scp to get the file there to a name that isn't clobbering any important file, then append it using any command you like - ```
cat ~/.ssh/temp.pub >> ~/.ssh/authorized_keys
``` will work.

BTW, RSA keys are used for all sorts of things, not only ssh.

I'm sorry not to be able to read minds and need more information.

---

### Post by supertight on 2020-12-15
> **TheFu said:**
> Google found this: [https://ubuntu.com/tutorials/ssh-keygen-on-windows#1-overview](https://ubuntu.com/tutorials/ssh-keygen-on-windows#1-overview)

On Linux, these are the steps. RSA  generall considered less secure than ed25519 keys, but use whatever you want.
 
```
Step 1:  Run on the client as the normal user:
   $ ssh-keygen -t ed25519

Step 2:  Run from the client to the server:
   $ ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote
 The "username" is optional and not needed if the same between the
 client machine and remote server.
 "remote" can be a DNS name, IP address, some manually setup lookup
 inside the /etc/hosts or configured in the ~/.ssh/config file.

Step 3: Test that ssh works.  ssh into the remote system, 
   $ ssh username@remote
 All ssh-based connections between the client and server should now work
 just as easily.  ssh, sftp, scp, rsync, x2go, rdiff-backup, sshfs, and
  50 others regardless of the program.  Open a file manager like Caja,
 Thunar, whatever, Put sftp://username@remote/ into the URL. Hit <enter>.
```

That is it.

Sounds like the ssh-copy-id part is were the trouble is. In WSL, it should exist. Win10 has  a native ssh client now, but they didn't port ssh-copy-id.  ssh-keygen creates the private and public key files. Need to append the public key into the authorized_keys file in the ~/.ssh/ directory of the remote host. Lots of ways to accomplish that. I'd use scp to get the file there to a name that isn't clobbering any important file, then append it using any command you like - ```
cat ~/.ssh/temp.pub >> ~/.ssh/authorized_keys
``` will work.

BTW, RSA keys are used for all sorts of things, not only ssh.

I'm sorry not to be able to read minds and need more information.

Ok man. look, the remote host is a CentOS machine, it's already configured. I can access it at will with other methods. eg putty or another CentOS machine. The key on the host is configured correctly. Like I said in the first post, I'm using the Ubuntu shell on my windows 10 laptop to access the remote host. You keep posting help for the other way around. BTW nobody asked you to "Read Minds". Try to keep up bud. Please don't reply again.

---

### Post by QIII on 2020-12-16
If you intend to dictate who may and may not respond to your query, especially when you exclude someone like TheFu, then there is little reason for this thread to remain open.

Closed.

---

