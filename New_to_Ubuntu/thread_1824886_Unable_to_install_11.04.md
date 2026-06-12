---
title: "Unable to install 11.04"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by dodgy geezer on 2011-08-14
Hi,

New user - just trying this O/S.

I downloaded and burnt a copy of Desktop 11.04, and went to try it out in a spare machine I have - a Compaq Deskpro EN SFF - (P3, around 350Mb ram, 4.5Gb drive)

I assumed that you just stick the CD in and boot from it. This I did. It tool a fair time to boot, and then put up a complete desktop. I was expecting a simple menu. 

On the desktop were two icons - a folder marked 'Examples', and an icon marked 'Install Ubuntu 11.04'. I double-clicked the Examples folder, and got a window called 'example-content'. Then I double-clicked the Install icon, and nothing happened. 

I re-ran the boot sequence several times, and the same thing happens. Is there some special way to click this icon to get it to install?

---

### Post by akand074 on 2011-08-14
Did you burn it at a slow speed? Your specs are a little weak for standard Ubuntu 11.04. I'm sure you can get it running, but I think you'd have a better experience with either XUbuntu, or LUbuntu which are less resource heavy.

---

### Post by Enigmapond on 2011-08-14
I would try it again and this time, when the option comes up to "Try" or "Install", just choose install.

---

### Post by dodgy geezer on 2011-08-14
I used my standard speed - never had any problems before. I will try burning at half-speed and see if that helps...

---

### Post by dodgy geezer on 2011-08-14
> **Enigmapond said:**
> I would try it again and this time, when the option comes up to "Try" or "Install", just choose install.

I get NO option to 'try or install'

The install disk boots straight into a desktop screen. Should it boot into a menu first?

---

### Post by Rex Bouwense on 2011-08-14
Welcome to forums Dodgy.  You may be a bit lite on the RAM for a full install of 11.04 and your hard drive may be a bit small but it should install, slowly.  First, did everything work when you booted from the CD, i.e.: could you open and run your applications from the launcher on the left side of your screen, could you launch the browser, etc.

---

### Post by Rex Bouwense on 2011-08-14
Slow typing gets me beat out.  It sounds like your desk top is not fully loading.  Since you only have 350 RAM (?), it is taking a real long time.  Perhaps you should try a lighter version.

---

### Post by dodgy geezer on 2011-08-14
> **Rex Bouwense said:**
> Welcome to forums Dodgy.  You may be a bit lite on the RAM for a full install of 11.04 and your hard drive may be a bit small but it should install, slowly.  First, did everything work when you booted from the CD, i.e.: could you open and run your applications from the launcher on the left side of your screen, could you launch the browser, etc.


Thanks for the response - didn't try the browser, but I could read drop-down menus and make the 'example' folder open, so I guessed that the system was fully functional. Apart from the Install icon... :(

I am now burning a half-speed CD.

---

### Post by Wim Sturkenboom on 2011-08-14
> **Enigmapond said:**
> I would try it again and this time, when the option comes up to "Try" or "Install", just choose install.One must first figure out how to get to the menu that displays that. It's hidden.

Press <shift> or <esc> while booting when there are some small symbols at the bottom of the screen. With some goodwill, you can see a keyboard and a human in there.

---

### Post by dodgy geezer on 2011-08-14
> **Wim Sturkenboom said:**
> One must first figure out how to get to the menu that displays that. It's hidden.

Press <shift> or <esc> while booting when there are some small symbols at the bottom of the screen. With some goodwill, you can see a keyboard and a human in there.


Thanks! That has moved me further ahead!

I wonder why people thought it was a good idea to hide the Install option. It does make it hard for people to try it out....:confused:

---

### Post by Rex Bouwense on 2011-08-14
> **dodgy geezer said:**
> Thanks for the response - didn't try the browser, but I could read drop-down menus and make the 'example' folder open, so I guessed that the system was fully functional. Apart from the Install icon... :(

I am now burning a half-speed CD.

