---
title: "Intrepid sources to Hardy not possible?"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by BastardNamban on 2008-12-03
Long story short, new to linux (10 days), I wanted **Open Office 3** on my new 8.04 install. Seeing as OO 3.0 is not part of Hardy's repositories (yet? will that happen?), and after looking for a couple hours across the net & of course these forums for installation directions I could understand (found none, including the OO SITE ITSELF that I could understand, & I'm getting used to terminal to some degree too), I found this site in a recent post: [http://www.akemapa.com/2008/11/21/install-openoffice-3-from-source-on-ubuntu-linux/](http://www.akemapa.com/2008/11/21/install-openoffice-3-from-source-on-ubuntu-linux/)

I saw the EASY part at the bottom, and having already followed some stuff earlier from the eminent Ryukent on adding some Japanese repositories to the repositories source list through terminal, I understood that, in theory, the easiest way to get a fresh working version of OO 3.0 was to add the Intrepid repositories to my Hardy build, seeing as on every OTHER set of instructions, I got through successfully unziping the .DEB tarball to my desktop and THEN got lost!

I used Synaptic & add/remove both to remove all traces of OO 2.4 that came with my Hardy, and managed to get rid of all of it except, for some reason, the menu icons under "office". 

Anyway, followed the "easy" directions, and got this. ```
(ME)@(COMP):~$ sudo gedit /etc/apt/sources.list
(ME)@(COMP):~$ sudo ap-get update
sudo: ap-get: command not found
(ME)@(COMP):~$ sudo apt-get update
Hit http://jp.archive.ubuntu.com hardy Release.gpg
Hit http://archive.ubuntulinux.jp hardy/ Release.gpg                           
Ign http://archive.ubuntulinux.jp hardy/ Translation-en_US                     
Hit http://archive.ubuntulinux.jp hardy/ Release                               
Ign http://jp.archive.ubuntu.com hardy/main Translation-en_US                  
Ign http://jp.archive.ubuntu.com hardy/restricted Translation-en_US            
Ign http://jp.archive.ubuntu.com hardy/universe Translation-en_US              
Ign http://archive.ubuntulinux.jp hardy/ Packages                              
Ign http://jp.archive.ubuntu.com hardy/multiverse Translation-en_US            
Get:1 http://jp.archive.ubuntu.com hardy-updates Release.gpg [189B]            
Ign http://jp.archive.ubuntu.com hardy-updates/main Translation-en_US          
Ign http://jp.archive.ubuntu.com hardy-updates/restricted Translation-en_US    
Ign http://jp.archive.ubuntu.com hardy-updates/universe Translation-en_US      
Ign http://jp.archive.ubuntu.com hardy-updates/multiverse Translation-en_US    
Hit http://jp.archive.ubuntu.com hardy Release                                 
Hit http://archive.ubuntulinux.jp hardy/ Packages                              
Get:2 http://jp.archive.ubuntu.com hardy-updates Release [58.5kB]              
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Hit http://jp.archive.ubuntu.com hardy/main Packages                           
Hit http://jp.archive.ubuntu.com hardy/restricted Packages           
Hit http://jp.archive.ubuntu.com hardy/main Sources                  
Hit http://jp.archive.ubuntu.com hardy/restricted Sources            
Hit http://jp.archive.ubuntu.com hardy/universe Packages             
Hit http://jp.archive.ubuntu.com hardy/universe Sources              
Hit http://jp.archive.ubuntu.com hardy/multiverse Packages           
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://jp.archive.ubuntu.com hardy/multiverse Sources            
Hit http://security.ubuntu.com hardy-security Release                
Get:3 http://jp.archive.ubuntu.com hardy-updates/main Packages [388kB]
Ign http://ppa.launchpad.net hardy Release.gpg                            
Ign http://ppa.launchpad.net hardy/main Translation-en_US                  
Ign http://ppa.launchpad.net hardy Release.gpg                             
Hit http://security.ubuntu.com hardy-security/main Packages                
Ign http://ppa.launchpad.net hardy/mainecho Translation-en_US              
Ign http://ppa.launchpad.net hardy/deb Translation-en_US
Ign http://ppa.launchpad.net hardy/http://ppa.launchpad.net/reacocard-awn/ubuntu Translation-en_US
Ign http://ppa.launchpad.net hardy/hardy Translation-en_US                   
Ign http://ppa.launchpad.net hardy/main Translation-en_US                    
Ign http://ppa.launchpad.net hardy Release.gpg                               
Ign http://ppa.launchpad.net hardy/main Translation-en_US
Ign http://ppa.launchpad.net intrepid Release.gpg      
Hit http://security.ubuntu.com hardy-security/restricted Packages            
Get:4 http://jp.archive.ubuntu.com hardy-updates/restricted Packages [7487B] 
Get:5 http://jp.archive.ubuntu.com hardy-updates/main Sources [102kB]
Get:6 http://jp.archive.ubuntu.com hardy-updates/restricted Sources [892B]
Get:7 http://jp.archive.ubuntu.com hardy-updates/universe Packages [147kB]
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Ign http://ppa.launchpad.net intrepid/main Translation-en_US
Get:8 http://jp.archive.ubuntu.com hardy-updates/universe Sources [34.0kB] 
Get:9 http://jp.archive.ubuntu.com hardy-updates/multiverse Packages [24.2kB]  
Get:10 http://jp.archive.ubuntu.com hardy-updates/multiverse Sources [4020B]   
Get:11 http://ppa.launchpad.net hardy Release [27.6kB]                         
Get:12 http://ppa.launchpad.net hardy Release [27.6kB]
Get:13 http://ppa.launchpad.net hardy Release [27.6kB]
Get:14 http://ppa.launchpad.net intrepid Release [27.6kB]
Ign http://ppa.launchpad.net hardy/main Packages  
Ign http://ppa.launchpad.net hardy/mainecho Packages
Ign http://ppa.launchpad.net hardy/deb Packages
Ign http://ppa.launchpad.net hardy/http://ppa.launchpad.net/reacocard-awn/ubuntu Packages
Ign http://ppa.launchpad.net hardy/hardy Packages
Ign http://ppa.launchpad.net hardy/main Packages
Ign http://ppa.launchpad.net hardy/main Packages
Ign http://ppa.launchpad.net hardy/main Sources
Ign http://ppa.launchpad.net intrepid/main Packages
Hit http://ppa.launchpad.net hardy/main Packages
Err http://ppa.launchpad.net hardy/mainecho Packages
  404 Not Found
Err http://ppa.launchpad.net hardy/deb Packages
  404 Not Found
Err http://ppa.launchpad.net hardy/http://ppa.launchpad.net/reacocard-awn/ubuntu Packages
  404 Not Found
Err http://ppa.launchpad.net hardy/hardy Packages
  404 Not Found
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://ppa.launchpad.net hardy/main Sources
Hit http://ppa.launchpad.net intrepid/main Packages
Fetched 766kB in 3s (199kB/s)
W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/hardy/mainecho/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/hardy/deb/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/hardy/http://ppa.launchpad.net/reacocard-awn/ubuntu/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/hardy/hardy/binary-i386/Packages.gz  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
(ME)@(COMP):~$ sudo apt-get upgrade -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  app-install-data-commercial awn-extras-applets-trunk libimlib2 libimlib2-dev libvorbis-dev libvorbis0a libvorbisenc2 libvorbisfile3
8 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 5210kB of archives.
After this operation, 81.9kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  awn-extras-applets-trunk
W: Duplicate sources.list entry http://ppa.launchpad.net hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_reacocard-awn_ubuntu_dists_hardy_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_reacocard-awn_ubuntu_dists_hardy_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: There are problems and -y was used without --force-yes
(ME)@(COMP):~$ 

``` So it seems like it got the Intrepid Open Office stuff ok, but checking the updates, nothing for Open Office showed up! My terminal install didn't work either.

I'm kinda lost now. What should I do? I've been trying to install OO 3.0 nearly ALL DAY, and no success- every set of directions I find here, or elsewhere, leave me stumped in terminal (how do you execute something from the home directory in terminal? confused), so I try another set.

It is really easy to remove stuff in linux, but I find it strange that it's so hard (for me, at least) to INSTALL something. Am I missing something? What should I do? Thanks for any help you care to give.

---

### Post by LowSky on 2008-12-03
8.10 doens't have OO 3.0 it was release to close to the release of Ubuntu Intrpeid

use this link to install
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by Paqman on 2008-12-03
> **BastardNamban said:**
> on every OTHER set of instructions, I got through successfully unziping the .DEB tarball to my desktop and THEN got lost!


You don't unzip .debs, you just run them. Try double clicking on it.

.debs are Debian package files, they're what the Add/Remove and Synaptic download when you install software the normal way.

---

### Post by Thelasko on 2008-12-03
I definitely don't recommend using Intrepid repositories for Hardy.  Installing software that is not in the repositories for your version can sacrifice stability of your system.

In the end, I recommend **against** running Open Office 3 at the moment.  Especially since you are new to Ubuntu.

Remember, if you do install Open Office 3, you may sacrifice stability.  Don't complain if OO or Ubuntu crashes afterward.

---

### Post by Thelasko on 2008-12-03
> **LowSky said:**
> 7.10 doens't have OO 3.0 it was release to close to the release of Ubuntu Intrpeid
I think you meant 8.10.  7.10 was Gusty.

---

### Post by LowSky on 2008-12-03
> **Thelasko said:**
> I think you meant 8.10.  7.10 was Gusty.

I did, thanks

---

### Post by Keen101 on 2008-12-03
to be honest i don't think open office 3 is available in any ubuntu repository yet. The people who seem to want it badly are downloading it from the openoffice site. I don't care about it that much, so i am just waiting until they have enough time to test it and put it in a repo.

there are lots of threads on ubuntu forums who have asked for help on how to install OO3, and they figured it out. See if you can search for those...

[http://ubuntuforums.org/search.php?searchid=52604897](http://ubuntuforums.org/search.php?searchid=52604897)

---

### Post by BastardNamban on 2008-12-03
Thanks for the replys.

Lowsky, I'm not using 7.10- I'm using 8.04 Hardy, as mentioned.

Paqman- I should have clairfied, the thing I've unzipped has deb in the name, my bad- OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz. I unzip that, and then I'm lost!

Thelasko, I kinda figured that. So, let me get this straight- when you install an ubuntu build, you are then STUCK with that version's software? I know this doesn't mean I CANT put 3.0 on, but I address the question, why would simply upgrading to the current version of software, proven to work in the NEXT build, be taboo for the one before? Aren't builds themselves just updates from the last? Ibex isn't just an upgrade to Heron, and so on?

Upgrading software is something I took as rather mundane and expected. If I can't run the latest program that works on the newest build, why not? Is Hardy not just a name, and my version should be updatable to Intrepid specs? If not, why? Not being ever able to upgrade without completely re-installing my OS, if that is what happens with linux, will both simultaneously stun me and piss me off.

---

### Post by BastardNamban on 2008-12-03
I did somehow manage to completely remove compiz 0.74 and replace it with 0.76, so I'm not a total wack.

Perhaps it's beyond me why terminal needs to exist for some things, because I was used to downloading an installer file, and everything unpacks itself in a GUI for me, in a way I could understand. I was under the impression that Ubuntu was the most user-friendly linux flavor, made for converting people away from XP et al, and so I'm still surprised a basic act like updating software/getting new software is so difficult (again, for me, maybe I'm the exception!).

Keen, I DID search, and nothing I found helped ME. I must be very dense, then, or it may be something that I am missing in understanding. I will keep looking, but it IS almost 2AM here my time! I gotta sleep. I'll check this tommorrow morning my time, sorry folks. 12 hour time diff from most of you!

---

### Post by Thelasko on 2008-12-03
> **BastardNamban said:**
> when you install an ubuntu build, you are then STUCK with that version's software? I know this doesn't mean I CANT put 3.0 on, but I address the question, why would simply upgrading to the current version of software, proven to work in the NEXT build, be taboo for the one before? Aren't builds themselves just updates from the last? Ibex isn't just an upgrade to Heron, and so on?
In a nut shell:

It's a fundamental difference in how Linux works compared to other operating systems.  Programs may or may not rely on other program for support.  

In Windows, 90% of programs are self contained (other than games) and therefore upgrading from one to the next isn't an issue.  The problem with this is that you may end up with several smaller programs that do the same thing on your machine.  It's a waste of space and resources.

In Linux, programs share these smaller programs with each other to prevent overlap.  Unfortunately, this causes problems when one program is upgraded and another one is not.

In order to prevent a condition lovingly called [dependency hell]("http://en.wikipedia.org/wiki/Dependency_hell"), Ubuntu upgrades all programs simultaneously.

P.S. I seriously recommend that you [read this]("http://www.psychocats.net/ubuntu/installingsoftware").  It's explains things so much better than I can.

---

### Post by BastardNamban on 2008-12-03
Thelasko, that was a very simple and elegant answer to something that I'm sure perplexes many newcomers like me. Thank you.

Although now, I have read all the "dependancy hell" wiki- that is frighteningly disappointing. I knew this was too good to be true. I thought linux was too sweet. I now see I figuratively seemed to have stepped from one hell (XP, virus prone, space hog, slow, and others) to another (linux seems to have a strong tendancy for dependancy hell, CANT PLAY GAMES WITHOUT SELLING MY SOUL, & yes, many of us find games IMPORTANT and don't switch because of that, can't we fix that???) and more so now that I understand why distros and repositories exist.

It's as if XP was an open field, and that anything could come in without screwing it up (normally), but that meant it was easy to be infected.
Linux I had been *led* to imagine over the years of reading \. and living with programmers was like the same field, except enclosed by an inpenatrable iron box with one door, for total penatration control, except each distro is it's own field boxed in, and doesn't play well with others. Too many gates need to be controlled to make things work well.

This is very dissapointing.

I guess it's blasphemy to say this here, but if we could have the single stand-alone dependance of XP programs running in a linux-based permission only environment, with authorizations needed to run/install anything affecting the system, as they do now, we could have some sort of ******* XP/Linux mutant child- ugly as hell, but works better than either! That would never happen, though, as XP will always be closed source.

Man, this sucks.

Please tell me that, since I assume repositories are updated, OO 3.0 could be added sometime soon to Hardy (and Intrepid, it seems!), so I could use it safely?

Before I go- there was a reason I wanted 3.0- I had a few bugs with mine (title bar flashing on & off randomly, adjusting font size undid my scrolling and refused to let me make it bigger, somehow skipping to smaller sizes.

I gotta sleep!

Edit: interesting it censors my name IN a post, but not my name itself! How'd I get away with that one?

---

### Post by Thelasko on 2008-12-03
Life is full of trade offs.  You also might want to know that there are tradeoffs within Linux as well.  You have the trade off between stability and cutting edge software.  Ubuntu is conservative in that it favors stability over cutting edge software.  If you must have cutting edge software, there are many other distributions.  Gentoo is widely considered to be the distribution that has the most up to date software, but is difficult to use.

What I like about Ubuntu is that I really don't have to deal with dependency hell.  I've just realized that I won't be able to run the latest software and everything works fine.  Dependency hell only becomes an issue if you try to run the latest software.

If you are having bug issues with OO 2, have you tried updating your current install?  Bugs that are fixed should find their way to Hardy, but I doubt OO 3 will become available for it.

I think the closest thing you will get to your idea of a "XP/Linux mutant child" is [Wine.]("http://en.wikipedia.org/wiki/Wine_(software)")

If you end up switching back to Windows, at least you gave Ubuntu a try.  I understand that Ubuntu isn't for everyone.

---

### Post by Paqman on 2008-12-03
> **BastardNamban said:**
> So, let me get this straight- when you install an ubuntu build, you are then STUCK with that version's software?

Not necessarily.

There's a repository called backports that is used to get updated versions of important software (like Open Office) into old versions of Ubuntu. You can enable it through System > Admin > Software sources.

The other obvious thing to do if you want updated packages is keep following the upgrade path. When the new version of Ubuntu comes out every six months, upgrade to it. It's fairly simple to do, and means you're only ever stuck for six months at most.

And if you really need an updated package in the meantime, sites like Getdeb will package up software into nice Ubuntu-friendly .debs of the latest versions.

---

### Post by oldos2er on 2008-12-03
"I was under the impression that Ubuntu was the most user-friendly linux flavor, made for converting people away from XP et al"

 No, not at all. Please read [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

 These instructions worked for me: [http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

---

### Post by Kellemora on 2008-12-03
Hi BN

Don't let them scare you like that!
Dependency Hell was 100 times worse in WinDOZE than it is in Linux, despite what the naysayers are screaming.

I had well over 100 programs (mostly business related) designed for Windows 3.11 (yeah I know ancient, hi hi)  A few of them worked on Doze 95, and then none of them would work on Doze 98.
Then came Doze XP and once again I could get most of my old programs running again, even if they were now outdated and superseded, at least they worked.

I'm still using the ORIGINAL Windows WRITE program with the global font increase decrease not found in even the most expensive of Word Processors.  And guess what, it runs under WINE in Linux perfectly, as do almost all other self-contained Windows programs.

You CAN do something in LINUX that you cannot do in Windows, and that is to install the dependencies needed to make a program work.  How I got some windows programs to work in other versions of windows was to repackage them into their own little world, so instead of looking outside the box, they stayed in jail so to speak, hi hi.  That was many moons ago when I was still Schmart enough to do it.

The only thing that really bothers me about about Linux (all flavors) is that they keep degrading the kernel so it's no longer backwards compatible with existing software and hardware.

And the fact that most manufacturers don't even know Linux exists, they are still living in the Mickey$oft dream world!  And a few manufacturers don't even support all of Windows flavors!  EG Windows XP-MCE edition is NOT supported by HP even though they sold HP branded computers with XP-MCE as the OS and things like Scanners were sold with them that can't possibly work in the XP-MCE flavor of Windows.  

Even at my ripe old age of 61 years old, I'm starting to study programming again, just so I CAN make some changes I want to the Open Source software.  I'm studying right now on how to write mouse software so I can make my mouses scroll wheel button do a BACK when in a web browser.  I used that feature a thousand times a day in Windows.  And as common as meeces are these days (every computer has one), one would think LINUX would at least have decent mouse support.  To me, the two primary interfaces we have between our computer and the outside world is the keyboard and mouse.  Yet they are the most ignored items by LINUX!
More effort is exerted on getting an MP3 player to run in stereo on a mono card and burn illegal CDs than is put to the more important matters, such as a properly functioning LAN in Ubuntu.

Nonetheless, Ubuntu is the very best of all the Linux distro's and has the most support of any that I've ever seen!

TTUL
Gary

---

