---
title: "can't load Lubuntu after &quot;Additional Drivers&quot; for Nvidia card installed"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by ~Maxx on 2011-01-11
Hey everyone.  I may or may not have made an error in judgment here.  I haven't had Lubuntu up and running for too terribly long - so I've been slowly tweaking things as I have time.  This week I decided to attempt to get my graphics card running to its full potential (or as much so as possible anyway).  so I selected "Additional Drivers" in the menu, and waited to see what the applet came up with.  Two drivers for my Nvidia card came up.  I don't recall what the first one was, but the second one was labeled as "current".  I downloaded, installed, and rebooted - and now I have only a blank screen.  I was suspicious that the refresh rate was screwy since I can see the screen flicker between different shades of black here and there, but I can't access anything to check it.  I can enter commands by hitting Cntrl+Alt+F1, but I have no idea where to go from there.  I'd really hate to have to reinstall, as I've put quite a bit of time into configuring things.  Is there a way to uninstall or fix these drivers?

I'm using Lubuntu 10.10 with a Nvidia GEForce 6200 dual head graphics card that includes an S-video out.  My goal is to get the S-vid working for my TV (probably at 800x600 resolution), and set my PC monitor as the primary with 1440x900 res.  I've come across a few things concerning this via Google search, but they are all geared toward Ubuntu, and I hesitate to try anything as I've come across several instances where Lubuntu differs from Ubuntu and requires extra steps, etc...

At any rate, if someone could at least help me get back to my previous settings I'd be very grateful.  From there I can experiment (more cautiously of course) with how to get my graphics card set up properly.  Thanks in advance...

---

### Post by SteveDee on 2011-01-12
You could try looking for an /etc/X11/xorg.conf file. If one has been created when you installed the driver, try to rename it (say to "xorg.bad") and reboot.

Basically xorg.conf is not required (on 10.10) except for customised settings. Hopefully renaming it (if you have one) will allow the system to start x normally (...sorry this reply is rushed...got to go to work...)

---

### Post by ~Maxx on 2011-01-12
Thanks Steve.  I was headed to work myself when I made my last post :)  

Pardon the noob question, but how do I go about searching for that file in the command line?  I tried following some suggestions that worked for another fellow on the forum recently at the post here -->  [http://ubuntuforums.org/showthread.php?t=1663339&page=2](http://ubuntuforums.org/showthread.php?t=1663339&page=2)

But that didn't seem to help matters.  When I typed in the command "sudo service gdm stop" it gave me an error message stating that gdm was not found.  I tried to follow the rest of the steps (searching out the driver and deleting it followed by installing the driver directly from Nvidia), but still have the same issue.

Something else I noticed...  When I'm in the command screen (alt+F1) it still blacks out every few seconds, and won't accept anything from the keyboard until I hit alt+F1 again.

Sorry to be so uneducated.  But I guess this is how one learns :)

---

### Post by SteveDee on 2011-01-12
OK, from the command line:-
```

cd /etc/X11

```
...this should put you in the correct directory
```

ls

```
...this should list all the files in this folder.
If is shows "xorg.conf" you should rename it:-
```

sudo mv xorg.conf xorg.bad

```
...you should use "ls" again to check that your change was successful.

Now reboot and see what happens!

Note: everything in the command line is case sensitive.

If this does not help, you can always reverse the process...but I hope it does help!

---

### Post by ~Maxx on 2011-01-13
Sorry I didn't get back to this right away.  Had to deal with a frozen water main.  The wife seems to think that being able to shower and wash dishes is more important than the living room computer.  :confused::P

Anyway...  Your fix has worked Steve!  I can now access my desktop!  The obvious problem is that I still can't edit my display settings.  It seems that after following the steps referenced in my last post I've now got the Nvidia X Server software installed.  But when I open it I end up with an error pointing out that I am not running the Nvidia x driver (probably because I renamed xorg.conf?) and that I should edit x configuration.  I tried that just to see what happened (according to the error msg:  sudo nvidia-xconfig), but it recreated the xorg.conf file and put me back at square one.  

