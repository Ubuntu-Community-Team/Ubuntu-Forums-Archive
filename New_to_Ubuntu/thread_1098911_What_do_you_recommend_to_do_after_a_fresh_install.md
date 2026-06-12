---
title: "What do you recommend to do after a fresh install?"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by suomalainen on 2009-03-17
Ubunteros,

I wanted to get some ideas as to the important things to do after a fresh install of Ubuntu 8.04LTS is completed.

A few that come to mind are:

1) install restricted drivers
2) Get multi media to work
3) install favorite programs from Synaptic

Do you have any other ideas? Any how-to's and web links would be welcomed.

Thank you!

---

### Post by BDNiner on 2009-03-17
Change the default theme and icons!!

At least that is what i always do.

---

### Post by suitedaces on 2009-03-17
I finished my install only a day and a half ago. So far I've got all the necessary drivers, trawled for a wallpaper and theme I liked, downloaded amarok and vlc, got flash going, imported bookmarks and files form my vista partition, and got codecs set up. Phew!

---

### Post by suitedaces on 2009-03-17
Also i got rid of that annoying error beep! [http://ubuntuforums.org/showthread.php?t=1098909](http://ubuntuforums.org/showthread.php?t=1098909)

---

### Post by BDNiner on 2009-03-17
Now that you have got all that out of the way you can finally start to use the computer!!

---

### Post by D3ath on 2009-03-17
One command i always do first thing
```
sudo apt-get install ubuntu-restricted-extras
```

that's it everything i need. Flash, Java, Fonts, and different dvd and video formats as well as audio!

---

### Post by LowSky on 2009-03-17
> **D3ath said:**
> One command i always do first thing
```
sudo apt-get install ubuntu-restricted-extras
```

that's it everything i need. Flash, Java, Fonts, and different dvd and video formats as well as audio!

best package ever!!

but I always add the medibuntu repos too, more codec support and a few more apps like google earth and skype.

Personally I just load the apps/codec/drivers I need and go from there, usually themes/wallpapers only get added whenI want to change them later on.

---

### Post by BDNiner on 2009-03-17
One of my most important apps is Virtual Box. I test out all new software packages that i come across there first before trying them on my main install. I would be great if I still had my testing computer. My girlfriend made me give it to my brother. she said 2 in the house is enough.

---

### Post by D3ath on 2009-03-17
> **LowSky said:**
> best package ever!!

but I always add the medibuntu repos too, more codec support and a few more apps like google earth and skype.

Personally I just load the apps/codec/drivers I need and go from there, usually themes/wallpapers only get added whenI want to change them later on.

nice didn't know about this im going to have to use this from now on right about the ubuntu-restricted-extras. Thanks man!

---

### Post by D3ath on 2009-03-17
> **BDNiner said:**
> One of my most important apps is Virtual Box. I test out all new software packages that i come across there first before trying them on my main install. I would be great if I still had my testing computer. My girlfriend made me give it to my brother. she said 2 in the house is enough.
She just doesn't get it man.  I feel for ya!

---

### Post by suomalainen on 2009-03-17
Regarding the "Multi media" experience should I do the command:

sudo apt-get install ubuntu-restricted-extras

OR FOLLOW THE INSTRUCTIONS HERE? See link Below.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)


OR do I need to do both???? Just want to err on side of caution.


Thanks everyone!

---

### Post by D3ath on 2009-03-17
> **suomalainen said:**
> Regarding the "Multi media" experience should I do the command:

sudo apt-get install ubuntu-restricted-extras

OR FOLLOW THE INSTRUCTIONS HERE? See link Below.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)


OR do I need to do both???? Just want to err on side of caution.


Thanks everyone!

Do the: 
```
ubuntu-restricted-extras
```

but also follow this link for the Media Experience:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by xpod on 2009-03-17
> she said 2 in the house is enough.

Get married to her then have loads of children......then you *need* just as many computers...

Worked for me.;)

---

### Post by mocoloco on 2009-03-17
My 2 cents, I think LTS is useful for a corporate environment where things should change infrequently, but for regular users I see no reason to go with the latest and greatest.  After a fresh 8.10 install I definitely install ubuntu-restricted-extras and also disable the pcskpr beep as have already been mentioned.  Also:

Enable DVD playback (must have libdvdread3 installed, which is part of restricted extras)
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

Install totem-xine (better DVD controls)
```
sudo apt-get install totem-xine
```

