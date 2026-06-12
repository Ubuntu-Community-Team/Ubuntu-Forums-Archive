---
title: "copying files from a remote computer using ssh"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by natirips on 2008-02-16
When I connect to a remote computer using "ssh user@server", how do I copy a file from the computer I'm logged in to my computer. So, in example I want to copy a file from "server" to "usercomp":

```
user@usercomp:~$ ssh user1@server
Password: 
...
user1@server:~$ 
```
What do I need to do to copy a file from server to usercomp from here?

---

### Post by Keith Hedger on 2008-02-16
```
scp ~/Documents/index.html AUSER@HOSTIP:Documents/index.html
```
you don't have to be logged in to the host to do this ( i think)
see the man page for scp(make sure you can get through the firewall)

---

### Post by JeSTeR7 on 2008-02-16
Well, if you need to do it using the terminal that I can't help you, but since you have the SSH server installed, if you are using a GUI (Gnome at least), you can go to Places-Connect to Server and choose SSH as the service type.  This will open your share in Nautilus and SHOULD allow you to drag-and-drop.

---

### Post by Lars Noodén on 2008-02-16
open a second terminal or tab

```

scp user@server:~/Public/html/foo.jpeg .
scp user@server:~/Public/html/foo.jpeg /tmp/.
``` 

Replace the first copies from the remote server from the directory Public/html, which is under your home directory on the remote machine, to your current working directory.  The second copies the same file to the local directory /tmp./

To copy from the local machine, to the remote machine, just reverse things:

```

scp foo.jpeg user@server:~/Public/html/
scp /tmp/foo.jpeg user@server:~/Public/html/
``` 

You can find more info about [scp]("http://linux.die.net/man/1/scp") in the man page.  
[INDENT][http://linux.die.net/man/1/scp](http://linux.die.net/man/1/scp)[/INDENT]

Same for [sftp]("http://linux.die.net/man/1/sftp"), which is a completely different protocol than ftp:
[INDENT][http://linux.die.net/man/1/sftp](http://linux.die.net/man/1/sftp)[/INDENT]

Just for completeness, the manpage for [ssh]("http://linux.die.net/man/1/ssh"):
[INDENT][http://linux.die.net/man/1/ssh](http://linux.die.net/man/1/ssh)[/INDENT]

---

### Post by natirips on 2008-02-16
I had to use a little diffrent syntax: "scp remote_file(source) local_file(destination)" istead of "scp local(dest) remote(source)" as you wrote, but it acctually worked, thanks.

---

### Post by natirips on 2008-02-16
> **Lars Noodén said:**
> open a second terminal or tab

```

scp user@server:~/Public/html/foo.jpeg .
scp user@server:~/Public/html/foo.jpeg /tmp/.
``` 

Replace the first copies from the remote server from the directory Public/html, which is under your home directory on the remote machine, to your current working directory.  The second copies the same file to the local directory /tmp./

To copy from the local machine, to the remote machine, just reverse things:

```

scp foo.jpeg user@server:~/Public/html/
scp /tmp/foo.jpeg user@server:~/Public/html/
``` 

You can find more info about [scp]("http://linux.die.net/man/1/scp") in the man page.  
[INDENT][http://linux.die.net/man/1/scp](http://linux.die.net/man/1/scp)[/INDENT]

Same for [sftp]("http://linux.die.net/man/1/sftp"), which is a completely different protocol than ftp:
[INDENT][http://linux.die.net/man/1/sftp](http://linux.die.net/man/1/sftp)[/INDENT]

Just for completeness, the manpage for [ssh]("http://linux.die.net/man/1/ssh"):
[INDENT][http://linux.die.net/man/1/ssh](http://linux.die.net/man/1/ssh)[/INDENT]

thanks for detailed info

---