So would anyone know how to install the Nvidia driver without causing these problems?  Again - any help is very much appreciated.

---

### Post by SteveDee on 2011-01-13
> **~Maxx said:**
> ....Had to deal with a frozen water main....Anyway...  Your fix has worked Steve!

Glad to see it recovered your desktop, sorry I can't help with the frozen pipe!

I did have a desktop configured as you describe, using an nvidia card and linked to our TV (I now have an old dedicated computer running Lubuntu, connected to the TV & stereo, used as a juke-box and video player). But the original config ran on Ubuntu, not Lubuntu.

One thing to consider about the 'buntu family is that distributions like Ubuntu, Lubuntu, Kubuntu & so on and really just 'buntu templates, or starting points from which you can either add or remove packages to suit your needs.

Given your plans and the spec of your equipment, I would recommend that you start with Ubuntu rather than Lubuntu. I think you will need more built-in support including "nvidia-settings" and probably many more packages. Once you get it running on Ubuntu you could always cut the system down a bit, install LXDE & so on. Good luck...

---

### Post by ~Maxx on 2011-01-13
> **SteveDee said:**
> ...sorry I can't help with the frozen pipe!It's all taken care of Steve.  Just took a few hours freezing my tush off underneath our house.:)

> **SteveDee said:**
> Given your plans and the spec of your equipment, I would recommend that you start with Ubuntu rather than Lubuntu. I think you will need more built-in support including "nvidia-settings" and probably many more packages. Once you get it running on Ubuntu you could always cut the system down a bit, install LXDE & so on. Good luck...
That thought had crossed my mind a couple of weeks ago.  Especially given that it seems to be much easier to find Ubuntu "how to's" than Lubuntu.  However this PC is fairly ancient (Pentium II/400MHZ).  I did have Xubuntu running on it a couple of years ago, but it was pretty sluggish compared to Lubuntu.  I'm not sure what is most responsible for Lubuntu's speed on older systems (LXDE?), but I suppose it's worth a try to install Ubuntu and add/subtract from there.  I think I'll set up a dual boot system for now and keep my current config so the wife can continue to use it.  Once I get Ubuntu tweaked I can cut the cord and wipe Lubuntu.  It so happens that I made an Ubuntu 10.10 CD when I installed Lubuntu, but I assumed that Ubuntu wouldn't even install on such a low-spec PC.  Guess I'll give it a try and see what happens...

Thanks again Steve for all your help!

---

### Post by SteveDee on 2011-01-14
> **~Maxx said:**
> ...However this PC is fairly ancient (Pentium II/400MHZ)....

Sorry Maxx, I'd assumed you had a more powerful PC (more in line with your graphics card) so I see why you started with Lubuntu.

I think Lubuntu is great, especially on my fleet of low power machines (cpu: 1.2-1.7GHz, approx 500MB RAM). But you have a tougher challenge if you hope to create a usable desktop machine that (presumably) will also drive the TV. You might also wish to consider what you will be using the TV display for.

I think you will need to end up with a pretty minimal install. The trick is to find the components/packages that you need to run it. If your system will temporarily run with Ubuntu, I think this gives you the best chance of discovering which packages you need to get your dual display running. You can then create a package list like this:-
```

~$ dpkg --get-selections > /home/maxx/Packages.txt

```
...then return to Lubuntu, create a similar list, and start the slow process of comparison.

