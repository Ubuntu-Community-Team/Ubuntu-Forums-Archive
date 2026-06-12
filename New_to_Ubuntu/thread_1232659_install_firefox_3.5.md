---
title: "install firefox 3.5"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by aparolin on 2009-08-05
i am up and running 9.04.:D  and wanted to upgrade firefox 3.0.8 to 3.5.2...

downloaded file and have:  
/home/oem/Desktop/firefox-3.5.2.tar.bz2. and
/home/oem/Desktop/firefox 
on the desktop screen

how do i get the file new firefox to replace and/or update 3.0.8?

thanx

---

### Post by TMAN 1 on 2009-08-05
Why not just D/L it directly from Mozilla site,it is quick and easy to do.

---

### Post by clparker on 2009-08-05
yeah, but it's just a tarfile, If it was a .deb file we'd be able to call that quick and easy...

---

### Post by aparolin on 2009-08-05
i did download it from mozilla and these two files are now located at: 
/home/oem/Desktop/firefox-3.5.2.tar.bz2. and
/home/oem/Desktop/firefox folder
on the desktop screen

should they be in another folder?  should i move them to file system?
there is an updater executable in the firefox folder, but it does not respond.

how would you go about updating this program.  add detail...
thanx

---

### Post by jmszr on 2009-08-05
aparolin,

