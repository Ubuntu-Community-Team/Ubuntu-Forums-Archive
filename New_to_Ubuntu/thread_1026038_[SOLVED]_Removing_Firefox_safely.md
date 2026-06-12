---
title: "[SOLVED] Removing Firefox safely?"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by mariane_08 on 2008-12-30
I want to remove the version of Firefox that comes packaged with Intrepid because I'm having some problems with it. How do I safely do that? I dont understand the message that I get if I try to do in under Add/Remove Applications.


Then I plan to replaaaace it with a differnt version of Firefox that is only on the Mozilla website. What procedur should I follow to install it?

Thanks

---

### Post by slammed87d21 on 2008-12-30
Try removing it through Synaptic.

---

### Post by shafi on 2008-12-30
> **mariane_08 said:**
> I want to remove the version of Firefox that comes packaged with Intrepid because I'm having some problems with it. How do I safely do that? I dont understand the message that I get if I try to do in under Add/Remove Applications.


Then I plan to replaaaace it with a differnt version of Firefox that is only on the Mozilla website. What procedur should I follow to install it?

Thanks

Completely remove Firefox from synaptic, then download your favorite Mozilla package and install.

---

### Post by gjoellee on 2008-12-30
use this code:
```
sudo apt-get remove firefox
```

---

### Post by eBoxNet on 2008-12-30
try this in terminal : 

```
sudo apt-get remove mozilla-firefox && sudo apt-get install mozilla-firefox
```

If you want to delete all your plugins

```
cd /home/yourusername
```
```
rm -rf .mozilla
```

"BE SURE YOU ARE INSIDE YOUR HOME DIRECTORY BEFORE YOU rm -rf .mozilla"

---

### Post by decoherence on 2008-12-30
Follow the menus...

System > Administration > Synaptic

do a search on firefox (use the search button, not the quicksearch)

find the package firefox, right click on the little green square and select "mark for removal"

do the same for package firefox-3.0, if it's there.

as for re-installing it, firefox should provide directions in the file you download

---

### Post by mariane_08 on 2008-12-30
> **eBoxNet said:**
> try this in terminal : 

```
sudo apt-get remove mozilla-firefox && sudo apt-get install mozilla-firefox
```

If you want to delete all your plugins

```
cd /home/yourusername
```
```
rm -rf .mozilla
```

"BE SURE YOU ARE INSIDE YOUR HOME DIRECTORY BEFORE YOU rm -rf .mozilla"

OK thanks everyone! If I download the other version to say my home directory whats the code for that?

---

### Post by eBoxNet on 2008-12-30
if you allready done ```
sudo apt-get remove mozilla-firefox && sudo apt-get install mozilla-firefox 
``` and you have your firefox up and running skip any other steps.

---

### Post by eBoxNet on 2008-12-30
the right order to clean install FF is :

1.Remove Firefox : ```
sudo apt-get remove mozilla-firefox
```
2.Clean FireFox Plugins Directory :
a.```
cd /home/username
```
b.```
rm -rf .mozilla
```
3.Install FireFox : ```
sudo apt-get install mozilla-firefox
```

---

### Post by decoherence on 2008-12-30
> **eBoxNet said:**
> if you allready done ```
sudo apt-get remove mozilla-firefox && sudo apt-get install mozilla-firefox 
``` and you have your firefox up and running skip any other steps.

yeah... we shoulda asked before....

what problems are you having with firefox? is there a particular reason you want to install it from mozilla or do you just hope to have better luck with it?

thanks

---

### Post by mariane_08 on 2008-12-30
> **decoherence said:**
> yeah... we shoulda asked before....

what problems are you having with firefox? is there a particular reason you want to install it from mozilla or do you just hope to have better luck with it?

thanks

