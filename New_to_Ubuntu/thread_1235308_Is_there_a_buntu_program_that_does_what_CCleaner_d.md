---
title: "Is there a *buntu program that does what CCleaner does?"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by JoeNZ on 2009-08-08
Hello from NZ,

I am wondering if there is a *buntu program that works the same as CCleaner does on Windows?

I already know about *sudo apt-get autoremove* but surely there are leftover bits and pieces from programs I have got rid of?

Any help is much appreciated.

Regards
JoeNZ

---

### Post by kerry_s on 2009-08-09
theres no need it's not windows. if you open your file manager & press ctrl+h it will show the hidden folders/files if you see the name of anything you got rid of you can delete the settings for it.
other than that, it does not keep nothing when you completely uninstall it, which i recommend you do from synaptic as it will tell you.

"sudo apt-get autoremove" does not remove the config files, so if you look in synaptic under status, it will show you that there not completely removed.

---

### Post by drs305 on 2009-08-09
Two apps that attempt to clean up things a bit which are in the repositories are *computer-janitor* (and computer-janitor-gtk) and *cruft*. 

I generally find no need for these but you can do a search for more information about them if you wish.

---

### Post by Maczimus on 2009-08-09
Try and install Bleachbit. it is like ccleaner but for Ubuntu. It's in 9.04 and 9.10 repos. or google to find older debs for 8.10.

---

### Post by ad_267 on 2009-08-09
You can use "apt-get purge" to remove an application and it's configuration files.

---

### Post by JoeNZ on 2009-08-09
Cheers. I went to *synaptic - status - not installed* and cleaned everything out of there (24 packages). Definitely things I had removed earlier.

How does *apt-get purge* work?

---

### Post by ad_267 on 2009-08-09
If you use "sudo apt-get purge package_name" it will remove a package and its configuration files. It's the same thing as selecting "completely remove" in synaptic, or clearing out the "not-installed" packages.

---

### Post by kerry_s on 2009-08-09
i use:
**sudo apt-get remove --purge**

you can set up alias's in your ~/.bashrc to save you some typing.
for example i just type-> r package-name

here's my apt ones:

```
alias u='sudo apt-get update;sudo apt-get upgrade'
alias s='apt-cache search'
alias i='sudo apt-get install' 
alias r='sudo apt-get remove --purge'
alias ?='dpkg -l | grep'
alias c='sudo apt-get clean'
```

u = update the package list & upgrade
s = search for a package
i = install package
r = remove package
? = check whats installed
c = clean the cache

---

