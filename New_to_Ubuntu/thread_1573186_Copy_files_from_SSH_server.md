---
title: "Copy files from SSH server?"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by Strategist01 on 2010-09-12
Hey guys.

I have a small account on an SSH server with some files on it that were already there. How do I copy these to a directory on the PC I'm working on? I mainly login using bash, so a command would be preferable as I have no other way of connecting right now...

Thanks :)

---

### Post by Rocket2DMn on 2010-09-12
Many SSH servers also allow you to connect using SFTP, so a graphical client like *gftp* might work for you.  Otherwise you can use the *scp* command to copy files to and from the server.

---

### Post by DemonBob on 2010-09-12
You can use rsync also. 

```
rsync -avzp --progress 192.168.30.3:/path/to/files/ /where/do/you/want/them/
```

---

### Post by baddnady23 on 2010-09-12
Go to Places>Connect To Server.

Under service type, select SSH.

In the Server field, type in your login.  Ex. ```
andrew@192.168.1.70
```

If it prompts you for a password, go ahead and enter it.  On your desktop then, you should see "sftp on your_server".  From there you can copy what you need.

---

### Post by slakkie on 2010-09-12
```

# Remote to local
scp you@remote.server.ip:/path/to/files .
# Local to remote
scp localstuff you@remote.server.ip:/path/to/dest_dir

```

---

### Post by baddnady23 on 2010-09-12
Thats the beauty of linux, there are 100 ways to do one thing.  Pick what works best for you!

---

### Post by Strategist01 on 2010-09-12
Ah, thanks guys. The server I'm on doesn't seem to like graphical SFTP clients... I'll use scp. thanks guys!

---

### Post by stmiller on 2010-09-12
Yet another:

```

sftp username@yourserver

```

You can then sort of browse around with commands like 'ls'. To get a file, do 'get filename.txt'  or to upload, do 'put filename.txt'.

---

