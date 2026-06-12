---
title: "Logging in as root?"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by Curtiee on 2009-10-17
Okay, it's me again! :$

I'm going to install XAMPP (well, LAMPP) onto Ubuntu, and on the site ([http://www.apachefriends.org/en/xampp-linux.html#377](http://www.apachefriends.org/en/xampp-linux.html#377)) it says I should type```
su
``` to login as the root.

Is there a default root password, because I don't even remember creating one... Or is there maybe a way to change it, because I kinda need to install this ):

Thanks guys! (L)

---

### Post by ubundave on 2009-10-17
try sudo -s

---

### Post by Bachstelze on 2009-10-17
Use [font=monospace]sudo -i[/font] instead.

*EDIT: **NOT** sudo -s.*

---

### Post by Sam on 2009-10-17
Or```
sudo su
```

---

### Post by starcannon on 2009-10-17
It's always good too know why one uses flag x instead of flag y.
```
man sudo
```
**sudo -i:**
-i  The -i (simulate initial login) option runs the shell specified in
           the passwd(5) entry of the user that the command is being run as.
           The command name argument given to the shell begins with a &#8216;-&#8217; to
           tell the shell to run as a login shell.  sudo attempts to change to
           that user&#8217;s home directory before running the shell.  It also ini&#8208;
           tializes the environment, leaving TERM unchanged, setting HOME,
           SHELL, USER, LOGNAME, and PATH, and unsetting all other environment
           variables.  Note that because the shell to use is determined before
           the sudoers file is parsed, a runas_default setting in sudoers will
           specify the user to run the shell as but will not affect which
           shell is actually run.

** sudo -s:**
-s  The -s (shell) option runs the shell specified by the SHELL envi&#8208;
           ronment variable if it is set or the shell as specified in
           passwd(5).

---

### Post by JoshuaRL on 2009-10-17
Is there any reason why you need to be logged in as root?  Can't you just use regular sudo/gksu here?

---

### Post by starcannon on 2009-10-17
> **JoshuaRL said:**
> Is there any reason why you need to be logged in as root?  Can't you just use regular sudo/gksu here?
Good call, after reading the directions the OP is following, it looks like sudo would be sufficient for the purpose. Doesn't look like a graphical sudo is required(gksudo).

---

### Post by JoshuaRL on 2009-10-17
> **starcannon said:**
> Good call, after reading the directions the OP is following, it looks like sudo would be sufficient for the purpose. Doesn't look like a graphical sudo is required(gksudo).

Thanks, wasn't sure if it was required for this app.

@ the OP:

Please be careful with logging in as root, either from the command line, or by enabling graphical root login.  When you do, there are little to no safeguards against really hurting your system.  That's what limited user accounts and sudo are all about.  For more info, please read this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Curtiee on 2009-10-17
> **Sam said:**
> Or```
sudo su
```
I used this in the end, thank you very much! (':

> **starcannon said:**
> It's always good too know why one uses flag x instead of flag y.
```
man sudo
```**sudo -i:**
-i  The -i (simulate initial login) option runs the shell specified in
           the passwd(5) entry of the user that the command is being run as.
           The command name argument given to the shell begins with a ‘-’ to
           tell the shell to run as a login shell.  sudo attempts to change to
           that user’s home directory before running the shell.  It also ini&#8208;
           tializes the environment, leaving TERM unchanged, setting HOME,
           SHELL, USER, LOGNAME, and PATH, and unsetting all other environment
           variables.  Note that because the shell to use is determined before
           the sudoers file is parsed, a runas_default setting in sudoers will
           specify the user to run the shell as but will not affect which
           shell is actually run.

** sudo -s:**
-s  The -s (shell) option runs the shell specified by the SHELL envi&#8208;
           ronment variable if it is set or the shell as specified in
           passwd(5).
Thanks very much for the explanation, but I ended up using ```
sudo su
```

> **JoshuaRL said:**
> Is there any reason why you need to be logged in as root?  Can't you just use regular sudo/gksu here?
I'm extracting a .tar.gz to /opt/ which only a root can write to.
> **starcannon said:**
> Good call, after reading the directions the OP is following, it looks like sudo would be sufficient for the purpose. Doesn't look like a graphical sudo is required(gksudo).
Like I said above, I needed to write to a folder I couldn't do as a limited user ):
> **JoshuaRL said:**
> @ the OP:

Please be careful with logging in as root, either from the command line, or by enabling graphical root login.  When you do, there are little to no safeguards against really hurting your system.  That's what limited user accounts and sudo are all about.  For more info, please read this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
Thanks very much. I have now extracted the files, and closed the terminal to terminate (u c wot i did der?!) the root session.

Thanks very much guys <3

---

### Post by coldReactive on 2009-10-17
> **Curtiee said:**
> I'm extracting a .tar.gz to /opt/ which only a root can write to.

I was able to sudo cp into the opt directory when I had to reinstall flash for firefox 3.5 ubuntuzilla in amd64.

[COLOR="White"]1000th bean.[/COLOR]

---

### Post by girish24 on 2009-10-17
you have to give a root password separately after installing linux. 

Go to System->Administration->Users and groups 
And enable ur root account and it requests for password.

This will be ur root password, and u have to enter it if u use 'sudo' command...

---

### Post by SunnyRabbiera on 2009-10-17
avoid logging in as root, its not good to log in as root

---

### Post by Devon64327 on 2009-10-17
i'm sorry but isn't this a don't? 12) Post how to allow root logins[http://ubuntuforums.org/showthread.php?t=885580   [COLOR=Black]  [/COLOR]]("http://ubuntuforums.org/showthread.php?t=885580")[COLOR=Black]_I don't mind and i dont see the problem but i had cake now im hyper and bored_[/COLOR][URL="http://ubuntuforums.org/showthread.php?t=885580"]       errr... cant stop this link uunderlining
[/URL]

---

### Post by ubundave on 2009-10-18
Oh, i really forgot the -i ...

---

### Post by igknighted on 2009-10-18
> **Devon64327 said:**
> i'm sorry but isn't this a don't? 12) Post how to allow root logins[http://ubuntuforums.org/showthread.php?t=885580   [COLOR=Black]  [/COLOR]]("http://ubuntuforums.org/showthread.php?t=885580")[COLOR=Black]_I don't mind and i dont see the problem but i had cake now im hyper and bored_[/COLOR][URL="http://ubuntuforums.org/showthread.php?t=885580"]       errr... cant stop this link uunderlining
[/URL]

I believe that has been interpreted to mean no graphical root logins, and no enabling the root account.  Technically there are differences between the two, but that gets a little bit trivial for this forum.

---

### Post by JoshuaRL on 2009-10-20
> **Curtiee said:**
> 
Like I said above, I needed to write to a folder I couldn't do as a limited user ):

Thanks very much guys <3

Glad you found something that worked.

By way of explanation, logging in as root is very dangerous.  You can change, delete, or do anything.  Even if it's by accident.  I'm a moderately knowledgeable user and I've jacked stuff up before that way.  So that word of caution is necessary.

Sudo means "Super-User Do" and lets users in the sudoers file have temporary root access.  You can do everything root can, but after 15 minutes of inactivity it takes that away from you.  Limited user accounts doesn't mean never have control, that's what's great about Linux.  You still need to be careful, but it keeps you safer by minimizing the time available to jack your system up.

Ubuntu by default doesn't have a root login set up.  That's a difference from Debian.  Here on the forums, and in most support channels, you'll find that people will tell you that in almost all cases it's better to use sudo than a root login.  If you know what you're doing (and typically have large batches of things to do) than the consequences are on you.  But, while your solution definitely worked and I salute you for it, in this case the safer thing to do would have been to use sudo.  You can do whatever you would in root, but just put sudo in front of it.

---

