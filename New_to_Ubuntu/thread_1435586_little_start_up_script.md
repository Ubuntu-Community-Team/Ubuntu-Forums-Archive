---
title: "little start up script"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by B-80 on 2010-03-21
I have a few tasks I do everytime I boot, so naturally I want to make a start up script. I need help with a few things though.

1) where do I put the script so that it will autorun on boot.
2) I need to be a super user to do some of them, so how do I get around that.
3) is there any way for me to look at a log of commands I have done? some of these commands(I.E. changing my screen resolution through nVidia's software) are done through GUI, so I don't know the actual command.

or

4) How do I mount a drive (I know the 'mount' command, but IDK where my drives are in the filesystem)
5) How do I change my screen resolution through command line(on startup, my screen is at the right resolution, but it is the size of two screens, IE if I move my mouse to the right, I get more screen and my desktop is stretched over the two screens)

I know how to do everything else I do through Terminal.

thanks in advance

---

### Post by Ozymandias_117 on 2010-03-21
> **B-80 said:**
> 
1) where do I put the script so that it will autorun on boot.
2) I need to be a super user to do some of them, so how do I get around that.
3) is there any way for me to look at a log of commands I have done? some of these commands(I.E. changing my screen resolution through nVidia's software) are done through GUI, so I don't know the actual command.

or

4) How do I mount a drive (I know the 'mount' command, but IDK where my drives are in the filesystem)
5) How do I change my screen resolution through command line(on startup, my screen is at the right resolution, but it is the size of two screens, IE if I move my mouse to the right, I get more screen and my desktop is stretched over the two screens)

1. Best way I know of, is to put it wherever you want, then go to System -> Preferences -> Startup Applications and add it there.

2. I'll check back to see if someone answers this, I have the same problem :P

3. Maybe try opening the app from a terminal and trying verbose mode, this may tell you what it is doing.

4. Best way to mount a drive on boot is to add it to your /etc/fstab file. If you need help with this, post back the output of ```
fdisk -l
``` and tell us what drives you want mounted.

5. My guess would be by modifying /etc/X11/xorg.conf

---

### Post by JKyleOKC on 2010-03-21
For 2, you can put the commands into the /etc/rc.local file, above the "exit 0" line. This file is executed as the last step of the boot process, before any user is logged in, and is run with root privileges so the commands will not need "sudo" to run.

To edit the file, you'll need to use the command "gksudo gedit /etc/rc.local" since it's owned by root. You'll get a dire warning that system damage can result; pay heed to it!

Since it does run before a user is logged in, the autostart features at login may override the effect of any rc.local commands -- and there's no guarantee that the PATH environment will be set when they run, so everything should be specified with absolute path names instead of just the command name itself. Use "which xxx" (where "xxx" is replaced by the command name) in a terminal window to get the absolute path name for each command.

---

### Post by tgalati4 on 2010-03-21
For system-level (and super user scripts)

cat /etc/rc.local

history will give you the last 500 commands.

Control-R (then type a few letters of a command) will search backwards through your history file.

Any changes you make in a GUI are stored in a configuration file, usually stored in your home directory with a .configfile

To get a listing of those files:

cd
ls -la

Some files are stored in the directory .gnome2

So there is no log, but all GUI's are simply easier ways to edit configuration files.  Don't forget the master directory of configuration files:

ls /etc

You can search for files by modification date to see what files were modified recently.  I normally save/backup configuration files that I have personally modified, including scripts that I have written in a separate folder:

cd
cd Projects
mkdir scripts

So when I update distros or change machines, I can review all the changes that I made in my scripts folder.

---

