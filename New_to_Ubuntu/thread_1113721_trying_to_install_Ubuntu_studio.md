---
title: "trying to install Ubuntu studio"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by elecmusic on 2009-04-01
I ran the install DVD for Ubuntu studio that I downloaded. It installed fine tell it was time to take out the DVD and reboot. it rebooted fine then it came to the Logan and password thing, I put mine in. then it went to the following messages and Stoped.  My name is Roy.  >>>>the following is what code it came up with and stoped
 
To run a comand as administrator (user "root"), use "sudo <sudo <command>.
see "man sudo_root" for details.

roy$roy:$


So what do I type there????

---

### Post by 123456789123456789123456 on 2009-04-01
> **elecmusic said:**
> I ran the install DVD for Ubuntu studio that I downloaded. It installed fine tell it was time to take out the DVD and reboot. it rebooted fine then it came to the Logan and password thing, I put mine in. then it went to the following messages and Stoped.  My name is Roy.  >>>>the following is what code it came up with and stoped
 
To run a comand as administrator (user "root"), use "sudo <sudo <command>.
see "man sudo_root" for details.

roy$roy:$


So what do I type there????
sounds simular to a grub error I once encountered.  the prompt roy$roy$ is a new one on me.  do linux commands work?  do you know any linux commands?

try ls-l, that should provide you with a list of files and directories, with the permissions, and onwer information beside them

if that works, type in
runlevel = 5
if there was no error in installing the xwindows environment, that command should force it to use GUI interface, instead of the text mode only.
if the runlevel does not run, use sudo before the runlevel command, that will allow you to use the command as if you were root.

if you typr runlevel without anything else, it will identify what runlevel the computer is running in
runlevel 1 is text only
2 is text only also, but has extra commands.
3 is text mode, but you can run GUI
4 is GUI mode, more like safe mode in windows
5 is full GUI mode.  5 should be the normal operating mode for ubuntu.

---

### Post by elecmusic on 2009-04-02
I made an error on my last message on here.
the problem that I see flashing in front of me says

roy@roy:~$

my user name is roy and I am also using roy as administrator  and root logan I do not know what to type there.

---

