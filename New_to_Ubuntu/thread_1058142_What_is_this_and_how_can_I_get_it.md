---
title: "What is this and how can I get it?"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by Slacker20 on 2009-02-02
I'd use the search tool if I knew what this was called, but I don't (I'm obviously new to Linux).  I came across this screen shot and I've seen others with the same OSX-like desktop, but I have no idea what it's actually called or how to go about getting it (referring to the menu across the bottom of the screen).  I'm running Ubuntu 8.04 by the way.

[IMG]http://img.photobucket.com/albums/v655/Slacker_Master17/itunes-main-window-thumb.png[/IMG]

Sorry for the incredibly noobish question, but then again, this is under the "absolute beginner" section after all, lol.

Thanks in advance,
~Slacker20

---

### Post by estyles on 2009-02-02
> **Slacker20 said:**
> I'd use the search tool if I knew what this was called, but I don't (I'm obviously new to Linux).  I came across this screen shot and I've seen others with the same OSX-like desktop, but I have no idea what it's actually called or how to go about getting it (referring to the menu across the bottom of the screen).  I'm running Ubuntu 8.04 by the way.

Sorry for the incredibly noobish question, but then again, this is under the "absolute beginner" section after all, lol.


Check out awn.  It's in the repos.  The easiest way to get it is```
sudo apt-get install awn
```  There's another similar dock that a lot of people like, but I personally hate them (I prefer standard gnome-panels), so I don't know what it's called.  The general term for it is a "dock".

---

### Post by perlluver on 2009-02-02
That would be Avant Window Navigator, not sure if it is in the repos on 8.04, but it is in the repos for 8.10.  It might simply be called AWN.  It might also be Cairo Dock.  If you search for them in the search box, you should be able to find info on both.

---

### Post by mangurt on 2009-02-02
The tool bar application is call Avant windows navigator and you can find out more information here
[http://ubuntuforums.org/showthread.php?t=762363&highlight=Avant+window+manager](http://ubuntuforums.org/showthread.php?t=762363&highlight=Avant+window+manager)

---

### Post by kestrel1 on 2009-02-02
My suggestion would be to install Cairo-Dock, very nice program:
[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)
This will show you how.

---

### Post by Therion on 2009-02-02
The other options would be things like [Cairo Dock](http://tombuntu.com/index.php/2008/05/01/how-to-install-cairo-dock/) or [Docky](http://do.davebsd.com/wiki/index.php?title=Docky).

---

### Post by Slacker20 on 2009-02-02
Thanks a lot.  Without these forums, I'd definitely be lost with Linux.  Thanks for all the quick responses and links

---

### Post by halovivek on 2009-02-03
thanks i will try in my system :)

---

### Post by bobpur on 2009-02-03
Check out OpenGEU (formerly GEUbuntu) at [www.distrowatch.com](www.distrowatch.com). It is , currently, at 35 on the list.

I think this is Ubuntu with the dock and other "eye candy" already installed.

Read their homepage for features, screenshots and other considerations.

Also, check out Dreamlinux and Elive on distrowatch. They feature the dock, too.

---

### Post by tomtom1982 on 2009-02-03
To make your gnome look like osx:


 Making your Ubuntu-desktop look like Mac OSX (requires an installed gnome-desktop):
 
 At first you have to download the current version of the Mac4Lin-project. That´s a pool of components which let your gnome-desktop looks like OSX. It contents themes, pictures and layouts for the login-screen. You´ll find it at 
HTML Code:
[http://sourceforge.net/porjects/mac4lin](http://sourceforge.net/porjects/mac4lin)
. Current version is 1.0RC. After download unpack the archive in any folder. 
 
 Only if emerald is currently not installed:
 For later installation you have to install emerald via sudo apt-get install emerald. After this you have to start and close emerald. It will make a new folder in your home folder. 
 
 Now open a terminal and change folder with
 
 

[CODE]cd <path>[CODE]
(please insert the folder were you saved mac4lin instead of <path>, /home/user/documents/ for example)
 
 Now you type the following into terminal:
 
 
[CODE]
./Mac4Lin_Install_v.10_RC.sh[CODE]

This will start the installation script.
 
 During the installation, you will be asked for your password. Please type Y and Enter, after this insert your pass. The first changes will appear on your desktop. The wallpaper and the window-designs will change.
 
 If nothing is changed, you have to activate it by opening &#8222;System->Preferences->Appearance&#8220;. There you change to &#8222;theme&#8220;. Here you see the themes &#8222;Mac4Lin_Aqua&#8220; and &#8222;Mac4Lin_Graphite&#8220;. You´ll activate a theme by clicking it. You also can install the themes manually by clicking &#8222;install&#8220; and choosing into the folder you downloaded the files. There you go to folder &#8222;GTK&#8220; and choose the theme-archive &#8222;Mac4Lin_GTK_v1.0_RC.tar.gz&#8220;.
 
 Now you have to change fonts. Open &#8222;System->Preferences->Appearance&#8220; and change to register &#8222;fonts&#8220;. Change the fonts from top to bottom like this:
 &#8222;Bitstream Vera Sans Roman&#8220; Size 10
 &#8222;Aquabase&#8220; Size 9
 &#8222;Trebuchet MS Standard&#8220; Size 9
 &#8222;Lucida Grande Bold&#8220; Size 9
 &#8222;Bitstream Vera Sans Mono Roman&#8220; Size 10
 
 After this click on &#8222;close&#8220;.
 
 On your screen you have a Mac OS X-Wallpaper. For more wallpapers please visit 
HTML Code:
[http://sourceforge.net/projects/mac4lin](http://sourceforge.net/projects/mac4lin)
 and download the file &#8222;Leopard Wallpapers&#8220; from section &#8222;Downloads->Additional Files&#8220;. Please unpack the downloaded file into any folder. Open &#8222;System->Preferences->Appearance&#8220;, go to &#8222;Background&#8220; and open these folder to choose another Mac OS X-Wallpaper.
 
 Please install AWN via 
 
 

[CODE]sudo apt-get install avant-window-navigator[CODE]

Now open &#8222;System->Preferences->Awn Manager&#8220;. Go to &#8222;Themes&#8220; and click on &#8222;&#8220;.Choose the folder you´ve download the Mac4Lin-files, go to folder &#8222;AWN&#8220; and choose the only archive in this directory. After this click on &#8222;Apply&#8220;.
 
 Change Log-In-Screen:
 Open &#8222;System->Administration->Login Window&#8220; and go to register &#8222;Local&#8220;. Click on the box in front of &#8222;Mac4Lin GDM v1.0 RC&#8220; and make it the only active box. After this, click on &#8222;Background color&#8220; and type into &#8222;Color name&#8220;: #E5E5E5
 
 After this you will get a new login screen after restarting ubuntu.
 
 You also can install screenlets with
 
 
[CODE]
sudo apt-get install screenlets compizconfig-settings-manager[CODE]
.
 
 That´all.
 
 Sorry for my English, it´s not my native language, only what I learned at school

---

### Post by LowSky on 2009-02-03
**tomtom**, your English is pretty good fo a non-native speaker., just remember that when using code tags the one on the end needs a /
for example: [/code]

Slacker20, if you just would like the cool OS/X bar use Avant-window-navigator (aka: awn), but you also need to run compiz fusion, like before search add/remove for ccsm for that. Please note tat you will have to add all the icons yourself to the launcher, it isn't hard just time consuming

---

### Post by Slacker20 on 2009-02-06
I was finally able to get everything working, now my only question is how can I make it so that the AWN dock starts automatically when Ubuntu loads?

---

### Post by directhex on 2009-02-06
> **Slacker20 said:**
> I was finally able to get everything working, now my only question is how can I make it so that the AWN dock starts automatically when Ubuntu loads?

System, Preferences, Sessions

---

### Post by kestrel1 on 2009-02-06
Just add the command that starts AWN in Sessions.
Not sure what the command is as I use Cairo-Dock.

---

