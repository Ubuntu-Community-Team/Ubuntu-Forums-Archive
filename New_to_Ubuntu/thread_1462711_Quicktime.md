---
title: "Quicktime"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by orphanlast on 2010-04-26
I went onto apple.com and tried to view some videos about the ipad just because I wanted to take a look at what a real piece of crap looks like... but I was so disappoint when I needed to install quicktime and it was only for windows. 

Wine successfully installed it. But Wine doesn't seem to communicate with the browser, so those online quicktime videos still weren't able to be played.

Is there anything called "BEER" or "CHEEP WHISKEY" or something that can simulate the Mac OS? Lol.  

Or is there an equivalent to Quicktime that I can install from Synaptic that will allow me to watch quicktime files, be they on or off the Internet?

---

### Post by Gone fishing on 2010-04-26
If you've installed the restricted extras etc and the multimedia codecs from medibuntu [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
vlc or smplayer will play quicktime files

---

### Post by orphanlast on 2010-04-26
I've read and placed all this text into my terminal and now my computer not only can't play quicktime, but it's now doing really weird things. When I close my computer a pop up window comes up at the bottom of the screen but too brief for me to be able to read it, and when the computer boots up, it takes me to the login screen. It never used to do that. It'd just place me to the desktop. 

THIS login screen just says "Automatic Login" and sits and loads there for about five seconds and then places me on my desktop.

I'm hoping none of this is going to cause problems.

---

### Post by no2498 on 2010-04-26
is quick time starting up during restart up

to get smplayer open a terminal type, smplayer
it tells you how to install it

9 out of 10 times you do not need to open it. it is part of mplayer

---

### Post by orphanlast on 2010-04-26
> **no2498 said:**
> is quick time starting up during restart up 

Quicktime isn't on my computer except for on wine. It's not doing anything. If I downloaded a quicktime program I'm sure wine can open it now, but there's nothing new happening during start up other than an irritating login screen that I don't even use.

>  to get smplayer open a terminal type, smplayer
it tells you how to install it 

I've typed "smplayer" and "mplayer" and "apt get smplayer" and "apt get mplayer" and the terminal doesn't recognise the command.

>  9 out of 10 times you do not need to open it. it is part of mplayer

Cool, but I'm not sure if I understand what I was supposed to have done...

---

### Post by orphanlast on 2010-04-26
Yeah... I just keep repeating all the things on that website: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and I still can't watch quicktime videos on apple.com... and my computer is acting like crap.

Great... this reminds me of having a virus on windows... I've only had Ubuntu for a month and a half and its already acting like crap JUST BECAUSE I'm trying to get it to behave like a computer.

---

### Post by orphanlast on 2010-04-27
There... reinstalled Ubuntu.

It was acting WEIRD.

I hope doing this again won't cause problems... Then again, I did quite a bit of other things yesterday, that might have messed things up. I'm a rookie...

---

### Post by orphanlast on 2010-04-27
This is what my terminal is saying... I have no idea if it was successful or not. If it was, then this still didn't run quicktime...

