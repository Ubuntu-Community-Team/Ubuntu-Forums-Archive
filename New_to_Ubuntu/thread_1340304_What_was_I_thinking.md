---
title: "What was I thinking?"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by OldGoat58 on 2009-11-28
I am so tired of Windows updating every other week, or so it seemed, I was talking to friends and they suggested trying open source operating systems built on the Linux kernel.  I didn't understand what corn had to do with a computer but who was I to question people that work with computers for a living?  After asking around and reading a glut of information I made my choice, Ubuntu 9.10, Karmic Koala.

I followed the instructions on downloading a distribution for Ubuntu 9.10 for AMD64 64 bit, and actually made a live CD successfully.  I was so proud of myself!  (reminder, PRIDE goeth before a fall)  I brought the CD home and put it in my HP dv9810us Pavilion laptop.  I booted off the CD and played around enough to realize that all the nay sayers were wrong and that I could find drivers for my hardware.  So I clicked "INSTALL UBUNTU 9.10".  Hind sight being 20/20 I really should have made the choice to dual boot my hard drive.

Anyway, here I sit with Ubuntu.  Now honestly I have managed to get myself to a point where I can do most of the things I did on my Windows box on my Ubuntu box.  Always looking to improve my experience I decided to pick up some applications that I had used in Windows but gave up on due to registry errors, missing ActiveX controls, and poor performance.  

That is where my happy experience with Ubuntu sits.  I have downloaded some applications, or so I thought, but I just can't seem to figure out how to get them from the download folder into a functional state.  To say that I am frustrated is an understatement.  My biggest regret was not dual booting.  Since my laptop came from HP with Windows already installed I do not have have the installation discs to go back to Windows and I am stuck with a computer that will allow me to email people and play game on POGO.  

WHAT WAS I THINKING?  (BANGHEAD)

---

### Post by ranch hand on 2009-11-28
If you are trying to install apps for MS it will not work.

Some of them will run in wine, see your synaptic package manager for it (System>Administration>Synaptic Package Manager)

Running a search for equivillent programs to what you want would be a better idea.

---

### Post by japhyr on 2009-11-28
What applications are you trying to run, unsuccessfully?

---

### Post by OldGoat58 on 2009-11-28
> **ranch hand said:**
> If you are trying to install apps for MS it will not work.

Some of them will run in wine, see your synaptic package manager for it (System>Administration>Synaptic Package Manager)

Running a search for equivillent programs to what you want would be a better idea.


I know enough to know that MS applications will not work in Linux.  Everytime I open the Synaptic Package Manager it fads to black and freezes up.   I have tried to get Google Earth, Adobe Air, and a number of other things suggested on Ubuntu forums, and have succeeded in nothing more than making myself feel like a complete idiot.

I tried following instructions to get Pandora to work and everytime I try to enter the commands into the terminal I get advised that I do not have permission to create directories or that my password is incorrect.  I can't even download and open the Ubuntu Beginners Guide posted by Technoviking to try and figure out my problems.

At 51 I do believe I have bitten off more than I can chew.  I should have listened to the one techie friend at work that said, "Dude, Linux is over your head"!

---

### Post by candtalan on 2009-11-28
> **OldGoat58 said:**
>  I have downloaded some applications, or so I thought, but I just can't seem to figure out how to get them from the download folder into a functional state.  To say that I am frustrated is an understatement.  My biggest regret was not dual booting.  Since my laptop came from HP with Windows already installed I do not have have the installation discs to go back to Windows and I am stuck with a computer that will allow me to email people and play game on POGO

Welcome to Ubuntu!
Sorry to hear you have found a stage which frustrates. However, hopefully it will not last too long.

I am not sure which things you have downloaded, or how you downloaded them but the Ubuntu way is a good deal simpler than what you have been used to.

Most programs that you will need are held in special ubuntu libraries, called Repositories, and there are several types of these. There are some 20,000 such programs to choose from and the way to get them easily is to use (9.10) the software centre or system>administration>synaptic package manager.

Having said that, I now see (later message) you mention external programs  such as google earth. These are a special case,  but are not hard to deal with, with a little more information, which I am sure people here can help with.

---

### Post by japhyr on 2009-11-28
It seems to me that when we buy a computer with a pre-installed operating system like Windows or Mac, we are used to it working right away.  Then over time things slow down or stop working, and we consider replacing them.  We start with a well-functioning computer, and then performance degrades.

With ubuntu, it seems that we spend some time initially setting it up.  But once it's set up, we end up with a very stable computer.  Personally, I have found it more satisfying to spend some time setting up an Ubuntu system and knowing I will have a stable system.

