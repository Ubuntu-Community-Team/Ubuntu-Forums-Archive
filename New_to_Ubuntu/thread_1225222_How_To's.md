---
title: "How To's"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by acimna on 2009-07-28
Where does one get a list of, what appear to be, very informative how to's?  

Moreover, where can a beginner such as I find step-by-step tutorials?  My knees get weak when I think of having to enter the system on a command level (terminal area?).

I got Hardy going eventually, but can't get Huawei EV-DO USB Modem working and Open Office keeps on bombing out.

Will I ever get to Edubuntu and guiding children into the wonderful world of Ubuntu?

---

### Post by frodon on 2009-07-28
Moved to beginner talk forum.

---

### Post by tarps87 on 2009-07-28
This is probably a good place to start:
[https://help.ubuntu.com/](https://help.ubuntu.com/)

There is all so the ubuntu pocket guide
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

failing that, one this forum and google.

Looks like you may be in luck with the modem
[http://ubuntuforums.org/showthread.php?t=1090119](http://ubuntuforums.org/showthread.php?t=1090119)
It looks like the solution is on Ubuntu 9.04 Jaunty but may work on Hardy.
If not post back and we'll see what we can do.
You may want to replace the line
```
sudo vi /etc/wvdial.conf
```
with
```
sudo gedit /etc/wvdial.conf
```

ps the terminal is not so scary once you get to know it, don't let it put you off

---

### Post by superprash2003 on 2009-07-28
also [www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by aysiu on 2009-07-28
> **acimna said:**
> 
Moreover, where can a beginner such as I find step-by-step tutorials?  My knees get weak when I think of having to enter the system on a command level (terminal area?).
> **superprash2003 said:**
> also [www.ubuntuguide.org](www.ubuntuguide.org) The Ubuntu Guide is great, but it is all terminal commands, so in this particular situation, I don't think that'd be the first place for this user to go.

I created a little site targeted at beginners. It's full of screenshots and really takes you step by step through the process:
[http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu)

---

### Post by acimna on 2009-07-28
Thanks Friends!

This is really great help ... perhaps more than you may know.

Being an education curriculum developer (and homeschooler) decisions need to be made shortly as to how to coherently proceed in Computer Science from Grade 2 (Binary Code level) to ... well, we haven't decided yet.  

I'll only today start digging into the terminal area myself - following the guidance you provided - but I was wondering whether the terminal could provide hands-on stimulation, acquaintance, practice and exploration opportunities ... or perhaps even formal educational experiences??

It would have been so much more fun if my son (age 7, Grade 2) had been ready to do this installation I'm busy with!

---

### Post by acimna on 2009-07-28
Okay, Tarps87, is the advice you gave to replace sudo vi /... with sudo gedit /... to save me the hassle of having to find out what "favourite editor" means by giving me "gedit" as one or will the programme find the editor by itself (given the misspelt get-it as command)?

Thanks, this jargon is going to take some getting used to!

And to think I have to wade through it all myself and from scratch!!

Will look at the other URLs now.

---

### Post by aysiu on 2009-07-28
Should be *gksudo gedit*, not *sudo gedit*.

It's good to get into the habit of using *gksudo* with graphical applications.

More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by llamabr on 2009-07-29
While we're having this argument, rather than opening gedit, you could use my favorite text editor from the terminal, by typing:

```
nano
```

It's simpler and more intuitive than vi, and command line, unlike gedit.

---

### Post by utnubuuser on 2009-07-29
Ubuntu - the complete reference by Richard Petersen is very comprehensive.  - Ask your local library to bring in a copy.

---

### Post by QIII on 2009-07-29
You don't have to wade through it by yourself from scratch.  That's why we're all here.

It is advisable to first use resources available, and several posters have pointed you to some good ones.

But if you come across something you don't understand -- or simply can't find easily -- don't hesitate to come back with a question (best to start a new thread for each question) and say you read something and didn't understand it.

We won't bite.  Much.

---

### Post by acimna on 2009-07-29
Typed in the HUAWEI commands, as suggested ... but no [Shhh] sound ... or any connection.

When I tried to use Firefox and Pidgin, they, as does OpenOffice, simply bomb out the moment I click on anything.

We had a few power-outs yesterday (as is common in Namibia).  Should I re-install Hardy?

---

### Post by tarps87 on 2009-07-29
> **acimna said:**
> Thanks Friends!

This is really great help ... perhaps more than you may know.

Being an education curriculum developer (and homeschooler) decisions need to be made shortly as to how to coherently proceed in Computer Science from Grade 2 (Binary Code level) to ... well, we haven't decided yet.  

I'll only today start digging into the terminal area myself - following the guidance you provided - but I was wondering whether the terminal could provide hands-on stimulation, acquaintance, practice and exploration opportunities ... or perhaps even formal educational experiences??

It would have been so much more fun if my son (age 7, Grade 2) had been ready to do this installation I'm busy with!

> **aysiu said:**
> Should be *gksudo gedit*, not *sudo gedit*.

It's good to get into the habit of using *gksudo* with graphical applications.

More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

> **acimna said:**
> Okay, Tarps87, is the advice you gave to replace sudo vi /... with sudo gedit /... to save me the hassle of having to find out what "favourite editor" means by giving me "gedit" as one or will the programme find the editor by itself (given the misspelt get-it as command)?
...

gedit is the default text editor for Ubuntu, I suggested it a I assume you do not have a favourite editor and it is simple to use

> **acimna said:**
> Typed in the HUAWEI commands, as suggested ... but no [Shhh] sound ... or any connection.

When I tried to use Firefox and Pidgin, they, as does OpenOffice, simply bomb out the moment I click on anything.

We had a few power-outs yesterday (as is common in Namibia).  Should I re-install Hardy?

Could you post the output of the command "sudo wvdial". it should end something like ip set and then an ip address. You will need to leave this terminal running (ctrl+c to close connection). As far a I am aware there should been no sound hear, or at least there isn't when I use my moblie as a modem.
To test the connection you could try pinging google.

As for the programs exiting this seem very strange, can you try running the programs from a terminal and see if there are any obvious errors repoted. e.g.
```
firefox
```

> **llamabr said:**
> While we're having this argument, rather than opening gedit, you could use my favorite text editor from the terminal, by typing:

```
nano
```

It's simpler and more intuitive than vi, and command line, unlike gedit.

actually my favourite is nano :P

---

### Post by philinux on 2009-07-29
> **acimna said:**
> Where does one get a list of, what appear to be, very informative how to's?  

Moreover, where can a beginner such as I find step-by-step tutorials?  My knees get weak when I think of having to enter the system on a command level (terminal area?).

I got Hardy going eventually, but can't get Huawei EV-DO USB Modem working and Open Office keeps on bombing out.

Will I ever get to Edubuntu and guiding children into the wonderful world of Ubuntu?

Keep this forum in mind too.
[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

---

### Post by acimna on 2009-07-29
Okay, I'm working on a faulty Pentium II while trying to set up the new 4GHz, 500GBHDD machine we bought with money donated from an unknown person in Australia (we are full-time volunteers who have not earned wages for 16 years now).  The machines share the same monitor, so it's a lengthy stop-start process to and fro between the machines.

To answer your questions: 

I first installed the "tweaked" option, but got nothing, so I typed in the first option.

Yes, the response did go past the local and remote IP addresses and primary and secondary DNS addresses to end at -

pppd: ??[06][08]

and medium-pitched sounds coming from the speakers.

So I tried Firefox and typed in my webmail address.  then it disappeared from the screen.  Attempts to get it back or open Pidgin simply resulted in the loading wheel running for awhile and then stopping, but no program.

I'll try your suggestion (hoping that to type firefox on the first screen is what you mean):

As for the programs exiting this seem very strange, can you try running the programs from a terminal and see if there are any obvious errors repoted. e.g.
 	Code:
 	firefox 
Incidentally, how to I close threads I started in the forum that were not responded to?

---

### Post by tarps87 on 2009-07-29
By the firefox command I mean open up a terminal ant typing in firefox followed by enter, this will run the program.

It sounds like it has connected and working, although it does seem like something has gone badly wrong with the install which is causing programs to close. If you have got the live cd it maybe worth booting into it (try but don't install option) and trying to open up firefox or open office.

To confirm that you have a working connection, in another terminal
```
ping www.google.com -c 3
```
this should return ping successful.

I have just seen the other threads, it should work in Jaunty which may be worth a try if we can solve the crashing programs problem. On a more technical note, if you choose to install Jaunty you may want to manually partition and set the format to ext3 rather that ext4 as there have been problems reported when ext4 an a power failure occurs. Ext3 is used in Hardy

---

### Post by winemaker9 on 2009-07-29
Interesting tool I found about 6 months ago which may interest some.  I know some of us use that "OTHER" system and have external drives with data more often than not formatted as either FAT32 (common across almost all platforms) or NTFS which is XP native, but can be accessed by ntfs3g   

Wouldn't it be nice to have your external drives formatted at EXT3, but still accessible from XP?  Well, if you go to 

[http://www.ext2fsd.com/projects/projects.htm#ext2fsd](http://www.ext2fsd.com/projects/projects.htm#ext2fsd)

Take a look, it really works and is painless to set up in XP..., handles both ext2 & ext3, eventually will do ext4 I believe.  Just plug in a linux drive and xp handles it with no issue.    

Enjoy...

---

### Post by theozzlives on 2009-07-29
> **acimna said:**
> Okay, Tarps87, is the advice you gave to replace sudo vi /... with sudo gedit /... to save me the hassle of having to find out what "favourite editor" means by giving me "gedit" as one or will the programme find the editor by itself (given the misspelt get-it as command)?

Thanks, this jargon is going to take some getting used to!

And to think I have to wade through it all myself and from scratch!!

Will look at the other URLs now.

I started from scratch in 2007, I was an avid DOS and Windows tech. In 2004 my friend tried to talk me into Linux (I thought Linux = UNIX) and I wouldn't hear of it. Well long story short I had no clue when I jumped in with both feet (lost contact with my friend). Turned out, it's not as hard as it looks, I believe you'll do fine and we're here to help.

---

### Post by acimna on 2009-07-29
Okay, so let's go Jaunty then, as suggested.

But then I need to find out if this machine is 32Bit or 64Bit in order to get the correct Edubuntu software for Jaunty.  The supplier's invoice reads: Intel Dual Core @ 2.5GHz, 4GB DDRII Memory, ... 512MB Geforce NVidia graphics card.

Also, where do I read how to correctly partition the HDD - this time BEFORE I plunge in headlong - again!  I may need to install Linux Suze in one partition.  Ubuntu's Open Office document workspace (visible on the screen) has a considerably smaller area than Suze's - and I need all the workspace I can get for the design of educational worksheets for students.

I thank every advisor for the time spent to help out.  The hick-ups are really no worries to me.  They provide great learning experiences to pass on to the next generation and those less informed than myself (if indeed there are folk in that category!).  It will all come together soon and we'll all be the wiser for the journey we experienced together.

This is a most encouraging experience of collaborative participation - true community - and I thank you for your invaluable contribution to the raising of the collective human consciousness.

---

### Post by QIII on 2009-07-30
Your machine will run the 64 bit version.  It'll run the 32 bit version, too, if you like.

As for partitioning, I'll let someone else give that a go.

I used to do dual boots on single drives, but gave that up years ago for separate drives so I could be lazy and just use the whole drive when installing.

Lazy these days, and I'm able to weedle the wife out of a little more pocket change for extra hard drives ...

---

### Post by tarps87 on 2009-07-30
> **acimna said:**
> Okay, so let's go Jaunty then, as suggested.

But then I need to find out if this machine is 32Bit or 64Bit in order to get the correct Edubuntu software for Jaunty.  The supplier's invoice reads: Intel Dual Core @ 2.5GHz, 4GB DDRII Memory, ... 512MB Geforce NVidia graphics card.

Also, where do I read how to correctly partition the HDD - this time BEFORE I plunge in headlong - again!  I may need to install Linux Suze in one partition.  Ubuntu's Open Office document workspace (visible on the screen) has a considerably smaller area than Suze's - and I need all the workspace I can get for the design of educational worksheets for students.
...

Apologise for the needless confusion, I have just tested a default install and the default format is actually ext3 so all you needed to do is select the option "use entire disk"

There is some useful information on partitioning here if you need it:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

I would suggest waiting until you decide if you are going to install Suse before worrying about making a partition for it as it will do this automatically for you.

As QIII said you can use either version and if you install the Edubuntu packages through the package manager it will sort the rest out for you

---

### Post by acimna on 2009-07-30
> **tarps87 said:**
> Apologise for the needless confusion, I have just tested a default install and the default format is actually ext3 so all you needed to do is select the option "use entire disk"

There is some useful information on partitioning here if you need it:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

I would suggest waiting until you decide if you are going to install Suse before worrying about making a partition for it as it will do this automatically for you.

As QIII said you can use either version and if you install the Edubuntu packages through the package manager it will sort the rest out for you


[COLOR=Blue]Do you mean to say that Edubuntu will give me Suse's smaller toolbars and fonts i.e. larger visible workspace?

I did read the psychocats partitioning guidelines (thank goodness!) and also the Ubuntuguide, which is more comprehensive.  The /home (Ext3) idea makes a lot of sense, but do I need just one /home if Suse is the only way I can get a larger workspace and then file all docs in that one /home (also from Ubuntu/Edubuntu)?  Or should I go the Logic partition route and make one /home for Suse and one for Ubuntu?

It really will be helpful if I could get it all - Suse's looks and Ubuntu's body!
[/COLOR]

---

### Post by tarps87 on 2009-07-30
I was referring to sorting which version to install in terms of 32bit and 64bit.
I would advise separate /home partitions and you settings are save in you /home folder and this can cause issues between distributions.

"It really will be helpful if I could get it all - Suse's looks and Ubuntu's body!"
You can Suse used Gnome desktop manager and so does Ubuntu it's just a case of finding the right settings.
I have just done a bit of poking around and in open office under tools -> options -> openOffice.org -> view you will find a section called user interface. Try setting the scalling to 80% and the icon size to small.

If you want to change the appearance even more have a look at [http://www.gnome-look.org/](http://www.gnome-look.org/) but be warned it can be very addictive :)

---

