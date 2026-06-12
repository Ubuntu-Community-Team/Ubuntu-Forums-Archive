---
title: "Where to install new programs?"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by spirit.986 on 2011-03-26
I am kinda new to linux and by my former experience from windows all of the new installations were placed in C:\My Documents...

However, i am little confused here?
Since I am a PHP developer i've downloaded a program gPHPedit and was following the installation readme but nowhere was mentioned where is a preferred place to put the contents of the program?

> The simplest way to compile this package is:

1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

**Is there a preferred place to put the package (like Program files in win)? or i can install it anywhere I want?**

**Also what if after the installation i don't like it and i want to remove this program? What should i do then?** (this is also very important to me since i really hate keeping junk in mu pc :) )

---

### Post by mcduck on 2011-03-26
Actually the preferred way is to not download things from websites, but instead use Ubuntus software sources and package management tools instead.

It makes your life easier, provides you with tested versions and updates for all your programs through the same system that handles updates for the OS itself. And downloading & installing is done automatically for you.

Just go to Applications/Ubuntu Software Center (or System/Administration/Synaptic Package Manager),search for gphpedit and click the install button. Or pop open a terminal and run "sudo apt-get install gphpedit" to download  install it.

Or if you are currently in Ubuntu, and browsing with Firefox, click the following link: [apt:gphpedit]("apt:gphpedit") :)

(What comes to situations when you end installing something manually anyway, the logical place would be /opt, which is meant for programs coming from outside of your Linux distribution's own sources. If you install programs manually, you'll also have to uninstall them manually. How that's done depends on how you installed the program. If you compiled it from source it most likely included a script for uninstalling. Although I recommend using checkinstall when compiling programs, it creates a .deb package from the program and installs that, allowing you to unistall the program easily through the package management tools)

---

### Post by duanedesign on 2011-03-26
It is prefered to install packages with the package manager. Installing with the package manager means using Add/Remove Software, Synaptic Package Manager, apt-get install <package>. The executables are generally stored in (or linked to, from) /bin, /sbin, /usr/bin or /usr/sbin. You can use the command 'which <package>' to see where the executable is. ex. which gedit

However there are rare cases where the software you want does not have .deb file. For those you will have to[ compile it yourself]("https://help.ubuntu.com/community/CompilingEasyHowTo").

You should build a common directory for yourself where you'll be building these packages. We recommend creating /usr/local/src, but really you can put it anywhere you want. Make sure this directory is writable by your primary user account, by running

```
sudo chown $USER /usr/local/src
```

and, just to be safe

```
sudo chmod u+rwx /usr/local/src
```


To remove a program when you are done with it use [CheckInstall]("https://help.ubuntu.com/community/CheckInstall") while installing it. You will use the following command instead of 'sudo make install'.

```
sudo checkinstall
```

If you have any further questions see  [CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")

---

### Post by spirit.986 on 2011-03-26
I just found out that in the Ubuntu Software Center there are several editors avaible for PHP Development, CodeLite, Geany, gPHPedit etc..

Also if anyone else is interested about manually installing an application in Linux here is a great guide I've found while goggling this problem:

**Installing Software in GNU/Linux**
[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html]("http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html")

P.S.
> Or if you are currently in Ubuntu, and browsing with Firefox, click the following link: apt:gphpedit
I've decided to get rid of windows once and for all!

Thanks to all for the support.. indeed a Ubuntu has a really awesome comunity!

---

### Post by Old_Man_Unix on 2011-03-26
Welcome to Ubuntu. I think you will find it a rewarding experience.

Very good information here.  I'd just like to add some things that are sometimes confusing to newcomers, especially those coming from Windows.

First of all, the official repositories are*** release-specific***. So there may be applications that *never show up* for your release even though later releases of Ubuntu are using them.  

Second, as duanedesign said, there are sometimes programs that do not appear in* any *of the official repositories. Perhaps they are too new or not stable enough for Ubuntu to accept them.  However, compiling source from scratch is really the last thing that a beginner ought to be thinking of doing.

There is a better way  - it is called a **PPA**, which stands for Personal Program Archive.   Think of it as a mini-repository for one application - or a small group of applications - that have not been 'officially accepted' by Ubuntu.  The PPA contains packages that are built just like the official packages, with all the dependencies identified, etc. 

But there are other reasons to use a PPA.  Consider that first situation that I described.  Users of those earlier releases may want that new application.  So the application developers open a PPA to enable those users to install the software.  Currently, for example, **Libreoffice, ** which is to be included in 11.04, is not in the official repositories for earlier releases and will only only available in a PPA.  

PPAs  function much as the official repositories do.    Updates are offered just like with the official repositories, so your Update Manger will see them in the same way.

---

### Post by donkyhotay on 2011-03-26
> **mcduck said:**
> Actually the preferred way is to not download things from websites, but instead use Ubuntus software sources and package management tools instead.

It makes your life easier, provides you with tested versions and updates for all your programs through the same system that handles updates for the OS itself. And downloading & installing is done automatically for you.

Just go to Applications/Ubuntu Software Center (or System/Administration/Synaptic Package Manager),search for gphpedit and click the install button. Or pop open a terminal and run "sudo apt-get install gphpedit" to download  install it.

Or if you are currently in Ubuntu, and browsing with Firefox, click the following link: [apt:gphpedit]("apt:gphpedit") :)

(What comes to situations when you end installing something manually anyway, the logical place would be /opt, which is meant for programs coming from outside of your Linux distribution's own sources. If you install programs manually, you'll also have to uninstall them manually. How that's done depends on how you installed the program. If you compiled it from source it most likely included a script for uninstalling. Although I recommend using checkinstall when compiling programs, it creates a .deb package from the program and installs that, allowing you to unistall the program easily through the package management tools)

+1

Downloading/installing files from the internet is a bad habit almost everyone learns using windows and is a good part of the reason windows is so insecure. As mentioned *always* look in the repos (software center) first and if you can't find the program you need there then *maybe* download/install from the web. Even then you're better off finding an alternative that does the same thing then downloading/installing from the web.

---