Eyecandy:
Install extra backgrounds & themes, and card styles for card games
```
sudo apt-get install gnome-backgrounds ubuntustudio-wallpapers gnome-themes-extra gnome-games-extra-data
```

If users install KDE apps they won't be able to access help without this
```
sudo apt-get install khelpcenter
```

---

### Post by suomalainen on 2009-03-17
Wow.... So really excellent feedback!!! Thanks everyone.


But if I understood running both:

1. sudo apt-get install ubuntu-restricted-extras
2. [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)


Is the best thing to do????? Just confirming...

---

### Post by chewit on 2009-03-17
Updates!

I will always check for updates and downloads. Love Updates!

---

### Post by D3ath on 2009-03-17
> **suomalainen said:**
> Wow.... So really excellent feedback!!! Thanks everyone.


But if I understood running both:

1. sudo apt-get install ubuntu-restricted-extras
2. [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)


Is the best thing to do????? Just confirming...

O Yea!

---

### Post by cirabisi2009 on 2009-03-17
> **mocoloco said:**
> 

Eyecandy:
Install extra backgrounds & themes, and card styles for card games
```
sudo apt-get install gnome-backgrounds ubuntustudio-wallpapers gnome-themes-extra gnome-games-extra-data
```


yep def. didnt work for some reason.. said couldnt read package list's or something or other!! 

can you give me a code or a place to download a full package to turn ubuntu into a mac os x theme? icons and everything PA LEASE!!!! thanx!!!!

---

### Post by Therion on 2009-03-17
> **cirabisi2009 said:**
> can you give me a code or a place to download a full package to turn ubuntu into a mac os x theme? icons and everything PA LEASE!!!! thanx!!!!
Go here:  [http://www.gnome-look.org/](http://www.gnome-look.org/)

Search on Mac or OSX or whatever... Making Ubuntu look like a Mac OS is very popular.  There are plenty of mac look-alike themes, wallpapers, GDM's and icon packs.

I'm sure you'll be able to find a theme that satisfies.

---

### Post by stchman on 2009-03-17
> **suomalainen said:**
> Ubunteros,

I wanted to get some ideas as to the important things to do after a fresh install of Ubuntu 8.04LTS is completed.

A few that come to mind are:

1) install restricted drivers
2) Get multi media to work
3) install favorite programs from Synaptic

Do you have any other ideas? Any how-to's and web links would be welcomed.

Thank you!

Run my script.

