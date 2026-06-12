---
title: "Hello, please walk me through setting up itunes and limewire"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by SpyderFly on 2008-12-26
I just dropped windows xp completely and have no idea how to set up anything I'm used to using from xp.  I'm using ubuntu 8.04.1 LTS desktop edition.  I'm having trouble with itunes, limewire, flash players and active x controls also.  I see when people post a code to help someone but that blows my mind right now.  Can someone please walk me through it.  Maybe some screen shots...  Thanks.

---

### Post by HotShotDJ on 2008-12-26
> **SpyderFly said:**
> I just dropped windows xp completely and have no idea how to set up anything I'm used to using from xp.  I'm using ubuntu 8.04.1 LTS desktop edition.  I'm having trouble with itunes, limewire, flash players and active x controls also.  I see when people post a code to help someone but that blows my mind right now.  Can someone please walk me through it.  Maybe some screen shots...  Thanks.
_iTunes_: I'm not familiar with it.  There are any number of software options for managing your digital music library in Linux, such as Rhythm Box (installed by default) and Amarok (available via Applications --> Add/Remove).  Give these tools a try and see if they meet your needs.  If not, post again and somebody can help you out.
_LimeWire_: Use frostwire instead.  It is based on Limewire.  If you are familiar with LimeWire, it will be completely familiar to you.  Unlike most other software in Ubuntu, you'll have to download this one manually and then double-click on the file to install. Get it here: [http://www.frostwire.com](http://www.frostwire.com) NOTE:  It is a Java based applications, so be sure to install Ubuntu Restricted Extras before installing it (see my instructions for Flash)
_Flash_: Install Ubuntu Restricted Extras (again, via Applications --> Add/Remove).  Let us know if you have any problems after that.
_ActiveX_: This is a Windows/I.E. only train-wreck.  It is not, will not, and SHOULD NOT, ever be available in Linux.  Count your blessings for that.

---

