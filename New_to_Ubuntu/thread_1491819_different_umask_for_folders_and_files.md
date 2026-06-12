---
title: "different umask for folders and files"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by csyoen on 2010-05-24
Hello together,

I have ubuntu installed on my computer and want to give the following default rights to one user on the filesystem:

files:
rw-r-----

and for folders:

rwxr-x---

I think I have to use **umask **for this, but I don't know how to specify whether I configure the umask for files or for folders ?

Maybe I don't have to use the umask - command for this ?

Many thanks for your help,

Best regards,
Claude

---

### Post by jbrown96 on 2010-05-24
```
man umask
```

---

### Post by csyoen on 2010-05-24
Hi [jbrown96]("http://ubuntuforums.org/member.php?u=304717").

Many thanks for this help. But I tried this out yet, and I could not find the solution.

That's the reason why I posted this question in this forum.

Are you sure you have found the solution by using 

[B]man umask

or even

man 2 umask ???

Best,
Claude

[/B]

---

### Post by ublintu on 2010-05-24
Hi,

You can change it like this.
                                                                  **chmod u=rw,g=rx,o= files**
 
Are you looking for this?

---

### Post by Lucky. on 2010-05-24
I don't know how to set the umask for a single user, but I know how to do it for all users.

Edit: /etc/profile

On the very last line there it should say the following by default:

```

umask 022

```

To have all newly created files and folders have permissions of rw-r----- and rwxr-x--- you will want to change the umask to

```

umask 027

```

Save the file, reboot, and you should be good.

However this will only change **new files and folders** that are created.  Everything else will still probably be as it was before.

I hope this helps!

---

### Post by csyoen on 2010-05-24
Sorry, but this doesn't work too:

[B]chmod: Ungültiger Modus: „u=rw,“
„chmod --help“ gibt weitere Informationen.


[/B]Sorry my system is in german, but as you can see, the mode u=rw is not recognized.

---

### Post by ublintu on 2010-05-24
sorry, I changed it
chmod u=rw,g=rx,o= files

---

### Post by csyoen on 2010-05-24
Thank you Lucky, this worked fine.

You only have to write umask 027 in command line and the umask is set for this session.

Thanks again.

Problem solved, now I have to try to understand why it worked like this ;-)

---

### Post by csyoen on 2010-05-24
For a single user, I think you have to put the mask in the file

**.bashrc**

in it's home directory

Best

---

### Post by Lucky. on 2010-05-24
> 
For a single user, I think you have to put the mask in the file

.bashrc



Thanks csyoen, I will try that out!

---

### Post by ublintu on 2010-05-24
Single user -R
[http://www.linuxforums.org/forum/misc/31582-permissions-single-user.html](http://www.linuxforums.org/forum/misc/31582-permissions-single-user.html)

---

