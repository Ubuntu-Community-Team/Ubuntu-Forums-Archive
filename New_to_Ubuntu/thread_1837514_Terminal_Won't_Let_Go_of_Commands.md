---
title: "Terminal Won't Let Go of Commands"
date: 2011-09-01
forum: New to Ubuntu
---

### Post by Josh3693 on 2011-09-01
Hello everyone.

I'm currently running Ubuntu 11.04 desktop primarily as a upnp/samba media server with the occasional Libre Office application. This is my first experience with GNU/Linux and so far it's been a very rewarding although occasionally frustrating experience. Up until now I've been able to google my way out of everything but after several hours I'm ready to admit I'm stuck.

My problem is when I run a "service" type command i.e. "sudo service mediatomb restart" the terminal won't let go of the service. I get status reports from the service but the command prompt never returns. If I close the terminal the service is terminated. I've been working around it but recently something came up that I'm having trouble working around. 

Compiz started giving me issues. Windows won't move, resize, minimize, etc.  All due to user error of course! A simple "compiz --reset" fixed my problems with compiz but now I can't close the terminal without terminating compiz which completely wrecks my desktop making it unresponsive to the keyboard among other things. I restarted my pc by using "ctrl+alt+f1" and rebooting from that terminal but that brings back the same window problems.

Now I found a fix for my compiz issues which is basically just restoring my compiz settings to their defaults but I'd really like to know why my terminal is behaving the way it is. The issue *seems* to have started with the latest kernel update. It may have existed before but on a fresh install (about two months ago) I didn't have this problem.

Thank you all for your time.

---

### Post by gardnan on 2011-09-01
If you want to start a process that is not attached to the terminal you are using, add '&' at the end of the command. It will automatically make it a background process. Not sure if this is what you wanted to know, though.

---

### Post by Josh3693 on 2011-09-01
> **gardnan said:**
> If you want to start a process that is not attached to the terminal you are using, add '&' at the end of the command. It will automatically make it a background process.

Thank you! That absolutely works! I am still curious as to why my terminal suddenly started acting this way though. Previously, simply typing the command was sufficient. 

Thanks again!

---

### Post by 3rdalbum on 2011-09-01
> **Josh3693 said:**
> Thank you! That absolutely works! I am still curious as to why my terminal suddenly started acting this way though. Previously, simply typing the command was sufficient. 

Thanks again!

The command doesn't "return" unless it finishes, or detaches.

compiz never detaches.

I thought Service should detach, but maybe I'm wrong.

---

### Post by yetiman64 on 2011-09-01
As well as using the ampersand (&) after the command (for sending the command to the background), to release a stuck terminal to a command prompt use the keyboard combination CTRL + C. Be sure the command has finished its job though as that key combination will also break out of a running process.

Some processes have a tendency to hold the terminal after completing, I'm not sure why but use CTRL + C to get the terminal back whenever it happens. Also even if you use the  & with a command note that closing the terminal often shuts down the process it launched, if you wish the process to continue and want to close the terminal consider launching the process via the run dialog ALT + F2.

Hope this helps, cheers.

Edit: as 3rdalbum notes compiz never detaches and using CTRL + C will crash it (that can get messy). I always launch anything compiz or metacity related with ALT + F2.

---

### Post by Josh3693 on 2011-09-02
Thank you all for the replies!

Yeah, I already made a mess by using ctrl+c to close the terminal while running compiz. Huge mess. Using the & seemed to have worked but exiting the terminal caused another crash. Mediatomb still won't "let go" when i run service mediatomb restart but using alt+f2 works great for both.

Thanks again everyone, I'm marking this as solved.

---

