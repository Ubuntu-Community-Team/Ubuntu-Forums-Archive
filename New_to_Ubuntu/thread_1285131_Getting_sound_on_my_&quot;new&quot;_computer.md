---
title: "Getting sound on my &quot;new&quot; computer/"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by Chris Edgell on 2009-10-07
I had worked through so many glitches with my old computer and now a friend has given me a refurbished less-than-5-year-old Dell and I need so much help, but let me address one problem at a time.  I used to have Hardy Heron 8.o4 but he has put in Jaunty Jackalope 9.04.

When I go to Youtube, I am informed that either my Java is not activated or that I need to update or get Adobe flash player.  When I press download it says: Select version to download:
  YUM for Linux
  .tar.gz for Linux
  .rpm for Linux
  .deb for Ubuntu 8.04+

What shall I do?  Thanks.

---

### Post by oldos2er on 2009-10-07
Choose 'deb for Ubuntu'.

---

### Post by the.phantom on 2009-10-07
or you can do

applications
add/remove
enable all the respositories
search for "sun java" and also click the "plug in" below it on the list
and macromedia flash player ( could be adobe in 9.+)

and in firefox you can add a pugin called "aboutplug"
and it will show up in firefox help

and show you what plugins you have for firefox and then just go after what you need are have missing ;-D

---

### Post by Chris Edgell on 2009-10-07
(Ann, okay?)  That didn't seem to have worked, the same message comes to me on Youtube.

Phantom, I couldn't seem to get anywhere with your series of steps to take. By "Emable all repositories", all I could see that would be like that would be "All open source applications..."  There is no "Sun Java" not even any Java...heck, not even Adobe.  (Am I looking in the wrong place?)

---

### Post by halitech on 2009-10-07
Chris,

can you open a terminal and post the results of
```
cat /etc/apt/sources.list
```

---

### Post by Chris Edgell on 2009-10-07
Oh, when I press All, in the list on the left, I find "Sun Java 6 Runtime"
The next app. is "Ubuntu restricted extras".

Then below in the explanation box is this:

The Sun Java Platform Standard Edition Runtime Environment (JRE) 6 contains the Java virtual machine, runtime class libraries, and Java application launcher that are necessary to run programs written in the Java progamming language. It is not a development environment and doesn't contain development tools such as compilers or debuggers. For development tools, see the Java Development Kit JDK(TM) 6 (package sun-java6-jdk). 
This package contains architecture dependent files.

Now what?

---

### Post by Chris Edgell on 2009-10-07
Hi, Halitech!

Here's what I get:

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
chris@computer:~$

---

### Post by halitech on 2009-10-07
> **Chris Edgell said:**
> Oh, when I press All, in the list on the left, I find "Sun Java 6 Runtime"
The next app. is "Ubuntu restricted extras".

Then below in the explanation box is this:

The Sun Java Platform Standard Edition Runtime Environment (JRE) 6 contains the Java virtual machine, runtime class libraries, and Java application launcher that are necessary to run programs written in the Java progamming language. It is not a development environment and doesn't contain development tools such as compilers or debuggers. For development tools, see the Java Development Kit JDK(TM) 6 (package sun-java6-jdk). 
This package contains architecture dependent files.

Now what?