[http://www.stchman.com/install_scripts.html](http://www.stchman.com/install_scripts.html)

Has pretty much everything you need.

---

### Post by BDNiner on 2009-03-17
LOL xpod and D3ath. She fell in love with the idea of a NAS to backup her huge collection of pictures and music. I am trying to convince that for the same price I can put together another computer that will do that same plus much more. 

Funny how all the stuff i learnt in marketing classes in college only applies to convincing her to let me get another computer. Even funnier how i have to get permission to get another computer. 

Back to the original topic. It is hard to stay satisfied with your linux machine. My windows box has stayed the same for almost 4 years now. Not even a reinstall. There are so many packages to try in linux and the fun is getting them to work exactly how you want them to.

---

### Post by blueridgedog on 2009-03-17
Here is my latest install:

[http://ubuntuforums.org/showthread.php?t=1023832](http://ubuntuforums.org/showthread.php?t=1023832)

---

### Post by D3ath on 2009-03-17
> **BDNiner said:**
> LOL xpod and D3ath. She fell in love with the idea of a NAS to backup her huge collection of pictures and music. I am trying to convince that for the same price I can put together another computer that will do that same plus much more. 

Funny how all the stuff i learnt in marketing classes in college only applies to convincing her to let me get another computer. Even funnier how i have to get permission to get another computer. 

Back to the original topic. It is hard to stay satisfied with your linux machine. My windows box has stayed the same for almost 4 years now. Not even a reinstall. There are so many packages to try in linux and the fun is getting them to work exactly how you want them to.

Figures I was told that I could not have three computers and a file/ftp server. Long story short I broke up with her. She is just a girl. Linux has given me much more hours of enjoyment then her. 

Back on track I do like dark themes alot. but I'm designer and trying to edit a gtk theme for my needs is too much.  It would be alot easier to make a theme where the text input boxes are not black on black.  Along with drop downs or other things alog those lines. Because darker themes are better for your  eyes and make you look cool too!

---

### Post by shinoj on 2009-03-18
Hey, i always go for installing some of my favourite fonts. Book antiqa and book man old. The second thing would be installing the restricted extras.

---

### Post by blueridgedog on 2009-03-18
> **D3ath said:**
> Figures I was told that I could not have three computers and a file/ftp server. Long story short I broke up with her. She is just a girl. Linux has given me much more hours of enjoyment then her. 



Now that man is dedicated to Linux!

---

### Post by D3ath on 2009-03-18
> **blueridgedog said:**
> Now that man is dedicated to Linux!

Hell Yea!

---

### Post by mocoloco on 2009-03-19
> **blueridgedog said:**
> Now that man is dedicated to Linux!

I would guess that D3ath did a comparison of Linux vs the relationship.  On factors like stability or security from virus infection, as well as maintenance and upgrade costs Linux always wins.
Plus we are talking about a free/open platform vs a proprietary one that no one really understands.

---

### Post by D3ath on 2009-03-19
> **mocoloco said:**
> I would guess that D3ath did a comparison of Linux vs the relationship.  On factors like stability or security from virus infection, as well as maintenance and upgrade costs Linux always wins.
Plus we are talking about a free/open platform vs a proprietary one that no one really understands.
Yes actually. Had a few pie charts and showed her exactly why we could be together anymore. I feel much more secure knowing that linux will not give me a virus and in today's age females have a redundant source of viruses.(There is no protecting from that, Norton or system recovery). In a relationship the cost and maintenance fees are outrageous!  I was willing to put up with it until she said I couldn't have my computers! There is not a person in this world that will take away the one thing that takes me away from all the proprietary BS we live in. Free movies, friends, music, and entertainment is the way to go. For all those reasons is my i love linux so much. Never again will I fall for some dumbass female with a nice body and perfect breast. I have faith that linux will build me one! Open Source 4 Life!

Now on to find a chick that actually knows what I'm talking about.  Any of you girls out there!?@:(

---

### Post by DonaldJ on 2009-03-19
[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

___________________________________________________________

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

___________________________________________________________


Firewall and AVS...

Synaptic Manager>Search for>Clam

Then search for Firestarter...

___________________________________________________________


Hydrogen   (drum machine)  plus Hydrogen drumkits...

___________________________________________________________


SeaMonkey

___________________________________________________________


Gimp extras

___________________________________________________________


Language Translator

___________________________________________________________


 Reboot before you run any cleaners or backups...

---

### Post by sp176 on 2009-03-19
> **D3ath said:**
> One command i always do first thing
```
sudo apt-get install ubuntu-restricted-extras
```

that's it everything i need. Flash, Java, Fonts, and different dvd and video formats as well as audio!

I tried this and it failed for me.  As soon as java was installed a new screen opened in terminal showing the user agreement, and all the other installations stopped.  Now I cannot continue in terminal or open up package manager.

The response I get when trying to run this again:

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

Nevermind, figured it out.  I restarted and ran:
sudo dpkg --configure -a
then I went back to synaptic and fixed my broken d/ls

---

### Post by D3ath on 2009-03-19
> **sp176 said:**
> I tried this and it failed for me.  As soon as java was installed a new screen opened in terminal showing the user agreement, and all the other installations stopped.  Now I cannot continue in terminal or open up package manager.

The response I get when trying to run this again:

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

Need to say ok to the Java. Maybe that is were something messed up. Run this:
```
top
```

copy what you see for your user here.  This will show the PIDs for what running and see if something is running that shouldn't be.

PS. I install
```
htop
```
it works really nice top or htop but you have to install htop! Let me know what you come up with!

---

### Post by UnknownFear on 2009-03-19
Well, I just installed a fresh copy of Ubuntu 8.10, and at the moment I am installing all the updates, than I'm going to install all the restricted drivers, like my video card. Next, I'll install sound, and some apps, codecs, and anything else. Than I'll FINALLY be set up :)

---

### Post by D3ath on 2009-03-19
> **UnknownFear said:**
> Well, I just installed a fresh copy of Ubuntu 8.10, and at the moment I am installing all the updates, than I'm going to install all the restricted drivers, like my video card. Next, I'll install sound, and some apps, codecs, and anything else. Than I'll FINALLY be set up :)

I'm happy knowing that your happy. Linux makes me happy! That's the first thing i install.

```
sudo apt-get install smile!
```

---

### Post by DonaldJ on 2009-03-19
I think the Java install screws-up if you fail to agree to the contract while it's installing and configuring...  Maybe try reinstalling Java..  and this time click the OK's...  That install needs to be babysat...

Or maybe a reboot will bring-up some info on it.. or maybe try to bring it up on the screen...

---

### Post by oldos2er on 2009-03-19
The Java EULA can't be clicked, you need to use Tab, then Enter.

---

### Post by davo11 on 2009-03-19
download wine it is very useful for running most windows execs.
as long as they are not a file deleting program/one that needs windows files specifically

---

### Post by suomalainen on 2009-03-19
Man.... You all are die hard Ubuntu users as I can tell.. I'm sure people reading this post will learn quite a few GOOOD tib-bits from all of You!!!....

P.S. is it my imagination or was the "Thank You" option removed? If so, why????

---

### Post by jlochhead on 2009-03-19
Change /boot/grub/menu.1st to your preference.

In preferences > sessions uncheck anything you do not use.

Install BootUp Manager (BUM in Synaptic) and uncheck anything you do not want to load at start-up. For example, I would uncheck bluetooth and cups.

---

### Post by peyre on 2009-03-19
> **suomalainen said:**
> Ubunteros,

I wanted to get some ideas as to the important things to do after a fresh install of Ubuntu 8.04LTS is completed.

A few that come to mind are:

1) install restricted drivers
2) Get multi media to work
3) install favorite programs from Synaptic

