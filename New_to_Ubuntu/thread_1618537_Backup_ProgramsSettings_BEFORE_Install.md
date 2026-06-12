---
title: "Backup Programs/Settings BEFORE Install"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by Ron Carson on 2010-11-10
I recently installed 10.10 and as expected, had to reinstall all my apps.  I backup my home folder so once it was restored and programs reinstalled, everything was back to normal.

But, is there a way to NOT be required to separately reinstall apps?

---

### Post by cipherboy_loc on 2010-11-10
Try AptOnCD. It "queries" your system to see what applications are installed, and backs up the .deb files (which are needed to install packages) to a CD/DVD, or an ISO image. Just pop the CD into your new system, use Synaptic to add it to the repositories, and install all the programs that are on the CD. No need to download anything. It will not back up your settings, just your applications.


But for some reason, I remember it not working the last time I tried it... But don't let that stop you from using it. :lolflag: 



Cipherboy

---

### Post by Cheesehead on 2010-11-10
There are several methods to preserve your packages...but some may not be worth the effort.

The 'jablicator' package creates a metapackage (a dummy package that 'depends' on the packages you really want) of your current applications. You can save the metapackage from your old /var/apt/cache, and then import it into your new system.

You can do much the same thing even more easily with a text file and the command line:
```
dpkg --get-selections > myfile #Write a list of all the installed packages
dpkg --set-selections < myfile #Read a list of all the packages to install
```

But these effort may not be worthwhile. Package names sometimes change across releases. Package 'foo' may not exist in the new release, having been folded into 'libfoo' and 'foo-utils'. Both of those methods give you a few errors to figure out and fix before you get your beloved apps back. The repositories try to ease the pain with transitional packages and dummy packages...but they don't test for what you are trying to do.

You can also do much the same with a private web page - create AptUrl links to your favorite apps. Upon reinstall, simply click on each link - if an error pops up, it will be immediately obvious which package has the problem.

But probably the easiest method is to keep a simple text file of the package names. 
My list of packages to add upon reinstall: fish goat parasail
My list of packages to delete upon reinstall: horse cow mars
I can look over the list -it changes over time- without a lot of jargon, I can organize it anyway I wish, and the whole list can be cut-and-pasted into apt-get with two keystrokes. Easy and maintainable.

But I don't know if that's what you are looking for.

---

### Post by Ron Carson on 2010-11-11
> **Cheesehead said:**
> I can look over the list -it changes over time- without a lot of jargon, I can organize it anyway I wish, and the whole list can be cut-and-pasted into apt-get with two keystrokes. Easy and maintainable.

But I don't know if that's what you are looking for.

Will you further explain this?

---

### Post by Cheesehead on 2010-11-11
Maintaining applications using a text file:
This method takes advantage of a feature in apt-get - many package names can be in the same line.


My Text File, which I created and maintain by hand:
```
My reinstall package list.

Packages to remove upon reinstall: frippery bloatware useless junk3
Reminder - the command is: sudo apt-get purge


Packages to add upon reinstall: needme essential cool-to-have
Reminder - the command is: sudo apt-get install

Reminder - when finished, run: sudo apt-get autoremove

```

Upon a fresh install, simply cut-and paste so your package manager sees the following terminal commands (run each one, wait for completion, run the next one):
```
sudo apt-get purge frippery bloatware useless junk3
sudo apt-get install needme essential cool-to-have
sudo apt-get autoremove
```
Your actual list can run to dozens of packages on a single line.

Does that help?

---

### Post by Ron Carson on 2010-11-11
Yes, that helps a lot.

What is the difference between "purge" and "remove"?  I use "remove" for getting rid of programs, but I'm not familiar with "purge".

Good ideas about autoremove.

---

### Post by mcduck on 2010-11-11
> **Ron Carson said:**
> Yes, that helps a lot.

What is the difference between "purge" and "remove"?  I use "remove" for getting rid of programs, but I'm not familiar with "purge".

Good ideas about autoremove.

"remove" only uninstalls the package, while "purge" also removes it's configuration files. Not a big difference if you think about disk space, but useful if you have misconfigured something to the point you want to really start with a fresh table.

(just keep in mind that even "purge" won't touch the config files in user's home directories. If you want to remove those you need to do it by hand. Makes sense, really, you wouldn't want an admin task like updating packages to remove all your Firefox bookmarks or friends from Empathy etc...)

---

### Post by toekneewood on 2010-11-11
You might want to check for old config files.  "rc" stands for removed but config files remain
```

dpkg -l | grep ^rc

```

Output looks like this
```

rc  freeradius                                                  2.1.9+dfsg-1ubuntu1                               a high-performance and highly configurable RADIUS server
rc  irb1.9.1                                                    1.9.1.378-1                                       Interactive Ruby (for Ruby 1.9.1)
rc  kdelibs-data                                                4:3.5.10.dfsg.1-3ubuntu2                          core shared data for all KDE applications
rc  kdelibs4c2a                                                 4:3.5.10.dfsg.1-3ubuntu2                          core libraries and binaries for all KDE applications

```

To tidy things up run the following
```

dpkg -l | grep ^rc | cut -d' ' -f3| sudo xargs dpkg -P

```

---

### Post by Isyaltut on 2010-11-11
> **Ron Carson said:**
> I recently installed 10.10 and as expected, had to reinstall all my apps.  I backup my home folder so once it was restored and programs reinstalled, everything was back to normal.

But, is there a way to NOT be required to separately reinstall apps?

I've had similar situation like yours not a long time ago. Try [http://www.geekconnection.org/remastersys/.]("http://www.geekconnection.org/remastersys/")

It will create custom iso of your current installation so you won't have to reinstall all of those program which can be time consuming if you don't have fast internet connection such as myself.

---

### Post by toekneewood on 2010-11-11
Your could do them all from one line, for example
```

sudo apt-get install -y apache2 php5 compizconfig-settings-manager 

```

---