you want to install both of those packages. You may also want to add the medibuntu repos to get more multimedia stuff

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```

there is more info on how to install adobe acrobat reader, playing dvds and other formats.

---

### Post by Chris Edgell on 2009-10-07
sudo sed -e 's/ non-free//' -i /etc/apt/sources.list.d/medibuntu.list

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update

halitech,

the first code copied there is the one from the Medibuntu site you gave me on that last post.  The second code copied is the one you gave me in the code box on that post also.

I entered the one from the Medibuntu site and I can't quite recall what it said (I can check back after I write THIS response)

Shall I go and enter the code you gave me?  I did install those 2 applications (would that be how I would refer to them?) I'm going to go and see if I get sound at Youtube.

BTW it would help me if I could find my trusty old clipboard.  I sure could use it on this endeavor.

I'll be back...thanks again so far!

---

### Post by halitech on 2009-10-07
Chris

the first command will prevent you from getting apps in the non-free repo which you may find you want but not everyone does. The command I posted will simply set up the repo so you can use it to get all the apps (it also says to run the non-free command after you setup the medibuntu repo)

also, are you using Ubuntu or Xubuntu? for Xubuntu it would be xubuntu-restricted-extras

If you have Xubuntu, you should be able to right click the top panel and add to panel and select clipman to get your clipboard. I'm not sure what its called in Ubuntu.

---

### Post by Chris Edgell on 2009-10-07
Ah,

I must say I already installed the Ubuntu-restricted-extras.  That install of Sun Java and the Ubuntu-restricted-extras took some time and was about 70 files.  Shall I just install the XUbuntu and will the computer sort out or shall I uninstall all that stuff and re do?

Such a simple solution, with the clipman, or whatever.

---

### Post by halitech on 2009-10-07
> **Chris Edgell said:**
> Ah,

I must say I already installed the Ubuntu-restricted-extras.  That install of Sun Java and the Ubuntu-restricted-extras took some time and was about 70 files.  Shall I just install the XUbuntu and will the computer sort out or shall I uninstall all that stuff and re do?

Such a simple solution, with the clipman, or whatever.

if the computer is working fine with Ubuntu, just leave it installed. If you want to try Xubuntu to see how it compares, just open a terminal and run
```
sudo apt-get install xubuntu-desktop
```then log out, click sessions and select XFCE and log in.

---

### Post by Chris Edgell on 2009-10-07
The guy who set me up, I'm quite sure he said he'd installed the XUbuntu.  (Is there somewhere I could look to see?)

You know I was refering to the extras I was installing when I was installing the Sun Java.

I have (do you call it run?) run the code you gave me back there and it gave me pages of print...so I guess that's that...as far as that code goes, I mean.

I still went to you tube and got that same message either your Java is not ON, or your Adobe player is out of date, (or too old, or too obsolete---something to that effect...)

Is there an easy way to test my SOUND?

---

### Post by sandyd on 2009-10-07
usin 64 bit?

---

### Post by ikisham on 2009-10-07
Don't you have NoScript installed? It's a Firefox extension that blocks scripts and unless you allow that site it'll show that message.
To see if you have NoScript you must check if there's a little 's' icon on the bottom-right-hand corner. Then, if you have it, just click on the icon to allow the site.

---

### Post by Chris Edgell on 2009-10-07
I don't see any little "s"....I just have no idea about 64 bit...where would I get to see that fact.

And about the little s, I have no idea.  
I appreciate you both taking the time, but I have gotten lost, since those other things, especially halitech, haven't worked yet.  If you can be more explicit about what we're doing, I'll be glad to try to follow.

---

### Post by halitech on 2009-10-07
Chris

to find out if you have 64bit, open a terminal and run```
uname -a
```and post the results here

for the sound, let's go back to basics. In the terminal run the following and post the output
```
lspci
```
```
aplay -l
```
```
lshw -C sound
```

---

### Post by Chris Edgell on 2009-10-07
Linux computer 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux
chris@computer:~$

chris@computer:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
chris@computer:~$ 

chris@computer:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
chris@computer:~$ 

chris@computer:~$ lshw -C sound
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Multimedia audio controller
       product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0
chris@computer:~$ 

Oh, halitech

---

### Post by halitech on 2009-10-07
Chris

ok, you are using 32bit Ubuntu based on this [color="red"]i686[/color]

Everything looks fine as far as the sound card goes. For testing, go to System - Prefs - Sound (I think) and click on test sound and see what happens.

---

### Post by Chris Edgell on 2009-10-07
When I click on systems, the drop down choices are:

Authorizations
Hardware drivers
Language support
Login window
Printing
Remote filesystem
Services
Shared folders
Software sources
Synaptic packaging manager
System monitor
Time and date
Update manager
Users and groups

---

### Post by halitech on 2009-10-07
ok, I'm not sure where it is an since I'm using XFCE the menus are different but there should be an option about sound in one of the drop downs. Maybe look around and see if you can find anything regarding sound.

---

### Post by Chris Edgell on 2009-10-07
I've been clicking around and can't seem to see anything about sound and/or options.  

(On my drop down from Applications the next to last one is About XFCE, there it mentions XFCE and XUbuntu.)

I'm serving spaghetti to friends at 6:00, so I will be busy until about 9:30.  I'll be checking back here then...

Thank you so much for all your help so far.

---

### Post by halitech on 2009-10-07
ok so you do have Xubuntu. In your menu,  you should have a settings option and in there you should have a sound option but I think it only gives the option to set which device to use. Maybe try another way, find an mp3 file and see if that will play so we know if its a sound issue or youtube issue.

---

### Post by Chris Edgell on 2009-10-07
Just taking a minute to get back here.  

Sorry to be so ignorant of stuff, but never HAVE seen an MP3, can you tell me how to find one to try to play??!!

---

### Post by ikisham on 2009-10-07
Here you may download a video file which may serve for the testing
[http://www.suprememasterchinghai.org.uk/bbs/board.php?bo_table=download&sca=vege](http://www.suprememasterchinghai.org.uk/bbs/board.php?bo_table=download&sca=vege)

---

### Post by Chris Edgell on 2009-10-07
Thank you, Ikisham. I did go there and, well, there is no sound..... I am about to hook up my old computer, just to make sure the speakers still work... but that's a lot of work, especially since I tried to hook it up last night (for some other purpose) but when I did, I got the message about being unable to boot up and so I should put in the CD, I only have this Jaunty, so may do that, as I said just to see that the speakers do work...unless there's an easier way to test them....wish I had a little walkman...

---

### Post by ikisham on 2009-10-08
Hi, Chris. Since you say you installed the restricted extras you must have the flash player. In this case, even if you have no sound the video on Youtube should appear. Also if you have the codecs (which come with the restricted extras) your media player will show the videos you download.
If you're still receiving a message that flashplayer isn't installed, please check two things in Firefox:
- Open 'Tools' > 'Add-ons', click on the 'Plugin' tab and see if there is 'Shockwave Flash' and if it is enabled.
- Also go to 'Edit' > 'Preferences', click on the 'Privacy' tab and check if 'Accept cookies from sites' is ticked. If not, tick it.

Apart from that, can you call your friend that installed Ubuntu for you? He may give you a hand.

Cheers.

---

### Post by Chris Edgell on 2009-10-08
Somewhere in this process,I have now gone to Youtube and no longer receive that message and, yes, the video plays...just no sound...also, when inserting and removing the jack (is that the term, the name for the connector end of the connecting wire???), anyway when I plug in and unplug there is plent of static-y noise coming from the speaker,making me think that the problem is the connection point in the computer.

Thanks, ikisham.

---

### Post by ikisham on 2009-10-08
It may be a hardware problem. Maybe you could boot from a live-cd if you have one and see if sound works, too.
I don't think I can be of much help since I use a desktop with VIA chipset which usually works very well (this particular chipset version).

Keep going, you'll eventually find out if it's hardware or software and fix it.
If you sort out that it ain't a hardware problem try to search the forum for your chipset or laptop model and sound issues.

Actually it may even be your speakers, right?

---

### Post by Chris Edgell on 2009-10-08
Thanks.  I'll lyou know what happens...and how it all sorts out.

---

### Post by Chris Edgell on 2009-10-08
My friend, who set this computer up, emailed me to say he hasn't had time to read this thread but sent me the URL for a thread about sound.

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I went, I saw that it began in 2004, I believe....it continues yet today... it has nearly 1700 posts... I read and read and read...

Check it out.

---

### Post by Chris Edgell on 2009-12-02
"After having just installed Xubuntu on a virtual box, I believe I
know what the problem is...In the upper right hand corner you should see a small faded speaker.  Left click on it.  It should open a window that tells you that there's no controls available.  In the lower left hand corner of the window should be a button that says "Select Controls"  Click on that, you'll get a list of controls with a checkbox next to each.

Select "Master" and "PCM" from the list and hit "Close".  Slide both of these up to max (or near max) and then note that perhaps it still has the little Mute icon turned on for Master volume?  It will show like a little red X, click on that and you should have sound!

AND I DO, I do have sound.  I just wanted to tell you how I got it... thanks to a sharp Ubuntu user.

---

