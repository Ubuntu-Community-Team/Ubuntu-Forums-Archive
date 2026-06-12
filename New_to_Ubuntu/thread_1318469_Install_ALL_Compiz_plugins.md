---
title: "Install ALL Compiz plugins?"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by steigerjb on 2009-11-07
Is there a way I can install **ALL** the Compiz plugins (Main, extra, unsupported, experimental,...) all at once?

Though, I don't even know how to do one at a time.

I already did

```
sudo apt-get install compizconfig-settings-manager
```

course that's not nearly all the plugins.

Steigerjb wants **ALL** the eyecandy! :lolflag:

---

### Post by NuclearStr1der on 2009-11-07
Take a look here:

[https://launchpad.net/~compiz/+archive/ppa](https://launchpad.net/~compiz/+archive/ppa)

That should have everything you need ;)
Just add it to your software sources, etc.

---

### Post by steigerjb on 2009-11-07
> **NuclearStr1der said:**
> Take a look here:

[https://launchpad.net/~compiz/+archive/ppa](https://launchpad.net/~compiz/+archive/ppa)

That should have everything you need ;)
Just add it to your software sources, etc.

what do I do?

---

### Post by oktapod on 2009-11-07
System -> Preferences -> CompizConfig Settings Manager

or

type ccsm in terminal.

---

### Post by NuclearStr1der on 2009-11-08
> **steigerjb said:**
> what do I do?

Go the link I gave you earlier.

Click on "Technical Details about this PPA",
and then click on "Read about installing"

That should help you - it's really not that hard to find.

---

### Post by MelDJ on 2009-11-08
add the compiz repo from the site NuclearStr1der gave

then install this package:                  compiz-fusion-plugins-unsupported

---

### Post by steigerjb on 2009-11-08
> **MelDJ said:**
> add the compiz repo from the site NuclearStr1der gave

then install this package:                  compiz-fusion-plugins-unsupported

That didn't get me all, only gave me a few more.

---

### Post by blazemore on 2009-11-09
Right what if I've written a compiz plugin but have never released it?
Do you expect to be able to get that as well??

---

### Post by NuclearStr1der on 2009-11-09
Yeah - now you have ALL of them...

A lot are included by default.

---

### Post by Tholley on 2009-11-09
Check out these sites.
 
