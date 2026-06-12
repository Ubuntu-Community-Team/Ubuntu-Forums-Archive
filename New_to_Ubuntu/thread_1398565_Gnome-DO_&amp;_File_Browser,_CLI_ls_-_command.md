---
title: "Gnome-DO &amp; File Browser, CLI ls -?? command"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by Sceiron on 2010-02-04
Have some small stuff that needs answering :)

How do i launch Nautilus file browser with Gnome-DO
typing "nautilus" or "File Browser" dont work..?

What is the command for ls that lets you read the files page by page, and not in one list (-l) that you have to scroll up in?

And i want to add "Artha" to the startup apps, but i dont know where to go to find the app (binary file?) when i press the Browse button?
Thanks!

---

### Post by sisco311 on 2010-02-04
> **Sceiron said:**
> 

What is the command for ls that lets you read the files page by page, and not in one list (-l) that you have to scroll up in?



You can pipe the output of ls (or any other command) in more or less:
```
ls | more
```or
```
ls -l | less
```
You can create an alias for the command, i.e.:
```
alias ll=`ls -al | less`
```
(append the ~/.bashrc file with the above line, start a new shell & type ll to list the files)

> **Sceiron said:**
> 
And i want to add "Artha" to the startup apps, but i dont know where to go to find the app (binary file?) when i press the Browse button?
Just type *artha* in the command field. The binaries are usually in the /usr/bin, /usr/sbin, /bin & /sbin directories, but you don't have to specify the full path to run them.

---

### Post by ankspo71 on 2010-02-04
Hi,
The ls command can be used like this:
```
ls | more
```Most binaries we need are located in /usr/bin , but sometimes they can be installed elsewhere, like /bin or ???. most of the time we can find binaries by using the which command:
```
which artha
```If that doesn't help, you can use the locate command:
```
sudo updatedb
locate artha
```I'm not a gnome-do user so I can't help with the other parts.

---

### Post by ibuclaw on 2010-02-04
For Gnome-Do, you can't type in "Nautilus" or "File Browser" as such, but you **can** type in folder names.

ie:
Home
Pictures
Documents
Downloads
Desktop

Should all open up a file browser to that directory.
Regards
Iain

---

### Post by Sceiron on 2010-02-04
Thank you guys, i really appreciate it!

---

### Post by ibuclaw on 2010-02-04
No probs, don't be a stranger for any talk, arguments, agreements, advice, answers and articulate announcements.

It's only talk

---

