---
title: "Flashflashplugin-nonfree error.Updates doesn't work!"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by vasiauvi on 2009-05-13
Hello all,
this is the error when I try to install/remove flashplugin:
```

The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
Also I can't install anything because of this error.
I have read on this forum and also on internet and seems that for some people worked finally but for me nothing works.
Can anyoane help me with this?

---

### Post by vasiauvi on 2009-05-13
Nobody can help me?
I also got this error:
"E: flashplugin-nonfree: Package is in a very bad inconsistent state - you should...."

I think that upgrading to the 9.04 version was a BAD mistake!!!:(

---

### Post by vasiauvi on 2009-05-13
How can I remove a broken pakage?
I try:
```

sudo dpkg -r flashplugin-nonfree

``` and get this:
```

dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree

```

---

### Post by Bodsda on 2009-05-13
Hi, 

Could you please try running the following command

```
sudo apt-get install --reinstall flashplugin-nonfree
```

If that fails, please try the following,
```
sudo apt-get remove --purge flashplugin-nonfree
```

This may help also
```
sudo apt-get install --fix-broken
```

please provide all the terminal output for both commands as it may provide important information.

Thanks,

Bodsda

p.s: Less then two hours is not really long enough to warrant two bumps, please be patient

---

### Post by vasiauvi on 2009-05-13
Sorry, I now that I'm not patient but until now this problem didn't occurred and I've tried this commands and didn't worked and also after reading on the internet I couldn't repair this issue.

First command:
```
/usr/lib$ sudo apt-get install --reinstall flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
Second command:
```

/usr/lib$ sudo apt-get remove --purge flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libarts1c2a libboost-test1.34.1 libboost-regex1.34.1 libartsc0 amarok-engine-xine libboost-wave1.34.1
  libgcj8-1 libboost-program-options1.34.1 ttf-dustin libboost-doc libgcj8-jar libexiv2-4
  libboost-serialization1.34.1 libboost-date-time1.34.1 librasqal0 python2.5-dev libglide2 python-qt3
  libboost-signals1.34.1 gcj-4.2-base libboost-graph1.34.1 mbr libgcj8-1-awt libboost-iostreams1.34.1
  libmjpegtools0c2a libtunepimp5 libifp4 libdvdread3 exim4 libimlib2 graphviz libnjb5 xutils-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  flashplugin-nonfree*
0 upgraded, 0 newly installed, 1 to remove and 71 not upgraded.
1 not fully installed or removed.
After this operation, 168kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing flashplugin-nonfree (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The big problem is that none of the update are working.

---

### Post by loomsen on 2009-05-13
> please provide all the terminal output for both commands as it may provide important information.

No it wont provide any useful information actually.

```
uname -m
```

actually would be nice to know (architecture of your install)

if it's x86 you can stick to flashplugin-nonfree out of the repos, or any other flash you get your hands on, for instance the official release from adobes downloadcenter

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

If the cmd tells you that you have amd64/x86_64 architecture installed, I'd go for the 64bit alpha plugin adobes offers...

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)

download it, in the meanwhile uninstall everything flashplayer related with sth like for instance:
```

sudo aptitude --purge remove flashplayer.?*
```

Then, run another search to make sure its really gone:
```

sudo find / -iname libflash

```

You shouldnt get any output (well, except the just downloaded 64bit plugin. If you happen to get output, run 
sudo rm /path/to/output.so

to make sure your system is clean. Then extract the 64bit package, of you're using opera you may decide where to extract it yourself. Then point opera there, and it should be instantly recognized.

For firefox you can extract the pkg into userspace, not sure but I think the folder is:
~/.mozilla/firefox or so. There are a lot howtos around for firefox.

However, if you really wanna improve your web browsing experience significantly, I'd recommend advancing through the link below ;)

---

### Post by Bodsda on 2009-05-13
Yeah, this is going to cause problems until the dependencies and packages are satisfied and fixed respectively.

But, I think we are getting somewhere, if you take a look at the first block of output you pasted.
```
/usr/lib$ sudo apt-get install --reinstall flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

And now look at the last line
```
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
It kindly tries to give us a solution. So in your terminal run the following.
```
sudo apt-get -f install
```

And hope this helps things,

Paste any error messages or output that that command produces,

Thanks,

Bodsda

---

### Post by Bodsda on 2009-05-13
> **loomsen said:**
> No it wont provide any useful information actually.

Oh, i see, so the bit where it tells us what to try ```
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
``` is useless? And also its telling us a cause of the/a problem. But hey, its not important, instead lets talk about installing something which may cause issues rather then fixing the problem at hand.

Regards,

Bodsda

---

### Post by ugm6hr on 2009-05-13
> **Bodsda said:**
> It kindly tries to give us a solution. So in your terminal run the following.
```
apt-get -f install
```

Don't forget sudo:

```
sudo apt-get install -f
```

---

### Post by Bodsda on 2009-05-13
> **ugm6hr said:**
> Don't forget sudo:

```
sudo apt-get install -f
```

ah, missed that, edited, cheers ugm6hr

---

### Post by vasiauvi on 2009-05-13
Thanks for helping me!
I really appreciate this!
Here is the output of sudo apt-get -f install:
```
paula@paula:/usr/lib$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  flashplugin-installer flashplugin-nonfree
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
The following packages will be upgraded:
  flashplugin-nonfree
