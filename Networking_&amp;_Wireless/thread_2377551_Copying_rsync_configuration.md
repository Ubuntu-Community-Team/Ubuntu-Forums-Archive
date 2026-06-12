---
title: "Copying rsync configuration"
date: 2017-11-14
forum: Networking &amp; Wireless
---

### Post by valipost on 2017-11-14
Hi there :)
Due to work, I have to learn a lot about Linux recently.
I have a script running every day thanks to crontab and it works fine  on a xubuntu 12.10 VM. I want to create a copy of this VM on a clean  Xubuntu 16.04, and almost everything works but this script, because of a  rsync issue.  
```
rsync -azh --delete vbackup@perforce:/var/p4depot /tmp/p4depot

```  
This line on the original server works fine, but on the clone I'm  creating, the script asks me vbackup's password. It happens several  times during the full script. Since I want to run it with my crontab, I  don't want to enter the password every time rsync is called!
I've read it has to do with ssh configuration, but I don't know how to  copy the ssh configuration for my rsync to work without modifying all  the VM it's connected to.
From what I saw it's mainly command line, but I'll ask anyway : is it possible to just copy/paste the files from /home/account/local/.ssh/ for it to work?
I'm a real linux beginner, so please be exhaustive if there are path or command to run, thank you :)!

---

### Post by SeijiSensei on 2017-11-14
You should be able to fix the problem by copying the contents of /home/vbackup/.ssh on the original server and make an equivalent directory on the new machine.  That directory contains the public and private keys belonging to the vbackup user which are used to authenticate to the server.

---

### Post by valipost on 2017-11-15
Ok, I found what was wrong. My python script was called with 
[PHP]sudo python3.5 myscript.py [/PHP]
The sudo was there because I had permission errors without it. I solved the permission errors, removed the sudo and the script stopped asking for my password.
In the end I still set up the ssh again, I found this thread very helpful : [https://superuser.com/questions/555799/how-to-setup-rsync-without-password-with-ssh-on-unix-linux](https://superuser.com/questions/555799/how-to-setup-rsync-without-password-with-ssh-on-unix-linux)

Thanks :) (Didnt find how to mark my topic solved)

---

