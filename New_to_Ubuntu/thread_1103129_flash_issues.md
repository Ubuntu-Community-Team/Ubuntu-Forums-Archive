---
title: "flash issues"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by nynoah on 2009-03-22
Has there been something that has come down the update pipe that has messed up the Flash code?  A friend of mine started to complain that his flash was not working right.  Within the next few days mine broke too.  I am running 64 bit Ultimate Edition Ubuntu based on 8.10 while my friend is running standard 8.10 32 bit.  

I tried installing, purging, reinstalling, adding Kubuntu restricted extras and Ubuntu restricted extras.  

Anyone know if there is a issue that started  with an update.......... but anyone have a clue how to fix this?

---

### Post by skymera on 2009-03-22
How have you installed Flash on the 64bit machine?

---

### Post by nynoah on 2009-03-22
yeah....... had my install going for a long time with no issues.  Mine was not acting up until just recent.  About a week ago a friend wrote to me telling me he was having issues with Flash.  Mine was fine at the time and then mine just started acting up now too.

---

### Post by skymera on 2009-03-22
Did you install flashplugin-nonfree or download Flash from Adobe site?

64bit : Download the Flash 10 alpha from Adobe Labs
32bit: sudo apt-get install flashplugin-nonfree

---

### Post by nynoah on 2009-03-22
I got mine from synaptic.  version 10.0.22.87 flashplugin nonfree

His I am not to sure of.

---

### Post by eilios on 2009-03-22
Try running this in terminal, I had the same problem and this worked.

```

**tar zxvf libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz**[B]
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/[/B]
[B]
```
[/B]

---

### Post by Dai Bando on 2009-03-22
This is what I got :-

dave@dave-desktop:~$ tar zxvf libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz
tar: libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
dave@dave-desktop:~$ sudo cp libflashplayer.so /usr/lib/mozilla/plugins/

I did a complete re-install of 8.04 and still the same.

---

### Post by nynoah on 2009-03-22
did not work.  Its also the same version as the version that is in synaptic.

---

### Post by gn2 on 2009-03-22
[Here's a very simple step by step how-to for 64-bit flash]("http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml").

NB you must uninstall all previous versions of Flash and nspluginwrapper and not have Firefox running when you copy the Flash file into the plugins directory.
Doesn't hurt to remove Gnash as well.

But [get the latest version here first]("http://labs.adobe.com/downloads/flashplayer10.html").

---

### Post by nynoah on 2009-03-22
Dai Bando the commands that were posted before were dependent on downloading the newest version of flash from the Flash website.  If you don't have that file in your home directory the "tar" commands will not work.

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

But ..... the strange part is the version of flash on the flash website is the same as the version in synaptic.  And neither is working currently.  I am wondering if we have to roll back to a previous version.

---

### Post by nynoah on 2009-03-22
Ok the link to this site worked to get Flash working. 

[http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)


The reason the code from ellious did not work is because unless you have previously created a folder for "plugins" inside of the .mozilla file.  There is nowhere for the file to be pasted into.

---

### Post by Dai Bando on 2009-03-22
I have just checked and Flash is working correctly again; so I re-installed my OS for no reason at all.

---

### Post by kansasnoob on 2009-03-22
I know nothing about 64 bit flash other than this:

[http://www.howtoforge.com/installing-adobe-flash-10-on-a-64bit-ubuntu-8.04](http://www.howtoforge.com/installing-adobe-flash-10-on-a-64bit-ubuntu-8.04)

My most recent flash problems have involved:

(1) Making sure that gnash and swf-gnome (or swf-mozilla) are NOT installed. The easiest way I've found to do that is opening Synaptic and typing flash into the search window, if gnash or either swf-* is installed mark them for complete removal.

(2) While you're looking also look for "adobe-flashplugin" and "flashplugin-nonfree". Make sure only one of the two is installed, sometimes one seems to work better than the other - not always the newest - and you don't want both installed! This may require some trial and error to see which works best.

(3) Flash is very hungry so I always use Flashblock. Make sure the repo version of Flashblock is NOT installed! Instead go to Tools > Add-ons > Get Add-ons and make sure you have Flashblock 1.5.8 or newer!

(4) Consider all plug-ins/add-ons! Are they needed? Are they the newest version? I prefer the Mozilla build of Firefox to the repo version because you'll generally be informed of "add-on" updates.

The easiest way I've found to install the true Mozilla build of Firefox is Ubuntuzilla:

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

It really is as simple as downloading it to your Desktop, then double clicking the icon, then going to terminal and running:

```
ubuntuzilla.py -a install -p firefox
```

After answering a few simple questions you're done and you'll get more frequent update notices. (You'll notice you can download either the 32 bit or 64 bit version of Firefox from Ubuntuzilla):

[http://ubuntuzilla.wiki.sourceforge.net/#tochome6](http://ubuntuzilla.wiki.sourceforge.net/#tochome6)

---

### Post by nanotube on 2009-03-22
> **kansasnoob said:**
> 
After answering a few simple questions you're done and you'll get more frequent update notices. (You'll notice you can download either the 32 bit or 64 bit version of Firefox from Ubuntuzilla):

[http://ubuntuzilla.wiki.sourceforge.net/#tochome6](http://ubuntuzilla.wiki.sourceforge.net/#tochome6)

correction: the firefox build is always 32bit - mozilla doesn't release 64bit builds. 

the amd64 .deb package of ubuntuzilla merely makes sure the required dependencies are installed to enable running the 32bit firefox on a 64bit system. 

p.s.: howdy, kansasnoob! :)

---

