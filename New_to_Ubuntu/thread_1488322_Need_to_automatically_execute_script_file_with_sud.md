---
title: "Need to automatically execute script file with sudo"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by anewguy on 2010-05-19
I have searched the net and the forum, and as best I can tell I've got this set up the way things said to.  What I have is a script file that needs to be executed at login, and in that script file is a command with "sudo ".

Here's the script /usr/local/bin/hp3970-chmod.sh

```
echo Change permissions on scanner > hp3970-chmod.log
sudo chmod 777 /dev/bus/usb/001/010 >> hp3970-chmod.log
ls -al /dev/bus/usb/001/010 >> hp3970-chmod.log
```


Here's how the sudoers file is set:


```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
Cmnd_Alias HP3970CMD=/usr/local/bin/hp3970-chmod.sh
dave ALL=NOPASSWD: HP3970CMD
```


I tried creating a .bash_profile file for user dave in /home/dave containing only the following:

```
./usr/local/bin/hp3970-chmod.sh
```

but upon logout/login the script appears not to execute since the permissions on the USB device didn't change and the log file is not created.

There is nothing added to syslog indicating any errors.

Help??

Thanks in advance!
Dave ;)

---

### Post by Ozymandias_117 on 2010-05-20
I believe it's because you have the . at the beginning ( **.**/usr/local/bin/hp3970-chmod.sh ) I think that is making it look in /home/user/usr/local/bin since it should default to ~ Try removing the . so it starts at /

---

### Post by anewguy on 2010-05-20
> **Ozymandias_117 said:**
> I believe it's because you have the . at the beginning ( **.**/usr/local/bin/hp3970-chmod.sh ) I think that is making it look in /home/user/usr/local/bin since it should default to ~ Try removing the . so it starts at /

Well, the script itself is located in /usr/local/bin, so I know I need the path.  I put the "." at the beginning since that is what I do at the command line to execute a script (./xxxxxx.sh).  I thought that to indicate your home folder it was either /home/"userid" or "~".

Perhaps the .bash_profile name is incorrect.  Perhaps the syntax of the statement that goes in the login script to execute a script is different (note that .profile looks very different from my "./path-to-file/file.sh").

Dave ;)

---

### Post by lukeiamyourfather on 2010-05-20
If you call the script or put the whole thing in /etc/rc.local then you don't have to worry about putting sudo in front of anything. The rc.local file is run when the system starts as root. Cheers!

---

### Post by Ozymandias_117 on 2010-05-20
the "." when you execute a script just tells it to look in the current directory, since you've spelled out the directory, you don't need the ".".

In a terminal "." means "The directory I'm currently working in" and ".." means "The parent directory of the directory I'm working in" so, if I was in "/home/Ozymandias/scripts" and typed "./myscript.sh" it would be the same as typing "/home/Ozymandias/scripts/myscript.sh".

The problem you're running into, is that it's working directory is "~" so when you type "./usr/local/bin/script.sh" it is looking in "/home/user/usr/local/bin/script.sh" instead of "/usr/local/bin/script.sh" This is because the "." at the beginning tells it to start from the directory you're currently in.


Edit: added quotes around the path names so it was easier to read.

---

### Post by lukeiamyourfather on 2010-05-20
Also you don't need the period in front of the path for the script. Using the period in front of the path means look in the current directory for the script or command. Imagine a script is in /usr/local/bin called foo.sh and see examples below.

```

cd /usr/local/bin
./foo.sh
```

```

/usr/local/bin/foo.sh

```

Both of those will do the same thing, note there's no period in front of the path when calling the script with the explicit path.  If you run a command like foo.sh by itself without any path or period it looks for foo.sh in the system path ($PATH). Cheers!

---

### Post by anewguy on 2010-05-20
Okay, I did some testing and indeed if you specify the entire path and filename you don't need "./".  I've just never understood why, if you are in the directory the file exists in, you can't just say "filename" instead of "./filename" (does this mean in the current directory (.) execute (/) the named file?).

As for the rc folders, I thought about that, but since /dev/bus/usb will be dynamically allocated at boot based on what is connected, I don't know where in the initialization routines the /dev/bus/usb devices get populated, and hence didn't know where I need to put the execute for changing the permissions on one of them.  I'm sure it would go in rc2.d, but also know that it appears all the scripts go in init, then links are set in the various rcx.d directories, and I've been having a *heck* of a time trying to set up a link that looks like the rest when I "ls" the directory.

