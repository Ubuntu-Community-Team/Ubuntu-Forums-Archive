---
title: "Terminals are running as root!"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by nathan28 on 2010-07-31
(Running Ubuntu 10.04 64-bit)

I left my laptop with the screen up and went to work. I came back home from work. Needless to say, one of my cats had opened so many terminal windows I couldn't even CTRL+ALT+F1 to kill Xorg and had to hold down the power button instead.

I logged in as the regular user, the only login I have. Did a sudo mount of an ISO and *didn't* get prompted for the root password. I got worried, then did a cp of a desktop file, chmod it to 700, and then was able to run an rm on it without getting prompted for the root password.

What happened? How do I stop this? Is my Windows partition running .jpgs with AIDS as executables behind my back right now? PLS HALP.

---

### Post by Terl on 2010-07-31
> **nathan28 said:**
> (Running Ubuntu 10.04 64-bit)

I left my laptop with the screen up and went to work. I came back home from work. Needless to say, one of my cats had opened so many terminal windows I couldn't even CTRL+ALT+F1 to kill Xorg and had to hold down the power button instead.

I logged in as the regular user, the only login I have. Did a sudo mount of an ISO and *didn't* get prompted for the root password. I got worried, then did a cp of a desktop file, chmod it to 700, and then was able to run an rm on it without getting prompted for the root password.

What happened? How do I stop this? Is my Windows partition running .jpgs with AIDS as executables behind my back right now? PLS HALP.

Well, the desktop stuff is yours (owner) most likely and I believe you can mount without sudo.

Does your prompt have a $ or a # ?

---

### Post by nathan28 on 2010-07-31
> **Terl said:**
> Well, the desktop stuff is yours (owner) most likely and I believe you can mount without sudo.

Does your prompt have a $ or a # ?


It's a $. The problem is that I'm not getting prompted for the password on *any* command I run with sudo (even if I close the terminal window) and have full root access with any new terminal on any command. Same if I ctrl-alt-F1--I've got root privileges without entering a password or using a sudo.

---

### Post by sandyd on 2010-07-31
> **nathan28 said:**
> It's a $. The problem is that I'm not getting prompted for the password on *any* command I run with sudo (even if I close the terminal window) and have full root access with any new terminal on any command. Same if I ctrl-alt-F1--I've got root privileges without entering a password or using a sudo.
try
```

mkdir /testing_new

```
if you can do that, theirs a definate problem.

if you can't, everythings still fine.

if you can, run
```

groups
```
and post output.

if the root group is supplimentary,
use
```

gpasswd -d USERNAME root
```

---

### Post by marshmallow1304 on 2010-07-31
I *think* normal users are allowed to delete root-owned files if the user owns the directory where the file is.

Try
```
less /etc/sudoers
```
as a normal user to make sure you actually have root permissions.

---

### Post by chriswyatt on 2010-07-31
I think your cat is an elitist computer hacker.

---

### Post by nathan28 on 2010-08-01
> **chriswyatt said:**
> I think your cat is an elitist computer hacker.

I can no longer replicate the problem, which makes me feel like a mac user. Can't mkdir at / or less the sudoers without a sudo + password. The only other issue I've noticed is that my chromium profile got corrupted, so... ghost process? That survived a hard reboot?  #-o

Time to backup. And use the "lock screen" function.

---

### Post by mcduck on 2010-08-01
> **marshmallow1304 said:**
> I *think* normal users are allowed to delete root-owned files if the user owns the directory where the file is.
No, they aren't. But nathan28 didn't create a root-owned file, it was owned by his normal user and he only changed the *permissions*.

Removing a file you own, regardless of it's permissions, doesn't require root privileges.

Actually I don't see anything here that would really indicate that the terminal would give root access without a password, as the user prompt indicates a normal user, not root, and doing things that require root privileges like creating directories in / doesn't work...

Also, the 15 min timeout on sudo isn't tied to any particular terminal session or window, the same timeout works regardless of if you close the terminal window and open it again or switch to a TTY.

---

### Post by da burger on 2010-08-01
> **mcduck said:**
> No, they aren't. But nathan28 didn't create a root-owned file, it was owned by his normal user and he only changed the *permissions*.

It IS the directory permissions that are important, not the file permissions. To test this, in your home directory run the following:
```
touch file
chmod 000 file
sudo chown root:root file
rm file
```

(Authenticate the sudo command in there of course)

It will ask you if you want to remove the file and then it will be gone.

---

### Post by sisco311 on 2010-08-01
EDIT: da burger beat me to it.


To remove (rename, create) a file from a directory you need write permission for the _directory_ and execute permission for the directory and its parent directories.


[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