I am pretty sure more knowledgeable people than me will say something about the trouble you are having with Synaptic.  I hope you stick it out a little bit, and you end up with a computer that does what you need it to do.

---

### Post by RedRat on 2009-11-28
OK, I hate to write this and some here will probably dump on me for saying this, but since you are new and that is a fresh install, you might want to consider going to a slightly older distro of Ubuntu, e.g., 9.04 or even 8.04 or 8.10. The reason you might be experiencing problems with 9.10 is that it was just released in October and many times there are still bugs in the release. Experienced users know how to get around them. 

Since you are a newbie, perhaps a more stable and mature version might be better to test the waters, so to speak. Also, you might want to consider Mint in place of the Ubuntu distros. Mint is based on Ubuntu but is geared to newbies and ex-Windows users. The current stable version of Mint is called Gloria and is based on Ubuntu 9.04. Further it comes with all the codecs you need to view video and music. 

However, before doing any of this, it would helpful to those here if you could give some information about your system, e.g., amount of RAM, hard drive size, CPU, age of the computer, etc. This information helps those here to make a guess at where you problem(s) lie.

BTW, I am nearly 70 and so age is not the problem.

---

### Post by nothingspecial on 2009-11-28
> **OldGoat58 said:**
> .  I should have listened to the one techie friend at work that said, "Dude, Linux is over your head"!

