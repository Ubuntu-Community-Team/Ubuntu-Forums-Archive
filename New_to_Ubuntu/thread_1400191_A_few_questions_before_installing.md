---
title: "A few questions before installing"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by fabis94 on 2010-02-06
1. Can you do most of the things you can do with CLI with a GUI? I'm not really a CLI kind of a person and i would hate to have to remember all the commands for doing basic things like installing, extracting or even just making new folders. That's the reason why i didn't use Linux before - because i want to be able to do everything (well most of it) with a GUI easily.

2. Many programs come with a bz2. How do you install those without using the CLI?

3. I have ~448MB RAM, about 1.8GHz CPU and 64MB VRAM. Which kind of Linux (ubuntu, kubuntu, xubuntu etc.) i should use if i want to be able to develop Java and other applications without lag? Will Ubuntu be good?

4. If you play Windows games on Linux (through that program), does it use up more than when played on Windows? Are there many games that run on Linux by default?

5. Is it true that Ubuntu uses less CPU than Windows?

---

### Post by mushwars on 2010-02-06
> **fabis94 said:**
> 1. Can you do most of the things you can do with CLI with a GUI? I'm not really a CLI kind of a person and i would hate to have to remember all the commands for doing basic things like installing, extracting or even just making new folders. That's the reason why i didn't use Linux before - because i want to be able to do everything (well most of it) with a GUI easily.

2. Many programs come with a bz2. How do you install those without using the CLI?

3. I have ~448MB RAM, about 1.8GHz CPU and 64MB VRAM. Which kind of Linux (ubuntu, kubuntu, xubuntu etc.) i should use if i want to be able to develop Java and other applications without lag? Will Ubuntu be good?

4. If you play Windows games on Linux (through that program), does it use up more than when played on Windows? Are there many games that run on Linux by default?

5. Is it true that Ubuntu uses less CPU than Windows?
In *buntu there is no need to use the commandline interface. 

As far as which is easiest I would say ubuntu, as far as which one looks nicer definitly kubuntu.

In any *buntu you will have no problem with your system specs. Unless you plan on playing games, you will run it just as well as someone that has a brand new alienware. ;)

Games. lets see, if you are into games like doom3 and quake you can play those on linux. There are many other games like exitebike and torcs that are quite fun, so be it they are nothing like windows games that doesnt mean you wont have fun. Also there is a program called **wine that allows you to install windows programs** I run games like halflife  in wine and it runs no problem for me and my laptop has simmilar specs.

Ubuntu as far as cpu will us preceviably WAY less cpu, it is not a resource hog like winblows, you will be able to make it look nicer with less fuss too.


Good luck.

p.s. yes programs that run in "that program" >> wine will run slower than on windows, because it has to EMULATE windows binaries. No big deal though depending on the program you wont even notice a difference.

check out [http://www.winehq.org/]("http://www")****

---

### Post by halitech on 2010-02-06
> **fabis94 said:**
> 1. Can you do most of the things you can do with CLI with a GUI? I'm not really a CLI kind of a person and i would hate to have to remember all the commands for doing basic things like installing, extracting or even just making new folders. That's the reason why i didn't use Linux before - because i want to be able to do everything (well most of it) with a GUI easily.

yes, most things can be done with the GUI instead of the command line. Most often you will get help on the forums with a command to copy and paste because its easier then trying to explain where to click

> 2. Many programs come with a bz2. How do you install those without using the CLI?

easiest way to install things is with Synaptic or Software Center

> 3. I have ~448MB RAM, about 1.8GHz CPU and 64MB VRAM. Which kind of Linux (ubuntu, kubuntu, xubuntu etc.) i should use if i want to be able to develop Java and other applications without lag? Will Ubuntu be good?

I would go Ubuntu or Xubuntu. I don't do any developing so I can't say what kind of lag you would run into while programming

> 4. If you play Windows games on Linux (through that program), does it use up more than when played on Windows? Are there many games that run on Linux by default?

Windows programs (games or apps) don't run natively on Linux and you need to use WINE. I'm not a gamer so not sure how they run. Some supposedly run fine and others don't work at all.

> 5. Is it true that Ubuntu uses less CPU than Windows?

Depends on what you are doing and what apps you are running. It does use resources more efficiently overall though

---

### Post by fabis94 on 2010-02-06
Thanks for the fast reply. So you really don't even need to use the CLI? Every time someones talking about Linux, eventually people start saying it is very complicated and you must use the CLI. If that's not true, then Linux sure as hell is awesome :)

Also what about my computers drivers? How do i update them on Linux?

---

### Post by mushwars on 2010-02-06
> **fabis94 said:**
> Thanks for the fast reply. So you really don't even need to use the CLI? Every time someones talking about Linux, eventually people start saying it is very complicated and you must use the CLI. If that's not true, then Linux sure as hell is awesome :)

