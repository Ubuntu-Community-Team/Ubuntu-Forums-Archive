---
title: "Brand new and stumped already !!"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by Entwood on 2009-02-06
Hi folks

Thought I'd give this Linux thing a try, and have been given a UBUNTU CD by a mate .. version 6 I think.

First problem solved by reading lots .. I now know how to press F6 at the right time and then type noacip .. to get the CD to actually boot !!

When I then choose the install option I'm getting error messages about "failure to start X server (your graphical interface) "              whatever option I choose I end up at what I would,in windows speak, call a DOS window with command line prompts. Starts with

ubuntu@ubuntu:~$

By playing around I've found the --help command .. but the problem is it scrolls down too fast to read the commands. Now in old DOS a -p would have limited this to one page....

So, a couple of questions if I may ..... 1) how do I in this command line mode limit scrolling to a single page ? 2) How do I get ubuntu back into install mode from this position ?

Regards, and thanks for any help, Entwood

---

### Post by hyper_ch on 2009-02-06
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by LowSky on 2009-02-06
> **Entwood said:**
> Hi folks

Thought I'd give this Linux thing a try, and have been given a UBUNTU CD by a mate .. version 6 I think.

Version 6? Doesn't exist and anything that has 6.06 or 6.10 is really out of date.
> **Entwood said:**
> 
First problem solved by reading lots .. I now know how to press F6 at the right time and then type noacip .. to get the CD to actually boot !!
How old is your computer that you are trying to use?

> **Entwood said:**
> 
When I then choose the install option I'm getting error messages about "failure to start X server (your graphical interface) "              whatever option I choose I end up at what I would,in windows speak, call a DOS window with command line prompts. Starts with

ubuntu@ubuntu:~$[/code]
this happens alot, just type: startx
that should get you the the GUI

[QUOTE=Entwood;6688283]
By playing around I've found the --help command .. but the problem is it scrolls down too fast to read the commands. Now in old DOS a -p would have limited this to one page....

So, a couple of questions if I may ..... 1) how do I in this command line mode limit scrolling to a single page ? 2) How do I get ubuntu back into install mode from this position ?

Regards, and thanks for any help, Entwood

1.Try a newer disc. Ubuntu current long term release is 8.04.02, downloadable from the Ubuntu website
2.Older computer may not do well with Ubuntu as it is for recent machnes (thoise made in the last 5-8 years). If your machine doesn't fit into this then try another version of Linux.

---

### Post by Entwood on 2009-02-06
Thanks for the 2 quick responses ... 1) thread retitled as requested

2. a) system is about 15 months old Asus M2N32 Deluxe M'board with 4 Gb RAM AMD 64 X2 4200 CPu with a GeForce 8500 GT graphics card

b) Now downloading a newer version :)

c) startx command gives an error "(EE) no devices detected" and Fatal server error: No screens found XIO: fatal error ........(snip)

d) still can't get the help page  --help to stop so I can actually read it

Regards

Entwood

---

### Post by GMachine_24 on 2009-02-06
Re: your comment

```



By playing around I've found the --help command .. but the problem is it scrolls down too fast to read the commands. Now in old DOS a -p would have limited this to one page....


```

as a general "good things to know," a couple things:

1. If you have a page full of text and want it all to go away and get you back to a command prompt at the top of a clear screen, type

```


clear


```

at the command prompt.

Also, if you're trying to limit the information posted to your screen to one screen worth of info at a time, I use this command "| more" without the quotes and that is a 'pipe' and the word 'more' after the command you give to display text. In other words, e.g.:

```


ls /usr/bin | more


```

[Note: The pipe command is usually the upper case of the \ keyboard key and often looks like two short vertical lines, one just above the other.]

You will end up with one screen of text with the word "more" highlighted in the lower left corner of your terminal window. To get to the next page of text, merely hit the 'space' bar. To quit displaying text, hit 'q' and that should take you back to a prompt.

Be advised that previous comments in this thread should be taken to heart so helpers have some idea what your problem is from the title - in other words, be specific.

--gm

---

### Post by Entwood on 2009-02-06
Thanks for that..

Tried to retitle the thread but the system won't let me. Downloaded V8.10 and that seems to be installing right now.. 83% complete at the moment.

Interesting that this uses pipe commands ...haven't used them for many a long year.. do all the old DOS pipes work or just a certain few ??

I'll have a play once the install completes... probably be back with more questions that the "pocket guide" doesn't cover  

Regards

Entwood

---

### Post by Zill on 2009-02-06
Entwood:  Just in case you hadn't realised it most Linux distributions, including Ubuntu, are also "Live" CDs.  This means that it is not essential to install your new OS to the HDD initially.  All you have to do is to reboot your PC with the Linux CD in the drive and chose the "run from CD" option, rather than "Install".

The OS, and all the included applications, will then run directly from the CD, albeit more slowly than on a full HDD installation.

This is an excellent method of checking that your hardware is compatible and giving you a taste of the OS without changing anything on your HDD.

If you are happy with the new OS then there is an "Install" icon on the desktop to install it permanently to your HDD.

---

### Post by LowSky on 2009-02-06
> **Entwood said:**
> 
Interesting that this uses pipe commands ...haven't used them for many a long year.. do all the old DOS pipes work or just a certain few ??


Dont expect that many old DOS commands will work, most wont.
And with Ubuntu most commands can be done from a GUI, just like in MS Windows. Just like Windows you can still use the command line as often as you like, as many linux users prefer.

---

### Post by Celegorm on 2009-02-06
> **Entwood said:**
> Interesting that this uses pipe commands ...haven't used them for many a long year.. do all the old DOS pipes work or just a certain few ??

Well I don't know how dos pipes work, but the pipe in linux is used to connect commands; it just treats the output of the first command as the input of the second. Also it's generally suggested to use "less" rather than "more" for viewing long output (press 'q' to exit less). In addition to using the --help flag to get help with commands, you can also use the commands "man" and "info", for example, "man less", "info startx", or "info info". Man tends to give very terse and technical information on a topic, whereas info will be of a more tutorial nature.

---

### Post by SteveNorman on 2009-02-06
what will happen on all ubuntu installs....


no proprietary drivers

usually means no wifi and no 3d graphics.

to get your hardware to work the kernel needs specific modules added to it. Older versions cant have modules for hardware from the future, so that may be why you install didnt take. You either have to build your kernel with the modules you need (pain in the butt) or load the latest version, which you are wisely doing.


So for the proprietary drivers you will have to add them yourself. Ubuntu software is available from on line storage called repositories (repos). you will have to add some repro addresses to a special file that contain proprietary material, or other gray area material. I recommend googling your computer type and ubuntu, which should lead you to a help page on setups for your particular hardware.

there are a few files that will need to be familiar with, one is
 /etc/X11/xorg.conf  (most problems with your display are here)
/etc/apt/sources.list  (file containing repo addresses)


a couple good articles to read through

[http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html](http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html)

[http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/)


once you get linux configured I think youll like it better than ms/mac.

---

