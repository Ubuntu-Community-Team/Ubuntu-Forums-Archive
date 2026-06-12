---
title: "need recommendation for book on Ubuntu"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by eisenstadt on 2011-02-04
I would like to read a book on Ubuntu. I CANT use the 166 page Ubuntu pdf because I am photosensitive and the default white of a pdf file for 166 pages is impossible for me to read. I read white printed pages, so I need your recommendation for a book on Ubuntu or more general. I have an Ubuntu OS on a flash drive but unfortunately for the moment I cannot change my BIOS boot disk priority from the hard drive to the flash drive. This is a Gigabyte mb and Gigabyte support has suggested a workaround which doesnt work. I plan to physically remove hard drive cable with the thought that there would then only be the flashdrive listed 1 in the harddrive boot priority window. But I also conclude that I should reinstall with great care.

I suspect I have a currupted Ubuntu o.s. on the flash drive. I would like to reinstall os on this flashdrive and reformat it if necessary. Is there a Webpage with step-by-step instructions? The local library has 5 or 6 books on Ubuntu. 

The app I used to install Ubuntu 10.04 claimed that it would wipe all files on flash drive, but the files it came with from Kingston were not deleted. I have put a screen grab of the files on the flashdrive at [www.charlesumlauf.com/files.jpg]("http://www.charlesumlauf.com/files.jpg") - PLEASE excuse the grey background color as I have it set. Aside the intrusive Kingston files which I will delete, is there anything that can be deduced from the files as displayed?

I apologize for the many questions here. As you see, I am serious fumbling arround.

Newbie Michael Eisenstadt
Austin Texas

---

### Post by mikewhatever on 2011-02-04
I'd search amazon.com for a book on Ubuntu, in fact, I just did, and here is the outcome.
[http://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Dstripbooks&field-keywords=ubuntu&x=0&y=0](http://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Dstripbooks&field-keywords=ubuntu&x=0&y=0)

---

### Post by Tyggna on 2011-02-04
The best book you'll ever find on Ubuntu (if you're just getting started with it) is in Ubuntu itself. 

Let me throw out a few quick pointers to get your started:

First, you don't need to browse around the internet and find a program you can download and install to get new software--it's all in the repository, and it's all free.  Just find the add/remove programs button, and type in something to help it find what you're looking for.  This is referred to as installing a package, rather than a program--because it includes programming libraries and configuration files with it as well.

Second,  Linux is a text-based OS.  Everything you see in front of you is running on top of a text-based terminal (like back in the old DOS/windows 3.1 days, if you've been around that long).  If you want to learn Linux, you're gonna need to know your way around the terminal.

Third: inside the terminal, if you start typing a command (command can be the name of any program you have installed) you can hit tab once to have the terminal finish typing for you, or if nothing happens, you can hit tab twice and it'll give you a list of options.  Simply hitting tab twice (don't recommend that) will give you an exhaustive list of all the programs installed.

From there, if you have questions on what a command does, you can type: ** man command** and it'll give you a description of how to use that command and what it does.


Those are the three things I wish someone had told me when I started in with Linux.  If you have more questions, feel free to ask.

---

### Post by davidmohammed on 2011-02-04
if you use adobe reader in windows (called acroread in ubuntu) then you can change the background colour as follows:

1) Open Adobe Reader. Go to Edit - Preferences - Accessibility.
2) Make sure the "Replace Document Colors" is checked and click on Custom Color.

I would warmly recommend the [ubuntu manual]("http://ubuntu-manual.org/") for beginners.

---

### Post by eisenstadt on 2011-02-04
Thanks Mikewhatever. The local library has this very book and I have requested it.

---

### Post by eisenstadt on 2011-02-04
> Let me throw out a few quick pointers to get your started:

> First, you don't need to browse around the internet and find a program you can download and install to get new software--it's all in the repository, and it's all free. 

What is the repository?

> Just find the add/remove programs button, and type in something to help it find what you're looking for.  This is referred to as installing a package, rather than a program--because it includes programming libraries and configuration files with it as well.

This is Chinese to me for the moment.

> Second,  Linux is a text-based OS.  Everything you see in front of you is running on top of a text-based terminal (like back in the old DOS/windows 3.1 days, if you've been around that long).  If you want to learn Linux, you're gonna need to know your way around the terminal.

I am familiar with line commands.

> Third: inside the terminal, if you start typing a command (command can be the name of any program you have installed) you can hit tab once to have the terminal finish typing for you, or if nothing happens, you can hit tab twice and it'll give you a list of options.  Simply hitting tab twice (don't recommend that) will give you an exhaustive list of all the programs installed.

I'm not yet at a point to follow your recommendations.

> From there, if you have questions on what a command does, you can type: ** man command** and it'll give you a description of how to use that command and what it does.

