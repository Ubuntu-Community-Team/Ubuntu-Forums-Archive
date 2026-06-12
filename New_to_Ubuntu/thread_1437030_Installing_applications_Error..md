---
title: "Installing applications Error."
date: 2010-03-23
forum: New to Ubuntu
---

### Post by sinhanikhil.5 on 2010-03-23
[B]Now its third of using Ubuntu and now I am pretty satisfied, not to the core so i give up windows completely.
I am trying to install few applications like for example we take i tunes, the following is the error message i am getting for all applications i am trying to install.

An error occured while loading the archive
command line output
Archive:  /media/CAD0718AD0717D8F/Users/Musician/iTunesSetup.exe
[/media/CAD0718AD0717D8F/Users/Musician/iTunesSetup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/CAD0718AD0717D8F/Users/Musician/iTunesSetup.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/CAD0718AD0717D8F/Users/Musician/iTunesSetup.exe or
          /media/CAD0718AD0717D8F/Users/Musician/iTunesSetup.exe.zip, and cannot find /media/CAD0718AD0717D8F/Users/Musician/iTunesSetup.exe.ZIP, period.

I am struck.
feedback welcomed.



[COLOR=White].[/COLOR] [/B]

---

### Post by Paqman on 2010-03-23
That copy of Itunes is a Windows app. Generally speaking, you can't install Windows apps on Linux.

There is an exception to this rule, a compatibility layer called Wine, but it's very hit-and-miss and if you're new it'll probably save you a lot of anguish to simply use one of the many excellent Linux apps that do the same job as Itunes.

What was it about Itunes that you most wanted to use it for?

---

### Post by Calash on 2010-03-23
Here is the Wine db entry on iTunes

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)


Are you trying to install this using Wine?

---

### Post by sinhanikhil.5 on 2010-03-23
To upload songs in  my i pod. by the way its i tunes 9. and also its giving same error for other applications. :(



 [COLOR=White].[/COLOR]

---

### Post by drpjkurian on 2010-03-23
Hi
Any programmes with the file** setup.exe** cannot be installed in Linux
Those are windows setup files

Well try this link for installing your itunes
[http://www.ehow.com/how_5197743_download-itunes-linux-ubuntu.html](http://www.ehow.com/how_5197743_download-itunes-linux-ubuntu.html)

---

### Post by sinhanikhil.5 on 2010-03-23
It looks like i need to d/l wines 1st using terminal, and using wine i can install windows .exe applications in any linux os.
Ok let me try..


[COLOR=White].[/COLOR]

---

### Post by sinhanikhil.5 on 2010-03-23
i used following command to install wines as per the website:-
sudo dpkg -i wine_0.9.45~winehq0~ubuntu~7.04-1_i386.deb
and i got following response:-
-bash: wine_0.9.45~winehq0~ubuntu~7.04-1_i386.deb: command not found



[COLOR=White].[/COLOR]

---

### Post by drpjkurian on 2010-03-23
> **sinhanikhil.5 said:**
> It looks like i need to d/l wines 1st using terminal, and using wine i can install windows .exe applications in any linux os.
Ok let me try..


[COLOR=White].[/COLOR]

Yep
Wine is a windows emulator. It may give you some snags as mentioned in first post..

---

### Post by sinhanikhil.5 on 2010-03-23
> **Calash said:**
> Here is the Wine db entry on iTunes

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)


Are you trying to install this using Wine?
its giving me option to install itune 7, can i not get the higher version.




.

---

### Post by sinhanikhil.5 on 2010-03-23
> **drpjkurian said:**
> Yep
Wine is a windows emulator. It may give you some snags as mentioned in first post..
can u help me d/l wine using terminal commands..



.

---

### Post by Paqman on 2010-03-23
> **sinhanikhil.5 said:**
> To upload songs in  my i pod.
 [COLOR=White].[/COLOR]

If it's a regular Ipod (ie: not a Touch) then any of the normal Linux music players will do that. The defaults are Rythmbox and Amarok (Gnome/KDE respectively), but other options include Banshee, Exaile and Songbird.

The only thing you actually need Itunes for is connecting to the Itunes music store, but there's plenty of other options like Amazon or Ubuntu's new integrated music store coming out in a few weeks.

---

### Post by sinhanikhil.5 on 2010-03-23
Thank you all for ur valuable feedback.
Well itunes is just an example i have used i want to install many other .exe application.
Now i have installed wine microsoft windows compatibility layer (beta release) through Uduntu software centre and also itune 7.2 .exe, so my question is now how can i install itune in ubuntu using wine???

---

### Post by Calash on 2010-03-23
First. a reality check.

While Wine does a wonderful job there is an inherant instability that comes from running Windows apps in Linux.  Quite simply they are not designed to run.

Using Wine you may, and I must stress may, be able to get your required windows applications running.  It is also likely that you will not be able to.

Please keep this in mind as you move forward.  I am stressing the negative only to make sure the point is understood.

If you have Wine installed from the Software Center then you are in good shape to try iTunes.  Go back to your CD and try the installer again.  If you run into issues the link I posted may have some additional adjustment you will need to get this working.


As noted, if all you are interested in is music Rythembox will sync your music with your iPod.  You may be able to find additional replacements for your Windows apps in Ubuntu.

---

### Post by philinux on 2010-03-23
> **sinhanikhil.5 said:**
> i used following command to install wines as per the website:-
sudo dpkg -i wine_0.9.45~winehq0~ubuntu~7.04-1_i386.deb
and i got following response:-
-bash: wine_0.9.45~winehq0~ubuntu~7.04-1_i386.deb: command not found
[COLOR=White].[/COLOR]

Easier to install wine from the software centre or synaptic.

Or even easier click this link. [wine]("apt:wine1.2")

---

### Post by halitech on 2010-03-23
> **sinhanikhil.5 said:**
> Thank you all for ur valuable feedback.
Well itunes is just an example i have used i want to install many other .exe application.


Excuse me for being blunt but are you looking for a free windows replacement or do you actually want to learn how to use Linux? .exe's are Windows programs and installers and Windows apps are designed for *gasp* WINDOWS! If you want to run Windows programs, run Windows as your OS, not Linux. If you are not stuck on Windows programs, look into native apps that will do what you want to do.

---

### Post by sinhanikhil.5 on 2010-03-23
Thanks all for there help.

Its finally done. I installed i tune thro wines.
I really want to learn Linux and to install windows program in linux is just a part of my learning, sorry if i really acted dumb.
Sorry for late reply, i slept off.;)


[COLOR=White].[/COLOR]

---

### Post by halitech on 2010-03-23
> **sinhanikhil.5 said:**
> 
I really want to learn Linux and to install windows program in linux is just a part of my learning, sorry if i really acted dumb.


If you honestly want to learn how to use Linux, don't rely on Windows programs running unreliably through WINE and learn how to use the native apps that are available. Honestly, I've been using Linux for over 4 years now and there was 1 app I installed in WINE and it ran so horribly that I swore I would only run native apps. I won't say I'm an expert by any stretch but the best way to learn how to use Ubuntu is by actually using it and using the apps that come with it and drop the "Windows mindset"

---

