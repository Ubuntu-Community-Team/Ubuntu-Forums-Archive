---
title: "Just kicked windows off my laptop."
date: 2010-04-10
forum: New to Ubuntu
---

### Post by philodice on 2010-04-10
And now the reading begins.  Switching to Linux is more like a journey or a process.  I seem to need a woeful amount of re-education.  Also, software center is useless.  Authentication help threads aren't helping me, and I can't get email to send from evolution.  
Problem after problem.  I know why Ubuntu isn't the programming os of choice now, but it is too late for me to go back without spending money on a company that offers an even LESS satisfactory experience.  Do I satisfy myself that my laptop now ONLY surfs the internet and runs open office, or do I try for more?

Is this going to take years of study just to get music to play on my Acer Aspire one?  
I've been studying help forums and tutorials for two weeks, and I'm not figuring this out.
What good is free software my computer won't allow me to download and install?
Generally confused and dissatisfied.

Pros:  This Acer hasn't frozen, stopped, randomly overheated, lost connection to the internet, or shut off since installing Ubuntu netbook remix.

---

### Post by sigmarhophi on 2010-04-10
Lets see if we can get you up and running.  Ask some specific questions and we can give some specific answers.  

Lets start with downloading and installing software.  You mentioned software center is useless.  How?  are you getting errors?  issues finding apps you want?

---

### Post by wojox on 2010-04-10
Authenticate what? just type in your password.
What mail server are you trying to connect to?
Click on my link in my signature and add medibuntu repo's to play music.

You are using 9.10 Karmic Koala correct?

---

### Post by Pikestaff on 2010-04-10
> **philodice said:**
> And now the reading begins.  Switching to Linux is more like a journey or a process.  I seem to need a woeful amount of re-education.

Yup, that is how it works. :)  Be patient, if you are dedicated enough to keep at it-- it often takes a lot of work to switch to Linux.

I agree with the above posters, though, in needing more details.  Specifically what sort of problems are you having?

---

### Post by philodice on 2010-04-10
Specifically, I'm trying to install ubuntu restricted extras.  Of course, it doesn't want to allow me to install unauthenticated packages.
I am now reading "how to install popular proprietary software."

As for the email, evolution email comes in, but outgoing mail doesn't go out.  Could be an ISP issue according to my research, I'm not giving up on that yet but I may  have to change the server I'm using in settings.

I have about 5 linux tutorials on my PDA right now.  One thing...learning how to fix windows bugs gave me a headache.  Learning Linux...well, it's fun.

---

### Post by Pikestaff on 2010-04-10
> **philodice said:**
> One thing...learning how to fix windows bugs gave me a headache.  Learning Linux...well, it's fun.

Hehe, that's how I feel also.

As for the restricted extras, have you tried [this page]("https://help.ubuntu.com/community/RestrictedFormats")?

---

### Post by linuxman94 on 2010-04-10
EDIT: Pikestaff, you  beat me to it. :) Your way is much easier.

Here is an easy way to install the restricted-extras.

1. Open a terminal (Applications -> Accessories -> Terminal).

2. Copy&paste this code lint into it:
```
sudo apt-get install ubuntu-restricted-extras
```

It will ask for your password to continue.  Go ahead and type it in.  NOTE: Nothing will appear when you type in your password but it is being entered.

Hit enter and wait. :)

---

### Post by 2hot6ft2 on 2010-04-10
> **philodice said:**
> Specifically, I'm trying to install ubuntu restricted extras.  Of course, it doesn't want to allow me to install unauthenticated packages.
I am now reading "how to install popular proprietary software."

Let's just cut to the end and install it all at once so you can play pretty much everything.

I could spend a half hour saying go here click this open that  yada yada yada instead do this.

Open a terminal
Applications > Accessories > Terminal
and run these commands one at a time and your password wont be shown when you type it in just type it in and hit enter.
This first one enables the medibuntu repository for restricted codecs and such
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
Remove any browser media player plugin you currently have installed (totem-mozilla is installed by default, but you may have installed mozilla-mplayer or mozilla-plugin-vlc) like this:
```
sudo apt-get remove totem-mozilla mozilla-mplayer mozilla-plugin-vlc
```
then for all the multimedia, mp3's, divx web player, and dvd playback
```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 gecko-mediaplayer vlc
```
Oracle Java is part of the ubuntu-restricted-extras package so use your arrow keys and Tab key to select and Enter to decline the Java terms of use since we'll install suns java next.
Next we want the sun version of Java since it works better and will pass the test on this page.
[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)
It will say there is an update available but the main thing is it works.
```
sudo apt-get ininstall sun-java6-jre sun-java6-plugin
```
And to get rid of one package in the restricted extras that causes problems:
```
sudo apt-get purge ttf-mscorefonts-installer
```
ttf-mscorefonts-installer bug report
[https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217](https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217)

