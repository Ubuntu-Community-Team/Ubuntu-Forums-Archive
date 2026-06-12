---
title: "Changing File/Folder permissions"
date: 2011-05-21
forum: New to Ubuntu
---

### Post by Weighty Ghost on 2011-05-21
Hey Everyone,

Kind of stressing, I've got a lot of work to get done over the weekend.

Just wondering if there is a way to get rid of all the "permissions" nonsense system-wide so I can quickly move, copy, past, extract, files and folders using the gnome gui?

---

### Post by audiomick on 2011-05-21
Obvious question: what are you doing that is causing you problems with permissions? Knowing that might have a bearing on how to get around it.

---

### Post by Weighty Ghost on 2011-05-21
Hey Mick,

Sorry, what I mean is, can I relax the default security settings(?).

I need to be able to move files in and out of my /opt directory (including sub-directories)

What I'm doing specifically is moving my local Joomla install from Windows to Ubuntu but it is going to be trial-and-error-hell so I need to be able to do this with the gui instead of the terminal or alt+f2.

ubudog showed me how to do this by typing in alt+f2 employing the "sudo" command, but it is way counter productive to have to do this all day when my cpu has a perfectly good track pad and functioning buttons.

Any help?,

---

### Post by audiomick on 2011-05-21
Short answer: no you can't relax the securities. File permissions are right down at the lowest level of how the system works. Changing how the are set up is practically not possible.

Working as root would be an option, except the root account is disabled in Ubuntu, and it is against the forum policy to explain how to activate it. And I don't know how... ;)

I reckon you should be able to do what you need to do by starting nautilus with root privileges as I explained. You only need the terminal for that one command. Everything else should, I think, be possible from the instance of Nautilus that you start that way.

One tip for the road: If you want to re-do a command that you have just used in the terminal, try pressing the up arrow. It will scroll back through the last commands you have used. I think this will even work if you have closed the terminal and re-open it, so long as the computer hasn't been shut down in between.

---

### Post by fabricator4 on 2011-05-21
> **Weighty Ghost said:**
> Hey Mick,

Sorry, what I mean is, can I relax the default security settings(?).

What you can do is add a "joomla" group, then add your user to that group.  You can then make that the group attached to all the joomla files and directories.  So, if the owner is "root" for security purposes, you can still access, read, write files in those directories under the "joomla" group access.

To change file permissions to add read/write use the chmod command.  To change the owner.group of the files and directories use the chown command

> 
ubudog showed me how to do this by typing in alt+f2 employing the "sudo" command, but it is way counter productive to have to do this all day when my cpu has a perfectly good track pad and functioning buttons.


You could start file manager with sudo privileges.

```

Edit: Sorry I meant to say how to start file manager as root.
Just use the <alt><F2> and in the dialog type:
gksudo nautilus

It's as easy as that. :-)

```

This is generally not advised because of the safety and security issues involved.  If you do this then you should at least change the background to fire engine red so that any time you open filemanager with root privileges it is obvious.

In any case, the permissions issue is something you are going to have to deal with at some point when setting up.  The joomla files will need to be owned by either root, or your user for the system to work properly in any case.  Consult the Joomla documentation for the correct set up.

Chris.

---

### Post by AlphaLexman on 2011-05-21
@ WeightyGhost:
I think you need to look at some background info about linux permissions:
[LIST][filepermissions]("http://www.tuxfiles.org/linuxhelp/filepermissions.html")
[linux-permissions]("http://www.zzee.com/solutions/linux-permissions.shtml")
[/LIST]

---

