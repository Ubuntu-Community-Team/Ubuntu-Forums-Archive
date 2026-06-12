---
title: "CCTV system?"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by celticbhoy on 2010-06-21
I run a pub, and have a CCTV system that runs to a PC. The hard disk has gone, and I was wondering if there was an open source solution for the PC software that I can put into the unit? I use Ubuntu almost exclusively, and would prefer if it would run on an Ubuntu system.

Does anyone have experience of, or know of anything that will fit the bill?

---

### Post by phr0ze on 2010-06-21
First link here: [http://www.google.com/search?q=open+source+cctv&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=open+source+cctv&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

Try it out. Seems to be a good system I'm going to try too.

---

### Post by ronnielsen1 on 2010-06-21
This was copied from synaptic 

> ZoneMinder is intended for use in single or multi-camera video security
applications, including commercial or home CCTV, theft prevention and child
or family member or home monitoring and other care scenarios. It
supports capture, analysis, recording, and monitoring of video data coming
from one or more video or network cameras attached to a Linux system.
ZoneMinder also support web and semi-automatic control of Pan/Tilt/Zoom
cameras using a variety of protocols. It is suitable for use as a home
video security system and for commercial or professional video security
and surveillance. It can also be integrated into a home automation system
via X.10 or other protocols.

Canonical does not provide updates for zoneminder. Some updates may be provided by the Ubuntu community.[http://www.zoneminder.com/](http://www.zoneminder.com/)
[IMG]http://www.zoneminder.com/typo3temp/f73e64629b.jpg[/IMG]

---

### Post by phr0ze on 2010-06-21
> **ronnielsen1 said:**
> This was copied from synaptic 

[http://www.zoneminder.com/](http://www.zoneminder.com/)
[IMG]http://www.zoneminder.com/typo3temp/f73e64629b.jpg[/IMG]

Well, I was trying to teach a man to fish...

---

### Post by Peterfc on 2010-06-21
Hi Guys

I have just downloaded Zoneminder but it's a Tar.gz file. I have moved it into my home directory. 

I have tried a search for information on install tar.gz but don't seem to find out how to install. Could anybody explain in simple terms.

I have found that Zoneminder is in Synaptic manager. I have installed Zoneminder using Synaptic manager. I can find it is installed when looking in Ubuntu Software Centre. It says it is installed software

New question how do i get it to run

Thanks

---

### Post by ronnielsen1 on 2010-06-21
> I have just downloaded Zoneminder but it's a Tar.gz file. I have moved  it into my home directory. 

I have tried a search for information on install tar.gz but don't seem  to find out how to install. Could anybody explain in simple terms.

It should be available in synaptic. Much easier. System > Agministration > Synaptic Package Manager or open a terminal and type[COLOR=Blue] sudo apt-get install zoneminder[/COLOR]

> Well, I was trying to teach a man to fish... 	
:lolflag:

---

### Post by ronnielsen1 on 2010-06-21
You edited at the same time. There's not a howto for 10.04 but (There appears to be a few terminal commands)


[http://www.zoneminder.com/wiki/index.php/Ubuntu_9.10_Desktop](http://www.zoneminder.com/wiki/index.php/Ubuntu_9.10_Desktop)

---

### Post by Peterfc on 2010-06-21
Hi Ronnielsen1

When i used Synapric it looks like i installed Mysql-server along with others.

When i use a Terminal and try to do "$ sudo apt-get install mysql-server"

What i get is "$: command not found"

In the Ubuntu Software centre it says that Zoneminder is installed. 

I tried the Wiki link you mentioned but it looks like i have all those installed when i used Synaptic. 

I would love to ditch my windoooooz CCTV and i am then gates and windoooooooz free.

---

### Post by ronnielsen1 on 2010-06-22
Even installing through synaptic should have asked you about setting up mysql
> When i use a Terminal and try to do "$ sudo apt-get install  mysql-server"

What i get is "$: command not found"

Don't type in the $

Follow the rest of the link without typing in the $

[http://www.zoneminder.com/wiki/index.php/Ubuntu_9.10_Desktop](http://www.zoneminder.com/wiki/index.php/Ubuntu_9.10_Desktop)

---

### Post by Peterfc on 2010-06-22
Hi Ronnielsen1

Just tried what you said and left of the $ but now i have found another problem. I did apt-get autoremove but now i have "13: Permission denied"

I will not give up

Thanks

Peter

peter@peter-desktop:~$ sudo apt-get install mysql-server
[sudo] password for peter: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server is already the newest version.
mysql-server set to manually installed.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
peter@peter-desktop:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
peter@peter-desktop:~$

---

### Post by da burger on 2010-06-22
That command also needs to be run as root (with sudo) so you want
 
```
sudo apt-get autoremove
```
 
In fact all apt-get commands should be run with sudo

---

### Post by Peterfc on 2010-06-22
Hi Da Burger

Thanks that's sorted one problem.

Now after installing Zoneminder. I can find it in the Ubuntu Software Centre as installed. But i can't find it to run.

Thanks

Peter

---

### Post by skaarr on 2010-06-22
Try running ```
zoneminder
``` (with or without sudo) from the terminal.

An installation/setup guide can be found here: [http://www.zoneminder.com/forums/viewtopic.php?t=5391](http://www.zoneminder.com/forums/viewtopic.php?t=5391) (if it's any use).

---

### Post by ronnielsen1 on 2010-06-23
> I will not give up

:lolflag:
I'm not real good at understanding the mysql thing. I've had issues myself. Hopefully someone else knowledgable about this pipes up. You would probably get more responses if you started a new thread about installing mysql since that seems to be the main problem

---

### Post by no2498 on 2010-06-23
if im thinking right he needs a home page to send the pictures to
as if he lost his computer he could still see them
from a diff computer

---

### Post by at100plus on 2010-12-13
Has anyone gotten a DVR card to work with Zoneminder?

I have a chinese DVR card in a Windows Box running 8 Cameras on software called SuperDVR.

It seems all of these camera cards are the same, some made by Avermedia, or QSee.  My card actually came with SuperDVR software that didn't work properly, the documentation was obviously bad chinese translation and I had a really tough time getting it to work on the Windows box initially.  Finally I found that it just won't work with Windows 7 or 64 bit, so I reinstaled WinXP 32 bit onto the box and found an upgraded SuperDVR software on the QSee camera driver website.

Anyway,

I've started using Ubuntu exclusively and would love to make the switch to Ubuntu for my Camera box.

Anyone done this? 

I'm wondering if Ubuntu will recognize the camera card.  It's basically a TV tuner card, has 2 plugs that allow BNC pigtails to be input.

I was even thinking maybe running Virtual Box ontop of Ubuntu and run the DVR in Virtual XP.

I'd really like to take advantage of the 64 bit hardware, so I was thinking about running Ubuntu Server 10.10 64 bit on this machine, is that a bad idea?

---

### Post by skompier on 2010-12-13
They have some really helpful forums that are very specific to your needs.

[http://www.zoneminder.com/forums/](http://www.zoneminder.com/forums/)

---

### Post by at100plus on 2010-12-30
How did Da Burger ever make out?  Like you I don't give up!

Anyway,

I've been on the Zoneminder Forums, I've been downloading distros and trying live CDs (Melin's Zoneminder Mandriva) and Torrent downloading stuff.

It seems to me after playing with the Mandriva Live CD that this Zoneminder is a bit overcomplicated, and looking at the Zoneminder Forums, it appears not much is going on with the software over the last couple years.

What's the easiest way to get this up and running?  I just want a simple DVR progran like the one I have in Windows, but without Windows.

---

### Post by at100plus on 2010-12-30
How did Da Burger ever make out?  Like you I don't give up!

Anyway,

I've been on the Zoneminder Forums, I've been downloading distros and trying live CDs (Melin's Zoneminder Mandriva) and Torrent downloading stuff.

It seems to me after playing with the Mandriva Live CD that this Zoneminder is a bit overcomplicated, and looking at the Zoneminder Forums, it appears not much is going on with the software over the last couple years.

What's the easiest way to get this up and running?  I just want a simple DVR progran like the one I have in Windows, but without Windows.  I don't really see why this software needs SQL or PHP and why the control panel is so fragmented.  I've been searching for an alternative but the only thing I see is Motion and that's all command line, doesn't appear to be what I want either.

---

### Post by MeanRoy on 2011-01-10
> [QUOTE]re:ZoneMinder

I'm trying to install it from the software center but I get the message:
"Package operation failed"
"The installation or removal of a software package failed."
installArchives() failed: 

Apparently at line 7 due to Use of uninitialized value $_[1] ...(perl module)

Has me baffled.

Anyone have an idea what's going on?
I'm running 10.04 LTS

Roy

More detail:
-when I first attempted to install ZoneMinder, the installation went ok until I arrived at some MySQL configuration questions which appeared to require the apache server having been previously installed.
I backed out of the installation and removed it via the package manager.
I then installed Apache, which went ok and worked. I then re-tried the ZoneMinder installation and got the above message.

I have now un-installed Apache and am about to re-try the ZoneMinder installation.

The docs on installing ZoneMinder are not very helpful, IMHO.

Roy.[/QUOTE]

OK, I found a page in the ZoneMinder Wiki with [details on the installation for Ubuntu 10.04]("http://www.zoneminder.com/wiki/index.php/Ubuntu_10.04_%28Lucid_Lynx%29_Desktop").
Here's a clue!
> Do not install XAMPP, LAMPP, Apache, MySQL, etc. 
MySQL was installed the first time I tried the installation, I've un-installed it.

Gee, I'd forgotten how much fun this was! ;-)

---

### Post by MeanRoy on 2011-01-10
I removed ZoneMinder, MySQL, and Apache.
I've tried to install it both from the software center and from a [terminal]("http://www.zoneminder.com/wiki/index.php/Ubuntu_10.04_%28Lucid_Lynx%29_Desktop#Troubleshooting").

I still get the following error:
> Use of uninitialized value $_[1] in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN0> line 7.

Use of uninitialized value $val in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.

Use of uninitialized value $val in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.


This leads me to believe that ZoneMinder installed a perl module which has to be removed as well.

I registered on the ZoneMinder forums but they haven't yet sent me the confirmation e-mail (been ~3hrs) so I can't ask for help there.

Perl is used for lots of things so I don't want to completely remove it.

Anyone know what I should do now?

Roy.

---

