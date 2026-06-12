---
title: "Want full permissions/ownership  on all folders"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by jplyons on 2011-07-21
Hi,
Is there some way I can make my Ubuntu gnome gui allow me to
drag and drop and edit or execute files on any folder.
It keeps telling me I don't have permission so I cant do anything.
I am aware of chown used in terminal for changing ownership
one folder at a time. I want a global permission loosening so
I can work through gnome without worrying about permissions at all.
I can always tighten up security at some other time.

Also, MOST IMPORTANT, where is the login script located in the
filesystem. I need to set PATHS. I am the only user.

Thank you.
Joe

---

### Post by aktiwers on 2011-07-21
Open terminal and type:
```
gksudo nautilus
```Remember there is a reason you need to be root in these areas ;)

Edit:
You would NEVER chmod 777 -R / 
Actually I think it will [COLOR=Red]kill your install[/COLOR]. And it would make your computer extremely unsecure. 
You need to do it as root and if you wanna do it through GUI, opening the filemanager as root should be enough.

---

### Post by AlphaLexman on 2011-07-21
> **jplyons said:**
>  Also, MOST IMPORTANT, where is the login script located in the
filesystem. I need to set PATHS. I am the only user.
Look at...

[LIST]
[*]/etc/profile
[*]the first existance of: ~/.bash_profile, ~/.bash_login, or ~/.profile
[*]~/.bashrc (not really a login file, just for interactive shells)
[/LIST]
However you can set $PATH from the command line by...
```
PATH=$PATH:/path/to/newpath
```Good Luck!

---

### Post by jplyons on 2011-07-21
Hi,
Hi aktiwers

Thanks for your reply.
I found something that you can add to launcher to change permission.
[http://maketecheasier.com/ubuntu-easy-and-quick-ways-to-open-any-files-as-root/2008/02/19](http://maketecheasier.com/ubuntu-easy-and-quick-ways-to-open-any-files-as-root/2008/02/19)

Also, what folder contains login script? When you wrote 
"Remember there is a reason you need to be root in these areas"... what is
the reason?

Thanks again 
Joe

---

### Post by aktiwers on 2011-07-21
> **jplyons said:**
> Hi,

"Remember there is a reason you need to be root in these areas"... what is
the reason?

Thanks again 
Joe

The main reason is security - but a lot of those files need to be configured correct.
When you are root - you are allowed to do anything, even screw everything up. So be careful when editing files. Sometimes it good to make a backup of the file before you edit it, that way its easy to go back if you screw up.

And you could do as in your link if that is easier for you. Some times the terminal is faster to work with in my oppinion. 

You can quickly edit files by simply typing:
```
sudo gedit <drag the file into terminal>
```

Or start writing the path to the file, and hit the <tab> key all the way til you find it.

---

### Post by robertc36 on 2011-07-21
Ubuntu Tweak has scripts to add to right click, one of them is browse as root.

---

### Post by CatKiller on 2011-07-21
> **aktiwers said:**
> ```
sudo gedit <drag the file into terminal>
```

**gksudo** for graphical applications.

To the OP: Running as root all the time is fundamentally insecure, and you will break something eventually. Chowning things will lead to immediate breakage. Just don't.

Running a program as root is something that only needs to be done rarely, and only for specific tasks.

You don't need to do anything as root to change your own PATH.

---

### Post by mcduck on 2011-07-22
> **robertc36 said:**
> Ubuntu Tweak has scripts to add to right click, one of them is browse as root.

...not that you'd need Ubuntu Tweak for that, since the nautilus-gksu extension is available in the repositories as it's own package. just install that and you'll get the option to open things as root in the right-click menu.

---

### Post by sadaruwan12 on 2011-07-22
But if you manage to get your system rooted you need to know what you're doing other wise you'll end up with a dead system.

---