>  skyler@skyler-desktop:~$ sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
[sudo] password for skyler: 
Sorry, try again.
[sudo] password for skyler: 
--2010-04-26 23:37:37--  [http://www.medibuntu.org/sources.list.d/karmic.list](http://www.medibuntu.org/sources.list.d/karmic.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 272 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 272         --.-K/s   in 0s      

2010-04-26 23:37:38 (36.1 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [272/272]

Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg [197B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_US
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release [9,237B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages [3,279B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages [7,553B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Fetched 20.3kB in 1s (13.2kB/s)
Reading package lists...
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
Reading package lists...
Building dependency tree...
Reading state information...
The following NEW packages will be installed:
  medibuntu-keyring
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,448B of archives.
After this operation, 49.2kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Authentication warning overridden.
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free medibuntu-keyring 2008.04.20 [3,448B]
Fetched 3,448B in 0s (5,654B/s)
Selecting previously deselected package medibuntu-keyring.
(Reading database ... 129836 files and directories currently installed.)
Unpacking medibuntu-keyring (from .../medibuntu-keyring_2008.04.20_all.deb) ...
Setting up medibuntu-keyring (2008.04.20) ...
OK

Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg [197B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release [9,237B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Fetched 198B in 1s (146B/s)
Reading package lists...
skyler@skyler-desktop:~$ sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  app-install-data-medibuntu apport-hooks-medibuntu
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 17.1kB of archives.
After this operation, 176kB of additional disk space will be used.
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free app-install-data-medibuntu 0.2ubuntu1 [14.5kB]
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free apport-hooks-medibuntu 1medibuntu1 [2,592B]
Fetched 17.1kB in 0s (21.6kB/s)              
Selecting previously deselected package app-install-data-medibuntu.
(Reading database ... 129840 files and directories currently installed.)
Unpacking app-install-data-medibuntu (from .../app-install-data-medibuntu_0.2ubuntu1_all.deb) ...
Selecting previously deselected package apport-hooks-medibuntu.
Unpacking apport-hooks-medibuntu (from .../apport-hooks-medibuntu_1medibuntu1_all.deb) ...
Processing triggers for software-center ...
  
sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
Setting up app-install-data-medibuntu (0.2ubuntu1) ...

Setting up apport-hooks-medibuntu (1medibuntu1) ...

skyler@skyler-desktop:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libdvdcss2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 38.0kB of archives.
After this operation, 111kB of additional disk space will be used.
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free libdvdcss2 1.2.10-0.3medibuntu1 [38.0kB]
Fetched 38.0kB in 0s (39.4kB/s)    
Selecting previously deselected package libdvdcss2.
(Reading database ... 129856 files and directories currently installed.)
Unpacking libdvdcss2 (from .../libdvdcss2_1.2.10-0.3medibuntu1_i386.deb) ...
Setting up libdvdcss2 (1.2.10-0.3medibuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
skyler@skyler-desktop:~$ wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
--2010-04-26 23:40:56--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 36270 (35K) [application/x-debian-package]
Saving to: `libdvdcss2_1.2.9-2medibuntu4_i386.deb'

100%[======================================>] 36,270      51.4K/s   in 0.7s    

2010-04-26 23:40:58 (51.4 KB/s) - `libdvdcss2_1.2.9-2medibuntu4_i386.deb' saved [36270/36270]

skyler@skyler-desktop:~$ sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
dpkg: warning: downgrading libdvdcss2 from 1.2.10-0.3medibuntu1 to 1.2.9-2medibuntu4.
(Reading database ... 129864 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.10-0.3medibuntu1 (using libdvdcss2_1.2.9-2medibuntu4_i386.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.9-2medibuntu4) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
skyler@skyler-desktop:~$ sudo apt-get install w64codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package w64codecs
skyler@skyler-desktop:~$ sudo apt-get install ppc-codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ppc-codecs
skyler@skyler-desktop:~$ wget -c [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2.1_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2.1_i386.deb)
--2010-04-26 23:42:15--  [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2.1_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2.1_i386.deb)
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14284826 (14M) [application/x-debian-package]
Saving to: `w32codecs_20071007-0medibuntu2.1_i386.deb'

100%[======================================>] 14,284,826   879K/s   in 18s     

2010-04-26 23:42:33 (769 KB/s) - `w32codecs_20071007-0medibuntu2.1_i386.deb' saved [14284826/14284826]

skyler@skyler-desktop:~$ sudo dpkg -i w32codecs_20071007-0medibuntu2.1_i386.deb 

---

### Post by orphanlast on 2010-04-27
Further updates on how gay this situation is, I've tried out this website  [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

I've concluded that help.ubuntu.com not only doesn't describe things well enough for lay fold like myself, but its instructions don't do as promised, even when you DO understand what they're talking about. I waited for 45 minutes for this thing to install one ungodly program after another just for me to STILL be completely unable to watch quicktime videos from a website.

Did someone hack the Ubuntu website or something? Because this stuff should be working.

Since none of these massive programs seem to work, I doubt I'll ever be able to find out how to get all these things off without reinstalling Ubuntu (agian)... 

I JUST reinstalled too.

---

### Post by orphanlast on 2010-04-27
Wow... I just tried to follow their instructions on how to install songbird 

[https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

and not even that worked out.

Really? really!

WTF...

QUICKTIME! EVERYONES USING IT... but Linux.

---

