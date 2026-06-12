---
title: "Could not download all repository indexes"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by jltrafton on 2009-04-28
I am an absolute beginner with this operating system, I know less than nothing. When I click on the icon to update the computer it runs through a couple things then comes to a box that says "could not download all repository indexes" and then it has this...

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.92.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.92.46 80]
Some index files failed to download, they have been ignored, or old ones used instead.

I tried looking up a solution, but I'm so new with this I fear I might need someone to give me step by step instructions. I'm not sure if this is really a huge problem or not, but I'm fairly neurotic and like everything to be just so. If someone could help me I'd really appreciate it! 

Oh, I just purchased the computer a few weeks ago from Dell, so I believe I have the latest version. Also I don't know a lot of the terms used with this OS, just a warning =).

---

### Post by coffeeaddict22 on 2009-04-28
Welcome to Linux!
404 Not Found is the same in Linux as in Windows- for some reason, your PC can't see the files it's looking for- so you want to figure out where the glitch is.  When you open firefox (or whatever browser you use) can you browse the web?  Do pages like google open up OK?
How do you get on the 'net?  A wired connection or wireless?

---

### Post by kpkeerthi on 2009-04-28
> **jltrafton said:**
> I am an absolute beginner with this operating system, I know less than nothing. When I click on the icon to update the computer it runs through a couple things then comes to a box that says "could not download all repository indexes" and then it has this...

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.92.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.92.46 80]
Some index files failed to download, they have been ignored, or old ones used instead.

I tried looking up a solution, but I'm so new with this I fear I might need someone to give me step by step instructions. I'm not sure if this is really a huge problem or not, but I'm fairly neurotic and like everything to be just so. If someone could help me I'd really appreciate it! 

Oh, I just purchased the computer a few weeks ago from Dell, so I believe I have the latest version. Also I don't know a lot of the terms used with this OS, just a warning =).
Can you post the the output of ```
 cat /etc/apt/sources.list
```

---

### Post by Titan8990 on 2009-04-28
> **coffeeaddict22 said:**
> Welcome to Linux!
404 Not Found is the same in Linux as in Windows- for some reason, your PC can't see the files it's looking for- so you want to figure out where the glitch is.  When you open firefox (or whatever browser you use) can you browse the web?  Do pages like google open up OK?
How do you get on the 'net?  A wired connection or wireless?


he got a 404 because that location really doesn't exist not because of net issues.

---

### Post by capnthommo on 2009-04-28
hi there, i had a similar one to this recently.  maybe you might like to take a look at []("http://ubuntuforums.org/showthread.php?t=1137312").  i followed the instructions and now the issue is solved.
it was caused by a rogue repository in aptitude third party software sources and when i removed them it was ok.
its just update manager/synaptic trying to download from an address that doesn't exist.
do you need more detailed instruction? just post back if so.
cheers
nigel

---

### Post by snowpine on 2009-04-28
This is a common issue with the special version of Ubuntu that Dell pre-installs on the Mini series. I solved it as follows. Open a terminal and:

```
gksu gedit /etc/apt/sources.list
```

Find the lines that gave the error (the ones starting [http://archive.ubuntu.com/](http://archive.ubuntu.com/)...) and type a # symbol at the beginning of each of these problem lines. The # will comment out the line so that it is skipped by the update manager. Save the file and quite out of gedit. Now try running the update manager again, and you should be good.

---

### Post by jltrafton on 2009-04-28
To start answering questions:
I do use firefox, it freezes sometimes.
I can access Google, GMail, Facebook, and really anything I want.
I use a wireless connection

I don't know how to "post the output..." of anything (like I said, I'm completely new to this). I feel sort of silly, I'm sure it's something simple.

If anyone gives me suggestions I would need to know how to get to where ever I'm supposed to be on the computer. I'm really good at following directions. =)

Part of the problem is is that I don't know which settings, places, etc are ones that can really mess up the computer. I knew Windows quite well, enough to know where I should not be messing with things. I haven't had a lot of time to learn things with this one (had it about a month, but not a lot of significant time on it). I appreciate all the help, much better support than I was offered for my Windows computers!!

PS. Also just noticed that every time I close Firefox I have to force quit, not sure if this means anything, but there it is.

---

### Post by snowpine on 2009-04-28
Ubuntu will prompt you for your password if you're trying to do something that can "really mess up the computer". If you aren't prompted for the password, any changes you make only affect your user settings (in your /home/username folder).

In Ubuntu, we use the "sudo" (command line) or "gksu" (graphical applications) command to temporarily gain root access (to make system-wide changes).

