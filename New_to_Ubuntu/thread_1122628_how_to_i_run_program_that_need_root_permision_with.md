---
title: "how to i run program that need root permision without sudo"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by y_garti on 2009-04-11
hi I wrote a script and in the script I use a command that need root permission I use the sudo command but it waits for the user password is there a program that works like sudo but i can give it the password so I can automate my script (without the need of puting the password every time)

---

### Post by waspbr on 2009-04-11
I am not 100% sure, more like 90 but I reckon this command should work

```
chmod a+x <filename>
```

essentially you will be changing the permissions of the use of the file. 

here is a good reference [http://www.washington.edu/computing/unix/permissions.html]("http://www.washington.edu/computing/unix/permissions.html")

gl

---

### Post by mvalviar on 2009-04-11
I hope you know what you are doing. You can open a root terminal for you script. ```
sudo su
```

---

### Post by iponeverything on 2009-04-11
As root, you can turn on the suid bit for command that you needed sudo for and it should eliminate the need for sudo in your script.

---

### Post by Gen2ly on 2009-04-11
Changing the suid of a command can be a huge security-risk, be very very careful.  If you're tired of typing in a password all the time you can increase sudo's timeout:

[http://ubuntuforums.org/showpost.php?p=4767816&postcount=5](http://ubuntuforums.org/showpost.php?p=4767816&postcount=5)

If I remember correctly you can set it to 0 and sudo timeout is never.  Again I'd recommend against this.  Even if you are the only person on the computer, a good hacker might be able to make use of this.

---

### Post by glennric on 2009-04-11
If you are executing the script yourself, at some point you are going to have to enter a password.  You can just use "sudo scriptname", and enter the password at the beginning to avoid having to enter it later.

If you are trying to have your script run unattended at some specified time you can add the script to the root crontab.  Then the script will be executed by root and you will not have to enter your password.

---

### Post by iponeverything on 2009-04-11
> **Dirk.R.Gently said:**
> Changing the suid of a command can be a huge security-risk, be very very careful.  If you're tired of typing in a password all the time you can increase sudo's timeout:

[http://ubuntuforums.org/showpost.php?p=4767816&postcount=5](http://ubuntuforums.org/showpost.php?p=4767816&postcount=5)

If I remember correctly you can set it to 0 and sudo timeout is never.  Again I'd recommend against this.  Even if you are the only person on the computer, a good hacker might be able to make use of this.

in the case of a local escalation, i wouldn't necessaryly classify it as "huge".  i would put a poorly chosen password much higher on the list -- this combined ubuntu's use of sudo for primary account -- makes a lucky guess on the user account direct path to root.  

I can understand conversations that must have been taking place regarding sudo and ease of use and why the compromise was made -- but it does make ubuntu an easy target for a brute force attack if someone knows the username.  In essence a weak user account is a weak root account.  It used to be that escalation required some effort..

---

### Post by Hospadar on 2009-04-11
When you say automated, do you mean like it runs every day at 5, every 5 minutes, etc, etc?

If so, you should do none of the above and use cron to schedule it to run as root 
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

You should read up on how to make cron jobs, but the basic thing to get a cron job that runs as root is
sudo crontab -e
<now add your cron job and save>

This will safely run the command/script/whatever as root whenever you scheduled it to run.  If the job has errors, they will be sent to your local mail account, which you can check with the "mail" command (it'll probably tell you you need to install something to use the command, go ahead and do that)

---