Dave ;)

---

### Post by anewguy on 2010-05-20
Okay, I've gotten a little further, but I still need some help.

I had to change the sudoers file by removing the command alias and instead specifying the entire path/file on the user "dave" statement.  This now allows me to manually execute the script in a terminal window without specifying sudo or supplying a password for the imbedded sudo chmod statement.

What I still need help on, because I apparently don't understand it all, is how to make the script get executed automatically when I log in.  I've tried creating a .bash_login file with /usr/local/bin/hp3970-chmod.sh as the only line in it, but it apparently does nothing at login.  I then deleted that file and added the line to the end of the .profile file - again it doesn't seem to do anything.  I can't figure out what I'm doing wrong, and I've been searching the forum and the net all night to try to figure this out.

WHERE do I put the line "/usr/local/bin/hp3970-chmod.sh" so that when I log in (using gnome) it is executed?  I just can't figure this out.  Is there a different syntax in some sort of login file versus just putting in what I have?

I hope I'm saying things in the correct language, so I'll try to demo what I want here:

- user enters userid and password to log in to Ubuntu
- as part of that login process, the shell script is executed, invisible and with no interaction with the user
- the user now is logged in

I hope that helps rather than confuse, as I am confused enough on this right now.  I've tried checking for ubuntu login script help on the net and in the forum, and it all has reinforced what I thought - it needs to go in .bash_login file and the file needs to be set to be executable.  The only problem is that it isn't doing anything.

Please help - I'm really lost here!

Thanks!
Dave ;)

---

### Post by Nythain on 2010-05-20
i dont remember exactly where (since i dont generally run gnome) but somewhere either in Preferences or Administration, there's a menu item that will allow you to edit services/applications that load at login... you could just add a new one something like

sh "/usr/local/bin/hp3970-chmod.sh"

anyone else know exactly where/what that menu is called? i used to use it to load Deluge automatically when i logged in

---

### Post by Dayofswords on 2010-05-20
[QUOTE=anewguy]Okay, I did some testing and indeed if you specify the entire path and filename you don't need "./". I've just never understood why, if you are in the directory the file exists in, you can't just say "filename" instead of "./filename" (does this mean in the current directory (.) execute (/) the named file?).[/QUOTE]

. = the current directory you are working, the terminal with automatically think "oh, a dot, you must mean /home/user/Music/ since you was currently working there"
./filename = you want to execute the file, / doesn't mean to execute, it just saying folder, without the ./ it would think your doing a command, not a file.

example, your in /home/user/myjunk  , you do './scriptness' it will look in your current directory (. saying this area, / saying just... it a folder) so it will work out its '/home/user/myjunk/scriptness' you want to run

there is also  ..  which means one folder up
from /home/user/, you do 'cd .." you will be in /home/

---

### Post by Drenriza on 2010-05-20
> **anewguy said:**
> ```
./usr/local/bin/hp3970-chmod.sh
```

but upon logout/login the script appears not to execute since the permissions on the USB device didn't change and the log file is not created.


Cant you copy your script into /usr/share/doc/adduser/examples/adduser/examples/adduser.local.conf.examples/skel/dot.bash_profile

and give the file the following permissions
```
chmod 4644 dot.bash_profile
```

???

---

### Post by anewguy on 2010-05-20
I fail to see how that would have anything to do with having it execute at log in.

---

### Post by Drenriza on 2010-05-20
> **anewguy said:**
> I fail to see how that would have anything to do with having it execute at log in.

the dot.bash_profile is read at user login. And the 4644 will execute the file with root permissions.

i dont know 100% if it will work. Its an suggestion.

---

### Post by anewguy on 2010-05-23
Well, the only reason I wanted this is that I wasn't able to get it to work automatically with a udev rule with RUN+= and a change to sudoers.  I found out that putting an alias in for a command in sudoers, then pointing to it on a user statement in sudoers, as recommended by 1 post in the forum, didn't work.  I had to remove the alias and but the command right on the user statement.  Since that worked, I no longer need this solution anyway as it is far less elegant for the problem.

Thanks for the replies.  I'll be marking this as solved since I got the original idea working as intended.

Dave ;)

---