Until 3 years or so ago, I`d never even turned a computer on. The first one I did had Ubuntu on it. Hang in there. Try and not think from a windows perspective. Forget all about windows while you are trying to use linux.

Post exactly what you are trying to do. I`ve never tried Google earth or air but if you post exactly what directories you are trying to create and what permissions issues you are having you`ll get more help.

For example try launching synaptic from the terminal and post any errors

```
gksudo synaptic
```

---

### Post by OldGoat58 on 2009-11-28
> **candtalan said:**
> Welcome to Ubuntu!
Sorry to hear you have found a stage which frustrates. However, hopefully it will not last too long.

I am not sure which things you have downloaded, or how you downloaded them but the Ubuntu way is a good deal simpler than what you have been used to.

Most programs that you will need are held in special ubuntu libraries, called Repositories, and there are several types of these. There are some 20,000 such programs to choose from and the way to get them easily is to use (9.10) the software centre or system>administration>synaptic package manager.

Having said that, I now see (later message) you mention external programs  such as google earth. These are a special case,  but are not hard to deal with, with a little more information, which I am sure people here can help with.

The Synaptic Package Manager is one of the applications adding to my frustration.  I found the Ubuntu Software Center and used it to pick up missing elements like my HP printer drivers.  Trying to understand the "repositories" (which i thought were things you put up your woohoo), and add repositories is also frustrating.

My experience with "Out of the Box" computers is limited to my HP.  My first Windows machine in 1998 was something a friend "put together" and I learned everything I know about Windows on my own.  That being said, I am trying to learn everything I can about Ubuntu but it is not as intuitive and my resources are limited to the good graces of the people on these forums.

Between Ubuntu Help and hopefully someone on one of these forums I hope to figure out how to maximize my Ubuntu experience and then SHARE my experience in PLAIN LANGUAGE so that the next person doesn't have the same level of difficulty I am having.

---

### Post by Zzl1xndd on 2009-11-28
OldGoat58, 

I am sure I speak for everyone when I say we will do as much as we can to get you up and running. Please let us know what issues you are specifically having and we will attempt to correct them

That being said you have entered a totally different way of doing things and when you learned everything on one system a new one can seem daunting but give it some time and I think you will find Linux as easy if not more so then Windows.

---

### Post by scorp123 on 2009-11-28
> **OldGoat58 said:**
>  At 51 I do believe I have bitten off more than I can chew.   My wife's parents are beyond 70 ... and they are Linux users now. If they can do it ...

---

### Post by candtalan on 2009-11-28
> **OldGoat58 said:**
> At 51 I do believe I have bitten off more than I can chew.  I should have listened to the one techie friend at work that said, "Dude, Linux is over your head"!

Cheer up! I am a lot more than 10 years older than you and age is not a problem. You have wanted to use ubuntu, and have found your way to these forums, two really good moves. Most of my elderly friends have Ubuntu - they ask me to help them. They soon become independent. Three of them have even splashed out to purchase laptops with only Ubuntu on - no windows at all. An elderly relative is 89 and she does shopping at tesco supermarket using ubuntu. These people are users, not administrators, so they have it a bit easier that you are finding it just now. You need to be administrator.

I am glad you did not listen to your so called friend who dissed your potential skills. Good for you to use Ubuntu! I can assure you that Ubuntu will not be over your head, but please stay with these forums and you will soon find your feet.

Question: How are you posting here, are you using your own Ubuntu machine?

---

### Post by Don1500 on 2009-11-28
> **RedRat said:**
> 

BTW, I am nearly 70 and so age is not the problem.

I'm over 60 and started with just about 2 1/2 years ago. I still cruze the beginners forum because I still make the same mistakes. But I am using it and have safely upgraded from Fistey to Gusty to Hardy to Intrepid, to Jaunty and on to Karmic. Each one had it's own problems and each one was a challenge in it's own way. Eventually (not that long really) you will have a stable system, built the way you want it.

---

### Post by Desert Sailor on 2009-11-28
Dude, what were you thinking.  Let me tell you from my own experience, please don't give up!!  I am 62 yrs myself.  I have finally made the switch from the Redmond Virus to the open source Ubuntu.  I feel like Martin Luther King.  "Free at last, Free at last, Great God Almighty, I am free at last."  Having a computer has become head banging frustrating again, but once you solve a problem, figure it out, make it work, "sudo gedit" a file and change it the way you want it, you have this enormous sense of satisfaction knowing that YOU are back in charge.  

Use this resource, it is truly one of the best, read, study, learn, check out Ubuntu Documentation and the Linux Documentation project.  If you must go back to Windoze, get a copy of XP they are available now at very reasonable prices, and dual boot.  But please don't give up.  Linux isn't over the heads of us old dogs, it's just a new challenge and at my age, I thank God for a good mental challenge.

---

### Post by OldGoat58 on 2009-11-28
> **RedRat said:**
> OK, I hate to write this and some here will probably dump on me for saying this, but since you are new and that is a fresh install, you might want to consider going to a slightly older distro of Ubuntu, e.g., 9.04 or even 8.04 or 8.10. The reason you might be experiencing problems with 9.10 is that it was just released in October and many times there are still bugs in the release. Experienced users know how to get around them. 

Since you are a newbie, perhaps a more stable and mature version might be better to test the waters, so to speak. Also, you might want to consider Mint in place of the Ubuntu distros. Mint is based on Ubuntu but is geared to newbies and ex-Windows users. The current stable version of Mint is called Gloria and is based on Ubuntu 9.04. Further it comes with all the codecs you need to view video and music. 

However, before doing any of this, it would helpful to those here if you could give some information about your system, e.g., amount of RAM, hard drive size, CPU, age of the computer, etc. This information helps those here to make a guess at where you problem(s) lie.

BTW, I am nearly 70 and so age is not the problem.


[IMG]file:///tmp/moz-screenshot.png[/IMG]HP dv9810us, 160gb HDD, 3gb DDR2-SODIMM 200 pin, computer is 2 years old.  I have attached a screen shot of the operating system and processors

---

### Post by Bartender on 2009-11-28
HP has a recovery utility on their PC's.  They put the Windows OS, drivers, and assorted bits and pieces into the recovery partition.  It's up to the consumer to make those discs ASAP after purchase.

Since you apparently didn't do that, you should be able to contact HP and order a recovery disc for your exact model for a nominal fee.  The recovery discs are dime a dozen, the only thing that makes your copy of Windows unique is the shiny 25-character COA sticker on the bottom.  As long as you still have that COA, all is not lost.

Then you could reinstall Windows and dual-boot.

I'm borrowing some broadband at the library so here's the HP website for you..
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00810334&cc=us&lc=en&dlc=en&product=3689885](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00810334&cc=us&lc=en&dlc=en&product=3689885)

Don't get me wrong, I agree with previous posters that you should dig into Ubuntu.  I just don't want to have you think of how you ruined Windows every time you look at the laptop.  And there are some things that still can't be done in Linux.  I'm 52 by the way, a youngster compared to you old duffers, but I've been messing with Linux for about five years now.

---

### Post by OldGoat58 on 2009-11-28
> **candtalan said:**
> Cheer up! I am a lot more than 10 years older than you and age is not a problem. You have wanted to use ubuntu, and have found your way to these forums, two really good moves. Most of my elderly friends have Ubuntu - they ask me to help them. They soon become independent. Three of them have even splashed out to purchase laptops with only Ubuntu on - no windows at all. An elderly relative is 89 and she does shopping at tesco supermarket using ubuntu. These people are users, not administrators, so they have it a bit easier that you are finding it just now. You need to be administrator.

I am glad you did not listen to your so called friend who dissed your potential skills. Good for you to use Ubuntu! I can assure you that Ubuntu will not be over your head, but please stay with these forums and you will soon find your feet.

Question: How are you posting here, are you using your own Ubuntu machine?


I have but one computer to give for my country and that is my Ubuntu box.  I chose not to dual boot because I SOMETIMES learn better when I do not have a crutch to fall back on.

---

### Post by candtalan on 2009-11-28
> **OldGoat58 said:**
> The Synaptic Package Manager is one of the applications adding to my frustration.  I found the Ubuntu Software Center and used it to pick up missing elements like my HP printer drivers.  Trying to understand the "repositories" (which i thought were things you put up your woohoo), and add repositories is also frustrating

Ahh, yes be clear about the diffeerence between repositories and the other things.....
By the way, many people use Ubuntu for years without needing to add new repositories, so please be aware that you are jumping a bit high rather quickly - no problem with that, just take it step by step, people here will be available to help you.

---

### Post by ed-koala on 2009-11-28
Let's get back to your original issue OldGoat, which is Synaptic going black and freezing.  Is this still going on?  Fixing this issue will go a LONG way toward making your Ubuntu experience easier!!

Does anyone have any idea what might be going on here with his Synaptic?  I did a quick search but didn't see any fast answers, will keep looking.

Is there any way to run synaptic from terminal so you get some debugging info?

Hang in there OldGoat, we got yer back!

---

### Post by 23dornot23d on 2009-11-28
Might be as well opening >>> a terminal window ......

and seeing if apt works .....

enter a simple command like



sudo apt-get update


and then enter your password ...... when requested to do so .......


see if it updates ok .......... it basically will just pull in and list the repositories  and show that it is working ........ ok

it will show the internet connection is working  ...... if he can give a sreenshot.

if everybody agrees ......

By the way I am 51 too .....

should look something like this

[IMG]http://i45.tinypic.com/2cmvlvb.jpg[/IMG]

---

### Post by qwerty2009 on 2009-11-28
the first thing you should do once ubuntu is set up is 

install all updates - system>administrator>update manger
this installs bug fixes that might be causing synaptic to crash 

then install "ubuntu-restricted-extras" from ubuntu software centre
this installs codec's for you to play your media and also installs flash player 

most application s are in software centre, i suggest you install ubuntu tweak for extra applications this also makes life easier for new users

---

### Post by OldGoat58 on 2009-11-28
> **ed-koala said:**
> Let's get back to your original issue OldGoat, which is Synaptic going black and freezing.  Is this still going on?  Fixing this issue will go a LONG way toward making your Ubuntu experience easier!!

Does anyone have any idea what might be going on here with his Synaptic?  I did a quick search but didn't see any fast answers, will keep looking.

Is there any way to run synaptic from terminal so you get some debugging info?

Hang in there OldGoat, we got yer back!

Following the advice from nothingspecial I opened a terminal and typed 'gksudo synaptic' as instructed.  A dialog box opened asking for my password, I entered it, the Synaptic window opened, faded to black, and is still in that faded stage.  I just closed it and the terminal and attached the error messages.

FYI - I'm new to these forums as well but I'm trying to learn so please let me know if I'm doing something I shouldn't.

---

### Post by OldGoat58 on 2009-11-28
> **qwerty2009 said:**
> the first thing you should do once ubuntu is set up is 

install all updates - system>administrator>update manger
this installs bug fixes that might be causing synaptic to crash 

then install "ubuntu-restricted-extras" from ubuntu software centre
this installs codec's for you to play your media and also installs flash player 

most application s are in software centre, i suggest you install ubuntu tweak for extra applications this also makes life easier for new users

Been there, done that, have the layout.  Actually just installed all available updates 3 days ago.  Tried getting Ubuntu Tweak and that is what lead to all this dialog.

---

### Post by jrrader on 2009-11-28
Welcome, looks like you're stuck with us unless you feel like shelling out some cash for Win 7.  I'd suggest working out your problems with Linux - in 2 weeks you'll feel like a computer expert.  In two months you'll be annoying all your friends and family as you try to install Linux on their computers (don't do that).

I have to agree with RedRat.  Using 9.04 would get you up and running with fewer problems.  I'd also like to suggest using the 32 bit version rather than the 64 bit version.  Personally I use 64bit 9.10, but when I install on other people's computers I've been using the 32 bit 9.04 because it just requires less maintenance. You will probably never see the advantages of 64 bit, but you'll notice the drawbacks.

It sounds like you need to reinstall anyway, and this would be a good time to do it.  It's a good idea to have separate partitions for your /home and /usr folders so you never lose that data in a reinstall.  So next April when Lucid comes out you can do a clean install without losing your home folder (but format /usr in a clean install and reinstall the apps you use) and then just keep Lucid for the rest of that computer's lifespan.

---

### Post by halitech on 2009-11-28
try turning off the visual effects - System - Preferences - Visual effects and see if that helps. What kind of video card do you have?

---

### Post by OldGoat58 on 2009-11-28
> **jrrader said:**
> Welcome, looks like you're stuck with us unless you feel like shelling out some cash for Win 7.  I'd suggest working out your problems with Linux - in 2 weeks you'll feel like a computer expert.  In two months you'll be annoying all your friends and family as you try to install Linux on their computers (don't do that).

I have to agree with RedRat.  Using 9.04 would get you up and running with fewer problems.  I'd also like to suggest using the 32 bit version rather than the 64 bit version.  Personally I use 64bit 9.10, but when I install on other people's computers I've been using the 32 bit 9.04 because it just requires less maintenance. You will probably never see the advantages of 64 bit, but you'll notice the drawbacks.

It sounds like you need to reinstall anyway, and this would be a good time to do it.  It's a good idea to have separate partitions for your /home and /usr folders so you never lose that data in a reinstall.  So next April when Lucid comes out you can do a clean install without losing your home folder (but format /usr in a clean install and reinstall the apps you use) and then just keep Lucid for the rest of that computer's lifespan.

What the bloody hell are you talking about?  Reinstalling?  Lucid?  Repartitioning?  Why would I down grade from 64 bit format to 32 bit format?  That is opposite of what I read prior to installing and using Ubuntu.  

I'll keep (BANGHEAD) on my desk and hopefully get the hang of this.  If not, then I might consider going to an older version of Ubuntu, or a different distribution, or.........

---

### Post by 23dornot23d on 2009-11-28
Did you try this ........ just make sure apt works ..... Synaptic relies on it to work as
far as I know ...... once you know its working ok we can go from there .....

[IMG]http://i45.tinypic.com/2cmvlvb.jpg[/IMG]

---

### Post by boballen55 on 2009-11-28
> **RedRat said:**
> Also, you might want to consider Mint in place of the Ubuntu distros.

I second that thought.

---

### Post by 23dornot23d on 2009-11-28
Whats the harm in trying to get him up and running ..... if it fails after an hour of trying
then by all means re-install ..... 

But if nothing else he will learn something ..... about the system ..... before giving up

without trying ........

---

### Post by ed-koala on 2009-11-28
Ubuntu tweaks huh?  What did you change, if anything?

First, change it back.
Second, open a terminal and type *sudo apt-get remove ubuntu-tweak*

Now try Synaptic again.

I'd only recommend Ubuntu-tweak for experienced users. I've never bothered with it and I've used Ubuntu for several years.

---

### Post by jwbrase on 2009-11-28
> **OldGoat58 said:**
> Following the advice from nothingspecial I opened a terminal and typed 'gksudo synaptic' as instructed.  A dialog box opened asking for my password, I entered it, the Synaptic window opened, faded to black, and is still in that faded stage.  I just closed it and the terminal and attached the error messages.

FYI - I'm new to these forums as well but I'm trying to learn so please let me know if I'm doing something I shouldn't.

He meant to post any errors that appear in the terminal window when Synaptic freezes (depending on what exactly is happening, you might or might not see any).

---

### Post by jrrader on 2009-11-28
Generally people install the first time using the option to just install over the entire drive.  This makes things difficult in the future.  

64 is a larger number, but that doesn't mean it's going to work better.  Better performance is debatable.  Software compatibility is improving for 64, but is not equal.

Lucid is the Ubuntu version after Karmic.  It is a long term support release and will be stable for a longer period of time than the 6 month releases (like Jaunty and Karmic).

---

### Post by halitech on 2009-11-28
> **jrrader said:**
> 
Lucid is the Ubuntu version after Karmic.  It is a long term support release and will be stable for a longer period of time than the 6 month releases (like Jaunty and Karmic).

actually the normal releases have 18months, not 6 months so you can continue to use a Non LTS release and get security and other updates for 18 months. LTS is supported for 3 years on the desktop and 5 on the server.

Stability depends on the hardware and how much the person running it likes to fiddle with things ;)

---

### Post by OldGoat58 on 2009-11-28
> **ed-koala said:**
> Ubuntu tweaks huh?  What did you change, if anything?

First, change it back.
Second, open a terminal and type *sudo apt-get remove ubuntu-tweak*

Now try Synaptic again.

I'd only recommend Ubuntu-tweak for experienced users. I've never bothered with it and I've used Ubuntu for several years.


First off I didn't change anything.  Second of all Synaptic hasn't functioned since the install.  I just found the following bits of information.  Can anyone tell me why I am not the "owner" of my file system?

---

### Post by OldGoat58 on 2009-11-28
> **jrrader said:**
> Generally people install the first time using the option to just install over the entire drive.  This makes things difficult in the future.  

64 is a larger number, but that doesn't mean it's going to work better.  Better performance is debatable.  Software compatibility is improving for 64, but is not equal.

Lucid is the Ubuntu version after Karmic.  It is a long term support release and will be stable for a longer period of time than the 6 month releases (like Jaunty and Karmic).


Lucid is the Ubuntu version of Karmic?  I thought Karmic Koala was just a release acronym for Ubuntu.  The only software I am trying to run for the immediate future is Ubuntu.

---

### Post by OldGoat58 on 2009-11-28
> **23dornot23d said:**
> Might be as well opening >>> a terminal window ......

and seeing if apt works .....

enter a simple command like



sudo apt-get update


and then enter your password ...... when requested to do so .......


see if it updates ok .......... it basically will just pull in and list the repositories  and show 


that it is working ........ ok

it will show the internet connection is working  ...... if he can give a sreenshot.

if everybody agrees ......

By the way I am 51 too .....

should look something like this

[IMG]http://i45.tinypic.com/2cmvlvb.jpg[/IMG]


OK, here is what I got when I followed the instructions for sudo apt-get update.  It is a long list.

---

### Post by ed-koala on 2009-11-28
Root is the owner of /, that's normal. / is your system files and you don't want just anything changing those, so it belongs to root and requires admin privlidges to make changes.

Still, did you manage to install ubuntu tweak?  If so, try that apt-get remove command I listed and see what happens.

Very strange Synaptic isn't working but everything else is.  Has *anything* else shown the same behavior?

---

### Post by OldGoat58 on 2009-11-28
> **ed-koala said:**
> Root is the owner of /, that's normal. / is your system files and you don't want just anything changing those, so it belongs to root and requires admin privlidges to make changes.

Still, did you manage to install ubuntu tweak?  If so, try that apt-get remove command I listed and see what happens.

Very strange Synaptic isn't working but everything else is.  Has *anything* else shown the same behavior?

I've had the terminal fade to black, Synaptic, Ubuntu Software Center, and something else.  I never got ubuntu tweak to install because the directions said to open an application manager, Synaptic, and it faded to black.  

Thanks everyone, I think I'll mark the thread as "Solved" so that everyone can go back to doing what they were doing before I interrupted.  THANK YOU ALL SO MUCH.
Mike

---

### Post by 23dornot23d on 2009-11-28
Just try .....


sudo apt-get install wine

it may get your windows app's working ..... its the old way of installing software

I do nearly all my installs this way ,,,,, and yours is working fine ...

( you do not need synaptic to load up your software .... but it is a nice graphical front end )


 before you go please ....

---

### Post by candtalan on 2009-11-28
> **halitech said:**
> try turning off the visual effects - System - Preferences - Visual effects and see if that helps. What kind of video card do you have?

Agreed, there seems to be transparancy being active and this is - or could be - a complication here.

the fancy graphics are great, if they help you. Canbe a wierd problem though.
Turn the fancy graphics off fo rthe time being.


Also - note that the screen darkens when something is about to be active, 
and also - the screen can darken for a screen saver activity after a set period. Do you have a period set for screensaver I wonder?

---

### Post by ed-koala on 2009-11-28
Sounds to me like something isn't right with your initial installation.  Verify your Live CD is good (or, download and burn **at slow speed** a new install CD, and verify it), and if you don't mind going to the trouble, do a clean install.

---

### Post by jrrader on 2009-11-28
> **halitech said:**
> actually the normal releases have 18months, not 6 months

Just meant that they come out every 6 months.

OldGoat - sorry for the confusion.  Lucid is the next release.  They come out in alphabetical order.  jaunty, karmic, lucid.

23dornot23d - Wine is not an old way of installing programs, it's basically a Windows emulator.  For most of the things he is looking to do there are native Linux applications.  Native will always work better.

> **ed-koala said:**
> Sounds to me like something isn't right with your initial installation.That's where I was coming from.

---

### Post by 23dornot23d on 2009-11-28
> **jrrader said:**
> Just meant that they come out every 6 months.

OldGoat - sorry for the confusion.  Lucid is the next release.  They come out in alphabetical order.  jaunty, karmic, lucid.

23dornot23d - Wine is not an old way of installing programs, it's basically a Windows emulator.  For most of the things he is looking to do there are native Linux applications.  Native will always work better.


apt-get install ...... is the old way rather than using synaptic ////

he wanted to run programs using wine ...... I was making sure it was installed properly ...

{Quote}
That is where my happy experience with Ubuntu sits. I have downloaded some applications, or so I thought, but I just can't seem to figure out how to get them from the download folder into a functional state. To say that I am frustrated is an understatement. My biggest regret was not dual booting. Since my laptop came from HP with Windows already installed I do not have have the installation discs to go back to Windows and I am stuck with a computer that will allow me to email people and play game on POGO.
{Quote}

he could have installed any application he wanted using ....... apt-get install .........

too late now he has gone ....


The problem with the graphics going black was probably compiz and it just needed turning off ......
but if everything was going black as he suggested .... 
even going to turn it off could have resulted in it going black on him.

The best way was to solve this from a terminal window .... which he could access with no problems


Here is a link to turn Compiz off from the terminal if he comes back ............

same problems were encountered ....... his system is probably fine ........

[http://ubuntuforums.org/showthread.php?t=980835](http://ubuntuforums.org/showthread.php?t=980835)   >>> This seems a complicated way though

Try this one ....... ( or you could even load up another Desktop from apt-get to do it ...... )

[http://ubuntuforums.org/showthread.php?t=662926](http://ubuntuforums.org/showthread.php?t=662926)

Lots of ways ........ to get it running ..... 

Never give up ...... there is a solution ..... somewhere ......

---

### Post by candtalan on 2009-11-28
> **ed-koala said:**
> Sounds to me like something isn't right with your initial installation.  Verify your Live CD is good (or, download and burn **at slow speed** a new install CD, and verify it), and if you don't mind going to the trouble, do a clean install.
The live CD can be checked for quality from its initial live CD boot menu 'check CD for errors'

---

### Post by OldGoat58 on 2009-11-28
Thank you all again.  I verified the CD was not corrupted prior to installing Ubuntu.  I turned off the graphic effects that everyone was talking about.  I had it set to normal but just changed them to off.  (i don't do anything from the desktop in the first place)  

Please DO NOT CONFUSE MY NEXT STATEMENT as being unappreciative, but if I wanted a sudo Windows environment I would have stayed with the Windows OS that I had.  I was one of the lame ducks that actually learned how to tweak Vista and got to enjoy it.  I was tired however of the compatibility problems with peripherals and the Windows environment.

Hopefully I will figure out why the Synaptic application fades and stalls, and why when I right click my file system and click properties it says I am not the owner so I can not make changes.  Hopefully after that when I try to execute the following from the terminal I don't get "Permission Denied".

chmod +x AdobeAIRInstaller.bin

sudo ./AdobeAIRInstaller.bin

or even

mkdir -p ~/.mozilla/plugins

cp ~/libflashplayer.so ~/.mozilla/plugins

---

### Post by nothingspecial on 2009-11-28
> **OldGoat58 said:**
> Thank you all again.  I verified the CD was not corrupted prior to installing Ubuntu.  I turned off the graphic effects that everyone was talking about.  I had it set to normal but just changed them to off.  (i don't do anything from the desktop in the first place)  

Please DO NOT CONFUSE MY NEXT STATEMENT as being unappreciative, but if I wanted a sudo Windows environment I would have stayed with the Windows OS that I had.  I was one of the lame ducks that actually learned how to tweak Vista and got to enjoy it.  I was tired however of the compatibility problems with peripherals and the Windows environment.

Hopefully I will figure out why the Synaptic application fades and stalls, and why when I right click my file system and click properties it says I am not the owner so I can not make changes.  Hopefully after that when I try to execute the following from the terminal I don't get "Permission Denied".

chmod +x AdobeAIRInstaller.bin

sudo ./AdobeAIRInstaller.bin

or even

mkdir -p ~/.mozilla/plugins

cp ~/libflashplayer.so ~/.mozilla/plugins

Where in your filesystem is AdobeAIRInstaller.bin

Which instructions are you following?

---

### Post by heyho on 2009-11-28
Hi.

I think a lot is being covered/discussed at the same time, without much progress being made.

As for your file system not being your own, all system files are owned by root, hence the reason why it is difficult for a normal system user to screw up a linux install, and easy to sabotage a windows install.  Pre-fixing terminal commands with "sudo" entitles you to do as you please with the entire system.

Pick the issue causing you the most problems, and make a fresh thread.  Post any terminal output when requested, it is the most important tool for diagnosing problems, far better that screenshots.

---

### Post by 23dornot23d on 2009-11-28
it should be 

sudo chmod u+x (filename)

for a executable filetype to work

---

### Post by OldGoat58 on 2009-11-28
> **heyho said:**
> Hi.

I think a lot is being covered/discussed at the same time, without much progress being made.

As for your file system not being your own, all system files are owned by root, hence the reason why it is difficult for a normal system user to screw up a linux install, and easy to sabotage a windows install.  Pre-fixing terminal commands with "sudo" entitles you to do as you please with the entire system.

Pick the issue causing you the most problems, and make a fresh thread.  Post any terminal output when requested, it is the most important tool for diagnosing problems, far better that screenshots.

MESSAGE RECEIVED LOUD AND CLEAR.  Thank you so very much!

---

### Post by Old *ix Geek on 2009-11-28
I see the thread is now marked solved, but OldGoat I just had to tell you I really like your wry sense of humor. :D  That kernel/corn thing was very funny, as was the repository/woohoo remark.

One other thing: I have an HP dv6000 laptop and EVERYTHING works perfectly on it for me.  So please be patient, ask all the questions you need to ask, and then sit back and be glad you're done with Micro$oft. :)

---

### Post by OldGoat58 on 2009-11-28
> **Old *ix Geek said:**
> I see the thread is now marked solved, but OldGoat I just had to tell you I really like your wry sense of humor. :D  That kernel/corn thing was very funny, as was the repository/woohoo remark.

One other thing: I have an HP dv6000 laptop and EVERYTHING works perfectly on it for me.  So please be patient, ask all the questions you need to ask, and then sit back and be glad you're done with Micro$oft. :)

I'm reasonably sure that ALL the difficulties, which really are few, are mostly of my own making!  I am not technology savvy and have never represented myself as being such.  I appreciate your comments but I believe that the sentiment that I read into heyho's comment was correct, new comers not welcome.

---

### Post by 23dornot23d on 2009-11-28
I believe he is trying to say ...... too many cooks ruin the broth ......

there are too many of us trying to help you out here .....

You need a one on one to get the problems solved ......

and by starting a new thread just asking how to install one package 

might be a start point .... but there is plenty of help here and newcomers are always

welcome .........

I started on Linux many years ago with something called Mandrake 7.1 and it came on 3.5" floppy disks ....

I would never go back to Windows .... 

As somebody else said ..... this is the hard part once you have it running properly then its a breeze ......

and so much quicker than Windows .... as well as being more secure .......

( The reason they have expressed that you re-install with a earlier package .... 
is we have seen a lot of new problems with Karmic .... the other Distros may be less troublesome )

But there is no reason why we cannot get the one you have ...... working properly ........

It just takes time ........ and what they might be saying is it could be quicker to do a re-install

of a earlier system like UBUNTU 9.04 ....... which is what the majority run ..... before the latest upgrade .....

and the install will take around 30 minutes to do ......... where solving the problem could be a lot longer

---

### Post by nothingspecial on 2009-11-28
> **OldGoat58 said:**
>  I believe that the sentiment that I read into heyho's comment was correct, new comers not welcome.

With respect again.

In that you are totally wrong.

The FACT that newcomers are welcome is what makes Ubuntu by far the most popular linux distribution.

The answers here ought to show you that.

What I, and others are trying to say is.....

What EXACTLY is your problem?????

Believe me, I want to help you fix it.

regards

---

### Post by Old *ix Geek on 2009-11-28
> **OldGoat58 said:**
> I'm reasonably sure that ALL the difficulties, which really are few, are mostly of my own making!  I am not technology savvy and have never represented myself as being such.That's okay. No one ever said that TODAY'S Linux user has to be a computer geek.  It's a shame you've had any problems at all--and a lot of windoze converts have nothing but smooth sailing when they make the switch--but these things happen.  I can pretty much guarantee you that all of your issues can be solved, and they really shouldn't be all that involved or difficult.  The whole thing might be resolved by just starting over.  It's possible that somehow, somewhere, something went wrong during your download or installation, and although I normally use my "this isn't windows! reinstalling/rebooting isn't the answer!" line, there ARE times when it may help. If I were you, really, I'd start there.  Do a fresh download--only this time, maybe you should choose Kubuntu (my favorite!)--then format the drive and start over.
> I appreciate your comments but I believe that the sentiment that I read into heyho's comment was correct, new comers not welcome.No, that's definitely not true at all.

Something you have to understand is that everyone here [the reasonable folks, anyway] understands that NO ONE starts out knowing everything.  Not about Ubuntu. Not about Linux. Not about computers. Not about ANYTHING.  We're all beginners/newbies at some point.  For some of us, when it comes to *nix, that was a long time ago! :D

You're very welcome here.  Please don't let anyone's attitude or comments discourage you.  This forum exists for peer-to-peer help with Ubuntu, so dive right in.

---