Well I hope it will run faster. I am happy with Intrepid but at my wits end trying to get firefox running at a decent speed. See my other thread on this
[http://ubuntuforums.org/showthread.php?t=1024761](http://ubuntuforums.org/showthread.php?t=1024761)

Thanks
Mariane

---

### Post by eBoxNet on 2008-12-30
i think its just a bad version..
i don't think you can do something to make it go better (better = like it used 2 be in prev vers)

---

### Post by kansasnoob on 2008-12-30
Look at Ubuntuzilla:

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

Note that it says:

> do not remove the repositories version of Firefox, as doing so will break a lot of Gnome packages that depend on the Gecko rendering engine.

I'm using the Ubuntuzilla version of Firefox with great results!

They have their own space here on the forums:

[http://ubuntuforums.org/forumdisplay.php?f=251](http://ubuntuforums.org/forumdisplay.php?f=251)

---

### Post by mariane_08 on 2008-12-30
> **kansasnoob said:**
> Look at Ubuntuzilla:

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

Note that it says:



I'm using the Ubuntuzilla version of Firefox with great results!

They have their own space here on the forums:

[http://ubuntuforums.org/forumdisplay.php?f=251](http://ubuntuforums.org/forumdisplay.php?f=251)

Thank you for pointing that out!

---

### Post by stchman on 2008-12-30
Do the following:

```
sudo apt-get autoremove firefox
```

The autoremove removes all unused dependencies.

The Firefox on Mozilla's website and the one that Ubuntu installs are the same.

What problem are you having?

---

### Post by mariane_08 on 2008-12-30
> **stchman said:**
> Do the following:

```
sudo apt-get autoremove firefox
```

The autoremove removes all unused dependencies.

The Firefox on Mozilla's website and the one that Ubuntu installs are the same.

What problem are you having?

Thanks!
I'm getting extremely slow web page loading since I installed Intrepid. See my other thread: [http://ubuntuforums.org/showthread.php?t=1024761](http://ubuntuforums.org/showthread.php?t=1024761)
Have tried all sorts of tweaks to resolve it. :confused:

---

### Post by mkvnmtr on 2008-12-30
On my 8.04 I have come to believe that Firefox is just not going ton be fast. I don't think it is Ubuntu. It seems to just have too many features. There are at least 5 other browsers in the repositories that are faster. They are just not as full featured. I use two or them and Firefox nearly all the time.

---

### Post by mariane_08 on 2008-12-31
> **kansasnoob said:**
> Look at Ubuntuzilla:

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

Note that it says:



I'm using the Ubuntuzilla version of Firefox with great results!

They have their own space here on the forums:

[http://ubuntuforums.org/forumdisplay.php?f=251](http://ubuntuforums.org/forumdisplay.php?f=251)

I'm a little confused about this bit? What should I do to ensure I DONT remove repository version? I can do it via terminal as advised but if I go to synaptic there are 8 different Firefox packages listed. Which of these should I not remove???

Thanks

---

### Post by mariane_08 on 2008-12-31
Or do I remove all 8 of the Firefox packages listed in Synaptic?

---

### Post by zika on 2008-12-31
**do You want speed, stability, compatibility forwards and backwards and peace of mind? if Yes then proceed ... **

my advice is **not to** remove firefox that came with Ubuntu.

just download Shiretoko (FF 3.1) from [http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-1.9.1/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-1.9.1/) to get appropriate package (depending if You are on 32-bit or 64-bit version) to Your home directory. extract it with ```
tar -xvf **name_of_the_package**
``` and edit the file ```
~/firefox/firefox
```so that a line ```
moz_libdir=/usr/local/lib/firefox-3.1b2
``` reads ```
moz_libdir=/home/**Your_user_name**/firefox
```Go to System->Preferences->Preffered_Apllications->Internet->Web_Browser choose Custom and write in a command line ```
/home/**Your_user_name**/firefox/firefox
``` and You are done. You do not have to change nothing in Your browsing habits and every call to web-brouser will be handled by Shiretoko.

this way all Your plugins and settings remain intact. also You have a valid broser to revert to if anything goes wrong. once FF gets to a new version You are upgraded and so on ... You'll find Your 'original' FF on the panel-application-launcher ...

Also read [http://ubuntuforums.org/showpost.php?p=6462096&postcount=41](http://ubuntuforums.org/showpost.php?p=6462096&postcount=41) to see what is going on about branching in development of FF so, once FF gets to 3.1 officially You can switch to Minefield branch and be ahead of updates ... ;)

---

### Post by albinootje on 2008-12-31
> **mariane_08 said:**
> OK thanks everyone! If I download the other version to say my home directory whats the code for that?

If you want to use Firefox from the Mozilla website ([http://www.mozilla.com](http://www.mozilla.com)), then it would be e.g. :
```

tar xzvf firefox-3.0.1-linux-686-orsomethinglikethat.tar.gz

```

The perhaps easier alternative is :
Double-clicking on the .tar.gz file should give you an option to extract it with the default archiving application.

Installing Firefox from the Ubuntu repositories does make more sense though, it's easier to have only one security updates popup to deal with, and the Ubuntu Firefox has e.g. the apt:// option, which is nice imho.

That would be :
```

sudo apt-get remove --purge firefox firefox-*
sudo apt-get install firefox

```

---

