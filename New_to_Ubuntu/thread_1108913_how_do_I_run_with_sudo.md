---
title: "how do I run with sudo"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by imparja2 on 2009-03-28
I'm trying to check if the message bus daemon is working or not and get it working someone suggested using this: 

/bin/dbus-daemon --system

They said "run it with sudo" so how do I do that what command should I type?

---

### Post by .Maleficus. on 2009-03-28
Place sudo in front of the command.  You'll get a line next that says 'Password:' - enter your password for YOUR user there.  No characters will appear on the screen, but trust me, it's recognizing the keystrokes.


Edit:  Also, I suppose I should give the little warning of using sudo.  Sudo gives you temporary root access (superuser) and blindly running commands from the internet as a superuser can be harmful towards your system.  Sudo is a very powerful tool and gives you access to EVERYTHING - just be careful.  Ubuntu removes the root account for a reason ;).

---

### Post by imparja2 on 2009-03-28
that's not what I mean. I don't know the command or the syntax that should go in front of /bin/dbus-daemon --system

I know the command line should be:

sudo .?.?.?. /bin/dbus-daemon --system

like this right can you help me fill in the gaps?
I'm trying run the message bus daemon

---

### Post by anon642 on 2009-03-28
```
sudo /bin/dbus-daemon --system
```

---

### Post by imparja2 on 2009-03-28
I get the following result

branden@branden-laptop:~$ sudo /bin/dbus-daemon --system
[sudo] password for branden: 
sudo: /bin/dbus-daemon: command not found

what command should I use what is the syntax for "run" file.

"execute" perhaps?

---

### Post by freak42 on 2009-03-28
the syntax for 'run file' is no command at all:
to execute a program you just call its path:

like /usr/bin/app

if you want to execute a file in the current directory prepend ./
./programinthisdirectory

there are certain folders in the app-path meaning if you don't give a path
in front of your application it will look through all the folders in the app path, if the application is there it will get executed. like:

firefox

your error message above implies that the dbus-daemon application is simply not there and therefore cannot be executed (or it's not at that location).

hth

---

### Post by issih on 2009-03-28
sudo, on it own, just tells the terminal to run the next command as root. The command in this case is "/bin/dbus-daemon --system"

(well technically the command is "dbus-daemon --system" and /bin/ is the path to where that command is)

so it is simply:

```
sudo /bin/dbus-daemon --system
```

As others have said, nothing more is needed.

I can only assume that the dbus-daemon is not in /bin/ 

Hope that helps

---

### Post by snova on 2009-03-28
You do not need to specify a full path to dbus-daemon. This would suffice:

```
sudo dbus-daemon --system
```

It should, however, be located in /bin, yet it seems to be missing. It is located in the **dbus** package, so check that it's installed with Synaptic.

---