Also what about my computers drivers? How do i update them on Linux?
put the word drivers out of your head, you wont even need to bother with them. ;)
*buntu takes care of all the drivers so you dont have to

[s]<-- I dont know why I am typing in italix, it says I am not[/s]

I use gentoo and I rarely have to use the CLI (aka shell / terminal) and it is the most terminal driven os, it doenst even come with a gui, but definitly start on *buntu as ALL of us have at one point, its a great starting point.

---

### Post by wojox on 2010-02-06
If you need to use the Terminal, just post on here and we'll tell you what to copy and past into it.

Not alot of programs are .bz2, that's what we have the repo's for. 

I would use ubuntu or xubuntu with those specs.

---

### Post by cbabbage on 2010-02-06
Using the CLI can be scary for those not used to it; but it is an efficient and neat way of system administration. A little effort in learning some of the basics will be well worth your while.
You'll find regular upgrades of the linux kernel will take care of most driver upgrades.

---

### Post by fabis94 on 2010-02-06
Yeah i know, but i would very much prefer to use CLI as less as possible.

Ok so i don't need driver updates. That's neat.
What about updating stuff? I remember i once tried to update Java on a computer using Ubuntu and it literally drove me nuts. I tried doing it with CLI and just messed up. Can i do updating with GUI too?

---

### Post by wojox on 2010-02-06
Sure, just use Synaptic Package Manager. Yes you can update with a GUI.

---

### Post by fabis94 on 2010-02-06
Ok thanks. What about the root user? When i used that Ubuntu computer once, it asked me the root user and pass for doing stuff on the CLI.

Is it possible to just make an admin account that doesn't ask you the root pass and username when you do stuff?

---

### Post by mushwars on 2010-02-06
> **fabis94 said:**
> I remember i once tried to update Java on a computer using Ubuntu and it literally drove me nuts. I tried doing it with CLI and just messed up. Can i do updating with GUI too?
It was not ubuntu then, or you were using apt in the terminal (which is what I would do) but you can use the update manager and it will do it automatically. If you dont see an update there then you can go to the package manager and update it through there

---

### Post by quik_lives on 2010-02-06
> **fabis94 said:**
> Ok thanks. What about the root user? When i used that Ubuntu computer once, it asked me the root user and pass for doing stuff on the CLI.

Is it possible to just make an admin account that doesn't ask you the root pass and username when you do stuff?

It may be possible somehow, but it's adverse to the whole setup of Linux - part of the reason the system is more secure is because you ONLY use root when you need to, rather than wandering around as admin all the time which gives you (not you specifically, the user in general) too much opportunity to do something stupid.

---

### Post by dearingj on 2010-02-06
> **fabis94 said:**
> Ok thanks. What about the root user? When i used that Ubuntu computer once, it asked me the root user and pass for doing stuff on the CLI.

Is it possible to just make an admin account that doesn't ask you the root pass and username when you do stuff?

Ubuntu asks you for your password (technically not root's password) to gain administrative rights when you need them. If you really want to log directly into the root account, that is possible to set up, but logging in as root for day-to-day activities such as web browsing is an unnecessary security risk so I'd advise against it.

---

### Post by tom.swartz07 on 2010-02-06
As you begin to use Ubuntu- I would DEFINITELY recommend you at least skim through this book.
[http://books.google.com/books?id=kHLlJzI6L20C&printsec=frontcover#v=onepage&q=&f=false](http://books.google.com/books?id=kHLlJzI6L20C&printsec=frontcover#v=onepage&q=&f=false)

It has helped me so much in the past, and even to this day I find myself looking things up in it just to refresh my memory! :D


Hope you enjoy it!




PS- dont worry about the CLI, its a bit intimidating at first, but as you grow and learn about the OS- you will find that you can do things nearly 5x faster. When I first started, I was a windows point-and-click user, now i can not only point-and-click, but i could do complex things that pointing and clicking would take hours to do, all in one simple command.

It will come- dont worry

---

### Post by Ubu2010 on 2010-02-06
I agree with many posts above, especially this last one ^^^.
I am fairly new to Linux, and am currently taking a Linux class in school, and the CLI is already less scary. Thats because the instructor is very thorough without being overbearing. 

So take the advice of asking people here, reading books, etc. But dont shy away from the CLI just because it is a bit unfamiliar. I am living proof that the CLI doesn't kill you and it actually can makes life easier depending on the task(s) at hand. There is room for both worlds - CLI and the GUI- in Linux. 

But to add my two cents about your concern regarding the GUI, it is very slick in Ubuntu, and some other notable Linux distros as well, though I keep coming back to Ubuntu personally.

---

