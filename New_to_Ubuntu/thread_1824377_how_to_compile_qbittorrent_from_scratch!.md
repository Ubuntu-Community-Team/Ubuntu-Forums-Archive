---
title: "how to compile qbittorrent from scratch!"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by the-new-x on 2011-08-13
Hello everyone, I have another question, I am still a super noob in Linux, as embarrassing as this is, but i need to know how to compile a program in Ubuntu 11.04, qbittorrent to be more exact ([http://qbittorrent.sourceforge.net/download.php](http://qbittorrent.sourceforge.net/download.php)), but just tell me the way in general and I will figure it out (I hope!).

Any help would be greatly appreciated, thanks for your time!

---

### Post by haqking on 2011-08-13
> **the-new-x said:**
> Hello everyone, I have another question, I am still a super noob in Linux, as embarrassing as this is, but i need to know how to compile a program in Ubuntu 11.04, qbittorrent to be more exact ([http://qbittorrent.sourceforge.net/download.php](http://qbittorrent.sourceforge.net/download.php)), but just tell me the way in general and I will figure it out (I hope!).

Any help would be greatly appreciated, thanks for your time!

choose binary and then your version and follow instructions given,

It will install using apt-get from command line

---

### Post by TeoBigusGeekus on 2011-08-13
Extract it somewhere, say your Desktop, navigate in the folder in which you extracted it via command line
```
cd ~/Desktop/whatever
```
and then
```
./configure
```
followed by
```
make
```
and
```
sudo make install
```

---

### Post by Brushstroke on 2011-08-13
Why would you need to compile that? It's available in the Natty repos. Save yourself the trouble and just install it through there.

---

### Post by the-new-x on 2011-08-13
> **TeoBigusGeekus said:**
> Extract it somewhere, say your Desktop, navigate in the folder in which you extracted it via command line
```
cd ~/Desktop/whatever
```and then
```
./configure
```followed by
```
make
```and
```
sudo make install
```
thanks for the fast reply!
But it is not working, after i write the cd ~/desktop/qbittorrent-2.8.5 command, an error occurs (tatah@Satellite-A505:~$ cd ~/desktop/qbittorrent-2.8.5
bash: cd: /home/tatah/desktop/qbittorrent-2.8.5: No such file or directory)
what can i do about that. And again, thank you!

---

### Post by the-new-x on 2011-08-13
> **Brushstroke said:**
> Why would you need to compile that? It's available in the Natty repos. Save yourself the trouble and just install it through there.
Well, simply because a newer version is out (2.8.5 instead of the 2.6.9) and also because a lot of other programs are not found in the software center even after installing a hell lot of extra repositories, so I figured that I will need to know how to compile a program sooner or later, so why not start right now!

---

### Post by Brushstroke on 2011-08-13
> **the-new-x said:**
> Well, simply because a newer version is out (2.8.5 instead of the 2.6.9) and also because a lot of other programs are not found in the software center even after installing a hell lot of extra repositories, so I figured that I will need to know how to compile a program sooner or later, so why not start right now!
There's a PPA for it that'll give you the latest version. Well, it'll give you 2.8.4 but I wouldn't doubt the author of this PPA, who also is the creator of qBitTorrent, will upgrade the PPA soon. All I'm saying is that it would be a lot less of a hassle to use a PPA to get the latest (or near-latest) version than compiling from source. I only compile if I absolutely have to.

[https://launchpad.net/~hydr0g3n/+archive/ppa]("https://launchpad.net/%7Ehydr0g3n/+archive/ppa") 

There's the PPA. 

Just run: 

```
sudo add-apt-repository ppa:hydr0g3n/ppa
sudo apt-get update
```And you'll have 2.8.4 in the repos instead of having to compile.

Or...if the reason you're doing this is to learn how to compile, be my guest! Go ahead!

---

### Post by snip3r8 on 2011-08-13
> **the-new-x said:**
> Well, simply because a newer version is out (2.8.5 instead of the 2.6.9) and also because a lot of other programs are not found in the software center even after installing a hell lot of extra repositories, so I figured that I will need to know how to compile a program sooner or later, so why not start right now!


It is good to learn this, but when compiling you need to have all the right libraries installed,judging from the name of qbittorrent you may need the qt libraries.

---

### Post by haqking on 2011-08-13
> **Brushstroke said:**
> There's a PPA for it that'll give you the latest version. Well, it'll give you 2.8.4 but I wouldn't doubt the author of this PPA, who also is the creator of qBitTorrent, will upgrade the PPA soon. All I'm saying is that it would be a lot less of a hassle to use a PPA to get the latest (or near-latest) version than compiling from source. I only compile if I absolutely have to.

[https://launchpad.net/~hydr0g3n/+archive/ppa]("https://launchpad.net/%7Ehydr0g3n/+archive/ppa") 

There's the PPA. 

Just run: 

```
sudo add-apt-repository ppa:hydr0g3n/ppa
sudo apt-get update
```And you'll have 2.8.4 in the repos instead of having to compile.

Or...if the reason you're doing this is to learn how to compile, be my guest! Go ahead!

I said that in my first post.

but yeah if you want to learn to compile then no harm in it, common question on here so good time to learn.

---

### Post by TeoBigusGeekus on 2011-08-13
> **the-new-x said:**
> thanks for the fast reply!
But it is not working, after i write the cd ~/desktop/qbittorrent-2.8.5 command, an error occurs (tatah@Satellite-A505:~$ cd ~/desktop/qbittorrent-2.8.5
bash: cd: /home/tatah/desktop/qbittorrent-2.8.5: No such file or directory)
what can i do about that. And again, thank you!

It should be Desktop and not desktop: linux is case sensitive.

---

### Post by the-new-x on 2011-08-14
Thanks for all the replies, especially you TeoBigusGeekus.

So the "D"esktop worked, but now it is saying that i need some libraries as someone mentioned above, but from where do i get these!?

Again, thanks for the help, and here is the error I am getting:

tatah@Satellite-A505:~$ cd ~/Desktop/fast
tatah@Satellite-A505:~/Desktop/fast$ ./configure
Configuring qbittorrent ...
Verifying Qt 4 build environment ... fail

Reason: Unable to find the 'qmake' tool for Qt 4.

Be sure you have a proper Qt 4.0 build environment set up.  This means not
just Qt, but also a C++ compiler, a make tool, and any other packages
necessary for compiling C++ programs.

If you are certain everything is installed, then it could be that Qt 4 is not
being recognized or that a different version of Qt is being detected by
mistake (for example, this could happen if $QTDIR is pointing to a Qt 3
installation).  At least one of the following conditions must be satisfied:

 1) --qtdir is set to the location of Qt
 2) $QTDIR is set to the location of Qt
 3) QtCore is in the pkg-config database
 4) qmake is in the $PATH

This script will use the first one it finds to be true, checked in the above
order.  #3 and #4 are the recommended options.  #1 and #2 are mainly for
overriding the system configuration.

---

### Post by Elfy on 2011-08-14
Basically you will need to install things you might need. 

Installing qt4-qmake should get that 

```
sudo apt-get install qt4-qmake
```

if you've not installed build essential yet, then I would do that too

```
sudo apt-get install qt4-qmake build-essential
```

You can search the cache for things as you need 

For instance 

```
apt-cache search qmake
```

returns

```
qt3-designer - graphical designer for Qt3 applications
qt3-dev-tools - Qt3 development tools
qconf - A nice configure script for your qmake-based project
qt3-assistant - The Qt3 assistant application
qt4-qmake - Qt 4 qmake Makefile generator tool
```

---

### Post by the-new-x on 2011-08-14
> **forestpiskie said:**
> Basically you will need to install things you might need. 

Installing qt4-qmake should get that 

```
sudo apt-get install qt4-qmake
```if you've not installed build essential yet, then I would do that too

```
sudo apt-get install qt4-qmake build-essential
```You can search the cache for things as you need 

For instance 

```
apt-cache search qmake
```returns

```
qt3-designer - graphical designer for Qt3 applications
qt3-dev-tools - Qt3 development tools
qconf - A nice configure script for your qmake-based project
qt3-assistant - The Qt3 assistant application
qt4-qmake - Qt 4 qmake Makefile generator tool
```
thanks for the reply, i am installed qt4 right now, and will install build essential afterwards, but may I ask, from where do you people know all of this code, is there some sort of e-book or a forum dedicated for that, or you just ask and get, or just get them from official website!?

---

### Post by Elfy on 2011-08-14
I learnt all I know - which is not all that much - here or on other forums.

Google is useful too - though I do find it better to use something like googlubuntu if I'm specifically searching for ubuntu. 

You might find some things to interest you in here - [http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

---

### Post by the-new-x on 2011-08-14
Ok, so I have installed qt4-qmake (successfully) and the build essential (successfully too) but I am still getting the same error, help please!

---

### Post by the-new-x on 2011-08-14
> **forestpiskie said:**
> I learnt all I know - which is not all that much - here or on other forums.

Google is useful too - though I do find it better to use something like googlubuntu if I'm specifically searching for ubuntu. 

You might find some things to interest you in here - [http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)
thanks for the reply, the link looks really helpful, reading the contents right now!

---

### Post by Elfy on 2011-08-14
[s]You might need qt4-dev-tools.[/s]

To be honest I rarely need to install like this and forget between times.

Edit - a quick look at the qtbittorent page and it's wiki gets this - [http://sourceforge.net/apps/mediawiki/qbittorrent/index.php?title=Debian_/_Ubuntu](http://sourceforge.net/apps/mediawiki/qbittorrent/index.php?title=Debian_/_Ubuntu)

Try looking about for the information you need at the same time as asking for help - it'll work wonders :)

---

### Post by the-new-x on 2011-08-14
So what you are saying is that i need to read the wiki always, and i will find everything i need in there, and i will definitely do that, thanks again for you help.
-a happy Ubuntu 11.04 user!

---

### Post by Elfy on 2011-08-14
> So what you are saying is that i need to read the wiki alwaysNot at all - sometimes there something that helps if it gets read - other times there isn't.

What I am saying is that if you look and there is something to read - read it :D

---

### Post by the-new-x on 2011-08-14
Will do!

---