I have done that in DOS but I never got much mileage out of what returned.

Thank you for writing.

Michael Eisenstadt

---

### Post by eisenstadt on 2011-02-04
> **davidmohammed said:**
> if you use adobe reader in windows (called acroread in ubuntu) then you can change the background colour as follows:

> 1) Open Adobe Reader. Go to Edit - Preferences - Accessibility.
> 2) Make sure the "Replace Document Colors" is checked and click on Custom Color.

> I would warmly recommend the [ubuntu manual]("http://ubuntu-manual.org/") for beginners.

Thanks David for instructions for changing .pdf page color. Never knew that could be done.

Michael Eisenstadt

---

### Post by uRock on 2011-02-04
> **eisenstadt said:**
> The local library has this very book and I have requested it.
Some of the best things in life free. If you run into problems, then you can ask them here and someone will help you find a fix.

Welcome to Ubuntu Forums,
uRock

---

### Post by Tyggna on 2011-02-04
> What is the repository?
A repository is a computer on the internet that keeps a copy of all the software your computer can have on it.  Think of it as a digital book store for all your programs--only everything is free and you can just take it off the shelves.

> Just find the add/remove programs button, and type in something to help it find what you're looking for.  This is referred to as installing a package, rather than a program--because it includes programming libraries and configuration files with it as well.
This is Chinese to me for the moment.

So, depending on which version of Ubuntu you have installed, go to Applications->Add/remove (at the bottom), or go to System->administration->add/remove, that's what I mean when I say the "add/remove programs button."  It's in one of those menus at the top, and it's your gateway to the repository.  Once you're there, you can install new programs on your Linux machine.
 

> Third: inside the terminal, if you start typing a command (command can be the name of any program you have installed) you can hit tab once to have the terminal finish typing for you, or if nothing happens, you can hit tab twice and it'll give you a list of options.  Simply hitting tab twice (don't recommend that) will give you an exhaustive list of all the programs installed.
I'm not yet at a point to follow your recommendations.

That's fine.  You are going to need to get familiar with the terminal though, and all the books will point you there as well.  When you get a chance, go to Applications->accessories->terminal and start playing around there.  For many people, that is more valuable than what you can read in the texts.   A good starter is to open up the terminal program and type "firefox"

---

### Post by uRock on 2011-02-04
> **eisenstadt said:**
> What is the repository?A repository is where the Update Manager looks for updates and Ubuntu Software Center looks for software.

> This is Chinese to me for the moment.If you are using Ubuntu 10.x, then you will want to open the Applications menu, then select Ubuntu Software Center. (See image 1)
> I am familiar with line commands. You don't have to learn the command line to get things done in Ubuntu. There is a GUI(Graphical User Interface) for just about everything you need to get done.

---

### Post by eisenstadt on 2011-02-04
> **Tyggna said:**
> > What is the repository?
A repository is a computer on the internet that keeps a copy of all the software your computer can have on it.  Think of it as a digital book store for all your programs--only everything is free and you can just take it off the shelves.

> Just find the add/remove programs button, and type in something to help it find what you're looking for.  This is referred to as installing a package, rather than a program--because it includes programming libraries and configuration files with it as well.

>>This is Chinese to me for the moment.

> So, depending on which version of Ubuntu you have installed, go to Applications->Add/remove (at the bottom), or go to System->administration->add/remove, that's what I mean when I say the "add/remove programs button."  It's in one of those menus at the top, and it's your gateway to the repository.  Once you're there, you can install new programs on your Linux machine.
 
> Third: inside the terminal, if you start typing a command (command can be the name of any program you have installed) you can hit tab once to have the terminal finish typing for you, or if nothing happens, you can hit tab twice and it'll give you a list of options.  Simply hitting tab twice (don't recommend that) will give you an exhaustive list of all the programs installed.


>> I'm not yet at a point to follow your recommendations.

> That's fine.  You are going to need to get familiar with the terminal though, and all the books will point you there as well.  When you get a chance, go to Applications->accessories->terminal and start playing around there.  For many people, that is more valuable than what you can read in the texts.   A good starter is to open up the terminal program and type "firefox"

I appreciate all the advice. At this point, my problem is to INSTALL Ubuntu 10.04 on a 
flash drive and have it boot up the Ubuntu OS. Unfortunately, the issues in my original post remain unanswered. 

How 'bout someone telling me where I can find step-by-step instructions to install Ubuntu to a flash drive? Perhaps there is a web page, perhaps the step-by-step instructions are in the manual (Yes I have been reading the manual, now that the page's background is not blinding white).

Anyone?

TIA

Michael Eisenstadt

---

### Post by uRock on 2011-02-04
Scroll down to step two. [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

