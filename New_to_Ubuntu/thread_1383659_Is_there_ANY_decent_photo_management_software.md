---
title: "Is there ANY decent photo management software?"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by cjnkns on 2010-01-17
First, I can not stand Picasa on Linux. Anything under wine looks like total garbage in my opinion.

Having said that - is there any decent photo management software for Linux? I have been looking around and just can't seem to find anything. 

I tried blueMarine today, but it's kinda of slow and just didn't' work correctly. Menus popped up in incorrect places etc...

F-Spot took ALL DAY yesterday just to load my photos. That is just ridiculous.

I run Gnome and I had thought of digiKam, but I hate to pollute my OS.

It's funny that the open source community can create such great software like Blender, but photo management seems to be a red headed step child....

---

### Post by Roger Allott on 2010-01-17
90% of GIMP is superb.

Unfortunately, the 10% that isn't is the user interface.

---

### Post by Sef on 2010-01-17
> F-Spot took ALL DAY yesterday just to load my photos. 

Are you running a 32-bit system?  If so, and if you can install a 64-bit system, downloading photos will be much faster.  I had a friend for who I download his photos because I had a 64-bit system with 2 gb ram.  Took me 20 minutes to download 400 photos.

---

### Post by mk1w86 on 2010-01-17
You could try gThumb which can be used as a basic photo manager. :D

---

### Post by John Bean on 2010-01-17
> **cjnkns said:**
> I run Gnome and I had thought of digiKam, but I hate to pollute my OS.

DigiKam does the job, I'm not a purist so to be honest I couldn't care less about the "pollution" of GNOME by all the dastardly KDE bits that get sucked in - I simply ignore them, they do no harm.

---

### Post by cjnkns on 2010-01-17
> Are you running a 32-bit system? If so, and if you can install a 64-bit system, downloading photos will be much faster. I had a friend for who I download his photos because I had a 64-bit system with 2 gb ram. Took me 20 minutes to download 400 photos.

I am running a 32bit system with 2GB of memory. Unfortunately, it's a 32 bit lappy so 64bit is out of the question for me.

---

### Post by Marlonsm on 2010-01-17
I use KDE's Kdenlive and it works very well for me, all I miss in it is being able to change brightness/contrast, but I can use GIMP for it.

---

### Post by mgmiller on 2010-01-17
> First, I can not stand Picasa on Linux. Anything under wine looks like total garbage in my opinion.

I have been using picasa for linux for years and love it.  If it looks like "garbage" to you, I suspect you are not installing/configuring it correctly.

First off, install it by adding the picasa repositories to synaptic, so it stays up to date and installs its own optimized wine.  Do not try to install wine and then install the picasa for windows version.  

There is also a .deb version, but that doesn't stay up to date.  Do it "the right way" by adding the repo.

Then, after it's installed, use picasa's font tool to tweak the fonts so they look good on your system.

I am now using picasa v. 3.0 and it is fast and looks fabulous.

Get more info here:

[http://picasa.google.com/linux/download.html#picasa30](http://picasa.google.com/linux/download.html#picasa30)

---

### Post by cjnkns on 2010-01-17
> I have been using picasa for linux for years and love it. If it looks like "garbage" to you, I suspect you are not installing/configuring it correctly.

First off, install it by adding the picasa repositories to synaptic, so it stays up to date and installs its own optimized wine. Do not try to install wine and then install the picasa for windows version. 

There is also a .deb version, but that doesn't stay up to date. Do it "the right way" by adding the repo.

Then, after it's installed, use picasa's font tool to tweak the fonts so they look good on your system.

I am now using picasa v. 3.0 and it is fast and looks fabulous.

Get more info here:

[http://picasa.google.com/linux/download.html#picasa30](http://picasa.google.com/linux/download.html#picasa30)

Thanks for your reply.

I have Picasa 3 installed from the google testing repos.
After toying with the font settings for picasa (maybe it's just me) the menus just do not look good to me.

Even opening the folder manager - for example the dialogs look crummy.
It might not be a big deal to some, but what is the use of having a GUI if it just looks like garbage? 

I installed digiKam and that seems like a really nice photo manager. I might have to give KDE a try it seem to have better tools (I know they can be run on gnome, but I guess I am a purist) than Gnome.

---

### Post by oldfred on 2010-01-17
I installed picasa 3.6 with winetricks and the extra fonts and cannot tell the difference.

I installed the standard wine with karmic then from my history:
                                       [LEFT]  114  wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)[/LEFT]
    [LEFT]  115  sudo wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)[/LEFT]
    [LEFT]  116  sudo chmod 777 winetricks[/LEFT]
    [LEFT]  117  sudo apt-get install cabextract wine wine-gecko[/LEFT]
    [LEFT]  118  winetricks allfonts fontsmooth-rgb gecko allfonts[/LEFT]
    [LEFT]Then download picasa for windows
[http://dl.google.com/picasa/picasa36-setup.exe](http://dl.google.com/picasa/picasa36-setup.exe)
 
 run it, and the installer should start.[/LEFT]
    [LEFT]I had to rename to picasa and move to wine programs from the download location to get it to run.
[/LEFT]

---

### Post by ChadMMc on 2010-01-17
Actually I had been using f-spot while I was still in Jaunty... I felt the tagging system they had in there was very flexible and powerful.  It never took me all that long to import new sets of photos (usually about 200 at a time) ... and it does keep logs of all import rolls.

After going to karmic though, the import and most of the tools just plain stopped working (f-spot would close down immediately), So had switched back over to digikam (I don't worry about kde in the gnome) ... It's tagging system is not nearly as good and also I don't like having to go into different dialogues just to do something, but it is still usable.

Note: I have it go to showfoto (part of digikam) for editing.

---