The alternative is just to concentrate on your existing Lubuntu installation. If you go to Synaptic and search for "nvidia" your list will include 30-40 packages. You could try installing the obvious ones (nvidia-common, nvidia-settings, nvidia-96-###, nvidia-173-###, & so on) and see what happens.

If you & Mrs Maxx rely on this machine, I'd also suggest you download a copy of Clonezilla, make a CD, and create an image of your (currently working) hard disk, so you can quickly restore your system if something goes badly wrong.

***This is something anyone installing 'Buntu alongside Windows should do if they rely on Windows (I know!  ...hard to believe people actually rely on Windows!)***

Getting back to the performance issue, for a low spec machine you need an OS that "ticks over" with a low cpu usage. Ubuntu (with Gnome) not only creates a much higher cpu load when its doing "nothing" but the cpu% seems to cycle from moderate to high. Lubuntu does not have so many background processes running. You may have noticed that the Quick Search function in Synaptic (on Lubuntu) does not work. I think this is because the Xapian search engine is not installed, and this is one of the processes that keeps sucking the life out of the cpu on Ubuntu.

And finally, an alternative to Lubuntu is to start with the minimal install (see [http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)) and add exactly what you need (you need a lot of spare time for this!). LXDE, or one of the other lite desktop environments, would be a better choice for you than Gnome or KDE.

I hope some of this rambling helps.

---

### Post by elgordodude on 2011-01-14
```
I hope some of this rambling helps.
```

That is some awesome rambling on low-power machines. For the record, I found ubuntu a little too heavy for my lightest-weight, a 1.0ghz PIII coppermine. I ended up having to go with puppyLinux, and from what I read setting it up, DSL was a valid option, but puppy got it done.

[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

What graphics card are you running? A PII will have trouble keeping up with a high end card.

---

### Post by SteveDee on 2011-01-14
Maxx, I don't know if this is helpful or worse-than-useless, but one of my 12 computers has a GeForce 7300 graphics card, running on Ubuntu 10.04. Attached is the list of installed packages and the xorg.conf file.

In addition to the packages that include "nvidia" it looks like those containing the word "nouveau" are also important.

PuppyLinux; yes, I like it, I have it on a memory stick, but I don't understand it!

---

### Post by ~Maxx on 2011-01-14
Wow...  Thanks a bunch for all the info!  I was feeling a bit impetuous after work this morning, so I went ahead and wiped my system drive on the Compaq (the one with the Pent. II) and installed Ubuntu 10.10.  Looking back at some of my older posts I was reminded that I did have Ubuntu on this machine (a couple of years ago), and then installed xfce over the top.  It was all fairly sluggish, but I only had 128 or 256 MB RAM at the time.  I'm maxed out now, so hopefully that will help a bit.  

This is a secondary "living room" PC for us, by the way.  So we don't really rely on it.  I have a "better" WinXP box in our office that I use for light audio production and most of our general use (another Compaq - 6430nx, 2.13GHz Athalon w/ 2 Gigs RAM).  My goals for the older pc include music server, slide show viewer, and web surfing.  I'm half hoping to get Skype working on it as well (our folks live out of state and like watching their grandbaby run around the living room :)).  I've got a USB 2.0 PCI card that I thought might help in that regard.  But we'll see.  I could probably live without integrating the TV, but it makes browsing pictures with family so much better, and the wife likes the visual eye-candy thingies that the music players have (shameful waste of resources if you ask me :confused:)

Anyway (*now *who's rambling? :p)...  I'll play around with all this a bit later.  Ubuntu is installed, and that sounds like my first step toward getting things straightened out.  Should I go ahead and install the additional drivers?  Change to LXDE?  I think this may deserve a new thread.  We'll see what I run into along the way.  Oh - elgordodude - my graphics card is Nvidia GEForce 6200 dual head.  Not new by any means.  But made for better PC's.  It worked great in my office PC for many years.  But I saw a better use for the svideo out by moving it to the living room PC.

---

### Post by ~Maxx on 2011-01-14
oops

---

### Post by ~Maxx on 2011-01-14
oops

---

### Post by ~Maxx on 2011-01-14
oops

---

### Post by ~Maxx on 2011-01-14
oops

---

### Post by ~Maxx on 2011-01-14
oops

---

### Post by ~Maxx on 2011-01-14
Six - count 'em -SIX accidental posts!  I am in rare form today. :)

Sorry.

---

