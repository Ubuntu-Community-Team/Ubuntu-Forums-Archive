---
title: "not a sudoer anymore"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by lucafrangi on 2009-01-29
hello everyone,

need help on a very simple and [stupid] problem:

just installed ubuntu, copied all data from former OS and enjoyed ubuntu until I had the [bad] idea to unlock the user settings panel, activate the root user and give it a psw. 

Then I had a [second] very bad idea to deny administration privileges to the default user (myself) I created when installing ubuntu.

The [third] bad idea was to reboot the system: it seems like that root can't login on ubuntu...
 
So I am now a simple user, can't sudo and can't administer the system.
Any idea how to sort out the matter? or any helpful thread?

luca@luxx:~$ sudo passwd root
[sudo] password for luca: 
luca is not in the sudoers file.  This incident will be reported.
luca@luxx:~$ 

thanks for any help
luca

---

### Post by epswinde on 2009-01-29
If I read correctly, you have created a root password.  This is how you should fix it.

Open a terminal.  Type
```
su
```
and enter the root password you selected during install.
This will start a root shell.  Notice how the prompt now ends with a # instead of $.

Next, you must edit the /etc/group file.  in the root shell, type:
```
nano /etc/group
```

In this file, you will see a rather long list.  Each line denotes a group of users.  formatted like this;  ```
group:passwd:GID:users
```

find the line that says:
```
admin:x:119:
```
(don't worry so much about the group id number, just leave it alone if its not 119, although i'd imagine its the same)
add your username after the last colon so it looks like:
```
admin:x:119:luca
```
you'll need to logout for changes to take effect.  Hope this helps.

---

### Post by lucafrangi on 2009-01-29
found the line
```
admin:x:115:root:
```
and changed to
```
admin:x:115:luca:
```
then WriteOut and Exit
and rebooted the system

still I can't unlock the window in

System:Administration:Users and Groups

and user properties:user privileges is now a blank window, nothing listed.

Funny is that if I revert the /etc/group file to its original, still is the user privilege dialog a blank window 
any clue?
tx anyway

---

### Post by epswinde on 2009-01-29
> **lucafrangi said:**
> found the line
```
admin:x:115:root:
```
and changed to
```
admin:x:115:luca:
```
then WriteOut and Exit
and rebooted the system

still I can't unlock the window in

System:Administration:Users and Groups

and user properties:user privileges is now a blank window, nothing listed.

Funny is that if I revert the /etc/group file to its original, still is the user privilege dialog a blank window 
any clue?
tx anyway

Change the line to 
```
admin:x:115:root,luca
```
using the same steps as before.  the user list needs to be delineated by a comma, and you want both your root user and your default user (luca) to be there.

for more info:
```
man group
```

---

### Post by lucafrangi on 2009-01-30
done and it works, especially after I omitted the colon at the end of the line...
thanks alot for your help

---

