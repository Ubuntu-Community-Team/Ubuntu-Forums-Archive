---
title: "How to run a command during startup automatically??"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by karthick87 on 2009-08-23
During startup i need a run  this command "sudo pon dsl-provider" automatically..How can i do this??

---

### Post by Grifulkin on 2009-08-23
Go to System--> Preferences--> Startup Applications.  Create new, in the command line type the command click Add. Presto starts at startup.

---

### Post by sahabcse on 2009-08-23
Go System => preferences => Startup Programs tab, and click Add, then just enter the command that you use

---

### Post by karthick87 on 2009-08-23
Normally while working in terminal for non root user it will ask us to enter the password to execute this type of commands..But how come this possible without entering password??

---

### Post by PGScooter on 2009-08-23
edit: I didn't see the sudo

---

### Post by karthick87 on 2009-08-23
So do i want to enter sudo before the command or simply "pon dsl-provider" is enough??

---

### Post by PGScooter on 2009-08-23
try:
```
gksudo gnome-session-properties
```

and yes, enter the sudo

---

### Post by karthick87 on 2009-08-23
It works fine,but similarly how to run a script during startup??

---

### Post by PGScooter on 2009-08-23
> **getyourkarthick said:**
> It works fine,but similarly how to run a script during startup??

Did the above method not work? In gnome-session-properties, you go to "add" and then if it's a small script, you can just enter it in the "command" field. If it's a big script, in the command, just run the script like you would run it from bash. If "sudo pon dsl-provider" is the only command you want it to run, then enter that in "command".

---

### Post by karthick87 on 2009-08-23
Yes the above procedure works fine for me..But i like to get some more information in depth..

---

### Post by PGScooter on 2009-08-23
> **getyourkarthick said:**
> Yes the above procedure works fine for me..But i like to get some more information in depth..

That seems like a good thing to do. I'm not sure what more information to include, though. Could you help me out? Do you have some more questions?

Now you know how to run a script at startup, right? What is next on your list?

---

### Post by karthick87 on 2009-08-23
Can you give me some information about writing a script and  rc.local file.

---

### Post by PGScooter on 2009-08-23
getyourkarthick,
I don't know much at all about rc.local.
As for writing a script, you can use various languages: bash, perl, and python are pretty common. For simple scripts, I would say that bash scripts are the most popular because you can just collect a sequence of commands that you put into a terminal and put them into a file and voila you have a script.

---

### Post by karthick87 on 2009-08-23
Fine,thanks a lot..

---

### Post by lswb on 2009-08-23
A stock install of 9.04 will definitely have a working /etc/rc.local file that you can edit and add commands to. The rc.local script itself is started by an initscript. Have you ever done anything like trying to edit startup services or change runlevels that may have removed the necessary files and links?

At any rate, ubuntu by default starts in runlevel 2. See if the file /etc/init.d/rc.local exists on your system. Also check for existence of /etc/rc2.d/S99rc.local. Now, all these files using "rc.local" in their names can be confusing. Note that /etc/rc.local is a different file from /etc/init.d/rc.local. The naming conventions can be confusing at times.

For more explanation, see the files in /usr/share/doc/sysv-rc, especially README.runlevels.gz

---

