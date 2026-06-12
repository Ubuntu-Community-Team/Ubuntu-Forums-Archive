---
title: "Problem Using Uppercase Only Terminal"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by toml_12953 on 2009-07-11
This is my first go at Linux so I really don't know what I'm doing. I have an uppercase-only terminal (Teletype ASR-33) that I'm trying to use on ttyS0. I get the sign-on message and login and password prompts just fine and I can see my username when I type it on the ASR-33's keyboard (in uppercase, of course) so I know the connection is good. 
 
Ubuntu doesn't accept my username and password, however. I'm pretty sure the problem is that my username and password are lowercase and my terninal only puts out uppercase. I've added -U to the respawn of getty but it does no good.
 
Here are the lines in /etc/event.d/ttyS0:
 
respawn
exec /sbin/getty -U 110 ttyS0
 
Can anyone help me get the old tty online? I know some people will say not to even try it with such an old terminal but I'm determined to make this work.
 
Thanks. :confused:

---

### Post by Cato2 on 2009-07-11
Wow, this is really quite esoteric and it's a bit bizarre seeing it on Absolute Beginner Talk! Not a beginner project at all, but you will learn a lot about Linux and serial interfacing.

I started using computers on just such a terminal, in the days when you had to toggle in the bootstrap code in binary on a front panel.  Also used Unix on slightly more up to date serial terminals for many years, in the days when you had multiple users on VT100 style terminals via serial lines into a Linux box.  

You will need to read up a LOT on stty(1) settings - search for <oldest Unix version you can think of> and teletype stty.  Try "stty iuclc olcuc" for a start, typing LS in caps means you run lower case 'ls' command, and it translates output back to upper case - just tried this and it does work.  This may be enough to get you logged in at least.

You will need to spend a lot of time messing about with stty options, since erase works entirely differently, and ideally find a forum with people who understand such stuff.    Some of the stty options go in the getty, but it's probably easier to put some of them in the .profile when experimenting.  You can actually use another terminal session (non-teletype) to do an stty onto the teletype, which is good when things are messed up - you redirect either stdin or stdout, it varies depending on Unix/Linux version.

You'll also need to learn line editors such as ex(1), ed(1), etc.  Using csh style history substitution in bash will help your sanity.

[http://daduke.org/tty/](http://daduke.org/tty/) looks like a good resource.  I found it by googling for "rtty teletype linux stty" - the RTTY (radio teletype) community does use Linux so may be able to help.

See [http://www.linux.org/docs/ldp/howto/Serial-HOWTO-12.html#ss12.4](http://www.linux.org/docs/ldp/howto/Serial-HOWTO-12.html#ss12.4) as well.

---

### Post by toml_12953 on 2009-07-12
> **Cato2 said:**
> You will need to read up a LOT on stty(1) settings - search for <oldest Unix version you can think of> and teletype stty. Try "stty iuclc olcuc" for a start, typing LS in caps means you run lower case 'ls' command, and it translates output back to upper case - just tried this and it does work. This may be enough to get you logged in at least.

 
Thanks for the quick response!  I created a user with an all-uppercase username and password (for testing only) and was able to login that user from ttyS0.  Of course I couldn't do anything once I was logged in (not even logout!)  This tells me my original assumption was correct.  The problem is the case of the input to the logon prompts.  I then tried your stty suggestion.  That worked for the PC's console.  To change the ttyS0 console, I had to do this:
 
stty -F ttyS0 iuclc olcuc
 
At first I was getting device not found.  I tried cd /dev then ran the stty.  That ran without error and typing stty -F ttyS0 with no parameters did show that iuclc and olcuc were in effect on ttyS0.  Great, I thought.  Tried to login from the ASR-33.  Still LOGIN INCORRECT.  I don't know why stty doesn't seem to have the correct effect on ttyS0 when it works OK on the PC's console.  More study for me, I'm afraid.
 
Thanks again for the pointers!  Some people have no patience with noobs but you're not one of them.

---

### Post by Cato2 on 2009-07-13
Probably you need to do "stty -F /dev/ttyS0 ...." - Unix/Linux always uses a full path to device names, unlike DOS/Windows.

Do have a look at some of those resources linked, there are certainly some stty options I don't know that are relevant here, and you can probably find a complete recipe from someone, which would save a lot of time.

---

### Post by Ronny Svedman on 2012-07-07
I found out the code for handling uppercase only terminals s gone from linux, but I do wonder when it went out? Would a 2.0.x kernel work for instance?

---

### Post by wildmanne39 on 2012-07-07
Old thread closed.

---

