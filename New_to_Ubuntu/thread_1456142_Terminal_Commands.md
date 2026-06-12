---
title: "Terminal Commands"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by noworldorder on 2010-04-16
Newbie question:
  
I want to learn...  

Are the commands used in the terminal on Ubuntu Linux commands?

Would learning Linux commands be a place to start?  

I fould this site and it seems good:

[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

but it doesn't mention Ubuntu so I want to be sure it is relevant for me.

Thanks - chris

---

### Post by zvacet on 2010-04-16
Yes,you can start from there.

---

### Post by Iowan on 2010-04-16
Earlier this afternoon, I discovered I had bookmarked [this]("https://help.ubuntu.com/9.04/basic-commands/C/") help page. Not exhaustive, but another place to start.

---

### Post by Miyavix3 on 2010-04-17
Learn these
```

pwd - Shows your working location
cd - Change directory
ls - List files in directory
cp - copy file(s)
mv - Move file/folder(s)
rm - Remove file(s)
touch - Make a new (empty) file
mkdir - Make a new directory (new folder)
rmdir - Removes an empty folder (folder must be empty). Alternatively you can use rm -rf

```

Those are all really essential to the terminal. They're great because some people will tell you to do everything you would normally do, with the GUI, in your terminal. That's a pretty good starting point, so I'll let you venture to find the rest. Good luck man.

Also, there are some cool apps that run on the command line. I'll list them by their package name, so you can find them in the synpatic 
mc - File browser (Midnight Commander)
moc - Music player [Music on Console (To launch, open the terminal and type mocp)]
irssi - IRC client
centerim OR naim - Instant Messenger (I don't know if you really want to use them, but they're fun)
nano OR vim 
mplayer - Can play music and movies (for moves a video pops up)

Heck, you should be able to find these packages in the repositories from the command line.

```
aptitude search package-name
```
To install:
```
sudo apt-get install package-name
```

Have fun and good luck!

---

### Post by iponeverything on 2010-04-17
> **noworldorder said:**
> Newbie question:
  
I want to learn...  

Are the commands used in the terminal on Ubuntu Linux commands?

Would learning Linux commands be a place to start?  

I fould this site and it seems good:

[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

but it doesn't mention Ubuntu so I want to be sure it is relevant for me.

Thanks - chris

It is relevant. It looks like a perfectly good tutorial.

---

### Post by noworldorder on 2010-04-17
Thanks everyone for the help and encouragement.

I thought I would try to install the file manager (as suggested) from the command line and I am not sure it worked properly.  This is what happened:

p   xtermcontrol                    - dynamic configuration of xterm properties 
chris@chris-laptop:~$ sudo apt-get install package mc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package package
chris@chris-laptop:~$ ls
Desktop    Downloads         Music     Public     Ubuntu One
Documents  examples.desktop  Pictures  Templates  Videos
chris@chris-laptop:~$ 

I am so new at this I don't even know how to run it or, if it didn't install properly, how to delete the files. How do I know where this installed to?

thanks - chris

---

### Post by Didius Falco on 2010-04-17
> **noworldorder said:**
> Thanks everyone for the help and encouragement.

I thought I would try to install the file manager (as suggested) from the command line and I am not sure it worked properly.  This is what happened:

p   xtermcontrol                    - dynamic configuration of xterm properties 
chris@chris-laptop:~$ sudo apt-get install package mc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package package
chris@chris-laptop:~$ ls
Desktop    Downloads         Music     Public     Ubuntu One
Documents  examples.desktop  Pictures  Templates  Videos
chris@chris-laptop:~$ 

I am so new at this I don't even know how to run it or, if it didn't install properly, how to delete the files. How do I know where this installed to?

thanks - chris

Here is where the problem is:

```
chris@chris-laptop:~$ sudo apt-get install [COLOR=Red]package[/COLOR] mc

```You don't need the word package, just the name of the package you are trying to install. for example, do this to install the mc package:

```
sudo apt-get install mc
```BTW, be careful with those rm commands. Have a read of this:

[http://ubuntuforums.org/announcement.php?f=326](http://ubuntuforums.org/announcement.php?f=326)

---

### Post by noworldorder on 2010-04-17
thanks!  I used Midnight Commander to delete some unnecessary files.  When I uninstalled some programs the folders were still there for some reason.

How do you  go about uninstalling a program that is installed via the terminal?  And where are they stored.

Thanks - chris

---

### Post by jaco223 on 2010-04-17
> **noworldorder said:**
> thanks!  I used Midnight Commander to delete some unnecessary files.  When I uninstalled some programs the folders were still there for some reason.

How do you  go about uninstalling a program that is installed via the terminal?  And where are they stored.

Thanks - chris

You can remove an installed package by doing the following in a terminal:
```

sudo apt-get remove --purge (package name)
```

You can find where a package is installed by the following:

```
whereis (package or file name)
```Hope this helps.

Jaco

---

### Post by mhgsys on 2010-04-17
read the man pages; 
f.e

```
man apt
```

many packages (almost all) come with man(uals) :-)

---