### Post by SlidingHorn on 2008-12-26
Well, unfortunately, iTunes is currently rated as bronze (translated: doesn't work) on Wine's AppDB.  Keep checking here for updates: [http://appdb.winehq.org/appview.php?iAppId=1347](http://appdb.winehq.org/appview.php?iAppId=1347)

Limewire can be installed by following the directions on this page: [https://help.ubuntu.com/community/LimeWire](https://help.ubuntu.com/community/LimeWire)

What problems are you having w/ flash/activeX

---

### Post by kiisu on 2008-12-26
Unless I'm mistaken, you won't be able to run iTunes on Ubuntu. I've never tried myself. If that's what you are used to, give Songbird -> [http://getsongbird.com/](http://getsongbird.com/) - a try, it has a similar feel.

As for Limewire, I know you can use Frostwire -> [http://www.frostwire.com/](http://www.frostwire.com/) if you like. But your fresh install of Ubuntu will have a torrent program or two ... I think Transmission is installed by default now?

The code you were talking about is the better way to install software but for now you can just use the 'Add/Remove'  program, or open 'Synaptic Package Manager' and search for your desired software.

---

### Post by crazyness003 on 2008-12-26
Hi and welcome to freedom.
I know you're gonna be hellova confused at the moment, but its normal.
The programs you seek are windows based, and one thing to understand about Ubuntu (or any other GNU/Linux distro) is that it is NOT windows. With that clear, here are some pointers.

**ActiveX is a no-no**. It sucked in windows and thank god is not in any gnu/linux. So just forget about that proprietary pos (piece of software:D).

As others have posted, instead of using the programs or applications you're so used to using, take a look at programs that functions VERY differently, but give you the same/similar user experience. A great place to find "alternates" to your beloved win apps is here: [http://www.osalt.com](http://www.osalt.com)
Just take a quick search to your prefered apps, and if it finds it, you'll get a list of alternate ones to use in your new Ubuntu.
Another site is here: [http://www.linuxalt.com/](http://www.linuxalt.com/)
or here: [http://linuxappfinder.com/alternatives](http://linuxappfinder.com/alternatives)
Use these sites to track down what you used to use, and replace it with what you should use.

Now about installing: You have 6 ways to install programs in Ubuntu gnu/linux. 3 are *EXTREMEMLY* easy (easier than in windows).
These 3 include: 

[LIST=1]
[*]**Add/Remove** [Applications -> Add/Remove] (Benefits: Easy, Quick search, friendly, gives descriptions)(Drawbacks: Not all apps are available, slow app to run in Linux terms) PERFECT FOR YOU
[*]**Synaptic** [System -> Administration -> Synaptic] (Benefits: huge database of apps, quick search, more robust)(Drawbacks: daunting at first(but not that bad), slow to load, too many options for inexperienced users) USE with RESPECT
[*]**DEB's** (or .deb is the equivalent of downloading an .EXE in windows) Download from the internet, double click, and follow the on-screen instructions.
[/LIST]
    The other 3 "hard ways" are as follows:

[LIST=1]
[*]**apt-get** [available through the terminal (Applications -> Accessories -> Terminal)] :: Use this option when someone gives you a piece of code that looks like this:```
sudo apt-get install cheese
```Lemme break this down:
[LIST]
[*][COLOR=Sienna]sudo[/COLOR] (stands for [COLOR=Sienna]S[/COLOR]uper [COLOR=Sienna]U[/COLOR]ser [COLOR=Sienna]DO[/COLOR], and basically gives you *temporary* access to root priveleges, the backbone of gnu/linux security. [COLOR=Red]USE AT YOUR OWN RISK[/COLOR]. If used imporperly. you can do lots of damage to your system.)
[*]apt-get (is the name of the app that downloads programs for you from the repositories*)
[*]install (obviously installs the program you just downloaded with apt-get)
[*]cheese (im not kidding, there is an app called cheese. try it)(is the name of this particular program (in this case, an Apple Mac substitute to PhotoBooth). But it can be any program ie: gimp, firefox, thunderbird, etc)
[/LIST]
 
[*]**aptitude** [available through terminal (sudo aptitude)] Is the "old-school" equivalent of Synaptic. You'll rarely use it.
[*]**Compiling from Source** [the old way of doing things] For now, you'll probably never have to do this, but if you do, its not really rocket science. If someone asks you to download a *.tar.gz* or *.tar.bz2* (both correspond to .zip in windows) then you *most likely* will have to compile from source. If you ever do run into that, just ask for help.
[/LIST]
*Now i know, i mentioned** Repositories** in there, so lemme give you a heads up to what they are: Repositories are servers that house programs that have been pre-compiled into .deb but have been grouped together so that Add/Remove, Synaptic, apt-get and aptitude can make it EXTREMELY easy for you to download and install. Think of them as "Install CD's OnDemand". You tell on the othe install apps to get you a piece of software, and everything else is taken care of over the internet. Hooray!

Well, this turned out a bit longer than i anticipate...but its for the best.

_**Remember**_: When you do find a program in any of the websites i mentioned earlier, make sure you look for them in Add/Remove or Synaptic first, before you download a .deb (it makes it easier). And if you're unsure OF ANYTHING, there are thousands of people available to help you...at no extra charge!

Enjoy Freedom

EDIT: Oh and if you're wondering how i learned all this, take a look at [my FIRST post eva]("http://ubuntuforums.org/showthread.php?t=95634"), and how lost I was when I started

---

### Post by indiana_crook on 2008-12-26
> **crazyness003 said:**
> Hi and welcome to freedom.
I know you're gonna be hellova confused at the moment, but its normal.
The programs you seek are windows based, and one thing to understand about Ubuntu (or any other GNU/Linux distro) is that it is NOT windows. With that clear, here are some pointers.

**ActiveX is a no-no**. It sucked in windows and thank god is not in any gnu/linux. So just forget about that proprietary pos (piece of software:D).

As others have posted, instead of using the programs or applications you're so used to using, take a look at programs that functions VERY differently, but give you the same/similar user experience. A great place to find "alternates" to your beloved win apps is here: [http://www.osalt.com](http://www.osalt.com)
Just take a quick search to your prefered apps, and if it finds it, you'll get a list of alternate ones to use in your new Ubuntu.
Another site is here: [http://www.linuxalt.com/](http://www.linuxalt.com/)
or here: [http://linuxappfinder.com/alternatives](http://linuxappfinder.com/alternatives)
Use these sites to track down what you used to use, and replace it with what you should use.

Now about installing: You have 6 ways to install programs in Ubuntu gnu/linux. 3 are *EXTREMEMLY* easy (easier than in windows).
These 3 include: 

[LIST=1]
[*]**Add/Remove** [Applications -> Add/Remove] (Benefits: Easy, Quick search, friendly, gives descriptions)(Drawbacks: Not all apps are available, slow app to run in Linux terms) PERFECT FOR YOU
[*]**Synaptic** [System -> Administration -> Synaptic] (Benefits: huge database of apps, quick search, more robust)(Drawbacks: daunting at first(but not that bad), slow to load, too many options for inexperienced users) USE with RESPECT
[*]**DEB's** (or .deb is the equivalent of downloading an .EXE in windows) Download from the internet, double click, and follow the on-screen instructions.
[/LIST]
    The other 3 "hard ways" are as follows:

[LIST=1]
[*]**apt-get** [available through the terminal (Applications -> Accessories -> Terminal)] :: Use this option when someone gives you a piece of code that looks like this:```
sudo apt-get install cheese
```Lemme break this down:
[LIST]
[*][COLOR=Sienna]sudo[/COLOR] (stands for [COLOR=Sienna]S[/COLOR]uper [COLOR=Sienna]U[/COLOR]ser [COLOR=Sienna]DO[/COLOR], and basically gives you *temporary* access to root priveleges, the backbone of gnu/linux security. [COLOR=Red]USE AT YOUR OWN RISK[/COLOR]. If used imporperly. you can do lots of damage to your system.)
[*]apt-get (is the name of the app that downloads programs for you from the repositories*)
[*]install (obviously installs the program you just downloaded with apt-get)
[*]cheese (im not kidding, there is an app called cheese. try it)(is the name of this particular program (in this case, an Apple Mac substitute to PhotoBooth). But it can be any program ie: gimp, firefox, thunderbird, etc)
[/LIST]
 
[*]**aptitude** [available through terminal (sudo aptitude)] Is the "old-school" equivalent of Synaptic. You'll rarely use it.
[*]**Compiling from Source** [the old way of doing things] For now, you'll probably never have to do this, but if you do, its not really rocket science. If someone asks you to download a *.tar.gz* or *.tar.bz2* (both correspond to .zip in windows) then you *most likely* will have to compile from source. If you ever do run into that, just ask for help.
[/LIST]
*Now i know, i mentioned** Repositories** in there, so lemme give you a heads up to what they are: Repositories are servers that house programs that have been pre-compiled into .deb but have been grouped together so that Add/Remove, Synaptic, apt-get and aptitude can make it EXTREMELY easy for you to download and install. Think of them as "Install CD's OnDemand". You tell on the othe install apps to get you a piece of software, and everything else is taken care of over the internet. Hooray!

Well, this turned out a bit longer than i anticipate...but its for the best.

_**Remember**_: When you do find a program in any of the websites i mentioned earlier, make sure you look for them in Add/Remove or Synaptic first, before you download a .deb (it makes it easier). And if you're unsure OF ANYTHING, there are thousands of people available to help you...at no extra charge!

Enjoy Freedom

EDIT: Oh and if you're wondering how i learned all this, take a look at [my FIRST post eva]("http://ubuntuforums.org/showthread.php?t=95634"), and how lost I was when I started

dido.  As mentioned earlier use Songbird.  And I've been using Frostwire for some time now, it's great for Ubuntu.  Same network I believe so you won't really notice a difference.

---

### Post by jamesstansell on 2008-12-26
> **SpyderFly said:**
> I just dropped windows xp completely and have no idea how to set up anything I'm used to using from xp.  I'm using ubuntu 8.04.1 LTS desktop edition.  I'm having trouble with itunes, limewire, flash players and active x controls also.  I see when people post a code to help someone but that blows my mind right now.  Can someone please walk me through it.  Maybe some screen shots...  Thanks.

Nice to hear from you.  Excellent move! :)

The Comprehensive Multimedia & Video Howto may be of interest to you.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Also, I think there may be some ubuntu video tutorials available too.  Not sure of a link right now though.

Keep searching, reading, and asking questions. And enjoy your new freedom!

---

### Post by nlz on 2008-12-26
If you want a good alternative for itunes, use songbird! It's really nice and stable, also really fast.

If you've got an ipod, i would suggest that you install Rockbox on it instead of further using the Apple firmware.

to install flash and other media (sound/video) things follow this guide:

[http://ubuntuforums.org/showthread.php?t=766683&highlight=comprehensive+media](http://ubuntuforums.org/showthread.php?t=766683&highlight=comprehensive+media)

---

### Post by adobrakic on 2008-12-26
Agree completely with first reply.
Easy to follow, and good advice.

Try it. :)


Also, like some have said before me, Linux is **not** Windows. 
So, just to save you trouble, instead of trying to run Windows programs on Linux, find alternatives instead (Songbird instead of iTunes -- Frostwire instead of LimeWire -- Audacious instead of Winamp).

---

### Post by lingenfr on 2008-12-26
> **SlidingHorn said:**
> Well, unfortunately, iTunes is currently rated as bronze (translated: doesn't work) on Wine's AppDB.  Keep checking here for updates: [http://appdb.winehq.org/appview.php?iAppId=1347](http://appdb.winehq.org/appview.php?iAppId=1347)

I was just looking at the same thing. Actually, ITunes 7.3 is 'Bronze', 8.0 and above are 'Garbage'.

---

