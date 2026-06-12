---
title: "Using Brasero"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by Robert1305 on 2011-03-07
I have been trying to make a copy of a CD I have, but every time I try I get this message
[ATTACH]185352[/ATTACH]
I have installed every file I can find with Brasero attached but still no luck. :(
Can anyone help please.

---

### Post by nomko on 2011-03-07
The message indicates that there are some libraries not installed. However, Brasero is a very buggy program, more users having some issue's with Brasero. Best thing to do is remove Brasero and install K3B. 
 
K3B is a Nero look-a-like program, but works much better then Brasero.

---

### Post by dionysius on 2011-03-07
Could you run brasero through terminal? 

Just open a Terminal window, type brasero, hit enter, try to do what you intended to do, and post the error message(s) from the Terminal window in this thread?

---

### Post by Robert1305 on 2011-03-07
> **dionysius said:**
> Could you run brasero through terminal? 

Just open a Terminal window, type brasero, hit enter, try to do what you intended to do, and post the error message(s) from the Terminal window in this thread?

This message appeared in terminal 

** (brasero:2379): WARNING **: ERROR loading background pix : Failed to open file '/usr/share/brasero/logo.png': No such file or directory

---

### Post by nomko on 2011-03-07
> **Robert1305 said:**
> This message appeared in terminal 
 
** (brasero:2379): WARNING **: ERROR loading background pix : Failed to open file '/usr/share/brasero/logo.png': No such file or directory
 
Some background image seems to be missing...
Open a terminal and type in:
**ls /usr/share/b***
Place the output here. It will check wether the directory exist or not.

---

### Post by dionysius on 2011-03-07
> **Robert1305 said:**
> This message appeared in terminal 

** (brasero:2379): WARNING **: ERROR loading background pix : Failed to open file '/usr/share/brasero/logo.png': No such file or directory

Is Brasero installed? When you type the following in the terminal, does it list anything at all? 
```
ls -a /usr/share/brasero/ 
```

Did you try to copy a CD as you intended to do but couldn't?

---

### Post by Anuovis on 2011-03-07
I will second the opinion that *Brasero* is a very poor piece of software. You might be better off trying *Gnome Baker* or some other burning apps from Ubuntu Software center. 

I don't think I burned a single CD with *Brasero* without getting some weird error or a crash. Now it's gone from my Ubuntu forever.

---

### Post by Linux_junkie on 2011-03-07
> **Robert1305 said:**
> I have been trying to make a copy of a CD I have, but every time I try I get this message
[ATTACH]185352[/ATTACH]
I have installed every file I can find with Brasero attached but still no luck. :(
Can anyone help please.

As everyone says, Brasero is buggy. A while back I tried to create a Data DVD using brasero. It would burn the files on to the disk but then when I tried to view the data afterwards it had errors and prevented me from viewing the files.  As the disks were DVD-R I simply had to throw them away.

I replaced Brasero with GnomeBaker  and have since never had the same problem.  Hope this helps.

---

### Post by dionysius on 2011-03-07
> **Linux_junkie said:**
> As everyone says, Brasero is buggy. A while back I tried to create a Data DVD using brasero. It would burn the files on to the disk but then when I tried to view the data afterwards it had errors and prevented me from viewing the files.  As the disks were DVD-R I simply had to throw them away.

I replaced Brasero with GnomeBaker  and have since never had the same problem.  Hope this helps.


And I on the other hand have never had issues with Brasero. Sure, install a different CD/DVD burner - but to me that sounds kinda the same as suggesting someone use a different OS if they're having issues with Ubuntu. 

Replacing one program with another doesn't solve all problems, the forums are littered with issues in K3B and Gnomebaker too. 

But by all means, uninstall Brasero and try some of the others in the repos. There's bound to be one that works.

---

### Post by nomko on 2011-03-07
If you search this forum, you will find more topics about Brasero and bad cd's/dvd's. Or weird error messages. In general i can only say (not conclude) that Brasero is too buggy for general use. I, for instance, uses K3B and with succes. Some others may use Gnomebaker with succes. But in overall, Brasero doesn't seem to work properly.

---

### Post by realzippy on 2011-03-07
..why is [brasero]("http://ubuntuforums.org/showthread.php?t=1158979") the default CD burner in Ubuntu?
For me it never worked,it definitely is bad advertisement for Linux generally. 

+1 for K3B !

---

### Post by dionysius on 2011-03-07
And that's probably because Brasero is the default app, so obviously when people are having issues with it they'll post a thread here. And then, instead of actually resolving the issue, they're told to install a different app. 

If the OP wishes to use Brasero I'm happy to help, if he decides to use a different program that's fine too. But perhaps trying to solve the problem *before* suggesting a different program would be a good idea? Otherwise we're only waving stuff away. Thunderbird doesn't work? Use Evolution. Empathy has issues? Try Pidgin. Et cetera ad nauseam. 

I'll leave it up to the OP.

---

### Post by nomko on 2011-03-07
> **realzippy said:**
> ..why is [brasero]("http://ubuntuforums.org/showthread.php?t=1158979") the default CD burner in Ubuntu?
For me it never worked,it definitely is bad advertisement for Linux generally. 
 
+1 for K3B !
 
That's the big question for me too. Most users are having troubles with Brasero. I'm using K3B also and i'm very happy with K3B. If i get some problems with K3B then it is related to the files i want to burnb and not the program. In the early beginning of my Ubuntu era i used to work with Brasero and got many problems with it. It won't burn a cd/dvd and if it did, then it was always with errors and bad cd's/dvd's.

---

### Post by realzippy on 2011-03-07
> **dionysius said:**
> And that's probably because Brasero is the default app, so obviously when people are having issues with it they'll post a thread here. And then, instead of actually resolving the issue, they're told to install a different app. 

If the OP wishes to use Brasero I'm happy to help, if he decides to use a different program that's fine too. But perhaps trying to solve the problem *before* suggesting a different program would be a good idea? Otherwise we're only waving stuff away. Thunderbird doesn't work? Use Evolution. Empathy has issues? Try Pidgin. Et cetera ad nauseam. 

I'll leave it up to the OP.

The point is that the default shipped burning application of an 
operating system simply ***has*** to work. (Remember [bug #1]("https://bugs.launchpad.net/ubuntu/+bug/1") ????????)
If a new Ubuntu user has to become a Forum member to burn a CD it is a marketing disaster.
If "we" were commercial,this would never happen..  ;-)

When I set up a system for a linux interested fellow,I always uninstall brasero to save me the unavoidable cry for help.

---

### Post by nomko on 2011-03-07
> **dionysius said:**
> And that's probably because Brasero is the default app, so obviously when people are having issues with it they'll post a thread here. And then, instead of actually resolving the issue, they're told to install a different app. 
 
If the OP wishes to use Brasero I'm happy to help, if he decides to use a different program that's fine too. But perhaps trying to solve the problem *before* suggesting a different program would be a good idea? Otherwise we're only waving stuff away. Thunderbird doesn't work? Use Evolution. Empathy has issues? Try Pidgin. Et cetera ad nauseam. 
 
I'll leave it up to the OP.
 
I agree with you, but i also agree with realzippy:
 
>  
The point is that the default shipped burning application of an 
operating system simply ***has*** to work. (Remember [[COLOR=#444444]bug #1[/COLOR]]("https://bugs.launchpad.net/ubuntu/+bug/1") ????????)
If a new Ubuntu user has to become a Forum member to burn a CD it is a marketing disaster.
If "we" were commercial,this would never happen.. :wink:

When I set up a system for an linux interested fellow,I always uninstall brasero to save me the unavoidable cry for help.


---

### Post by dionysius on 2011-03-07
> **realzippy said:**
> The point is that the default shipped burning application of an 
operating system simply ***has*** to work. (Remember [bug #1]("https://bugs.launchpad.net/ubuntu/+bug/1") ????????)
If a new Ubuntu user has to become a Forum member to burn a CD it is a marketing disaster.
If "we" were commercial,this would never happen..  ;-)

When I set up a system for a linux interested fellow,I always uninstall brasero to save me the unavoidable cry for help.

Er, the default burning application works here, every machine I've installed it on. 

There are worse issues with new installs, this problem with Brasero - though inconvenient - is hardly going to damage our image. 

As someone who works both in IT and marketing (communications consultant), let me say that an application that actually works is of course a good thing. Getting stuff fixed however is far more important, something our community excels at. Which is why I think it's disappointing that when someone asks for support with an application - and a default one at that - the message is "nevermind, download XYZ instead". 

With respect, I don't concern myself with Bug #1, or how things would be if we were commercial - in so far that I won't discuss it here on this thread.

---

### Post by realzippy on 2011-03-07
@IT and marketing communications consultant:
If I say *works*,I mean *works perfectly*.,not
*"needs to be fixed"* by the end-user.
I know that certain software companies have a different view...

@dionysius:
You are absolutely right,this thread is no "brasero in general" thread,
so I apologise for thread-napping.

---

### Post by Robert1305 on 2011-03-07
Thanks to everyone for their input, could not get Brasero to work at all, so removed it and loaded Kb3, worked first time no problems, so thanks again . :D

---

### Post by Anuovis on 2011-03-08
It seemed OP has resolved the problem by switching to a decent app.

> **dionysius said:**
> 
There are worse issues with new installs, this problem with Brasero - though inconvenient - is hardly going to damage our image. 


From my own experience, it has left a very bitter taste in my mouth. And it was the single app from all that I've tried so far that couldn't accomplish absolutely nothing at all. Now I see I'm not the only one. 

Newcomers to Ubuntu have enough to worry about by jumping to a totally new system and including this abomination as a default application surely does some damage and adds to your frustrations.

I don't mind the "fix if it doesn't work" approach but the less of that, the better. Mainstream Linux users (and Ubuntu seems to be aiming for them) probably don't mind solving problems but ultimately the OS is a tool that should work, not a goal in itself. 

Spending hours tinkering with a broken piece of software and getting your CDs destroyed (yup, it does that) when you can easily switch is not rational.

---