If you didn't see the launcher on the left side of your screen, then everything was not loaded.  There will be what looks like a panel on the left and above it will be the Ubuntu logo which you probably clicked and saw the drop down menu.  When I first tried Natty, I tried to get started before everything had loaded.  That may have been your problem.  It doesn't do any harm to re-burn a CD because those should be burned at the lowest possible speed.

---

### Post by apollothethird on 2011-08-14
> **dodgy geezer said:**
> Thanks! That has moved me further ahead!

I wonder why people thought it was a good idea to hide the Install option. It does make it hard for people to try it out....:confused:

Dodgy.  Good question.  The answer is simple.  It would be harder for most people if the system paused on every option for everything that could possible happen but was unlikely.

It's not very likely that people will have a machine that didn't have the resources to make it to the default menu.  The text screen options you paused to use will confuse many people.

There are other screens you can manipulate the startup to do also.  But are rarely used unless there are specific reasons.

I paused for a long time when I read your initial message.  It's been a long time since I've seen a description of total ram measure in megs instead of gigs.

I hope how quickly you were able to get a resolution shows you how well the OS is supported.

Welcome to Ubuntu Forums!

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by dodgy geezer on 2011-08-14
Hmm...

Well, it now seems to be installing - though I had expecyed it to ask to re-partition the disk, and it just showed a screen 'wait' icon. Then it came up with the message below:

busybox v.17.1 
enter help for a list of commands

can not mount /dev/loop0 (/cdrom/casoper/filesystem.squashfs) on filesystem.squashfs

(initramfs)


Does this mean I haven't got enough space for an install?

---

### Post by Wim Sturkenboom on 2011-08-14
> **dodgy geezer said:**
> Thanks! That has moved me further ahead!

I wonder why people thought it was a good idea to hide the Install option. It does make it hard for people to try it out....:confused:I forgot to mention that there is also an option to test the disk for defects.

And you don't want to know my opinion about hiding the menu behind some icons (or whatever); I recently gave it in another thread ;)

---

### Post by dodgy geezer on 2011-08-14
> **apollothethird said:**
> 

...I paused for a long time when I read your initial message.  It's been a long time since I've seen a description of total ram measure in megs instead of gigs...

L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")


Thanks for the welcome!

The reason I am investigating Ubuntu is that, until recently, I used Smoothwall as my firewall, and found it to be much more reliable than my windows systems.

