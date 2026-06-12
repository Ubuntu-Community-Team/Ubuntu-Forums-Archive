---
title: "login password box gone after update"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by tadcan on 2011-01-19
Turned on my laptop and get to the splash screen, I see my machines name, but not my user name or a password box to log in.

Before I do a backup and reinstall, is there a quick fix?

---

### Post by Paqman on 2011-01-19
Is this just a one-off or is it like that every time you boot up?

---

### Post by tadcan on 2011-01-19
It hasn't happened before. I did an update yesterday, so I presume the change happened then. I also enabled proposed updates, id that matters.

---

### Post by 101011010010 on 2011-01-19
Hello.
You might find this link helpful:

[https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates)

A.

---

### Post by Paqman on 2011-01-19
> **tadcan said:**
> It hasn't happened before. I did an update yesterday, so I presume the change happened then. I also enabled proposed updates, id that matters.

If you're able to boot up into recovery mode and get to the command line you could check your apt logs:
```
nano /var/log/apt/history.log
```
And see if there's anything in there about messing about with gdm from yesterday. If it doesn't seem obvious you might want to copy the whole list of what was installed yesterday and post it here. You probably also want to go to:
```
nano /etc/apt/sources.list
```

and comment out proposed by putting a # at the start of the line. Ctrl-X, Y enter to save your changes and exit nano.

---

### Post by tadcan on 2011-01-19
There was nothing in history.log about GDM.
The sources.list was empty.

It will be faster to just do a reinstall. Thanks for your help.

---

### Post by Trandre on 2011-01-19
Probobly something you tried but have you checked the settings on System --> Administration --> Login screen?

---

### Post by tadcan on 2011-01-19
How can I view that, if I can't login in the first place.

---

### Post by Trandre on 2011-01-19
Excelent point!!  Had a little logical breach there for a moment :-)

---

### Post by Paqman on 2011-01-20
> **tadcan said:**
> 
It will be faster to just do a reinstall. 

It often is when you're starting out. If you haven't already you might want to consider setting up /home on a separate partition to make reinstalls even more painless.

---

### Post by tadcan on 2011-01-20
Hmm, yes, just starting out, its not like I've been using ubuntu for over four years and mainly use the GUI..... ;)

When 11.04 comes out I'll install a home partition. Normally I would delete the current partition and choose install on continuous free space, but that option was gone in 10.10, so it was simpler to  assign the / and swap partitions.

---