I hope my suggestion in post #6 has solved your upgrade issues.

---

### Post by jltrafton on 2009-04-28
I posted again because of all the suggestions I didn't know how to actually execute ANY of them. Like I said, I know Windows, but even then it was not a super advanced knowledge. I do not know Ubuntu or anything else for that matter.  I've already said I need to be told how to get everywhere on this computer if someone suggests something. The #6 post was the least easy for me to understand. I don't know what a terminal is, I don't know anything. I can list on one hand what I do know about working with this computer. I can access all the programs, install/remove, get certain plugins and that sort of thing. That's about it.

Please reference this particular line in my last post:

"If anyone gives me suggestions I would need to know how to get to where ever I'm supposed to be on the computer. I'm really good at following directions."

However, I need the directions to be complete, not just the one thing I have to do. If I need to open a terminal, tell me how. If I need to "post the output" of something, tell me how.  


This applies to everyone. I hate feeling like I know nothing, so this is really difficult for me, especially since I assume it's REALLY easy. Please don't say I hope my previous suggestion helped, because if I'm still posting and it doesn't say "thanks for the help, it's fixed" that means I haven't tried anything because I don't know how to do it. Maybe you just can't teach an old dog new tricks.

Thanks again for putting up with such a green user. I appreciate the time and responses, I just can't stress enough how much I DON'T know about this OS. Please take that into consideration when responding.

---

### Post by egalvan on 2009-04-28
First off, let me say "Welcome to the Community".

You are starting on a long journey, that hopefully will take you places...

Second, please realize that you are posting on the **ABSOLUTE BEGINNER TALK** section of the forum...

That means, I think, that it is for **ABSOLUTE BEGINNERS**
Wow, what a concept :P

We all started out knowing nothing...
Welcome to the "other" club... :P


A "terminal" is simply one way of accessing your computer.
Although not technically correct, it is also known as the "command line"
or the "cli" which is short for **c**ommand **l**ine **i**nterface.

This is used to type commands that we want the computer to execute.

You access this by going to the menu bar at the top of your screen..

you should have

**Applications Places System**

up there....

click on **Applications**...

a "sub-menu" pops up... 
look for the one called **Accessories**
and move the mouse pointere over it...

another sub-menu opens up...

look for an application called **terminal**

click on it...

the terminal will open...

move the mouse pointer anywhere inside the window, and left-click...

you can now type commands on the cli, or command line...

You can also cut and paste commands from the suggestions that are given to you...
this cuts down on possible typos...

menu.lst 

is one such "typo-waiting-to-happen"... many folks think that is a "numeral one" **1**,
 followed by an "s"
 then a "t"...
nope, it's a "lower-case L" ** l**....

Also, spaces can be missed...

And Unix is case-sensitive...

Menu.lst
 is NOT the same as
menu.lst

doing a "copy&paste" will reduce these type of errors

By the way, there is a Beginner's Guide available for download...
either see the sticky at the top of the Absolute Beginner Talk
or click on this link

[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)



To post information that you may get from running commands in the terminal,
just highlight the desired text, and copy (either right-click or use the Edit menu)
then paste into the body of your message...

it is considered good manners to surround this with "code tags"..
to do this, highlight the text, then click on the # symbol at the top right of the message window.
I believe there are help pages that explain this and other forum stuff...

ErnestG

P.S.
Since you may be using terminal a lot, you can create a desk-top shortcut...
just access the terminal icon as explained above,
but** instead of left-clicking** on it to launch it,
**press and hold the middle button to "drag" it **to the desktop, then drop it anywhere you desire.
I did this after I got tired of accessing the menus for stuff such as "terminal" and "screen-shot" (another useful tool for transferring information)

---

### Post by capnthommo on 2009-04-28
hi jltrafton, just want to say egalvan is bang on about we all were absolute beginners once.  only a few weeks ago for me.  if you're willing to learn then you'll be ok in no time.  
just remember, if you remind people here that you need help to be explained in detail then that's what people will do - and i second the advice about the downloadable beginners guide - it's good.
there's plenty of help here and the crowd are friendly too.  as egalvan says, it's the absolute beginners section so don't be shy about asking for help.
i'll get out of the way now and leave it to people who know better than me
cheers nigel
):P

---

### Post by jltrafton on 2009-04-28
Thanks! I knew it was something easy like that (to find how to open terminal). I fear I haven't had the time to read the guide yet, packing to move from east to west coast. 

I'm still having problems but don't have time to do much about it right now. I will post later because it came up with something that I think should have been different.

Again, thanks!

---