1 upgraded, 1 newly installed, 0 to remove and 71 not upgraded.
1 not fully installed or removed.
Need to get 0B/21.0kB of archives.
After this operation, 53.2kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
localepurge: checking system for new locale ...
Some new locales have appeared on your system:

ca@valencia hne zh_cn 

They will not be touched until you reconfigure localepurge
with the following command:

    dpkg-reconfigure localepurge

localepurge: processing locale files ...
localepurge: processing man pages ...
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
For uname -m i get 
paula@paula:/usr/lib$ uname -m
i686

---

### Post by loomsen on 2009-05-13
> 
[b] --snip--
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
--snip--[/b]

```

sudo aptitude install flashplugin-nonfree
```

And hence you don't have 64bit arch you can stick with it.

Or get the latest from adobes download centerl...

---

### Post by vasiauvi on 2009-05-13
This is the output:
```
paula@paula:/usr/lib$ sudo aptitude install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  flashplugin-installer{a} 
The following packages will be upgraded:
  flashplugin-nonfree 
1 packages upgraded, 1 newly installed, 0 to remove and 71 not upgraded.
Need to get 0B/21.0kB of archives. After unpacking 53.2kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Preconfiguring packages ...
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
localepurge: checking system for new locale ...
Some new locales have appeared on your system:

ca@valencia hne zh_cn 

They will not be touched until you reconfigure localepurge
with the following command:

    dpkg-reconfigure localepurge

localepurge: processing locale files ...
localepurge: processing man pages ...
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
```
It's not working!:((

---

### Post by ugm6hr on 2009-05-13
This might be a bit tricky.  Try manually installing dependencies, then retry installing:

```
sudo apt-get install flashplugin-installer
sudo apt-get install --reinstall flashplugin-nonfree
```

---

### Post by vasiauvi on 2009-05-13
> **ugm6hr said:**
> This might be a bit tricky.  Try manually installing dependencies, then retry installing:

```
sudo apt-get install flashplugin-installer
sudo apt-get install --reinstall flashplugin-nonfree
```

The same thing:
```
paula@paula:/usr/lib$ sudo apt-get install --reinstall flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
It's says that I have a broken package and I have to resolve this problem to update the programs.

---

### Post by Bodsda on 2009-05-13
The only other things I can think of is to try to force the purge of the package or to install the dependencies with gdebi from packages.ubuntu.com

What do you guys think?

---

### Post by Bodsda on 2009-05-13
> **vasiauvi said:**
> The same thing:
```
paula@paula:/usr/lib$ sudo apt-get install --reinstall flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
It's says that I have a broken package and I have to resolve this problem to update the programs.

That output is from the wrong command, run this
```
sudo apt-get install flashplugin-installer
```

---

### Post by ugm6hr on 2009-05-13
I think using dpkg / gdebi to install dependency (-installer), and then reinstall main package (-nonfree) with dpkg.

I think apt-get clearly cannot resolve the problem at this stage.  Unusual, I've never been unable to sort out problems with apt-get.

EDIT: Try that command above first, just in case...

---

### Post by vasiauvi on 2009-05-13
> **Bodsda said:**
> The only other things I can think of is to try to force the purge of the package or to install the dependencies with gdebi from packages.ubuntu.com

What do you guys think?
How can I do this, to use the gdebi?

Thank you for helping me and I hope to resolve this issue.
I can not stay tonight longer because here is 23:34 now and tomorrow I will  go to work :D. Tomorrow I will try again!
Good night!See you tomorrow!

---

### Post by vasiauvi on 2009-05-13
```
paula@paula:/usr/lib$ sudo apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  flashplugin-nonfree
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
The following packages will be upgraded:
  flashplugin-nonfree
1 upgraded, 1 newly installed, 0 to remove and 71 not upgraded.
1 not fully installed or removed.
Need to get 0B/21.0kB of archives.
After this operation, 53.2kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
localepurge: checking system for new locale ...
Some new locales have appeared on your system:

ca@valencia hne zh_cn 

They will not be touched until you reconfigure localepurge
with the following command:

    dpkg-reconfigure localepurge

localepurge: processing locale files ...
localepurge: processing man pages ...
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Bodsda on 2009-05-13
Goodnight. 

And as for gdebi.

gdebi is a program to install downloaded .deb files. 

If you follow this [link]("http://packages.ubunut.com/jaunty/i386/flashplugin-installer/download") and choose a download mirror, it will download the dependency you need and gdebi should automatically try to install it for you, after it has done this try reinstalling the flashplugin-nonfree package.

EDIT: From the description of the package i think this package actually downloads flash for you so you may not have to reinstall the package after this, but apt will tell you whether or not you should, when you attempt to, so no harm can be done.

---

### Post by ugm6hr on 2009-05-13
> **vasiauvi said:**
> How can I do this, to use the gdebi?
Try this first:
```
sudo dpkg -i /var/cache/apt/archives/flashplugin-installer_10.0.22.87ubuntu2_i386.deb
sudo dpkg -i /var/cache/apt/archives/flashplugin-nonfree_10.0.22.87ubuntu2_i386.deb

```
Then try apt-get again:
```
sudo apt-get install -f
```

---

### Post by vasiauvi on 2009-05-14
It's WORKING!!!!
Thank you very much for your help.It worked with Ugm6hr code.
Now I can sleep better:D.
THANK YOU!

---