The Smoothwall was supporting a network of about 12 systems (max concurrency about 4), and doing it on a 386/486 machine (I wasn't too sure) with 32Mb of ram. 

I'm now looking to change my web server, and I thought Linux/Apache was the way to go. I tried to build a server, and found the command-line to be too much for me, so I'm looking at using a GUI system....

---

### Post by dodgy geezer on 2011-08-14
> **dodgy geezer said:**
> Hmm...

Well, it now seems to be installing - though I had expected it to ask to re-partition the disk, and it just showed a screen 'wait' icon. Then it came up with the message below:

busybox v.17.1 
enter help for a list of commands

can not mount /dev/loop0 (/cdrom/casoper/filesystem.squashfs) on filesystem.squashfs

(initramfs)


Does this mean I haven't got enough space for an install?


Alas, this message seems to be a regular occurrence. I have tried to install 4 times now, and got the same message each time. Looks like this system just cannot run Ubuntu 11.04 desktop. 

Bit odd, though, because it ran the server edition OK....

---

### Post by dodgy geezer on 2011-08-14
Having given up on 11.04, I am now trying 10.04.

Using the little trick of hitting shift when the man appears at the bottom of the screen, I have got it to present a start menu, and asked it to 'Install'. There was then a pause while the CD was being read...

I think it must have just loaded to memory, because it did not asked me to reformat a disk or anything. It then came up with a reddish screen, with a single 'Log in' window.

Of course, I have not entered a user-id or password yet. I have tried a few possible values, and each time it just rejects me. There appears to be no way to get past this screen. Are there any other little tips I should know?

---

### Post by apollothethird on 2011-08-14
> **dodgy geezer said:**
> Having given up on 11.04, I am now trying 10.04.

Using the little trick of hitting shift when the man appears at the bottom of the screen, I have got it to present a start menu, and asked it to 'Install'. There was then a pause while the CD was being read...

I think it must have just loaded to memory, because it did not asked me to reformat a disk or anything. It then came up with a reddish screen, with a single 'Log in' window.

Of course, I have not entered a user-id or password yet. I have tried a few possible values, and each time it just rejects me. There appears to be no way to get past this screen. Are there any other little tips I should know?

You're problem having these problems because the startup is running out of memory before properly loaded.  Your best bet would be to either add ram or change the Ubuntu flavor as suggested above.  Trying to find an older version might have to take you too far back... I'm sure further than a year or two.  If you go back far enough you might find a host of other issues which have since been resolved.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Whyzer on 2011-08-14
Ubuntu works well on older systems, but a P3 is really going to push it. It may work, but your Ubuntu experience probably won't be the best. I have it running on 1.6 Ghz P4 systems all day long (like all computers more RAM is better). A P3 machine is more likely to work better on a Slackware version of Linux. 
Personally i'd scrap the box and find something a few years newer and stick with Ubuntu, I've been a user now for 7 years and have converted all my machines to either 100% Ubuntu or a couple of them are dual boot (Windows for Itunes and some Tax software I need).
Hopefully  you are not far from joining the Ubuntu experience.

---

### Post by dodgy geezer on 2011-08-15
> **apollothethird said:**
> You're problem having these problems because the startup is running out of memory before properly loaded. Your best bet would be to either add ram or change the Ubuntu flavor as suggested above.-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")
 
That rather surprises me - I would have thought that a check would be made and the load would either adapt itself to the level of memory available or refuse to run with a meaningful error message.
 
I only wanted to load the desktop because I had problems reading a CD when in command line mode. What I really want to use the Compaq for is a web server, running Apache. I built this first (11.04 server version), and found that it worked fine, but that I could not find out how to read a CD and hence could not load all my web pages. 
 
I could FTP into it, but I needed to shift 1.5 Gb, and the transfer rate was way too slow. So I thought that if I put up a simple desktop I would find file transfer and config file manipulation much easier. 
 
If I can't fit a desktop onto this machine, I am back to trying to find out how to talk to a CD-Rom over the command line... :(

---

### Post by Wim Sturkenboom on 2011-08-15
System requiremenys for 10.04 (from wikipedia)

[http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#System_requirements](http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#System_requirements)

If you have integrated graphics, it's not going to do it.

---

### Post by apollothethird on 2011-08-15
> **dodgy geezer said:**
> That rather surprises me - I would have thought that a check would be made and the load would either adapt itself to the level of memory available or refuse to run with a meaningful error message.
 
I only wanted to load the desktop because I had problems reading a CD when in command line mode. What I really want to use the Compaq for is a web server, running Apache. I built this first (11.04 server version), and found that it worked fine, but that I could not find out how to read a CD and hence could not load all my web pages. 
 
I could FTP into it, but I needed to shift 1.5 Gb, and the transfer rate was way too slow. So I thought that if I put up a simple desktop I would find file transfer and config file manipulation much easier. 
 
If I can't fit a desktop onto this machine, I am back to trying to find out how to talk to a CD-Rom over the command line... :(

Your computer is probably over 20 years old.  Windows is very bloated because it remains compatible with computers that was built in the 70's.  I believe that's a good thing for it.  But it's also a flaw.  The Amiga, the Pet computer, that Atari and many of the other computers that changed with every edition and didn't build in downward compatible died.  You can probably still run some of the first applications that were made for Microsoft on a Windows computer.

All that isn't necessarily built into some things.  I understand the small CD that will install an OS rather than a bloated Windows DVD might not design all the logic you think should be to test if a computer is 20 years old.  I think it's enough that at least to allow the user to have the functionality of the cntrl or shift key.

To me hardware is inexpensive enough that I don't mind upgrading every 10 years.  At 60 years old, 40 more upgrades won't kill me.  I just hope the hardware developers continue with at least a fraction of the program every decade they have done in the past and the software developers push hardware to the limits.

I can see the logic.  There are utilities import from the older technology.

Personally I'm tired of the bloated logic of Windows.  I hope the Open Foundation will catch on and the hardware manufacturer will start to build in logical standards to make it easier for development with less bloat-ness.

Windows downward compatibility won out over a lot of the computers in the past, but that was with a price that Windows is paying for now... bloatiness.  Maybe Linux and the Open Foundation will learn from that with a careful balance.  In this case, there's a interrupt key and the option for the user to input his personal commanlines to adapt to the unexpected foreign or obsolete technology.

Again, hopefully the hardware developers and software developers can start to work at a happy medium.  The hardware developers don't have to be so restricted to what the software developers do, but can work with them for efficiency, compatibility, and respectful standards, and vice-versa.

If the people can understand this well enough they will help to guide this development by purchasing hardware from manufacturers that support the concept.  Companies like Lexmark will either jump onboard or drop out of sight.  Of course they have a hard time giving OS (Linux) support for their printers, many of their printers can't even survive a number of Windows version changes.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by dodgy geezer on 2011-08-15
> **Wim Sturkenboom said:**
> System requiremenys for 10.04 (from wikipedia)

[http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#System_requirements](http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#System_requirements)

If you have integrated graphics, it's not going to do it.

Thank you. Very good point. I have. That rules out the desktop, then. 

But the server on its own worked ok before. So long as I can work out how to read files from a CD into a directory, I should be able to get a web server up...

---

### Post by dodgy geezer on 2011-08-15
> **dodgy geezer said:**
> ... So long as I can work out how to read files from a CD into a directory, I should be able to get a web server up...

OK. I have tried several ways to read a cd. 

And I keep getting the error 'special device /dev/hdc does not exist'.

Does anyone know if the CD is called something different in Ubuntu?

---

### Post by snip3r8 on 2011-08-15
> **dodgy geezer said:**
> Thanks! That has moved me further ahead!

I wonder why people thought it was a good idea to hide the Install option. It does make it hard for people to try it out....:confused:

Its hidden because you are actually supposed to be prompted with a window with options,if this fails(which it did for you) you at least still have something to fall back on.

---

### Post by mastablasta on 2011-08-15
> **dodgy geezer said:**
> Thank you. Very good point. I have. That rules out the desktop, then. 

But the server on its own worked ok before. So long as I can work out how to read files from a CD into a directory, I should be able to get a web server up...

not necesasarily but you should use a lighter desktop environment such as LXDE or Openbox.

for example to get lxde all you need to do is install lubuntu-desktop package or you can also install fresh Lubuntu.


also i am going to guess here that the issue is graphics card driver or poor graphics card. also processor is weak.

you are also low on disk space so this might be causing additional slow down.

---

### Post by greenelf on 2011-08-15
> **dodgy geezer said:**
> Thanks! That has moved me further ahead!

I wonder why people thought it was a good idea to hide the Install option. It does make it hard for people to try it out....:confused:

[IMG]http://www.muktware.com/sites/default/files/images/manual/ubuntu-11-04/Install-01_Try_Install.png[/IMG]

It usually goes to a screen like this :P

---

### Post by dodgy geezer on 2011-08-16
> **greenelf said:**
> [IMG]http://www.muktware.com/sites/default/files/images/manual/ubuntu-11-04/Install-01_Try_Install.png[/IMG]

It usually goes to a screen like this :P

Mine didn't!

I think that if you have below min spec for the desktop it defaults to an earlier screen with hidden install, and if you load a server version it always goes for 'hidden install'.

Now I'm trying to get the server version to read a CD from the command line. It doesn't seem to wan to at all...

---