Do you have any other ideas? Any how-to's and web links would be welcomed.

Thank you!

Restore your data, of course.  Don't know if that's a "goes without saying" kinda thing though...

---

### Post by DonaldJ on 2009-03-19
I think Wine has a lot of good to it, but it also has a few dangers..  in that it might open ones hd up to potential Windows attacks, IF one has enemies on the Internet... 

Wine might even make ones hd susceptible to damage from bad websites...

I find that everything I need Wine for, Ubuntu and OpenSource has to offer...
But if you must run a Windows program in Ubuntu, then you probably need Wine...

---

### Post by mocoloco on 2009-03-20
> **suomalainen said:**
> P.S. is it my imagination or was the "Thank You" option removed? If so, why????

Yes, both the thank you and the solved options were removed unfortunately. They had some issues and had to disable them, but hope to turn them back on at some point. [Details here]("http://ubuntuforums.org/showthread.php?t=1044714").

---

### Post by suomalainen on 2009-03-20
Anyone know when we are having our spring break party?

---

### Post by DonaldJ on 2009-03-20
Probably in the spring...

---

### Post by Ms_Angel_D on 2009-03-20
I created a whole post on what I do after a fresh install in my blog [HERE]("http://www.thedallemagnes.info/index.php?option=com_content&task=view&id=203&Itemid=38")

---

### Post by markbuntu on 2009-03-20
First things first and the first thing I need after a fresh install is my sound all dialed in.

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by UnknownFear on 2009-11-13
> **D3ath said:**
> Yes actually. Had a few pie charts and showed her exactly why we could be together anymore. I feel much more secure knowing that linux will not give me a virus and in today's age females have a redundant source of viruses.(There is no protecting from that, Norton or system recovery). In a relationship the cost and maintenance fees are outrageous!  I was willing to put up with it until she said I couldn't have my computers! There is not a person in this world that will take away the one thing that takes me away from all the proprietary BS we live in. Free movies, friends, music, and entertainment is the way to go. For all those reasons is my i love linux so much. Never again will I fall for some dumbass female with a nice body and perfect breast. I have faith that linux will build me one! Open Source 4 Life!

Please tell me you're ******* joking...

---

### Post by pedja_portugalac on 2009-11-13
```
$ sudo apt-get update
    1  sudo ufw enable
    2  cd Desktop/
    3  sudo mv Gino.jpg /usr/share/backgrounds/
    4  cd Desktop/
    5  sudo /etc/init.d/gdm stop
    6  sudo ./NVIDIA-Linux-x86-190.42-pkg1.run 
    7  sudo /etc/init.d/gdm start
    8  alsamixer 
    9  cd Desktop/
   10  mplayer David.Haye.vs.Nikolai\ Valuev.07.Nov.2009.WS.x264-BigBossMan.avi
```
:D

---

### Post by the8thstar on 2009-11-13
ubuntu tweak...

---

### Post by patond on 2009-11-13
I always search for "Comprehensive Multimedia and Video Howto" in Forums and this gives scripts and advice to install Flash, Java, Mplayer etc along with all necessary repositories.

---

### Post by aysiu on 2009-11-13
This thread is super old.

---

