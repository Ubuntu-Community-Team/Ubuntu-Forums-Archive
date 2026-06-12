---
title: "permissions"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by mlempenau on 2010-10-14
mikee@mike-desktop:/home/mike$ ls -ld /home/mike
drwxr-xr-x 62 mike mike 4096 2010-10-13 17:12 /home/mike
mikee@mike-desktop:/home/mike$ cd /home/mike/.gconf
bash: cd: /home/mike/.gconf: Permission denied

I thought that I had permission to view and copy this directory yet it doesn't allow.  Can someone explain this to me?  thanks,  Mike

---

### Post by jespdj on 2010-10-14
The output of your first ls command shows that you have permission to look at the directory /home/mike. But it doesn't say anything about subdirectories in there, such as the .gconf subdirectory.

If you want to change the permissions on the .gconf subdirectory so that you can cd into it, try this:

chmod u+x /home/mike/.gconf

That sets the "x" (execute) permission on the .gconf directory, which for directories means that you are allowed to navigate into it.

---

### Post by mlempenau on 2010-10-14
mikee@mike-desktop:/home/mike$ ls -ld /home/mike
drwxr-xr-x 62 mike mike 4096 2010-10-13 17:12 /home/mike
mikee@mike-desktop:/home/mike$ cd /home/mike/.gconf
bash: cd: /home/mike/.gconf: Permission denied
mikee@mike-desktop:/home/mike$ chmod u+x /home/mike/.gconf
chmod: changing permissions of `/home/mike/.gconf': Operation not permitted
mikee@mike-desktop:/home/mike$ sudo chmod u+x /home/mike/.gconf
[sudo] password for mikee: 
mikee@mike-desktop:/home/mike$ cd /home/mike/.gconf
bash: cd: /home/mike/.gconf: Permission denied
mikee@mike-desktop:/home/mike$ ls -ld /home/mike/.gconf
drwx------ 4 mike mike 4096 2010-10-13 17:09 /home/mike/.gconf


I forgot to use sudo but then when i used it seemed to take it but still doesn't work???

---

### Post by SeijiSensei on 2010-10-14
> mikee@mike-desktop:/home/mike$ cd /home/mike/.gconf
bash: cd: /home/mike/.gconf: Permission denied

You've got two accounts there -- mikee and mike.  Each won't have permissions in the other's directories unless they share a group, and group permissions are enabled, or world permissions are used.

---

### Post by mlempenau on 2010-10-14
Got it!!  I didn't have mikee in the admin group.  Thanks, I'm in a big learning curve at the moment.  By brain is numb ... :confused: Mike

---

### Post by Rushyang on 2010-10-14
> **SeijiSensei said:**
> You've got two accounts there -- mikee and mike.  Each won't have permissions in the other's directories unless they share a group, and group permissions are enabled, or world permissions are used.

I would like to know how to add another user into admin group..?

---

### Post by matt_symes on 2010-10-15
Hi,

These may help.

[http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/](http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/)
[http://ubuntuforums.org/showthread.php?t=861112](http://ubuntuforums.org/showthread.php?t=861112)

Kind regards

---

