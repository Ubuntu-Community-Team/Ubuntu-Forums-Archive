---
title: "Lost Log In and Password"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by Phil King on 2009-04-28
I updated my version of Ubuntu last night, and it now presents me with a log in screen (it previously booted straight into my desktop). I've tried very combination of my usename and password, but it will not allow me to log on. Any ideas?

---

### Post by lisati on 2009-04-28
A couple of thoughts:
[LIST]
[*]Ubuntu's username and password are case-sentive: "Username" is not the same as "userName" or "USERNAME"
[*]If you put in your real name on the installer's "set up user" page, and didn't change the recommended username, it will be your first name, but in lowercase. Example: if you put your name in as Lisati Leoleo, then the installer will choose lisati as your username.
[/LIST]

---

### Post by lindsay7 on 2009-04-28
Look at this.


[http://ubuntuforums.org/showthread.php?t=1093682](http://ubuntuforums.org/showthread.php?t=1093682)

---

### Post by Didius Falco on 2009-04-28
At the GRub bootup menu, choose Recovery Mode. When the little menu of choices come up, choose the command line shell. This will bring you to a command line with Root privileges.

Once you are at the command line, type ```
ls /home
```This will display your username. Type ```
su username password
``` It will prompt you to add a new password. Pick a new password and reboot.

That should do it.

I hope this helps...

---

### Post by mcduck on 2009-04-28
..just to clean the unnecessary extra step from the process:

"ls /home" to find out the username
"passwd *username*" to change the user's password.

---

### Post by Phil King on 2009-04-28
> **lisati said:**
> A couple of thoughts:
[LIST]
[*]Ubuntu's username and password are case-sentive: "Username" is not the same as "userName" or "USERNAME"
[*]If you put in your real name on the installer's "set up user" page, and didn't change the recommended username, it will be your first name, but in lowercase. Example: if you put your name in as Lisati Leoleo, then the installer will choose lisati as your username.
[/LIST]
      
 
Thanks a lot, changing to lower case did the trick
 
Many thanks for the help

---

