---
title: "How to enable PHP GD image library?"
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by zoon_unit on 2006-09-07
I've currently installed the Ubuntu 6.06 LAMP setup in a server configuration, but the PHP GD image library does not appear when running phpinfo().  How does one install/enable the GD image library with this version of Ubuntu??

---

### Post by az on 2006-09-07
sudo apt-get install php5-gd

---

### Post by zoon_unit on 2006-09-07
Actually, the PHP and GD libraries are already installed, but for some reason, PHP doesn't see the libraries.  Here's what's installed on my system, per Synaptic:

libapache2-mod-php5  version: 5.1.2
libgd2-noxpm  version: 2.0.33
libjpeg62     version: 6b-11
libpng12-0    version: 1.2.8rel-5

When I run phpinfo() no GD library is recognized

????

---

### Post by zoon_unit on 2006-09-08
> **azz said:**
> sudo apt-get install php5-gd

Thanks!  That worked.  Even though all the proper libraries were installed, they didn't work together until I ran this command.  Many thanks.

---

### Post by tbonius on 2006-09-08
The image libraries were installed.. but not the PHP classes that use those libraries. :)

T

---

### Post by got_nix on 2006-09-23
I already installed php5-gd but still see nothing of gd in my phpinfo() output.. :( dont get it

---

### Post by dolarsrg on 2006-10-22
Maybe you have to restart apache. Well, I hope so :)

---

### Post by unclepete on 2006-12-24
I had exactly the same problem. I followed the advice and installed the php5-gd package and then restarted apache.

All is now ggodness :)

Thanks for the help

---

### Post by biofedora on 2007-04-23
Hi, 
I am a Fedora user making the jump to Ubuntu and all has been fabulous thus far. I have the Ubuntu 6.10 LAMP server up and running. However, I need to get GD going. I tried your suggestion:
    sudo apt-get install php5-gd
but I keep getting the following request:
Media change: please insert the disc labeled
 'Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)'
in the drive '/cdrom/' and press enter

I only have a 6.10 disk so have hit a roadblock here. I tried the 6.10 server disk and I just kept getting the same message. Am I making a newbie mistake here i.e. incorrect apt-get configuration? I was under the impression that apt-get worked like yum and went out online to gather packages for installation. 

If I am posting in the wrong place my apologies - give me hell and I will repost. 

Thanks in advance.

---

### Post by dzv on 2007-04-24
> **biofedora said:**
> Hi, 
I am a Fedora user making the jump to Ubuntu and all has been fabulous thus far. I have the Ubuntu 6.10 LAMP server up and running. However, I need to get GD going. I tried your suggestion:
    sudo apt-get install php5-gd
but I keep getting the following request:
Media change: please insert the disc labeled
 'Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)'
in the drive '/cdrom/' and press enter


I was having the same issue, but I found the solution here:

[http://ubuntuserver.info/]("http://ubuntuserver.info/")

In short, you need to comment a line in /etc/apt/sources.list

> The first reference to a source is on the third line, this tells the apt-get software to look on the installation CD-Rom to try to find the software you requested, although this can become a bit of a pain to put in a CD every time you want to install some software, so if you add a # before that line it will be ignored.

---

### Post by biofedora on 2007-04-24
Thanks for replying dzv. I remmed out the 3rd line but still could not get GD installed i.e. on "apt-get install php5-gd" after "apt-get update" the php5-gd package could still not be found. I found some help with GD and apt-get sources.lst choices in another thread:
[http://ubuntuforums.org/showthread.php?p=2525786#post2525786](http://ubuntuforums.org/showthread.php?p=2525786#post2525786)
I will post whatever solves my problem. Also I found a couple of other interesting sources.lst sites:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

Thanks again.

---

### Post by abhibera on 2007-05-05
I installed gd using

apt-get install php5-gd 

and also i installed libgd-dev using

apt-get install libgd-dev

Inspite of restarting apache and uncommenting extension=gd.so, GD doesn't work in my application. It doesn't render my images. I get a broken image. Any help any one?

I'm using Edgy Eft LAMP Server.

---

### Post by deneb829 on 2007-05-08
> **dzv said:**
> I was having the same issue, but I found the solution here:

[http://ubuntuserver.info/]("http://ubuntuserver.info/")

In short, you need to comment a line in /etc/apt/sources.list

Oh, this is awesome - It was an inconvenience that was starting to drive me crazy. I commented out the line and it stopped asking for the CD! 

):P THANK YOU!

---

### Post by cyrano24100 on 2007-06-25
I have the exact same issue: I've installed php5-gd, restarted apache, rebooted, ladilalala and still gd libraries are not responding

<?php print_r(gd_info()); ?> comes back with an error!

> **abhibera said:**
> I installed gd using

apt-get install php5-gd 

and also i installed libgd-dev using

apt-get install libgd-dev

Inspite of restarting apache and uncommenting extension=gd.so, GD doesn't work in my application. It doesn't render my images. I get a broken image. Any help any one?

I'm using Edgy Eft LAMP Server.

---

### Post by cruzdelsur on 2007-07-04
Hi

I tried:

sudo apt-get install php5-gd

but i get following error message

E: couldn´t find package php5-gd

Apache is working, my soft versions are:
SO  ubuntu 7.07 
PHP Version 5.2.1
Apache/2.2.3 (Ubuntu)


¿what can I do?

THANKS!!!

---

### Post by az on 2007-07-04
You need to enable the universe repo.

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by drummingpariah on 2007-12-02
> **az said:**
> You need to enable the universe repo.

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

Done, and I have every gd (pun intended) package suggested here.  Apache is running just fine, php is being handled just fine (with everything else, anyway), but I continue to receive squalk about gd_info() being undefined.  Exactly what package is it in?

---

### Post by ve6sar on 2008-01-09
I'm having a problem getting GD to work also.
I'm running Ubuntu 7.10 Gusty.

I've tried using apt-get to install php5-gd

restarted my apache server 
but I get this error which is preventing gd from starting

 PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/gd.so' - /usr/lib/php5/20060613+lfs/gd.so: undefined symbol: gdImageCreateFromJpeg in Unknown on line 0

I've looked around the net and nothing has poped up yet....

---

### Post by CLI-Linux on 2008-03-13
> I have the exact same issue: I've installed php5-gd, restarted apache, rebooted, ladilalala and still gd libraries are not responding

<?php print_r(gd_info()); ?> comes back with an error!

I'm having the exact same problem.

Installed php5-gd, restart apache, and zilch.  I also get the gd_info() error as being undefined.  What the heck is going on here?

---

### Post by gerpol on 2008-05-18
Same here,

using Ubuntu 8.04, PHP 5.2.4
 
did 
sudo apt-get install php5-gd
sudo /etc/init.d/apache2 restart

phpinfo does **not** show gd info

When i try the gd_info script I get the message that gd.so is not loaded.

when I run php -m an error occurs :

PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/gd.so' - /usr/lib/php5/20060613+lfs/gd.so: undefined symbol: gdImageCreateFromJpeg in Unknown on line 0

tried reinstall php5-gd and restart apche over and over again.

I really could use some help here.

Just tried some more :
after reinstalling PHP5-GD i went ahead and reinstalled (./confgure, make, make install) the gd-package.  Restarted apache and wtf  : it works !?!
I think, although one reinstalls PHP5-GD the system doesn't pick up the gd-package settngs right when it is already installed. Apparently you must follow a specific order.
So :  
1. make sure you have or get the right PHP5-GD installed (including libpng, libjpeg and so on) _prior_ to installing gd-package.
2. check GD support in PHP
3. only then install gd-package with configure, make, make install

Good luck !

> **CLI-Linux said:**
> I'm having the exact same problem.

Installed php5-gd, restart apache, and zilch.  I also get the gd_info() error as being undefined.  What the heck is going on here?

---

### Post by Fireball454 on 2008-05-28
> **gerpol said:**
> 
Just tried some more :
after reinstalling PHP5-GD i went ahead and reinstalled (./confgure, make, make install) the gd-package.  Restarted apache and wtf  : it works !?!
I think, although one reinstalls PHP5-GD the system doesn't pick up the gd-package settngs right when it is already installed. Apparently you must follow a specific order.
So :  
1. make sure you have or get the right PHP5-GD installed (including libpng, libjpeg and so on) _prior_ to installing gd-package.
2. check GD support in PHP
3. only then install gd-package with configure, make, make install

Good luck !

Hey I also have some problems with the GD library!
I'm still new to all the linux stuff so can you help me with
"configure, make, make install" ??
I tried this on the pakkage I downloaded from the GD website but I don't know if I did it right! Can you explain me how to do it? step by step?

---

### Post by kirkchen on 2008-06-30
> **ve6sar said:**
> I'm having a problem getting GD to work also.
I'm running Ubuntu 7.10 Gusty.

I've tried using apt-get to install php5-gd

restarted my apache server 
but I get this error which is preventing gd from starting

 PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/gd.so' - /usr/lib/php5/20060613+lfs/gd.so: undefined symbol: gdImageCreateFromJpeg in Unknown on line 0

I've looked around the net and nothing has poped up yet....

I have the same problem after upgrading to Gusty, and here's the solution for me:

As it turns out, /usr/lib/php5/20060613+lfs/gd.so had a dependency on /usr/local/lib/libgd.so.2.0.0 on my machine. But when I check the symbol definitions in /usr/local/lib/libgd.so.2.0.0, gdImageCreateFromJpeg indeed was missing.

nm -D /usr/local/lib/libgd.so.2.0.0 | grep gdImageCreateFromJpeg


On the other hand, I have another /usr/lib/libgd.so.2.0.0, which does have the symbol defined. So I did:

cd /usr/local/lib
sudo cp libgd.so.2.0.0 libgd.so.2.0.0.broken
sudo ln -f /usr/lib/libgd.so.2.0.0 libgd.so.2.0.0

Now run 

php -m

The undefined symbol error disappeared and "gd" appears.

In short, the problem was not caused by missing packages; rather, the broken dynamic library was being linked by php5-gd.

Hope this helps some one.

---

