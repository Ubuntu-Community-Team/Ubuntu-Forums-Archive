---
title: "How To: Compile/Install Plugins for Pidgin"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-09-23
**[SIZE="4"]How to compile/install additional plugins for Pidgin[/SIZE]**

Reference System
1. Ubuntu Feisty Fawn 7.04
2. Pidgin v 2.2.0 (possibly I'll write a tutorial how to compile this in the future.  It requires a lot of dependencies!!)
3. Purple Plugin Pack 2.1.1
4. OTR Plugin / Library and Toolkit - Versions 3.1.0

Plugins to be installed in this guide
1. Purple Plugin Pack (contains roughly over 30 pidgin plugins): _[http://plugins.guifications.org/trac/wiki/PluginPack](http://plugins.guifications.org/trac/wiki/PluginPack)_
2. OTR (Off-The-Record Recording): _[http://www.cypherpunks.ca/otr/](http://www.cypherpunks.ca/otr/)_

Requirements
1. Working Internet Connection
2. Installed version of Pidgin
3. Dependencies -- build-essential package, linux-headers package
If you havent installed these do the following:
```
sudo aptitude install build-essential linux-headers-`uname -r`
```
Notice in the above `uname -r` these are backticks and not quotes!!

**[SIZE="3"]Purple Plugin Pack[/SIZE]**
1. Download the sources:
```

cd ~
mkdir pidgin
cd pidgin
wget http://downloads.guifications.org/plugins//Plugin%20Pack/purple-plugin_pack-2.1.1.tar.gz 

```

2. Install required dependencies for Pidgin
```

sudo aptitude install gettext libgtk2.0-dev libglib2.0-dev libxml2-dev libgtkspell-dev libgpg-error-dev libgcrypt11-dev
wget http://freshmeat.net/redir/talkfilters/37168/url_tgz/talkfilters-2.3.7.tar.gz

```

The pidgin-dev package is also required if YOU HAVE NOT COMPILED AND INSTALLED pidgin.  This is contained in gutsy's repository by default, but not in earlier releases (feisty, edgy, etc).
If using gutsy, you can install this package with:
```

sudo aptitude install pidgin-dev

```

For those with earlier releases, the pidgin-dev package may be found here:  [http://packages.debian.org/sid/pidgin-dev](http://packages.debian.org/sid/pidgin-dev)
After downloading, this package would be installed by: sudo dpkg -i pidgin-dev
**Unconfirmed -- Others have reported that installing the gaim-dev libraries is all that is needed.  This can be done:  sudo aptitude install gaim-dev

To install the talkfilters dependency -- the file we downloaded in the last step
```

tar zxvf talkfilters-2.3.7.tar.gz
cd talkfilters-2.3.7
./configure --prefix=/usr
make
sudo make install

```

3.  Compile and install the purple plugin pack
```

cd ~/pidgin
tar zxvf purple-plugin_pack-2.1.1.tar.gz
cd purple-plugin_pack-2.1.1

```

The following process will install all the available plugins.  By default the purple plugin developers considered some of the their plugins dangerous, and deactivated some of the plugins by default -- these are specifically the **Broadcast and Group Message Plugins**.  More information is available here: _[http://plugins.guifications.org/trac/wiki/PluginPack#Faq4](http://plugins.guifications.org/trac/wiki/PluginPack#Faq4)_
To activate these plugins do the following, if you do not want to activate the additional non-default plugins, then skip this step:

```
for i in *; do cd $i && touch .build && cd ..; done

```

At the time of writing this guide I could not get the ignorance plugin to be compiled.  I'm not sure why (Please contact me if you are successful).  To remove this from the list of modules to be compiled:
```
rm ignorance/.build
```

Compile the plugin pack:
```

./configure --prefix=/usr
make

```

Either 
```
**sudo make install** or **checkinstall**
```
will install the package

Checkinstall allows the package to be installed through the apt user system.  In some cases however checkinstall does have some limitations (ie static libraries).  I used the simple sudo make install to install my package, however users insistent on not installing packages outside the apt tree may use checkinstall instead.

**[SIZE="3"]OTR (Off The Record Plugin)[/SIZE]**
1. Download the required sources
```

cd ~/pidgin
wget http://www.cypherpunks.ca/otr/libotr-3.1.0.tar.gz http://www.cypherpunks.ca/otr/pidgin-otr-3.1.0.tar.gz
tar zxvf libotr-3.1.0.tar.gz
tar zxvf pidgin-otr-3.1.0.tar.gz

```

2. Compile and install the source packages
```

cd libotr-3.1.0
./configure --prefix=/usr
make

```

Either 
```
**sudo make install** or **checkinstall**
```
will install the package

```

cd ~/pidgin/pidgin-otr-3.1.0
./configure --prefix=/usr
make

```

Either 
```
**sudo make install** or **checkinstall**
```
will install the package

That should be it for the installation of the plugins.  These plugins can be activated and individually configured in Pidgin under the Tools->Plugins menu

**Thanks to Snille and Sturmeh for providing corrections and suggestions to these instructions

---

### Post by ST.x on 2007-09-26
[COLOR=Black]There is no build file inside the ignorance folder, so 'rm ignorance/.build' gives 'no such file or directory'. Also '/.configure --prefix=/usr/' should be '**./configure** --prefix=/usr' and even then it is saying:
[/COLOR]```
checking for PURPLE... configure: error: Package requirements (purple) were not met:

No package 'purple' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PURPLE_CFLAGS
and PURPLE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

And then 'make' just gives: make: *** No targets specified and no makefile found.  Stop.

thanks


---

### Post by kevdog on 2007-09-27
Do you have pidgin installed - and if the answer is yes -- do you know the version, and how did you install it??

---

### Post by ST.x on 2007-09-27
Yes, I have version 2.2 but used the am64 deb from getdeb, it seems to be working fine at the moment, should I try and compile it then?

---

### Post by Snille on 2007-09-27
Hi, I think you are missing the pidgin-dev package.
sudo apt-get install pidgin-dev

Or search in Synaptec for "pidgin" and install the pidgin-dev package.

That did it for me. :)

---

### Post by ST.x on 2007-09-27
Okay, I installed pidgin this time by compiling and it's all good now. So I guess it only works with compiled versions.

edit: Snille: lol I just missed your post, but thanks anyway. btw since I compiled it, what happens when there's a new version of Pidgin? I can't uninstall the current one since it wont be listed in the packages. Would I just compile again? with the new version.

---

### Post by devzero on 2007-09-28
Hi,

i wonder, why the plugins wont work under linux the same way than in windoze,
just copy the la/so files in the required folder and thats it.

I cant compile the extended prefs plugin too, with the same fault.
I event dont have pidgin-dev in synaptic, i needed to download pidgin
from getdeb too.
I installed pidgin 2.2.0 where can i get the dev files in a deb pack?
Or doesnt it just exist?

thanks four your help

---

### Post by kevdog on 2007-09-28
Couple of things Ive found out

Pidgin-dev -- Ive found this package on the net, however its not in Feisty's repository.  Im not sure if this is in Gusty's repository.  To the best of my knowledge this package contains the libpurple libraries.  When you compile from source this library is built and installed -- hence I believe at this point to make this tutorial work you will have at least needed to compile Pidgin from source for Feisty.  Possibly these libraries will be included in Gusty's repositories.

As far as when a new version comes along (Ive done this part), go into the directory where you originally compiled pidgin and type:
sudo make uninstall

Ths will uninstall pidgin.  If you install a newer version from source, you will not need to reinstall/compile the plugins. (Unless you want to).

---

### Post by devzero on 2007-09-28
Hi,

thanks for the reply, an help I heard, if pidgin will added in the repository, I may get problems
with updating it?

So I have to check how can i save my settings and logs, can anyone tell me if they are all
in ~/.purple or are anywhre else some userdata?

So in fact if i want to uninstall compiled software, i make a place somehow as uninstall
and store the install files there?

cheers devzero

---

### Post by Sturmeh on 2007-09-30
Ok, it worked after installing pidgin-dev ( i didn't need to compile my pidgin. )

But, i do not have 2 of the listed plugins...
Broadcast, and Group Message. ( On the site they are flagged for abuse. xD )

Are those 2 plugins supposed to be visible, or is it correctly not there?

NOTE:

> cd libort-3.1.0

should be...

> cd libotr-3.1.0

Off The Record, not Off Record The. xD ( its in the second box in the OTR compile instructions. )

---

### Post by kevdog on 2007-09-30
Ok two things

1. Just to confirm -- you did not need to install pidgin from source -- only the pidgin-dev package??  If this is true I will change the instructions -- Thanks!

2. Those two plugins you mentioned are deactivated by default.  Hence the reason for the steps I mentioned:

for i in *; do cd $i && touch .build && cd ..; done

Another way you could do this however would be to enter into the individual directories of these two plugins (sorry Im not at my computer right now to tell you their exact names), and just type touch .build.

Once the .build file is present, just recompile with .configure, make, etc.

---

### Post by devzero on 2007-10-01
Hi 

Where did you get the precompiled dev package? i searched at google fpr pidgin-dev and *.deb but i got only forumposts. I even didnt find the source version of it.. Somehow I
make somehing wrong with my search string.

---

### Post by kevdog on 2007-10-01
Not sure if this will help since it lists it needs some dependencies, which usually need to be installed, however I guess you could always try to install this and see what happens:

[http://packages.debian.org/sid/pidgin-dev](http://packages.debian.org/sid/pidgin-dev)

---

### Post by Sturmeh on 2007-10-08
Thanks, just went through an re-install of ubuntu, and couldn't find the error i picked up last time, only to see you fixed it. xD

I think it broke pidgin *EDIT* nope, just the first start froze.

I used "for i in *; do cd $i && touch .build && cd ..; done" but the groupmsg and broadcast plugin are still hidden.

Heh.

---

### Post by kevdog on 2007-10-08
If that code isnt working for you, you will have to manually enter the groupmsg and broadcast directories, and once inside, just type 
touch .build

If you dont want to compile and install all the plugins you could just compile and install these two missing plugins.

While in the respective directories type:
./configure
make 
sudo make install

---

### Post by ninjaprawn on 2007-10-13
im getting nowhere! after compiling pidgin 2.2.1 from source, tried going thru this tutorial!

it went wrong at sudo aptitude install pidgin-dev. it couldnt find it!i couldnt apt-get it or find it in synaptic, so googled it and tried to install. then got dependency error.

missing libpurple-dev, did the same with that, got a dependency error.
missing libpurple0, did the same with that, and got another dependency error. 
missing pidgin-dev, which i knew i already had, but googled and tried to install anyway, at which point i got an error saying i had a later version installed! 

now im completly stuck!

bearing in mind i had a newer version of pidgin-dev installed, i skipped this part, carried on, and it all worked perfectly!

loads of plugins!

---

### Post by kevdog on 2007-10-13
It says in the tutuorial if you have compiled pidgin, skip installing pidgin-dev

---

### Post by ninjaprawn on 2007-10-13
sorry, i know, i rushed thru it, didnt realy read it properly.

is there a plugin for sounds? or do i need to put a specific command in the sound section in the preferences?

at the minute im stuck with a console beep!

---

### Post by kevdog on 2007-10-13
alsamixer is for gnome, but not specifically pidgin

---

### Post by cRoW2k on 2007-10-22
Same problem. I've touch ALL plugins directory but broadcast and group messages doesn't apper:

Purple plugins to be built.......:
         autorejoin autoreply awaynotify bash
         chronic dice eight_ball flip
         highlight ignore irc-more irchelper
         listhandler napster oldlogger showoffline
         simfix slashexec snpp sslinfo

Build pidgin plugins.............: yes
Installing pidgin plugins to.....: /usr/lib/pidgin
Installing pidgin plugin data to.: /usr/share
Pidgin plugins to be built.......:
         album bit blistops buddytime
         convbadger difftopic gRIM hideconv
         ignorance irssi lastseen mystatusbox
         nicksaid plonkers schedule sepandtab
         stocker switchspell talkfilters xchat-chats
         xmmsremote

I've try also to pass the --with-plugins=blabla1,blabla2 but without result.

Sure that these works?

---

### Post by kevdog on 2007-10-22
If you arent getting the plugins built that you want, change into each plugin subdirectory and then type touch .build

Here is a complete answer:
> Q. How do I enable a plugin you have not enabled by default?
A. There are a few ways if you're NOT on Windows. We will cover Windows in a separate question, as it is a different process. You can touch plugindir/.build from the top level source directory and then run the configure script again; this is the easiest way. The second way is to do a for loop in your shell, similar to this for bash: for i in *; do cd $i && make && su -c 'make install' && cd ..; done. The third way is to run the configure script with the argument --with-plugins=plugin1,plugin2,...,pluginN where you specify a comma delimited list of the plugins you want to build. After running the configure script in either way mentioned here, build and install as normal.

---

### Post by atze76 on 2007-10-31
I tried all three approaches:
1) automatically going through all plug-in directories an updating the date of the .build files with "touch .build"
2) manually doing the same thing as in 1), namely entering every plug-in directory and updating the .build files by "touch .build"
3) and also tried to specifying the plug-ins that I want to have using the "configure" option "--with-plugins=<PLUGIN-NAME>"

But as you can see below, some plug-ins are not compiled and I don't have a clue why not. For example I would like to have the mystatusbox plug-in but it doesn't matter what I do, the compiled set of plug-ins always stay the same (as listed below). Does anyone have a suggestion?

```

purple-plugin_pack 2.2.0 Configuration complete

Debugging enabled................: no

Build purple plugins.............: yes
Installing purple plugins to.....: /opt/pidgin/share/plugins/lib/purple-2
Installing purple plugin data to.: /opt/pidgin/share/plugins/share
Purple plugins to be built.......:
         autoreply bash dewysiwygification dice
         eight_ball flip highlight ignore
         irc-more irchelper listhandler oldlogger
         showoffline simfix slashexec snpp
         sslinfo

Build pidgin plugins.............: no

Build finch plugins..............: no

Type make to compile

```

---

### Post by kevdog on 2007-10-31
> You can touch plugindir/.build from the top level source directory and then run the configure script again; this is the easiest way. The second way is to do a for loop in your shell, similar to this for bash: for i in *; do cd $i && make && su -c 'make install' && cd ..; done. The third way is to run the configure script with the argument --with-plugins=plugin1,plugin2,...,pluginN where you specify a comma delimited list of the plugins you want to build. After running the configure script in either way mentioned here, build and install as normal.

That was taken directly from the plugin site.  Are you sure you have a directory for the mystatus plugin.  You could theoretically go into this directly, touch the .build file. but also run ./configure, make, sudo make install only in this plugin directory to only install this plugin.

---

