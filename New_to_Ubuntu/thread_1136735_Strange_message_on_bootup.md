---
title: "Strange message on bootup"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by Charlie Chick on 2009-04-25
Hello Everybody,

Just done a fresh install of 9.04 and am now getting a strange error message on bootup:

"User's $HOME/.drmc is being ignored. File should be owned by the user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users"

Can anybody help me with this?

Many thanks,

Charlie

---

### Post by spiderbatdad on 2009-04-25
well that seems strange. I can tell you mine has permissions 600, and there is virtually nothing in it anyway. Assuming you can get to your desktop, edit the file with a few simple terminal commands.
Go to Applications>>Accessories>>Terminal

type in:```
ls -al
```this will list all the files, including hidden files, in your home directory. Hidden filenames are preceeded by a dot. Scroll to the .drmc file and look at the beginning of the line where the permissions are...something like rw-r--r-- for example. Those are three groups of permissions: owner, group, others...and the permissions themsevles:read, write, execute. Read=4 write=2 execute=1. The above example would be 644. Use this command to set the permissions:```
chmod 644 ~/.drmc
```There are other ways to edit permissions. I think this is the easiest.

If the problem is ownership, you may have to put sudo in front of the chmod command above, and change ownership with the following:```
sudo chown username:username /home/username/.drmc
``` username in that command is the username you are operating under, and should be associated with user id 1000. Run ```
id
```and verify that you are uid 1000.

---

### Post by gandaran on 2009-04-25
try this to fix the problem, run in terminal
```
sudo  chmod   -R  750  /home/'your username'
```

---

### Post by spiderbatdad on 2009-04-25
> **gandaran said:**
> try this to fix the problem, run in terminal
```
sudo  chmod   -R  750  /home/'your username'
```

PLEASE do not run this command! This will certainly screw up your home directory.

---

### Post by gandaran on 2009-04-25
> **spiderbatdad said:**
> PLEASE do not run this command! This will certainly screw up your home directory.
nope, it wont!, and probably is the only one that can fix it!
I  have used it to fix the same issue!

---

### Post by Charlie Chick on 2009-04-25
Thanks for your suggestions. I've just tried your suggestion of chmod 644 ~/.drmc and I get a "cannot access ..... no such file or directory" even though I can see it in the output of ls -al. What am I doing wrong?

Thanks!

---

### Post by Charlie Chick on 2009-04-25
> **gandaran said:**
> try this to fix the problem, run in terminal
```
sudo  chmod   -R  750  /home/'your username'
```

Just tried this and got a "permission denied" error message.

---

### Post by spiderbatdad on 2009-04-25
How does making a recurrsive file permissions change to the user's entire home directory fix an error message that occurs in a single file? How does changing the default file permissions Ubuntu creates, 755 for /home/user, fix an error in a single file with out causing other problems?

---

### Post by spiderbatdad on 2009-04-25
typo...file name is dmrc

---

### Post by Charlie Chick on 2009-04-25
Guys, thanks for the info. Must go out now - will try the suggestions this evening.

Charlie

---

### Post by gandaran on 2009-04-25
> **spiderbatdad said:**
> How does making a recurrsive file permissions change to the user's entire home directory fix an error message that occurs in a single file? How does changing the default file permissions Ubuntu creates, 755 for /home/user, fix an error in a single file with out causing other problems?
that error is not on the single file, if it was then you would just delete /home/user/.dmrc file and should fix the problem but it wont.

Charlie Chick
```
sudo  chmod   -R  750  /home/'your username'
```
you did fill in your username?

here's another one you can try

> sudo chown -R 'user':'user' /home/'user'

---

### Post by spiderbatdad on 2009-04-25
my apologies to gandaran. I am prone to overreactions. I have seen it is generally a bad idea for new user to make -R permission changes to directories. Recurrsively editing user created folders is one thing. This type of change to a default directory is another. While I know *nix user generally don't distinguish directories and folders, I generally refer to system created as directory and user created a folder. More output is needed to fix this error. Like ```
ls -l /home
ls -al ~/
```

The correct permissions for .drmc are 644, so the command to fix this error is ```
chmod 644 ~/.dmrc
```but it may very well be that the poster is not uid=1000. So chown -R may be in order for /home/user. Not chmod -R 750 /home/user. Hard to say without more info.

---

### Post by philinux on 2009-04-25
Community documentation on this.

[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by Charlie Chick on 2009-04-26
Update: just booted up and the message has gone! Don't quite know why as when I tried lister's suggestions they didn't appear to work but it looks as if they have after all. The only shame is that I don't which solution did the trick.

Thanks to all who replied.

Charlie

---