[http://my.opera.com/ubuntunerd1/blog/how-to-install-compiz-fusion-in-ubuntu-hardy](http://my.opera.com/ubuntunerd1/blog/how-to-install-compiz-fusion-in-ubuntu-hardy)
 
 
[http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion)
 
These really helped me!

---

### Post by realzippy on 2009-11-09
[http://forum.compiz.org/showthread.php?p=68054](http://forum.compiz.org/showthread.php?p=68054)

---

### Post by steigerjb on 2009-11-09
> **NuclearStr1der said:**
> Yeah - now you have ALL of them...

A lot are included by default.

Plugins I want are the following:

Aquarium
Screensaver
Stackswitch
Freewins
Freescale
Rubix cube
Snow globe
Shelf
Photowheel
CubeModel
Wiimote....

I believe that's all ):P How do I get those?

> **blazemore said:**
> Right what if I've written a compiz plugin but have never released it?
Do you expect to be able to get that as well??

What's your plugin do? I might want it ;)

-------------------------------------------------------------------------

[COLOR="Red"]**Everyone, I know how to get Compiz and set it up. That is not what I am looking for in this thread. I am looking to get those extra plugins listed up there.**[/COLOR]

---

### Post by blazemore on 2009-11-09
> What's your plugin do? I might want it ;)

I didn't really write a plugin, I was just saying you can't expect to get ALL of them, some of them will be in some random obscure branch.

---

### Post by realzippy on 2009-11-09
[I]Plugins I want are the following:

Aquarium
Screensaver
Stackswitch
Freewins
Freescale
Rubix cube
Snow globe
Shelf
Photowheel
CubeModel....

I believe that's all How do I get those?[/I]

As suggested,here:
[http://forum.compiz.org/showthread.php?p=68054](http://forum.compiz.org/showthread.php?p=68054)

It works in Karmic also.

---

### Post by steigerjb on 2009-11-10
> **realzippy said:**
> [I]
I believe that's all How do I get those?[/I]

As suggested,here:
[http://forum.compiz.org/showthread.php?p=68054](http://forum.compiz.org/showthread.php?p=68054)

It works in Karmic also.

I don't know if that will work cuz I tried the script from this guy: [http://mathpages.blogspot.com/2008/06/tips-for-using-compiz-fusion-on-ubuntu.html]("http://mathpages.blogspot.com/2008/06/tips-for-using-compiz-fusion-on-ubuntu.html") and it didn't work

---

### Post by blazemore on 2009-11-11
When you tried out the script, did you install all the required packages beforehand?

---

### Post by Locutus_of_Borg on 2009-11-11
here are all of them:
[http://gitweb.compiz-fusion.org/](http://gitweb.compiz-fusion.org/)


install them by the usual compilation methods
./configure
make
sudo make install

---

### Post by steigerjb on 2009-11-11
> **Locutus_of_Borg said:**
> here are all of them:
[http://gitweb.compiz-fusion.org/](http://gitweb.compiz-fusion.org/)


install them by the usual compilation methods
./configure
make
sudo make install

can you do some examples please, I don't know how to compile

---

### Post by realzippy on 2009-11-11
*Install the packages required for compiling plugins:*

[B]sudo apt-get install compiz-fusion-bcop compiz-dev compizconfig-settings-manager build-essential libtool libglu1-mesa-dev libxss-dev libcairo2-dev libpango1.0-dev git-core
[/B]

------------------------------------------------------
[I]creating directory "compiz" in home folder:
[/I]
**mkdir -p  ~/compiz/**   

*example for screensaver plugin:*                      

**cd ~/compiz**


**git clone git://anongit.compiz-fusion.org/users/pafy/screensaver**


**cd ~/compiz/screensaver**

[I]Now compiling :

[/I]
[B]make clean

make

make install
[/B]

*Restart compiz and ccsm,new plugins can be found in ccsm*

([http://forum.compiz.org/showthread.php?p=68054](http://forum.compiz.org/showthread.php?p=68054))  ;-)

---

### Post by steigerjb on 2009-11-12
> **realzippy said:**
> *Install the packages required for compiling plugins:*
[I]creating directory "compiz" in home folder:
[/I]
**mkdir -p  ~/compiz/**

what would be the codes to put the plugins in a compiz folder in my downloads folder?

---

### Post by realzippy on 2009-11-12
mkdir -p ~/compiz/
*is the same as:* 
mkdir -p /home/youruserbutdontknowyourusername/compiz/

*So when your Downloadfolder is (as default in Karmic):*
/home/youruserbutdontknowyourusername/Downloads/
*same as*
~/Downloads/
[I]so to create a folder named compiz in Downloads:
[/I]
**mkdir -p ~/Downloads/compiz/**

*mind that if you do so* cd ~/compiz *has to be:* cd ~/Downloads/compiz *and* cd ~/compiz/screensaver *-you go tit!:* cd ~/Downloads/compiz/screensaver


But why not using nautilus and create new folder by right click????????

---

### Post by steigerjb on 2009-11-19
> **realzippy said:**
> mkdir -p ~/compiz/
*is the same as:* 
mkdir -p /home/youruserbutdontknowyourusername/compiz/

*So when your Downloadfolder is (as default in Karmic):*
/home/youruserbutdontknowyourusername/Downloads/
*same as*
~/Downloads/
[I]so to create a folder named compiz in Downloads:
[/I]
**mkdir -p ~/Downloads/compiz/**

*mind that if you do so* cd ~/compiz *has to be:* cd ~/Downloads/compiz *and* cd ~/compiz/screensaver *-you go tit!:* cd ~/Downloads/compiz/screensaver


But why not using nautilus and create new folder by right click????????

where did i go wrong:

```
joe@joe-laptop:~$ 
joe@joe-laptop:~$ mkdir -p ~/Downloads/compiz/
joe@joe-laptop:~$ cd ~/Downloads/compiz
joe@joe-laptop:~/Downloads/compiz$ git clone git://anongit.compiz-fusion.org/users/pafy/screensave
The program 'git' is currently not installed.  You can install it by typing:
sudo apt-get install git-core
git: command not found
joe@joe-laptop:~/Downloads/compiz$ git clone git://anongit.compiz-fusion.org/users/pafy/screensaver
The program 'git' is currently not installed.  You can install it by typing:
sudo apt-get install git-core
git: command not found
joe@joe-laptop:~/Downloads/compiz$ sudo apt-get install git-core
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dvdrip-doc python-pexpect xulrunner-1.9.2 xulrunner-1.9.3
  libevent-execflow-perl libnet-ssleay-perl librsvg2-2.18-cil libintl-perl
  libgdata1.4-cil transcode-utils transcode-doc transfig subtitleripper
  libxine1-ffmpeg libevent-rpc-perl ogmtools gtk2-ex-formfactory-perl
  transcode fping netpbm libwnck2.20-cil anyevent-perl sox gocr libevent-perl
  libnetpbm10 xine-ui libio-socket-ssl-perl libjpeg-progs
  libgnomedesktop2.20-cil libnet-libidn-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libdigest-sha1-perl liberror-perl
Suggested packages:
  git-doc git-arch git-cvs git-svn git-email git-daemon-run git-gui gitk
  gitweb
The following NEW packages will be installed:
  git-core libdigest-sha1-perl liberror-perl
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,175kB of archives.
After this operation, 14.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://mirror.cc.columbia.edu karmic/main liberror-perl 0.17-1 [23.8kB]
Get:2 http://mirror.cc.columbia.edu karmic/main libdigest-sha1-perl 2.12-1 [26.5kB]
Get:3 http://mirror.cc.columbia.edu karmic/main git-core 1:1.6.3.3-2 [7,125kB]
Fetched 7,175kB in 45s (157kB/s)                                               
Selecting previously deselected package liberror-perl.
(Reading database ... 270696 files and directories currently installed.)
Unpacking liberror-perl (from .../liberror-perl_0.17-1_all.deb) ...
Selecting previously deselected package libdigest-sha1-perl.
Unpacking libdigest-sha1-perl (from .../libdigest-sha1-perl_2.12-1_i386.deb) ...
Selecting previously deselected package git-core.
Unpacking git-core (from .../git-core_1%3a1.6.3.3-2_i386.deb) ...
Processing triggers for man-db ...
Setting up liberror-perl (0.17-1) ...
Setting up libdigest-sha1-perl (2.12-1) ...
Setting up git-core (1:1.6.3.3-2) ...
joe@joe-laptop:~/Downloads/compiz$ git clone git://anongit.compiz-fusion.org/users/pafy/screensaver
Initialized empty Git repository in /home/joe/Downloads/compiz/screensaver/.git/
remote: Counting objects: 176, done.
00% (172/172), done.
remote: Total 176 (delta 102), reused 0 (delta 0)
Receiving objects: 100% (176/176), 44.76 KiB | 17 KiB/s, done.
Resolving deltas: 100% (102/102), done.
joe@joe-laptop:~/Downloads/compiz$ cd ~/compiz/screensaver
bash: cd: /home/joe/compiz/screensaver: No such file or directory
joe@joe-laptop:~/Downloads/compiz$ cd ~/Downloads/compiz/screensaver
joe@joe-laptop:~/Downloads/compiz/screensaver$ make clean
Makefile:48: *** [ERROR] Compiz not installed.  Stop.
joe@joe-laptop:~/Downloads/compiz/screensaver$ make
Makefile:48: *** [ERROR] Compiz not installed.  Stop.
joe@joe-laptop:~/Downloads/compiz/screensaver$ make install
Makefile:48: *** [ERROR] Compiz not installed.  Stop.
joe@joe-laptop:~/Downloads/compiz/screensaver$ 
```

---

### Post by steigerjb on 2009-11-25
> **realzippy said:**
> *Install the packages required for compiling plugins:*

[B]sudo apt-get install compiz-fusion-bcop compiz-dev compizconfig-settings-manager build-essential libtool libglu1-mesa-dev libxss-dev libcairo2-dev libpango1.0-dev git-core
[/B]

------------------------------------------------------
[I]creating directory "compiz" in home folder:
[/I]
**mkdir -p  ~/compiz/**   

*example for screensaver plugin:*                      

**cd ~/compiz**


**git clone git://anongit.compiz-fusion.org/users/pafy/screensaver**


**cd ~/compiz/screensaver**

[I]Now compiling :

[/I]
[B]make clean

make

make install
[/B]

*Restart compiz and ccsm,new plugins can be found in ccsm*

([http://forum.compiz.org/showthread.php?p=68054](http://forum.compiz.org/showthread.php?p=68054))  ;-)

Can you redo the codes again???...put them in the downloads folder...i tried you post (#21) but it didn't work.

---

### Post by realzippy on 2009-12-10
Have you run 

[B]sudo apt-get install compiz-fusion-bcop compiz-dev compizconfig-settings-manager build-essential libtool libglu1-mesa-dev libxss-dev libcairo2-dev libpango1.0-dev git-core
[/B]

before?

---

### Post by steigerjb on 2009-12-11
> **realzippy said:**
> Have you run 

[B]sudo apt-get install compiz-fusion-bcop compiz-dev compizconfig-settings-manager build-essential libtool libglu1-mesa-dev libxss-dev libcairo2-dev libpango1.0-dev git-core
[/B]

before?


just did. what do I do next?

---

### Post by blazemore on 2009-12-13
Download and run this script
[http://www.box.net/shared/sbq91nzy8o](http://www.box.net/shared/sbq91nzy8o)

---

### Post by steigerjb on 2009-12-16
> **blazemore said:**
> Download and run this script
[http://www.box.net/shared/sbq91nzy8o](http://www.box.net/shared/sbq91nzy8o)

I would still like the following plugins:

Aquarium
Stackswitch
Rubix cube
Wiimote (not sure offical name)
Freescale

**[COLOR="Red"]Other:[/COLOR]** We all ready know Compiz can do the snap feature like Windows 7! (psh Win7, Ubuntu had it first!) My question is, can Ubuntu do the other 2 features too?: [http://www.youtube.com/watch?v=xO_7sbFEJrE]("http://www.youtube.com/watch?v=xO_7sbFEJrE") (Peek & shake)

---

### Post by locote on 2009-12-27
> **NuclearStr1der said:**
> Take a look here:

[https://launchpad.net/~compiz/+archive/ppa]("https://launchpad.net/%7Ecompiz/+archive/ppa")

That should have everything you need ;)
Just add it to your software sources, etc.


Thanks this helped

---

### Post by steigerjb on 2009-12-31
> **steigerjb said:**
> I would still like the following plugins:

Aquarium
Stackswitch
Rubix cube
Wiimote (not sure offical name)
Freescale
Wizard

**[COLOR="Red"]Other:[/COLOR]** We all ready know Compiz can do the snap feature like Windows 7! (psh Win7, Ubuntu had it first!) My question is, can Ubuntu do the other 2 features too?: [http://www.youtube.com/watch?v=xO_7sbFEJrE]("http://www.youtube.com/watch?v=xO_7sbFEJrE") (Peek & shake)

bump

---

### Post by steigerjb on 2010-01-20
> **steigerjb said:**
> Is there a way I can install **ALL** the Compiz plugins (Main, extra, unsupported, experimental,...) all at once?

Though, I don't even know how to do one at a time.

I already did

```
sudo apt-get install compizconfig-settings-manager
```

course that's not nearly all the plugins.

Steigerjb wants **ALL** the eyecandy! :lolflag:

bravo gotbletu!:
[http://www.youtube.com/watch?v=b616WSM-uYw](http://www.youtube.com/watch?v=b616WSM-uYw)

thanks a bunch! way easy way! party time with Compiz :guitar:

---

### Post by Throbbing Gristle on 2010-01-24
> **steigerjb said:**
> bravo gotbletu!:
[http://www.youtube.com/watch?v=b616WSM-uYw](http://www.youtube.com/watch?v=b616WSM-uYw)

thanks a bunch! way easy way! party time with Compiz :guitar:
Sweet!!!!!! Been looking for these I don't really no all the cool places to look great :D

---

### Post by PenguinInside on 2010-01-24
Wait, not all the plugins are compatible with each other, right?

---

### Post by Throbbing Gristle on 2010-01-24
There are some limitations. Cannot run everything at once. Compiz usually give a prompt saying to disable something that I have seen.

---

### Post by pocketman on 2011-02-17
Sorry to dredge up such an old post, but I was just looking for the same thing, and this post popped up in my search. 

If you're on Ubuntu 10.10, it's even easier. Just go to synaptic (system -> administrtion -> synaptic pkg mgr), search for compiz, click on 'compiz-fusion-plugins-extra', and hit apply. 

It's that easy, now you have all the plugins. :)

---

### Post by beew on 2011-02-17
> **pocketman said:**
> Sorry to dredge up such an old post, but I was just looking for the same thing, and this post popped up in my search. 

If you're on Ubuntu 10.10, it's even easier. Just go to synaptic (system -> administrtion -> synaptic pkg mgr), search for compiz, click on 'compiz-fusion-plugins-extra', and hit apply. 

It's that easy, now you have all the plugins. :)

Don't think so, maybe compiz-fusion-plugins-unsupported but that would remove compiz-fusion-plugins-extra. The extra package doesn't have, for example, the screensaver plugin and cube Atlantis.

---

