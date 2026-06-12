---
title: "Should I reinstall the Ubuntu system?"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by nikkizeng on 2011-01-13
Hi,

I just made a stupid action: chmod -R a+rwx /etc

Now I can't  access my computer remotely through ssh. I don't know what else problems it will have. Should I reinstall the system or is that a way to recover my stupid move?

Thanks,
Nikki

---

### Post by tekkidd on 2011-01-13
Heres what you do to fix it. First open up the terminal and type in ```
gksu nautilus
``` then enter your password. Now go to the root of the filesystem. Their find the folder "etc" and Right Click > Properties. Now under the premissions tab enter this 

Owner: Root
Folder Access: Create And Delete Files
File Access: ---

Group: Root
Folder Access: Access Files
File Access: --- 

Others:
Folder Access: Access Files
File Access: ---

Execute: Leave it unchecked

Now click at the bottom "Apply Permissions to Enclosed Files"

Then Click Done.

That should have fixed it. 


Im trying to build my blog so visit me: [http://tekkidd.tumblr.com/](http://tekkidd.tumblr.com/)

---

### Post by nikkizeng on 2011-01-14
[FONT=Times New Roman][SIZE=4]
Thanks, tekkidd!! But there is a strange problem - I can't uncheck the Execute option. It's already checked. When I click it, it will automatically become checked in 1 second. What's wrong? 
[/SIZE][/FONT]

---

### Post by zeroseven0183 on 2011-01-15
You can leave that last concern of yours since, by default, folders have x attribute.

If we are to translate the command
```
 chmod -R a+rwx /etc 
``` it changed (chmod) the permission of the folder (/etc) and everything under it (-R) to read, write, execute (+rwx) to all users, group and other (a).

You don't change the folder (and the files in it) /etc as it contains most of the system configuration files. Which, in your case, messed up ssh since it's inside that directory.

---

