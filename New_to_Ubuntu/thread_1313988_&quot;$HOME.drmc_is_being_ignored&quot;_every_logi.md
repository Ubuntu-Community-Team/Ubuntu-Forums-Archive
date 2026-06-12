---
title: "&quot;$HOME/.drmc is being ignored&quot; every login"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by wonderfullyrich on 2009-11-04
I think this was caused when I installed kde4-devel, but now every time I login, I'm getting the error message "User's $HOME/.dmrc is being ignored.  This prevents the default session and language from being saved.  File shhould be owned by the user and have 644 permissions.  User's $HOME directory must be owned by user and not writeable by other users."

Rather then logging in normally, as it just spits me back out to the log in screen eventually, I log in via the Failsafe Terminal, run the command 
```
sudo chown -R rjeong:rjeong /home/rjeong/
```
exit the Failsafe terminal, and log in normally.

The problem is that it does this every boot.  In the previous threads I read, [here]("http://ubuntuforums.org/showthread.php?t=371052") and [here]("http://ubuntuforums.org/showthread.php?t=1194908") if you apply the chown or chmod command, there's no more problem.  I'm lost as to how to retain control of my directory on every boot and what script is changing the ownership every time.

Anyone have a lead I can track?  Thanks in advance.

Rich

---

### Post by philinux on 2009-11-04
Follow the instruction here.

[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by wonderfullyrich on 2009-11-04
Is the only option to run these instructions every single boot?  

I ask as everytime I restart and do and ls -atl of /home/ I get 

```
drwxr-xr-x 105 root   root   4096 2009-11-04 14:23 rjeong
drwxr-xr-x  21 root   root   4096 2009-11-04 09:32 ..
drwxr-xr-x   3 root   root   4096 2008-04-13 01:21 .

```

This [instructions]("https://help.ubuntu.com/community/dmrcErrors") do indeed fix the problem, but only for that boot.

How do I figure out what the errant script/process is changing the ownership of my home directory every boot?

Rich

---

### Post by philinux on 2009-11-04
What's in system>prefs>startup applications

---

### Post by wonderfullyrich on 2009-11-04
I included a screenshot of what's coming up in the session preferences.  The only thing that's not in the shot is Volume manager.

Is there a file that this modifies that is easier to view and modify from the command line?

Rich

---

### Post by ukripper on 2009-11-04
> **wonderfullyrich said:**
> I think this was caused when I installed kde4-devel, but now every time I login, I'm getting the error message "User's $HOME/.dmrc is being ignored.  This prevents the default session and language from being saved.  File shhould be owned by the user and have 644 permissions.  User's $HOME directory must be owned by user and not writeable by other users."

Rather then logging in normally, as it just spits me back out to the log in screen eventually, I log in via the Failsafe Terminal, run the command 
```
sudo chown -R rjeong:rjeong /home/rjeong/
```
exit the Failsafe terminal, and log in normally.

The problem is that it does this every boot.  In the previous threads I read, [here]("http://ubuntuforums.org/showthread.php?t=371052") and [here]("http://ubuntuforums.org/showthread.php?t=1194908") if you apply the chown or chmod command, there's no more problem.  I'm lost as to how to retain control of my directory on every boot and what script is changing the ownership every time.

Anyone have a lead I can track?  Thanks in advance.

Rich

Check what umask value is set in ```
cat /etc/profile
```, it should be 022

---

### Post by wonderfullyrich on 2009-11-04
umask is 022 in /etc/profile

---

### Post by ukripper on 2009-11-04
you can try what couple of users have tried in this thread which worked for them - [http://ubuntuforums.org/showthread.php?t=91455&page=4](http://ubuntuforums.org/showthread.php?t=91455&page=4)

Change permission of your home to 700 and on another new logon change it back to 755 and make .dmrc 644

---

