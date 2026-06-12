---
title: "Why shouldn't I log in as root?"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2011-04-09
I've seen plenty of people say to not log in as root, but can I ask why exactly?
Does it open a computer up to outside attack or something?

---

### Post by dwhite on 2011-04-09
> **Learning Linux 2011 said:**
> 
Does it open a computer up to outside attack or something?

novice here also,  i look at it as protecting the computer from me!!! i know just enough to get me in a lot of trouble i couldn't get out of, lol :)

---

### Post by Vallar on 2011-04-09
From what I read in the book for beginners; logging as root will give you full command over the system. Picture administrator in Windows but with the ability to alter system files and what not. 
In other words you can change/edit/delete these files. Of course, for a newbie that is bad; that is why it is discouraged. 

That is at least what I understood from the book. Might be something else.

---

### Post by jerenept on 2011-04-09
as root, there is nothing stopping you, or anybody, from diong anything with your computer. 
As root, you can delete everything off your hard drive, nothing is off-limits.

so.... it's pretty bad.

---

### Post by tweaktolive on 2011-04-09
see if something goes wrong or any kind of malware then you dont have a place to fall back upon and the root gives access to everything to the malware .

thats why it is recomended to not use root.

although you can if there is a need.

---

### Post by uRock on 2011-04-09
> **Learning Linux 2011 said:**
> I've seen plenty of people say to not log in as root, but can I ask why exactly?
Does it open a computer up to outside attack or something?

Read the documentation. It sums this question up very well. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by PCNetSpec on 2011-04-09
Read these:

[http://linuxmafia.com/~rick/faq/index.php?page=virus](http://linuxmafia.com/~rick/faq/index.php?page=virus)

and

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

They might help.

---

### Post by AlanR8 on 2011-04-09
Also, the sun will go out and all human life will cease. :D:D

---

### Post by taseedorf on 2011-04-09
Simple answer is because logging in as root allows you to do almost everything without typing in a password.  For example, say you want to delete something important that is not marked as read-only... BOOM, deleted.  Say.... you want to make certain important system changes... BOOM...it's done without a password.  Having to enter the root password is a safeguard.... also it can prevent other people from coming over to your computer and doing things.... assuming you leave it on all the time.


If someone gains access to your system and you're logged in as root, it also gives them a lot more capability...

---

### Post by Learning Linux 2011 on 2011-04-09
So is it mostly just local access?

If you log in as root, does that open up some kind of security vulnerability from the outside if you are connected to the internet?

---

### Post by jaycount on 2011-04-09
It opens you up to a wider range of malware attacks. If malware is executed while you're logged in as root then it can do anything root can. 

The bottom line is: there's no good reason to log in as root. Use sudo :KS

---

### Post by Learning Linux 2011 on 2011-04-09
> **jaycount said:**
> It opens you up to a wider range of malware attacks. If malware is executed while you're logged in as root then it can do anything root can. 

The bottom line is: there's no good reason to log in as root. Use sudo :KS

Yes, I was just questioning the "bottom line" to help me understand why that is the case :-)

I hadn't really thought of the malware thing.  Like if you download a program while logged in a root, that could allow the downloaded program to do anything.

I guess I was mostly asking because if someone (a knowledgeable computer user) is the sole user of their system, it didn't seem logical why they couldn't be logged in as root, but I guess the malware issue is good enough.

---

### Post by SeijiSensei on 2011-04-09
I work as root on the servers I manage pretty regularly.  However I've been at this Linux stuff for fifteen years now, so I know what damage I can do.  That doesn't mean I have never caused great problems for myself from time to time running as root, but the last major problem like this happened at least half-a-dozen years ago now.  

If I'm editing a lot of system configuration files or doing similar things where I need root permissions, I'll just become the root user for a while.  Ordinary users generally have no need to run as root except in limited situations like installing software.  Using sudo for this task, as Ubuntu does, is a good compromise between safety and ease-of-use.

> I guess I was mostly asking because if someone (a knowledgeable computer user) is the sole user of their system, it didn't seem logical why they couldn't be logged in as root, but I guess the malware issue is good enough.

As root, you can run the simple command "rm -rf /" and delete your entire Linux distribution and any files on mounted devices.  I think you can see why giving that power to naive users is not a good idea.

---

### Post by idoitprone on 2011-04-10
> **Learning Linux 2011 said:**
> I've seen plenty of people say to not log in as root, but can I ask why exactly?
Does it open a computer up to outside attack or something?


Did you hear about windows xp, know why virus rained doom to the poor pc?  Guess what? everyone runs as root, so microsoft got so irrated patching every flaw and created UAC. Instead of microsoft get irrated, they shifted the irratation to the user.

---

### Post by Old *ix Geek on 2011-04-10
> **Learning Linux 2011 said:**
> I've seen plenty of people say to not log in as root, but can I ask why exactly?
Does it open a computer up to outside attack or something?Outside attack? Yes, it certainly can. But as others have noted, it's INSIDE attack that's the real issue. :eek:

I've been at this for 26 years--started on Tandy, and then SCO, Xenix/UNIX back in 1985. I learned to respect root's power from the get-go, and although I did--and still do--log in as root to do certain things, I'm ALWAYS mindful of the fact that one misplaced or premature keystroke can wipe out unintended files.

I prefer, and use, the old-fashioned prompts, $ as a regular user and # for root. So when I'm working at a command line, my prompt doesn't include the pathname of the directory I'm in, it's just a $ or a #--and it's up to *me* to know where I am. If I'm root, and I forget or lose sight of where I am...it can be disastrous.

The bottom line is that it's your computer(s) and you're free to do whatever you like with them, including logging in as root. But when you do so, you're putting yourself at unnecessary risk of damaging and/or rendering your system unusable. If you're okay with that--and have good backups--go for it!

---

### Post by stmiller on 2011-04-10
To keep your system safe and secure you should never login as root.

You can trash everything with one bad click or one command if you are not careful! Also you could potentially install/run malicious scripts if you are running as root and execute sketchy code.

In Ubuntu (and optionally in Debian) root is disabled by default. Same in OS X.

---

### Post by bodhi.zazen on 2011-04-10
I was going to say, ask Microsoft, they stopped this practice (logging in as the admin user by default) as of windows 2000.

But the answers on this thread are probably better.

#1 - 10 is security, both local (key loggers) and remote (buffer overflows). 

#11 Would be that significant data loss would be but a mouse click away. When running as a restricted user you can only delete your files, as root the sky is the limit.

---