[And to install Flash (the same as going to the adobe website) just click this link if using 9.04 or up, then on OK]("apt:adobe-flashplugin?channel=$distro-partner")

And you're done.

VLC Player will be in Applications > Sound and Video > VLC

---

### Post by Didius Falco on 2010-04-10
> **philodice said:**
> And now the reading begins.  Switching to Linux is more like a journey or a process.  I seem to need a woeful amount of re-education.  Also, software center is useless.  Authentication help threads aren't helping me, and I can't get email to send from evolution.  
Problem after problem.  I know why Ubuntu isn't the programming os of choice now, but it is too late for me to go back without spending money on a company that offers an even LESS satisfactory experience.  Do I satisfy myself that my laptop now ONLY surfs the internet and runs open office, or do I try for more?

Is this going to take years of study just to get music to play on my Acer Aspire one?  
I've been studying help forums and tutorials for two weeks, and I'm not figuring this out.
What good is free software my computer won't allow me to download and install?
Generally confused and dissatisfied.

Pros:  This Acer hasn't frozen, stopped, randomly overheated, lost connection to the internet, or shut off since installing Ubuntu netbook remix.

Here is a thread that should provide some help in configuring your email in Evolution:

[http://ubuntuforums.org/showthread.php?t=1450943](http://ubuntuforums.org/showthread.php?t=1450943)

This page will help with getting the music and videos to play properly:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Other questions or problems can often be solved by a thread search here on the forums with the relevant keywords.

Other resources include the Tutorials and Tips sub-forum:

[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

The Official Ubuntu Documentation:

[https://help.ubuntu.com/](https://help.ubuntu.com/)

Community Contributed Documentation:

[https://help.ubuntu.com/community/TitleIndex](https://help.ubuntu.com/community/TitleIndex)

You can also get a free PDF version of the "Ubuntu Pocket Guide and Reference" from here:

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

Of course, just some googling will often help find answers to common problems, and you can always start a thread in the appropriate forum to ask specific questions.

Yes, there is a learning curve, but Ubuntu has the best community-driven support I've ever seen, and in a year you'll be shocked at how much you've picked up without even realizing it.

One thing I did right away was to start a text file of my own where I cut/pasted things I learned that seemed like they'd be useful in the future, so I have my own little help file at hand.

Welcome to Ubuntu and the Forums!

Regards,

Didius

---

### Post by phibxr on 2010-04-10
> **philodice said:**
> Is this going to take years of study just to get music to play on my Acer Aspire one?  
I've been studying help forums and tutorials for two weeks, and I'm not figuring this out.

At least you've found the most likely best community available to assist you. :)

Good luck on your travels!

---

### Post by philodice on 2010-04-10
> **Pikestaff said:**
> Hehe, that's how I feel also.

As for the restricted extras, have you tried [this page]("https://help.ubuntu.com/community/RestrictedFormats")?

Yay...I now have restricted extras.  Go Me.  :popcorn:

Now to tackle email...

---

### Post by 2hot6ft2 on 2010-04-10
To add to the flood of info. headed your way I'll add these.

Guides

[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)
[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://ubuntuguide.org/wiki/Main_Page](http://ubuntuguide.org/wiki/Main_Page)
[Karmic Koala Bible AND so much more good info.]("http://www.makeuseof.com/tech-fun/search/?cx=009717636731598800244%3Aqhe4rh7wuxs&cof=FORID%3A11&q=Ubuntu+Karmic+Koala+Bible&sa=%C2%A0#288")
[http://fosswire.com/post/2008/4/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/4/ubuntu-cheat-sheet/)
[http://fosswire.com/post/2007/8/unixlinux-command-cheat-sheet/](http://fosswire.com/post/2007/8/unixlinux-command-cheat-sheet/)
[http://tldp.org/LDP/Bash-Beginners-Guide/html/](http://tldp.org/LDP/Bash-Beginners-Guide/html/)

More helpful things to bookmark for future reference.

Linux alternatives to windows apps
[http://www.osalt.com/](http://www.osalt.com/)
[http://www.linux.org/apps/](http://www.linux.org/apps/)
[http://www.gimpshop.com/](http://www.gimpshop.com/)
[http://www.linuxappfinder.com/](http://www.linuxappfinder.com/)

Everyone asks coming from windows
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

Customizing and apps
[http://ubuntuforums.org/showthread.php?t=856190](http://ubuntuforums.org/showthread.php?t=856190)
[http://www.quickstart.freeforums.org](http://www.quickstart.freeforums.org)

Learning Linux
[http://ubuntuforums.org/showthread.php?t=790485](http://ubuntuforums.org/showthread.php?t=790485)
[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)
[http://ubuntuforums.org/showthread.php?t=655207](http://ubuntuforums.org/showthread.php?t=655207)

Troubleshooting, multimedia and misc help
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
[http://tazbuntu.blogspot.com/2008/07/remove-old-kernels-in-ubuntu.html](http://tazbuntu.blogspot.com/2008/07/remove-old-kernels-in-ubuntu.html)

Welcome and enjoy.
I know it's more than what you wanted or than what you want to do right now but if you get bored or decide you want to know more.
:guitar:

---

### Post by philodice on 2010-04-10
At least I did try research first before calling in the penguin police.  
Now I have things to test.

OMG
The video of my doves kissing played!  I love you guys.  I mean, I would have enjoyed this laptop without all the toys and whistles but I'm enough of a geek that having things not work goes against the grain.

---

### Post by Pikestaff on 2010-04-10
> **philodice said:**
> At least I did try research first before calling in the penguin police.  
Now I have things to test.

OMG
The video of my doves kissing played!  I love you guys.  I mean, I would have enjoyed this laptop without all the toys and whistles but I'm enough of a geek that having things not work goes against the grain.

Awesome, congrats :D

---

### Post by 2hot6ft2 on 2010-04-10
> **philodice said:**
> I would have enjoyed this laptop without all the toys and whistles but I'm enough of a geek
Well when you get comfortable and think you know just about everything you can try Conky. That should keep you busy for at least a month if not a few years.
[http://ubuntuforums.org/showthread.php?t=867076](http://ubuntuforums.org/showthread.php?t=867076)
[http://ubuntuforums.org/showthread.php?p=9103810](http://ubuntuforums.org/showthread.php?p=9103810)
[http://ubuntuforums.org/showthread.php?p=8713982](http://ubuntuforums.org/showthread.php?p=8713982)
[http://conky.sourceforge.net/docs.html](http://conky.sourceforge.net/docs.html)

Enjoy

---

### Post by philodice on 2010-04-10
I've earned my coffee today.  Saving more learning for tomorrow. 

That was my first terminal session and it wasn't so bad.
 I thought installing from a USB was a learning experience.  To infinity.  And beyond.

---

### Post by 2hot6ft2 on 2010-04-10
> **philodice said:**
> I've earned my coffee today.  Saving more learning for tomorrow. 

That was my first terminal session and it wasn't so bad.
 I thought installing from a USB was a learning experience.  To infinity.  And beyond.
The terminal is your friend. It can make a 1/2 hour GUI job only take a couple minutes if that.

---

### Post by ranch hand on 2010-04-10
Just to add what I think is a great site for first setting up Ubuntu as everything seems well covered here;

[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)

---

### Post by haddog on 2010-04-10
> **ranch hand said:**
> Just to add what I think is a great site for first setting up Ubuntu as everything seems well covered here;

[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)

Agreed. My recommendation also.

---

### Post by skompier on 2010-04-10
Great to see that you're learning and making progress. Linux Mint, which is based on Ubuntu, comes with most codecs already installed, so media usually works right out of the box. I do applaud you taking the route that we all did but Mint is pretty nice for new users..:)

---

### Post by shae on 2010-04-11
> **philodice said:**
> And now the reading begins.  Switching to Linux is more like a journey or a process.  I seem to need a woeful amount of re-education.  Also, software center is useless.  Authentication help threads aren't helping me, and I can't get email to send from evolution.  
Problem after problem.  I know why Ubuntu isn't the programming os of choice now, but it is too late for me to go back without spending money on a company that offers an even LESS satisfactory experience.  Do I satisfy myself that my laptop now ONLY surfs the internet and runs open office, or do I try for more?

Is this going to take years of study just to get music to play on my Acer Aspire one?  
I've been studying help forums and tutorials for two weeks, and I'm not figuring this out.
What good is free software my computer won't allow me to download and install?
Generally confused and dissatisfied.

Pros:  This Acer hasn't frozen, stopped, randomly overheated, lost connection to the internet, or shut off since installing Ubuntu netbook remix.

I feel I should address some of the problems you have brought up.

I understand your frustration with the software center.  It is not intended for people who know what package to install, but rather to help users find packages based on name or purpose.  If you know the name of the package you want to install, you should use Synaptic Package Manager from the System>Administration menu to find and install it.  Alternatively you could also use the terminal to install it, like another user mentioned.

Concerning your comment concerning "programming os" and Ubuntu not being preferred as one.  Linux, including Ubuntu, is preferred by many developers.  The reason most commercial applications are written for Windows or Mac is due to their current install base.  Personally, the Linux way of programming is amazing in comparison.  If you would like the help, I would love to assist you getting started in this regard.

As I do not have your exact hardware but rather a computer that was designed for Ubuntu (thanks Dell!), I have little if any problems with my computer.  I just install Ubuntu and it is ready to go.  I suggest you begin by searching the forum and Google for any problem you experience.  If you need help understanding anything you find or cannot find any help, create a post concerning your problem here.

Good luck and enjoy.

---

