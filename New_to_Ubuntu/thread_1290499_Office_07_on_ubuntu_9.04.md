---
title: "Office 07 on ubuntu 9.04?"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by HamzahQaisar on 2009-10-13
can i get office 07 on ubuntu ??????????????????????????????????????
i really need it for my coursework at school:cry::(

---

### Post by Dougie187 on 2009-10-13
I think it works in wine. Check the appdb at winehq.com

Otherwise, no.

You could try using OpenOffice, but it might not work as well.

EDIT: Link [http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)

Looks like the Installer works decent, everything else appears to be silver. Which means it will have some issues.

---

### Post by LinLux451 on 2009-10-13
Ick. Sorry. I would have to say oo.o would be your best bet. I wouldn't mess with m$crosoft office. Open Office can open everything besides .docx... which you can use google docs for...plus at school, you can save everything in odt format... which is completely GNU friendly! :)

---

### Post by Dougie187 on 2009-10-13
> **LinLux451 said:**
> Ick. Sorry. I would have to say oo.o would be your best bet. I wouldn't mess with m$crosoft office. Open Office can open everything besides .docx... which you can use google docs for...plus at school, you can save everything in odt format... which is completely GNU friendly! :)

I believe OOo 3.0 and up open docx files. But I have yet to try it.

---

### Post by OpenGuard on 2009-10-13
Repeating question mark will not solve your problem. As other suggested, you better use something that's meant to work on Linux, not just works because of third-party software ( eg., Wine ).

---

### Post by HamzahQaisar on 2009-10-13
ok ive got wine but how do u work wine??

---

### Post by pythonscript on 2009-10-13
open office handles the .docx format on my laptop, at least, and I'm running v3.0x. There are a lot of things that open office doesn't do nearly as well as office 07 (at least for those of us accustomed to using office, any version) but I run office 2003 word in wine, and that works fine. If you really need certain functionality of office that's present in 2003 word, it runs *almost* perfectly in wine.

---

### Post by Dougie187 on 2009-10-13
> **HamzahQaisar said:**
> ok ive got wine but how do u work wine??

On the link I posted earlier, go to the section on "How to install"

---

### Post by QIII on 2009-10-13
Sorry about that!  Schools can be held under the sway of the "other OS", too.

(No Windows bashing here.  Not a bad series of OSs, really.  I just don't like Microsoft's business practices is the main thing.  Choice is what I am all about.  I don't like being forced into someone else's expectation of what my "user experience" should be.)

Those apps from the "other OS" are listed in Wine's database with the following performance for Office 2007.

Bear in mind that the test sample sizes can be fairly small.

Word -- Silver
Access -- Garbage
Excel -- Silver
PowerPoint -- Silver

It would not be a bad idea to dual boot the Windows version of your choice along side Ubuntu.  There is no shame at all in that (hack, cough!  I can't believe I just wrote that!).  If you need that OS, you need it.  Let's be pragmatic and honest.

---

### Post by sandyd on 2009-10-13
ill give complete instructions...
run this in the terminal.
```

cd /usr/bin
sudo wget  [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
sudo chmod 777 winetricks
sudo apt-get install wine wine-gecko cabextract
winetricks vcrun2005 vcrun2005sp1 wsh56 wsh56js 
winecfg

```then in the window that appears, go to the "Libraries" tab.
in the box under New override" type in "riched20"
hit enter
then type in usp10
hit enter.
Run the Microsoft installer (by double clicking on it) or by right clicking it and selecting run with wine.
otherwise, you can also do
```

wine *setup.exe*

```provided that you cd ed to the correct directory of the installer and the setup file is called setup.exe.

Below Optional just to improve the appearance ->
```

winetricks fontfix fontsmooth-rgb allfonts gecko gdiplus msxml3 fakeie6
winecfg
```in the window that appears, go to the "desktop integration" tab. then, from the internet or somewhere else, copy a windows theme (with the extension .msstyles). click on the "install theme" button, navigate to the direcoty where you downloaded it to, and install it.

---

### Post by Xalor on 2009-10-13
If there is a specific function that you need on word, I'll help you out in finding it in OpenOffice, but there's so many other alternatives, and you can always just use Google docs, I believe someone just mentioned it before. 

Just make sure to save as doc and some of the shortcuts aren't the same so just look them up.

---

### Post by HamzahQaisar on 2009-10-13
> **carlee said:**
> ill give complete instructions...
run this in the terminal.
```

cd /usr/bin
sudo wget  [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
sudo chmod 777 winetricks
sudo apt-get install wine wine-gecko cabextract
winetricks vcrun2005 vcrun2005sp1 wsh56 wsh56js 
winecfg

```then in the window that appears, go to the "Libraries" tab.
in the box under New override" type in "riched20"
hit enter
then type in usp10
hit enter.
Run the Microsoft installer (by double clicking on it) or by right clicking it and selecting run with wine.
otherwise, you can also do
```

wine *setup.exe*

```provided that you cd ed to the correct directory of the installer and the setup file is called setup.exe.

Below Optional just to improve the appearance ->
```

winetricks fontfix fontsmooth-rgb allfonts gecko gdiplus msxml3 fakeie6
winecfg
```in the window that appears, go to the "desktop integration" tab. then, from the internet or somewhere else, copy a windows theme (with the extension .msstyles). click on the "install theme" button, navigate to the direcoty where you downloaded it to, and install it.


thanks alotnow i just got to get hold of a office cd

---

### Post by pythonscript on 2009-10-13
HamzahQaisar, thanks for the instructions! Now I'm thinking I should give this a shot... but I'm probably going to wait until November, since I'm doing a fresh install of Karmic once that comes out anyways.

---

### Post by HamzahQaisar on 2009-10-13
> **pythonscript said:**
> HamzahQaisar, thanks for the instructions! Now I'm thinking I should give this a shot... but I'm probably going to wait until November, since I'm doing a fresh install of Karmic once that comes out anyways.
 

Im A thick Brain How can i Post These Instructions..

ALL CREDITS GO TO CARLEE!!!!!!

---

### Post by pythonscript on 2009-10-13
My mistake.

---

### Post by HamzahQaisar on 2009-10-13
> **pythonscript said:**
> My mistake.

aint that a fact.:):)

