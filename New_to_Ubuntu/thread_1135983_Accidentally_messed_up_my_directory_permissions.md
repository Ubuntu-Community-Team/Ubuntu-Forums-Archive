---
title: "Accidentally messed up my directory permissions"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by Wackjob on 2009-04-24
I am new to Linux and Ubuntu. Anyhow, I read that the home directory permission should be changed to 700, because the default permission is not very secure. I went into the terminal to try tweaking the permissions, and used "cd .." until it brought me to the top directory. I did sudo chmod 700 ./home. After that, I noticed that I was blocked from doing pretty much anything. For a secure desktop system, what should I set that directoy permission to? 

Also, is there a different "home" folder that is supposed to be set to 700 for optimal security? 

Lastly, are there any programs for Linux like Comodo Firewall? Something that would notify me whenever anything tries to connect to my computer or my computer tries sending outbound info?

Thanks in advance!

---

### Post by duruttye on 2009-04-24
Well, I don't know what and where you heard that, but the default configurations usually are pretty good, as far as security and firewall protection.

There is a firewall installed, called iptabels, whatever you install after, that you think it is a firewall will be a front end to iptables. A  commonly used front end applications to handle iptables: firestarter.

As far as your home folder:

press Alt-f2
insert: gksu nautilus
put in your password
in the new nautilus find your /home folder
right click, properties
permissions
at owner, find your user name
allow read and write

I'm a newbie user, too, so if someone can tell you more, please do so!

Hope this helps!

You can find out some more at:
[http://ubuntuforums.org/showthread.php?t=138356](http://ubuntuforums.org/showthread.php?t=138356)

by the way, typing into google chown 700 gave a few short messages, a few of them were: chmod 700 - do NOT do this to your /home directory!!
Pretty funny

---

### Post by cariboo on 2009-04-24
The permissions for /home should be 755, I have my home directory permissions set to 750. What you want to do is to set the permissions of /home/<user> where <user> is your username without the brackets.

the first thing you have to do is repair the permissions on /home. Start in recovery mode, press esc at the grub menu and select recovery. At the menu select drop to root prompt. Once at the prompt type:

```
chmod -R 755 /home
```

this will set the permissions of all the directories in /home to 755 including all the directories in your home directory. If you want to set the premissions of your home directory to 700 at the prompt type:

```
chmod -R 700 /home/<user>
```

you will get an error that it can't change the permissions for ~/.gvfs, that is normal.

When you are finished type:

```
exit
```

then select resume to continue to your desktop.

---

### Post by theozzlives on 2009-04-24
your home directory is supposed to be set to 755, use sudo no need to start nautilus in root mode

---

### Post by Wackjob on 2009-04-24
Thanks. It is fixed now.

---

### Post by Rocket2DMn on 2009-04-24
Typically files don't have executable permissions, so most of the files will have 644 or 600 permissions applied to them.  It is perfectly acceptable to have the folders with executable permissions though.  Removing the executable permissions on files means that when you double click them, you won't be prompted to run them, they will just open with whatever the default application is.

---

