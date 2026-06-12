---
title: "wine..!!!###???????"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by vivek.pandey on 2010-12-04
i installed wine using first sudo apt..and then using software package of ubuntu..each time same problem i am unable to install any windows software using it..it just displays error msg saying the software cannot be trusted as it has not been downloaded from ubuntu's software package....plssss pllss somebody suggest a solution i just wanna quit windows,,only i need wine then bye bye windows

---

### Post by Locke_99GS on 2010-12-04
```

wine --version

```

To make sure wine installed correctly.

You should be able to double click on a .exe or .msi in Nautilus and it should attempt to run it via WINE. If this does not work, right-slick on the file and have it "Open with WINE".

You don't install Windows applications in Software Centre - there should be no "trust" messages displayed.

---

### Post by vivek.pandey on 2010-12-04
but i wanna install some windows software like some downloader accelerators..i tried to open it with wine but THE ERROR MSG.. wats the exact prob with wine is it related to its compatibility with ubuntu

---

### Post by NightwishFan on 2010-12-04
Right click on the .exe, click "properties", go to the permissions tab, check "allow executing file as program". Ubuntu is not Windows, and you should not rely on Wine working properly. (It does at times)

---

### Post by ikt on 2010-12-04
> **neo_aryan said:**
> but i wanna install some windows software like some downloader accelerators..

Why not use Axel?

I just searched for "download acce" in the ubuntu software centre and it came up.

My point is try to look for linux equivalents first before using wine, I don't try and run windows applications on my android phone etc

---

### Post by vivek.pandey on 2010-12-04
> **ikt said:**
> Why not use Axel?

I just searched for "download acce" in the ubuntu software centre and it came up.

My point is try to look for linux equivalents first before using wine, I don't try and run windows applications on my android phone etc

but wat about video downloaders.. i downoad youtube videos using youtube-dl but i need to download videos from other sites too.. i have download toolbar plus speedbit downloader in windows wich makes downloading pretty easy n fast

---

### Post by Spyderkid on 2010-12-04
right click on properties then click on permissions, then click the "allow executing file as a program"


listen to the people with the most beans like nightwishfan

---

### Post by uriel1998 on 2010-12-04
> **neo_aryan said:**
> but wat about video downloaders.. i downoad youtube videos using youtube-dl but i need to download videos from other sites too.. i have download toolbar plus speedbit downloader in windows wich makes downloading pretty easy n fast

Since you'd need to have legal rights to the videos, you must already have your own copies, right?  Or are these ones you bought?  ;)

Seriously, there's lots of ways to do all the things you did in Windows just as easily.  Insisting that you do them the SAME way all the time is going to frustrate you.  Some programs work great WINE (notepad++).  Some programs will do horrible things and corrupt your data under WINE.

---

### Post by rburkartjo on 2010-12-04
neo it is just that linux is not windows.  i do also use a couple of windows programs but not many. here is a link that you may find useful 
linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software
 [http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)

---

### Post by Penguin=) on 2010-12-04
type this in terminal ```
wine --version
```

---

### Post by oldos2er on 2010-12-04
Before attempting to install any Windows app, I'd check [http://appdb.winehq.org/](http://appdb.winehq.org/) to see if it has a chance of working.

---

### Post by bug67 on 2010-12-04
Downloading videos from YouTube can be accomplished quite nicely via the Flashgot Firefox add-on.  No need for Windows programs running in Wine to do it.

---

### Post by vivek.pandey on 2010-12-05
> **uriel1998 said:**
> Since you'd need to have legal rights to the videos, you must already have your own copies, right?  Or are these ones you bought?  ;)

Seriously, there's lots of ways to do all the things you did in Windows just as easily.  Insisting that you do them the SAME way all the time is going to frustrate you.  Some programs work great WINE (notepad++).  Some programs will do horrible things and corrupt your data under WINE.
but in windows i have a toolbar for speedbit... i just need to click on download option in the toolbar to download any video being played on any website....i dont even need to play the video full just few secs is there no such provision in ubuntu with a good speed

---

### Post by uriel1998 on 2010-12-05
> **neo_aryan said:**
> but in windows i have a toolbar for speedbit... i just need to click on download option in the toolbar to download any video being played on any website....i dont even need to play the video full just few secs is there no such provision in ubuntu with a good speed

Look, you're going to get much more helpful responses if you're more specific about your problem. "I can't get any application to work in WINE" isn't the same thing as "I can't get **an application **to work in WINE".  As someone pointed out, checking the WINE database is important.  [Here's the listing for the SpeedBit downloader]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1463") - apparently older versions worked, but the newer ones don't.

And really, you don't need a whole bloody toolbar to download videos.  You put a [KeepVid bookmarklet]("http://keepvid.com/") on your existing toolbars, install the [DownThemAll extension]("https://addons.mozilla.org/en-US/firefox/addon/201/"), and you have **more screen space, less crapware, and the same functionality**.  (Oh, wait, one more click.)  Things not being the way you *expect* them to be is not the same as not being present.

---

### Post by mlentink on 2010-12-05
You might want to read the link in my signature.

Linux is not Windows. 

If you want it to be, you're better off using the original.

---

### Post by Giraffemonster on 2010-12-05
I agree with mlentink. Linux isn't meant to run Windows programs. A lot of software that the OP wants to download is meant for Windows, and may not be available for wine.

You might want to try searching Wine's Application Database for the programs you want to download first. Please search for a Linux compatible alternative first too, you'll be much happier.

---

### Post by arjunlalb on 2010-12-05
I guess u are using ubuntu 9.04 or greater. the default version of WINE that automatically installs from internet is the last stable release.that is wine 1.2.x.. It is incompatible with Ubuntu 9.04 and greater. type the following command in your terminal to explicitly install the version 1.3 (beta release) which is compatible with ubuntu 9.04 and greater

sudo apt-get install wine1.3

---

### Post by Mark Phelps on 2010-12-05
> i just wanna quit windows,

You're NOT doing this if you're using Wine, in fact, you're actually making the situation worse for yourself because Wine generally requires a LOT of work to get things running even reasonably well.

You would be MUCH better off if you used Linux alternatives, rather than trying to hack together kludgy solutions using Wine.

---

### Post by NightwishFan on 2010-12-05
I am inclined to agree. Wine is a great piece of software and can usually work for you, though some things will just not, and others will not be apparent how to fix.

---

### Post by Locke_99GS on 2010-12-06
If you're not using the latest and greatest flash player, just point your browser to a page containing a flash video, then copy the video out of the /tmp directory. You can even make a script to do this for you, and create a launcher to invoke it and put it on your panel. Bam, one click "downloading" of Youube (and other) vids.

---

### Post by cf0531 on 2010-12-06
> **neo_aryan said:**
> but wat about video downloaders.. i downoad youtube videos using youtube-dl but i need to download videos from other sites too.. i have download toolbar plus speedbit downloader in windows wich makes downloading pretty easy n fast
 
What about fire fox's downloader add-on? works fine for me. also why switch over if you want to use windows apps? try cutting the cord for a bit see how windows-less life works out.

---