These directions should do it: [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Or these: [http://ubuntumanual.org/posts/197/install-firefox-3-5-1-in-ubuntu-using-ubuntuzilla](http://ubuntumanual.org/posts/197/install-firefox-3-5-1-in-ubuntu-using-ubuntuzilla)

---

### Post by CatKiller on 2009-08-05
> **TMAN 1 said:**
> Why not just D/L it directly from Mozilla site,it is quick and easy to do.

or ```
sudo apt-get install firefox-3.5
```which is both quicker and easier. There are other methods, but this will always be the classic.

---

### Post by dreemreeper on 2009-08-05
i was successful using these instructions:
[http://www.psychocats.net/ubuntu/firefox]("http://www.psychocats.net/ubuntu/firefox") 
but alas, i use 64bit jaunty and after the install could not get flash to work for the life of me so i reverted.

---

### Post by kansasnoob on 2009-08-06
I prefer using Ubuntuzilla:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

It's also supported in these forums:

[http://ubuntuforums.org/forumdisplay.php?f=251](http://ubuntuforums.org/forumdisplay.php?f=251)

---

### Post by rsiddharth on 2009-08-06
CatKiller's suggestions is the best and a clean way to install Firefox 3.5 . 

After installing the Browser , obviously the next step will be to use . If access applications from the Applications menu , then you got to hit Applications-->Internet-->Shiretoko Web Browser to start the Browser . Or if you usually access applications from the 'Run' (Alt+F2) Dialogue box/Terminal  , then its 'firefox-3.5' ( straight forward ) though without the quotations .

---

### Post by Greasy_Larry on 2009-08-06
> **CatKiller said:**
> or ```
sudo apt-get install firefox-3.5
```which is both quicker and easier. There are other methods, but this will always be the classic.

Will this work with any files you download. I downloaded a torrent, and stored it to my desktop. Can I just type sudo apt-get install <file>

---

### Post by quinnten83 on 2009-08-06
> **Greasy_Larry said:**
> Will this work with any files you download. I downloaded a torrent, and stored it to my desktop. Can I just type sudo apt-get install <file>

if the file is a .deb
you should use sudo dpkg -i <file>

---

### Post by Greasy_Larry on 2009-08-06
> **quinnten83 said:**
> if the file is a .deb
you should use sudo dpkg -i <file>

No it is a folder containing several files. The install file is an x-shellscript. The supported platforms section of the read me file in the folder says.

 *"<software name> runs on red hat linux ws3 or later, suse linux pro 9.1 or later, mandrake linux 10.0 or later. <software name> can run without hardware driver support on any other distrubutions that provide GNU C Library (glibc, also known as libc.so.6) version 2.2.4*

---

### Post by rsiddharth on 2009-08-06
> 
Will this work with any files you download. I downloaded a torrent, and stored it to my desktop. Can I just type sudo apt-get install <file>

I don't think apt-get will install a file that you have placed in your Desktop . apt-get is used to download and install packages from the repositories that is mentioned in the " Software Sources " Dialog ( System-->Administration-->Software Sources) . 

You can use Synaptic to download and install Softwares for you ( System-->Administration-->Synaptic Package Manager ) . Synaptic can be considered as a front end to apt-get system . 

This may give you an Introduction to Synaptic : [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by aparolin on 2009-08-06
thanx for all your help

your assistance is appreciated:D
alan

---

### Post by nanotube on 2009-08-08
> **jmszr said:**
> aparolin,

These directions should do it: [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Or these: [http://ubuntumanual.org/posts/197/install-firefox-3-5-1-in-ubuntu-using-ubuntuzilla](http://ubuntumanual.org/posts/197/install-firefox-3-5-1-in-ubuntu-using-ubuntuzilla)

Hi jmszr:
please link directly to the ubuntuzilla website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/), rather than to that blog post. 

the instructions in the blog post have a couple of problems. 

specifically, it recommends the "hard way" of installing ubuntuzilla, manually installing dependencies using dpkg, which while ok, is harder than it has to be (just double-click on the .deb will work), and also will fail for 64bit users. 

second, for downloads, it links directly to an old version of ubuntuzilla.

---

### Post by nanotube on 2009-08-08
> **kansasnoob said:**
> I prefer using Ubuntuzilla:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

It's also supported in these forums:

[http://ubuntuforums.org/forumdisplay.php?f=251](http://ubuntuforums.org/forumdisplay.php?f=251)

Hi kansasnoob :)

please link to [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) rather than directly to the wiki page. sourceforge is making lots of changes to the site lately, and things are moving around. so the wiki link may change, but i'll always be keeping ubuntuzilla.sf.net pointing to the right place. :)

how goes it by the way? what do you think of the new language display next to the localization codes? :)

---

### Post by JoeNZ on 2009-08-09
Ubuntuzilla worked very well for me too. Easy.

---

### Post by noctua on 2009-08-12
> **CatKiller said:**
> ```
sudo apt-get install firefox-3.5
```

I ran this command and it appeared to be successful.  However, when I restarted Firefox and viewed Help > About Mozilla Firefox, it still shows as version 3.0.13.  Is there another step that I'm missing?

If it helps, this is the output of what I did:

```
me@mycomp:~$ sudo apt-get install firefox-3.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  firefox-3.5-branding xulrunner-1.9.1
Suggested packages:
  firefox-3.5-gnome-support latex-xft-fonts
The following NEW packages will be installed:
  firefox-3.5 firefox-3.5-branding xulrunner-1.9.1
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.1MB of archives.
After this operation, 28.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com jaunty-updates/universe xulrunner-1.9.1 1.9.1.2+nobinonly-0ubuntu0.9.04.1 [8993kB]
Get:2 http://us.archive.ubuntu.com jaunty-updates/universe firefox-3.5-branding 3.5.2+nobinonly-0ubuntu0.9.04.1 [156kB]                                     
Get:3 http://us.archive.ubuntu.com jaunty-updates/universe firefox-3.5 3.5.2+nobinonly-0ubuntu0.9.04.1 [930kB]                                              
Fetched 10.1MB in 33s (304kB/s)                                                                                                                             
Selecting previously deselected package xulrunner-1.9.1.
(Reading database ... 121262 files and directories currently installed.)
Unpacking xulrunner-1.9.1 (from .../xulrunner-1.9.1_1.9.1.2+nobinonly-0ubuntu0.9.04.1_i386.deb) ...
Selecting previously deselected package firefox-3.5-branding.
Unpacking firefox-3.5-branding (from .../firefox-3.5-branding_3.5.2+nobinonly-0ubuntu0.9.04.1_i386.deb) ...
Selecting previously deselected package firefox-3.5.
Unpacking firefox-3.5 (from .../firefox-3.5_3.5.2+nobinonly-0ubuntu0.9.04.1_i386.deb) ...
Setting up xulrunner-1.9.1 (1.9.1.2+nobinonly-0ubuntu0.9.04.1) ...

Setting up firefox-3.5-branding (3.5.2+nobinonly-0ubuntu0.9.04.1) ...
Setting up firefox-3.5 (3.5.2+nobinonly-0ubuntu0.9.04.1) ...
Please restart all running instances of firefox-3.5, or you will experience problems.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

me@mycomp:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
The following packages will be REMOVED:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 74.7MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 121688 files and directories currently installed.)
Removing linux-headers-2.6.28-11-generic ...
Removing linux-headers-2.6.28-11 ...
me@mycomp:~$ 

```

---

### Post by aysiu on 2009-08-12
> **noctua said:**
> I ran this command and it appeared to be successful.  However, when I restarted Firefox and viewed Help > About Mozilla Firefox, it still shows as version 3.0.13.  Is there another step that I'm missing?

If it helps, this is the output of what I did:

```
me@mycomp:~$ sudo apt-get install firefox-3.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  firefox-3.5-branding xulrunner-1.9.1
Suggested packages:
  firefox-3.5-gnome-support latex-xft-fonts
The following NEW packages will be installed:
  firefox-3.5 firefox-3.5-branding xulrunner-1.9.1
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.1MB of archives.
After this operation, 28.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com jaunty-updates/universe xulrunner-1.9.1 1.9.1.2+nobinonly-0ubuntu0.9.04.1 [8993kB]
Get:2 http://us.archive.ubuntu.com jaunty-updates/universe firefox-3.5-branding 3.5.2+nobinonly-0ubuntu0.9.04.1 [156kB]                                     
Get:3 http://us.archive.ubuntu.com jaunty-updates/universe firefox-3.5 3.5.2+nobinonly-0ubuntu0.9.04.1 [930kB]                                              
Fetched 10.1MB in 33s (304kB/s)                                                                                                                             
Selecting previously deselected package xulrunner-1.9.1.
(Reading database ... 121262 files and directories currently installed.)
Unpacking xulrunner-1.9.1 (from .../xulrunner-1.9.1_1.9.1.2+nobinonly-0ubuntu0.9.04.1_i386.deb) ...
Selecting previously deselected package firefox-3.5-branding.
Unpacking firefox-3.5-branding (from .../firefox-3.5-branding_3.5.2+nobinonly-0ubuntu0.9.04.1_i386.deb) ...
Selecting previously deselected package firefox-3.5.
Unpacking firefox-3.5 (from .../firefox-3.5_3.5.2+nobinonly-0ubuntu0.9.04.1_i386.deb) ...
Setting up xulrunner-1.9.1 (1.9.1.2+nobinonly-0ubuntu0.9.04.1) ...

Setting up firefox-3.5-branding (3.5.2+nobinonly-0ubuntu0.9.04.1) ...
Setting up firefox-3.5 (3.5.2+nobinonly-0ubuntu0.9.04.1) ...
Please restart all running instances of firefox-3.5, or you will experience problems.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

me@mycomp:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
The following packages will be REMOVED:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 74.7MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 121688 files and directories currently installed.)
Removing linux-headers-2.6.28-11-generic ...
Removing linux-headers-2.6.28-11 ...
me@mycomp:~$ 

```
Yes. The step you're missing is that both are now installed.

```
firefox
``` is linked to Firefox 3.

And ```
firefox-3.5
``` is linked to Firefox 3.5 (or Shiretoko).

---

### Post by fooman on 2009-08-12
look in applications > internet > *shiretoko*

shiretoko is firefox 3.5.

if you wish to have it called "firefox" and use the firefox icon and have all links point to this new 3.5 version of firefox....see this:

[http://ubuntuforums.org/showthread.php?t=1225754](http://ubuntuforums.org/showthread.php?t=1225754)

hope that helps.

---

### Post by noctua on 2009-08-12
Ah ok, thank you.  I didn't realize it was installing it separately, and assumed I was upgrading my existing Firefox (which is what I wanted to do).  I just installed Ubuntu today after messing around with the Live CD for a few days, so I'm still figuring out how this all works. :)

---

### Post by Gregz on 2009-08-12
I also have 3.0.13 that will not update.

 I know 3.0.15 was released awhile back has anyone seen the update yet??

---

### Post by colau on 2009-08-15
Easiest way to install firefox-3.5!
[firefox-3.5]("http://www.psychocats.net/ubuntu/firefox")

---

