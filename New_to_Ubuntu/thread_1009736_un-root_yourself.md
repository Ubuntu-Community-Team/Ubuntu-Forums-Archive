---
title: "un-root yourself"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2008-12-12
how do you de-sudo or undo the sudo when you are running as sudo for 10-15 minutes?

---

### Post by adult swim on 2008-12-12
if you are running sudo you are only root for one command at a time.  you stop being root after you enter the command and you arent root again until you prefix a command with sudo.

---

### Post by GuitarRocker2562 on 2008-12-12
If you ran sudo commands then you don't need to do anything.

---

### Post by shiningkenmonster on 2008-12-13
wait, i thought you can't run as root as 'su' on ubuntu. so you have to use sudo to run as root temporary. the effect last for 10-15 minutes. I just tried it. I opened 'Software Sources', than entered my password. than I opened gpart, which requires my password, but it didn't. cause i have access for it for 10-15 minutes.

i even opened firestarter. it didn't require my password. it will after 15 minutes.

---

### Post by adult swim on 2008-12-13
if you use sudo, there is a default 15 minute period where you do not have to enter in your password again to when using sudo.  this doesnt  mean that you are running in root though.  if you try to run any command in the terminal that needs root permissions, it will not let you unless you put in sudo first.
EDIT: if  you would like to take remove the sudo timeout feature, see this thread
[http://ubuntuforums.org/showthread.php?t=183418](http://ubuntuforums.org/showthread.php?t=183418)

---

### Post by lisati on 2008-12-13
As previously mentioned, if you're using "sudo" in front of each command that 'needs' root privileges, no worries, you'll need your password in 10-15 mins. If however, you have the "#" prompt instead of the "$" prompt, the "exit" command should suffice.

---

### Post by shiningkenmonster on 2008-12-13
well, i have this friend who used to use opensuse and a mac. he is a computer science major. i believe he knows his bash command lines. we would always joke around with each other. but i just dont trust him for what he'll do to my computer if i let him burrow it for 5 minutes after i run as sudo.

is there a way to undo the sudo instantly? without having to change my time stamp periods?

---

### Post by adult swim on 2008-12-13
it would be easir just to edit your sudoers file, but you can kill the time out each time you run sudo.  say you run sudo command and it runs.  to make it so you need to enter your password again you can  run sudo -K to kill the timeout.  the next time you run sudo youll need to enter your password again.

---

### Post by shiningkenmonster on 2008-12-13
hmm, i already did a
> sudo -K

all the applications that i listed above still open without having to use a password. unless i wait 10-15 minutes later.

---

### Post by bapoumba on 2008-12-13
The graphical applications do not share the timestamp with any terminal window. sudo -k works only for the current terminal.

You can ask, by editing the sudoers file, that the timestamp be zero, and the pwd asked every time (either from a terminal with sudo or a graphical app with gksudo):
[QUOTE=man sudoers]timestamp_timeout
    Number of minutes that can elapse before sudo will ask for a passwd again. The default is 5. Set this to 0 to always prompt for a password. If set to a value less than 0 the user's timestamp will never expire. This can be used to allow users to create or delete their own timestamps via sudo -v and sudo -k respectively. [/QUOTE]
[http://linux.die.net/man/5/sudoers](http://linux.die.net/man/5/sudoers)

---

### Post by Paqman on 2008-12-13
> **shiningkenmonster said:**
> i just dont trust him for what he'll do to my computer if i let him burrow it for 5 minutes after i run as sudo.


Log him into the guest session. He won't be able to do any damage. The guest's home folder is even in /tmp, so it'll be gone next reboot.

---

### Post by billgoldberg on 2008-12-13
> **shiningkenmonster said:**
> how do you de-sudo or undo the sudo when you are running as sudo for 10-15 minutes?

```
sudo -k
```

I believe.

Read this if you want to set the sudo timeout to 0:

[http://linuxowns.wordpress.com/2008/10/21/change-gksudo-timeout/](http://linuxowns.wordpress.com/2008/10/21/change-gksudo-timeout/)

---

### Post by billgoldberg on 2008-12-13
> **shiningkenmonster said:**
> hmm, i already did a


all the applications that i listed above still open without having to use a password. unless i wait 10-15 minutes later.

note that sudo -K isn't the same a sudo -k

---

### Post by rlunger on 2008-12-13
> **shiningkenmonster said:**
> wait, i thought you can't run as root as 'su' on ubuntu. so you have to use sudo to run as root temporary. the effect last for 10-15 minutes. I just tried it. I opened 'Software Sources', than entered my password. than I opened gpart, which requires my password, but it didn't. cause i have access for it for 10-15 minutes.

i even opened firestarter. it didn't require my password. it will after 15 minutes.

you can become root indefinitely via:

    sudo su 

and then entering your user password.

If you wish to set up root with a password, and want to be able to become root without 'sudo', just set the root password via:

    sudo su
    [enter user password]
    passwd
    [enter root password]
    [enter root password again]

Now, you can become root using 'su' instead 'sudo' for each command.
I would suggest not setting up a root password and just becoming root via 'sudo su' if you must.  Note that K/X/Ubuntu does not allow you to login as root at the login window.  You have to enable that with your settings manager.

Regards.

---

