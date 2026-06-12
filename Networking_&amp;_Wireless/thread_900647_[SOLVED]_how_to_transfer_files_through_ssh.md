---
title: "[SOLVED] how to transfer files through ssh??"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by bigdee973 on 2008-08-25
hello im connected to my friends computer through ssh, we're tyring to upload some files on his pc onto the one i have here... whats the command to transfer files AND folders? on to the PC's here and there?

---

### Post by lswb on 2008-08-25
On the client computer you can connect with sftp instead of ssh, or perhaps better yet,
from Main Menu/Places/Connect to Server then select SSH as the server type and enter the server name. After connection a regular file manager window will open for the directory on the server computer and you can drag & drop between the 2 systems.

---

### Post by cariboo on 2008-08-25
Use Nautilus and sftp. Make sure you have a location bar, if you don't click the icon on the far left next to location, then in the location bar type:

```
sftp://<username>@<remote_computer>
```

Where <username> is your user name on the remote computer and <remote_computer> is the ip address or how ever you access the remote computer.

Jim

---

### Post by y@w on 2008-08-25
If you don't need to browse the filesystem, I'd use scp. No need for the GUI. It's just an ssh transfer client for the command line. Do a quick 'scp' on the command line and it will tell you the usage. To get a folder mounted on /home to your /home directory, just do something like this:

```
scp -r user@server:/home/folder /home/
```

In general:
```
scp -r (recursive) username@server:(remote location) (local location)
```

You can do the transfer in either direction.

---

### Post by bigdee973 on 2008-08-25
thank all three of you guys for your help.  all 3 are perfect to know and i have the files i need thanks...

---

### Post by bigdee973 on 2008-08-25
> **y@w said:**
> If you don't need to browse the filesystem, I'd use scp. No need for the GUI. It's just an ssh transfer client for the command line. Do a quick 'scp' on the command line and it will tell you the usage. To get a folder mounted on /home to your /home directory, just do something like this:

```
scp -r user@server:/home/folder /home/
```

In general:
```
scp -r (recursive) username@server:(remote location) (local location)
```

You can do the transfer in either direction.

i also want to know how i would UPLOAD a file/folder from my pc to theirs using the commandline?

---

### Post by y@w on 2008-08-25
Just reverse it :)

```
scp -r (local location) username@server:(remote location)
```

---

### Post by bigdee973 on 2008-08-25
> **y@w said:**
> Just reverse it :)

```
scp -r (local location) username@server:(remote location)
```

AWESOME! ur the man :guitar:

---

