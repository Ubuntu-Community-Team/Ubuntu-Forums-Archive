---
title: "Does linux commands description exist?"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by liatodua on 2011-01-19
Hi

I am new to linux at all. I installed ubuntu 10.10 just couple of weeks ago and am trying understanding it. All the commands linux people are talking here are very confusing. Could you please suggest where can I find an understandable guide to all the linux commands (or at least the most useful ones)? A reference-source of all the commands with explanations would be great. Does it exist?

By the way: am I right assuming that use of the commands means opening Applications-Accessories-Terminal and typing them there?

Thanks for any information

---

### Post by Perfect Storm on 2011-01-19
> By the way: am I right assuming that use of the commands means opening Applications-Accessories-Terminal and typing them there?

Aye, but also if you're running without any form of Desktop and only CLI (Commandline Interface).

You can check each command with the **man** (manual) command.

Eg.
```
man cp
```
You quit man with [q]

---

### Post by mastablasta on 2011-01-19
> **liatodua said:**
>  
By the way: am I right assuming that use of the commands means opening Applications-Accessories-Terminal and typing them there?
 
 
yes.
 
have a look here: [http://linuxcommand.org/](http://linuxcommand.org/)
 
free e-book available here: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)
 
 
When in terminal you can use manual pages to find out how command works and what it does.
just type in
```
man
```
 in front of command.
 
you exit "help mode" with by pressing "q"
 
for nromal user commands are rarely necessery if at all. have a look in Ubuntu manual to find out mor eabotu Ubuntu Linux system.

---

### Post by Verbeck on 2011-01-19
> **liatodua said:**
> 
Could you please suggest where can I find an understandable guide to all the linux commands (or at least the most useful ones)? A reference-source of all the commands with explanations would be great. Does it exist?

there are lots of references. you can use google to see them
and if you want help regarding a specific command, type *man command*
> **liatodua said:**
> 
By the way: am I right assuming that use of the commands means opening Applications-Accessories-Terminal and typing them there?

generally, yes. but you could also use virtual consoles (alt+ctrl+F1/F6)

---

### Post by liatodua on 2011-01-19
> **Artificial Intelligence said:**
>  also if you're running without any form of Desktop and only CLI (Commandline Interface).

Brrrrr! How can I run without desktop?

---

### Post by liatodua on 2011-01-19
Ok, thanks. I will read those. And will try terminal manual.

---

### Post by Dave_in_MD on 2011-01-19
> **mastablasta said:**
> yes.
 
have a look here: [http://linuxcommand.org/](http://linuxcommand.org/)
 
free e-book available here: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)
 
 
When in terminal you can use manual pages to find out how command works and what it does.
just type in
```
man
```
 in front of command.
 
you exit "help mode" with by pressing "q"
 
for nromal user commands are rarely necessery if at all. have a look in Ubuntu manual to find out mor eabotu Ubuntu Linux system.
I am not the orig poster, but as a newbie of about about 4 days, I would like to thank you for the links.

---

### Post by liatodua on 2011-01-19
> **Verbeck said:**
>  you could also use virtual consoles (alt+ctrl+F1/F6)

I am not sure I understand that, but I will try pushing these buttons and will see...

---

### Post by Paqman on 2011-01-19
> **liatodua said:**
> I am not sure I understand that, but I will try pushing these buttons and will see...

Go for it. To get back to your desktop: Ctrl-Alt-F7

---

### Post by liatodua on 2011-01-19
Very useful remark. Thank you.

I tried and it works. I will now try the commands manual

---

### Post by liatodua on 2011-01-19
[http://linuxcommand.org](http://linuxcommand.org) is a great resource! Thank you!

---

### Post by liatodua on 2011-01-19
[http://linuxcommand.org](http://linuxcommand.org) seems to be exactly what I need! Thank you!

---

### Post by ndefontenay on 2011-01-19
Hi!

Welcome to the realm of the command line! It doesn't summarize linux (thank god, I love the Graphicak interface too much) but it does really really good thinks.

For instance, if you want to backup data between a folder on your computer to a hard disk, you could use rsync so it copies to the external hard drive only whatever you've modified or added to your folder

Be careful of dangerous commands particularly when running rm (ReMove and not RenaMe) and never run a command coming from someone else, you don't understand .

---

### Post by bikodog on 2011-01-19
> **liatodua said:**
> Brrrrr! How can I run without desktop?

Most users have become acclimated to using a GUI because of the Microsoft/Apple business model; informed capable users are not great revenue generators. Using the GUI for everything keeps users in check and leaves the closed-door corporate programmers with all of the control.

Take your time with it, and slowly begin using the command line for simple things (copying files, renaming files, starting up your browser, etc); eventually you will find that it is the best way to interface with your machine (fast, efficient, etc).

The man pages are the best way to learn about each command; and if the man page doesn't explain it well enough....google it. There's lots out there.

---