---

### Post by ST3ALTHPSYCH0 on 2009-10-13
Download the newest version of Wine for your application from here: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Open your office 07 disc
right click on "setup.exe"
select "open with Wine Windows Program Loader"
Install as normal


EDIT
Well, N/M... I just attempted this, and Office doesn't show up in my Wine menu... Hmmm.

---

### Post by HamzahQaisar on 2009-10-15
How do i install Office 07 on Ubuntu???? using wine

Thanks in advanced

---

### Post by halitech on 2009-10-15
info here

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)

its supposed to work with wine version 1.1.29

---

### Post by cariboo on 2009-10-15
have a look [here]("http://samanathon.com/how-to-install-microsoft-office-2007-in-ubuntu-9-04/"), it should help.

---

### Post by HamzahQaisar on 2009-10-15
THANKS A MILLION DUDES ITS INSTALLING ATM

Thanks thanks thanks

---

### Post by HamzahQaisar on 2009-10-15
They Say all good things come to a end and guess what!!

ms access dosent work 

How can i make it work @???

---

### Post by SonicSteve on 2009-10-15
From what I've  seen in the Linux community there is dare I say an Ostrich head in the sand happening in regards to Open office and Microsoft office.  

I work in Microsoft environment at my school. From my experience even if you use .doc instead of .docx it doesn't work well to mix open office and microsoft office. I've seen powerpoint files truncated when I've opened and edited the same file between both office suites.  

Another example is here at my school, if I could get Microsoft office to work on Linux (and work well) I'd have a much better chance of getting Linux installed. Silver is a nice start from the wine group and I'm not criticizing them or anyone else. The fact that Microsoft Windows products will run in Linux at all is great. However as much as we would like to believe that Open office is a replacement for Office 2007 I can say that my finding is the opposite. Any organization using office 2007 would have a long road of converting the O2K7 documents to ODF. There are many things that don't translate well like complex macros and database files. It's the converting process that I think scares most companies off, and keeps open office from wide spread adoption. 

Dang I wish this wasn't the truth but my experience says differently.

---

### Post by anewguy on 2009-10-15
I use OpenOffice.org as much as possible, but there are somethings it does screw up for me when I try to share a document between OO and Word.  Sometimes the formatting gets all messed up.  Other things, like label support, is better in Word as delivered.

Someone already mentioned how to install Office 2007:

- remove your existing wine installation via the package manager
- via the file explorer, change view to include hidden files and delete the existing .wine folder

- download the latest (mine is 1.1 31) wine (don't use the one in the package manager) and install it

- put in your Office 2007 CD, then click on the setup.exe file on the disk


Dave :)

---

### Post by djbon2112 on 2009-10-15
> **SonicSteve said:**
> From what I've  seen in the Linux community there is dare I say an Ostrich head in the sand happening in regards to Open office and Microsoft office.  

<snip> 

Dang I wish this wasn't the truth but my experience says differently.

And to think, Microsoft does this on PURPOSE and gets away with it! :confused:

OP, your best be probably IS to dual boot. If you need MS Office really badly, why do you want to move to Ubuntu?

---

### Post by lavinog on 2009-10-15
openoffice has some issues with rendering office formulas.  Sometimes if I open a doc file with a bunch of formulas, i have to double click on every formula to get the rendering correct.

I was able to install the trial version of office using wine with no noticable bugs.
Crossover office would be a good idea if you need a stable install with support...plus it helps with wine development.

---

### Post by cariboo on 2009-10-15
Please don't double post on the same subject, I have merged your two threads.

---

### Post by Mark Phelps on 2009-10-17
If you're going to use Wine, you need to become familiar with the CodeWeavers Application Compatibility site.  The link below shows Access 2007 as "garbage", meaning, it's most probably NOT going to work:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=12]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=12")

---

### Post by barkej on 2009-10-17
You could always run office from a vm like virtual box.

---

### Post by Devon64327 on 2009-10-17
If Wine won't work your options are a dual boot if (you've still got your XP/Vista boot cd)
virtual machine(same deal) 
live with open office (really not that bad)
**OR**
Google docs (SUPER convenient) 



Pssst go with google






Too bad you need it for school though. If it were work say I'm sure you could request changing that to ubuntu as well but schools are so paranoid about these things. My school wont even allow firefox.

---

### Post by Hperez on 2010-01-14
I have a question.

I'm using wine 1.1.36 installed winetricks, and ran office 2007 installer on Ubuntu, apparently office is loaded & is working great; however on Excell I tried running an add-in and keep getting an error message. Saying:

Microsoft office excell can't run this add-in. Microsoft office excell cannot install the necessary files due to windows installers error 2. File not found.

Microsoft office excell cannot access the file analys32.xll.

Again excell seems to be working fine on Ubuntu, except I'm having issues running this add-in. 

FYI-the add-in I'm trying to load is called Analysis Tool Pack for excell. I need this for some statistics lab work I'm doing for school. If you have ran into this problem and have found a solution, please help.

Thanks!
Henry

---

