---
title: "FTP &amp; CHMOD permissions on my webserver?"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by karlm on 2010-10-07
Hi all, 

Guess who's stumped again?


I have a webserver and in the past, when I was on Windoze, I would use cuteftp to do all my transfers and permissions.

Now I'm on Ubuntu (see sig for version) and can access my webserver via the .... uhhh... file browser. It asks my username & password and allows me access to do the jobs I need.

Except, it seems, I can't set CHMOD permissions on my webserver.

If I'm looking at the file I wish to edit, I right click and select Properties. From there I select the Permissions tab, and it greets me with the following message: "The permissions of xyz.php could not be determined"

Can someone please explain how I set CHMOD on specific files/folders?

ps - I know I can use the terminal/putty, but not sure how to do it that way either.



Cheers :)

---

### Post by Hippytaff on 2010-10-07
You should be able to
 
```

cmod r+w {/path/filename}

```
 
to change the permissions to read and write from terminal.
 
It might have something to do with file ownership, in which case look into the chown command

---

### Post by karlm on 2010-10-07
it works fine using putty with root access :) ty

---

### Post by Hippytaff on 2010-10-07
Excellent (remember to mark the thread as solved in the Thread Tools at the top) :-D

---

### Post by karlm on 2010-10-07
Done!

For those who may encounter similar issues, the way i did it was simple:

Log into putty as root.
navigate to where you want to edit file permissions using 'cd' command.
enter 'chmod xyz filename.php' (replace xyz with necessary values and filename.php with your real file name and extension)

Simples!

---

