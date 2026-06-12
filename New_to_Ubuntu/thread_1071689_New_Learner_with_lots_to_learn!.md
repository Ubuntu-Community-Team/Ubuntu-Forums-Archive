---
title: "New Learner with lots to learn!"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by Al Fischer on 2009-02-16
Well, been threatening to try Linux for a while. Downloaded 8.10 Server and proceeded to follow the HowTo and everything went well. Googled to find out what VI was, Googled for the commands, and Googled for the GUI. Done. Loaded. Working.

My purpose it twofold. LEARN Linux and have a local server for testing my websites. 

My hosting uses Apache so I googled and installed Apache2. Put Putty on my Windows laptop and connected (Got the 'IT WORKS! message) 

What are the steps I must follow from here to be able to FTP my webs and access them locally for testing? My hosting also uses cpanel and I would prefer that just for consistency. Security on the server in not a concern as I am behind a firewall with Verizon 3g and a password protected router with WPA2 on wireless in a fairly remote area and don't intend to have anything critical on it.

I am now waiting for Amazon to deliver the 'Pocket Refenence' and another Linux book. 

So, some direction would be appreciated. Steep learning curve!

---

### Post by hyper_ch on 2009-02-16
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by bodhi.zazen on 2009-02-16
You are doing fine :)

For all things server, start here :

[http://doc.ubuntu.com/ubuntu/serverguide/C/](http://doc.ubuntu.com/ubuntu/serverguide/C/)

vi is awesome, vim is easier to user :

```
sudo apt-get install vim-full
```

You may also like nano (another editor).

My advices is that you use scp rather then ftp. You already have an ssh server installed, so use winscp from windows. the problem is FTP is easy to exploit. If you need ftp for some reason, use proftp or vsftp.

Secure your ssh server (change the port, use keys).

---

### Post by Bölvaður on 2009-02-16
try to use the repositories as much as you can unless if the program doens't show up in (System &#8594; Administrator &#8594;) Synaptic Package Manager, or that you have to use a special version... ect.

Downloading, installing and setting up programs your self is thing of the past, unless if you have special needs and need to compile... and stuff...

---

### Post by uberg on 2009-02-16
There are all sorts of resources for learning Linux on the web.  The following site is a little bit dated at times but is an excellent starting off point for documentation:

[http://www.tldp.org](http://www.tldp.org)

In particular, under guides, I am a big fan of Machtelt Garrels' guides; Bash Guide for Beginners; and, Introduction to Linux - A Hands on Guide.  I am a big fan of her writing.  These are an excellent start.  I used them.

I am writing this response to you using vim.  Anything longer than a sentence or two and I have to use vim.  Learn vim and it will become a close friend.  The problem with vim is that it has a very steep learning curve and you should really be a touch typist.  After you installed vim as suggested above run vimtutor from a terminal command line for a nice introduction to using vim.  You'll soon be hooked.  If you are not a touch typist might i suggest gtypist or ktouch to help you learn how.

As suggested read the policy for posting.  Also, break your questions (grouped by relationship) up into separate posts where appropriate.  For instance you stated a two fold purpose - LEARN Linux - and - learn to set up a web server.  Two different topics.

I can tell by your enthusiasm that you will figure things out.  The journey is rewarding.  Good luck.

Joe

---

### Post by Al Fischer on 2009-02-16
Everything I installed was from the 'repository' I believe.
I did 'apt-get install'

However, what I installed was Apache2. What is the difference in Tomcat?  Should I remove Apache2? if so how?

I will read the server guide and possibly it will answer many of my questions.

---

### Post by Bölvaður on 2009-02-20
no you install Tomcat in addition to apache.
I was never any good with jsp and used orion :(

---

