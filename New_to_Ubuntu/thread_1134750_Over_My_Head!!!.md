---
title: "Over My Head!!!"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by Howard Roark on 2009-04-23
I'm trying to install a Brother MFC-790cw. According to Brother's support instructions, I must prep Ubuntu and install from the command line. This is what I did:
??????@??????-desktop:~$ sudo aa-complain cupsd
[sudo] password for linda: 
Setting /etc/apparmor.d/usr.sbin.cupsd to complain mode.
??????@??????-desktop:~$ sudo mkdir /usr/share/cups/model
mkdir: cannot create directory `/usr/share/cups/model': File exists
??????@??????-desktop:~$ psutils
bash: psutils: command not found
??????@??????-desktop:~$ ln -s /etc/init.d/cups /etc/init.d/lpd
ln: creating symbolic link `/etc/init.d/lpd': Permission denied
??????@??????-desktop:~$ mkdir /var/spool/lpd
mkdir: cannot create directory `/var/spool/lpd': Permission denied
??????@??????-desktop:~$ sane-utils
bash: sane-utils: command not found
??????@??????-desktop:~$ 

the commands are obviously ineffectual. Is this a problem with permission? as I recall I only set one permission. Could this be a problem with the way I'm reading Brother's instructions?:

    Requirement
    1. "sudo aa-complain cupsd" command is required before the installation.
    2. "sudo mkdir /usr/share/cups/model" command (as it is) is required before the installation.

    Requirement (superuser authorization is required to run the command) 
    "mkdir /var/spool/lpd" command is required if the folder does not exist.

---

### Post by Hospadar on 2009-04-23
You just need to install the programs you're trying to run,

you can get them in synaptic, or just copy-paste ```
sudo apt-get install psutils sane-utils
```

If you're ever in doubt, search through synaptic, or from a command line "apt-cache search psutils" (or whatever other program you need)

On a side note:
ln -s /etc/init.d/cups /etc/init.d/lpd
mkdir /var/spool/lpd

Probably require root permission, i.e. sudo, i.e.
sudo ln -s /etc/init.d/cups /etc/init.d/lpd
sudo mkdir /var/spool/lpd

If the "mkdir" commands tell you the file exists, than no worries.  This command just makes a folder, so if the folder already exists, no problem.  And just so you know, the "ln -s" command makes a symbolic link, which is like a shortcut (it basically allows you to give files different names, and link to them from other directories for convenience)

When they say things like "superuser authorization is required, blah blah blah" they mean that you need root (administrator) permission, and the way to run a command as root is to prepend "sudo"

Most things outside of your home directory (/home/username) are owned by root or some other user, so if you want to modify them, you'll need root permission.

If you're ever curious about a command, try "man commandname" from the command line to get more info about it (q to quit back to prompt)

I would strongly suggest a basic command line tutorial as well, it's not generally necesary, but often a great way to get things done and investigate problems, you might want to start [here]("https://help.ubuntu.com/community/UsingTheTerminal") in the ubuntu documentation tutorial on terminal handling.

---

### Post by oldos2er on 2009-04-23
If you're using Gnome, check System, Administration, Printing, to see if your printer's recognized.

---

### Post by duanedesign on 2009-04-23
permission denied means you need sudo in front of the command

Edit: Wow, several answers at once. Good thing too, those answers are much better than mine. If you ask they will come.

---