### Post by binbash on 2009-08-09
[http://www.ubuntu-inside.me/2009/03/clean-your-ubuntu-with-bleachbit.html](http://www.ubuntu-inside.me/2009/03/clean-your-ubuntu-with-bleachbit.html)

---

### Post by JoeNZ on 2009-08-09
Kerry_S, me thinks I have a fair bit of learning to go before I get to that stage. All good. It's awesome the amount of things you can do with Ubuntu as a whole.

---

### Post by longtom on 2009-08-09
> **kerry_s said:**
> i use:
**sudo apt-get remove --purge**

you can set up alias's in your ~/.bashrc to save you some typing.
for example i just type-> r package-name

here's my apt ones:

```
alias u='sudo apt-get update;sudo apt-get upgrade'
alias s='apt-cache search'
alias i='sudo apt-get install' 
alias r='sudo apt-get remove --purge'
alias ?='dpkg -l | grep'
alias c='sudo apt-get clean'
```

u = update the package list & upgrade
s = search for a package
i = install package
r = remove package
? = check whats installed
c = clean the cache

Now - this is why I love this forum.  Every now and again you'll find little gems like this.

Thanks kerry_s

---

### Post by Andrew.Z on 2009-08-09
> **Maczimus said:**
> Try and install Bleachbit. it is like ccleaner but for Ubuntu. It's in 9.04 and 9.10 repos. or google to find older debs for 8.10.

The version in the 9.04 repo is *ancient*.  There are always fresh packages for Ubuntu (8.04, 8.10, 9.04, sometimes 6.06) from the [BleachBit home page](http://bleachbit-project.appspot.com/).

---

### Post by JoeNZ on 2009-08-10
I will give BleachBit a try and let you all know how it goes. Cheers.

---

### Post by JoeNZ on 2009-08-10
Just tried BleachBit and got rid of 650mb of stuff. Sweet.

---

### Post by distortedecho on 2009-08-10
These tips should be in the Ubuntu help files, me thinks.

---

### Post by JoeNZ on 2009-08-10
Very true.

---

### Post by JoeNZ on 2009-08-10
BleachBit still lists programs I have deleted - Opera, Tremulous & Wine. Why is that?

---

### Post by ranger1911 on 2009-08-10
> **JoeNZ said:**
> Kerry_S, me thinks I have a fair bit of learning to go before I get to that stage. All good. It's awesome the amount of things you can do with Ubuntu as a whole.

ubuntu is definitely a great linux distribution, and it definitly helps having a strong foundation to work from (debian :))

i have installed ubuntu on machines will all types of specs and am impressed with how smooth most installations go, and it's great to see the operating system evolve with each new release!

---

### Post by stinger30au on 2009-08-10
every 6 months i backup my data and fasa

format
and
start
again

works for me!

---

### Post by Paddy Landau on 2009-08-10
> **stinger30au said:**
> every 6 months i backup my data and fasa

format
and
start
again

works for me!
What's the point? I stopped doing that when I stopped using Windows.

To answer the OP, Linux doesn't need the equivalent of CCleaner, because Linux isn't the equivalent of Windows.

Here are some things that you can do, if you really want to be paranoid.
```
# Clean up all old defunct installed programs.
sudo apt-get clean
sudo apt-get autoremove

# Delete old OpenOffice backup files.
rm -r ~/.openoffice.org/3/user/backup

# Empty the wastebasket.
rm -r ~/.local/share/Trash/files/*
rm -r ~/.local/share/Trash/info/*
rm -r ~/.local/share/Trash/expunged/*

# Delete all *~ and *.bak backup files in your computer. (Careful! Do you want to do this?)
sudo find / -ignore_readdir_race -mount -type f -regextype posix-egrep -regex '.*(~|\.bak)' -delete -print 2>/dev/null
```

---

### Post by stinger30au on 2009-08-10
> **Paddy Landau said:**
> What's the point? I stopped doing that when I stopped using Windows.



cos every 6 months you get another ubuntu o/s and install that,

thats the point

---

### Post by Andrew.Z on 2009-08-10
> **JoeNZ said:**
> BleachBit still lists programs I have deleted - Opera, Tremulous & Wine. Why is that?

The check boxes means you selected the options for cleaning, not that anything will happen once you try. To see if there are any files left to delete/change, run a preview.

---

### Post by Paddy Landau on 2009-08-10
> **stinger30au said:**
> cos every 6 months you get another ubuntu o/s and install that,
Ah, understood. Doesn't that mean that you have to re-add your software sources and reinstall all your non-default programs?

---

### Post by tom66 on 2009-08-10
I wrote a program to clear out some of the common GNOME caches. Also clears apt-get autoremove, and the apt cache.

[http://ubuntuforums.org/showthread.php?t=1056435](http://ubuntuforums.org/showthread.php?t=1056435)

Use at your own risk.

---

### Post by winotree on 2009-08-25
> **drs305 said:**
> Two apps that attempt to clean up things a bit which are in the repositories are *computer-janitor* (and computer-janitor-gtk) and *cruft*. 

I generally find no need for these but you can do a search for more information about them if you wish.
*Cruft* is mentioned in the repositories as being still in a pre-release state: it just saved me 10MB on my default 4GB SSD *and that's a good deal of free space!*  Thanks for the heads up!  ;)

---

### Post by mikewhatever on 2009-08-25
> **winotree said:**
> *Cruft* is mentioned in the repositories as being still in a pre-release state: it just saved me 10MB on my default 4GB SSD *and that's a good deal of free space!*  Thanks for the heads up!  ;)

10 out of 4000 is not that much if you think about it, in fact, it's only 0.25%.

---

### Post by winotree on 2009-08-25
You're right, of course -- however, every MB is precious when your device is physically limited.  Hmh, not that I'd think about changing it anytime soon...  ;)

---

