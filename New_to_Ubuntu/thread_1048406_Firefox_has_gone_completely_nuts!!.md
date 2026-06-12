---
title: "Firefox has gone completely nuts!!"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by nayeret43 on 2009-01-23
My Firefox and system has been running fine today until I downloaded the Linux version of Globe7.  And then for some reason it "failed in installation", and I got a lot of error messages that return value 1 (something regarding sub-processes). 

And then my Firefox (I am 99.99% sure this all started right after I "installed" Globe7), stopped working normally.  For starters, the back, forward, stop, and refresh buttons don't work- they are all grey, and I can't even press them.  Secondly, all my bookmarks disappeared, as well as my automatic logins to some websites, in addition to the fact that there is no home page (even though there is one defined in *options*).

So here is what I did:
1. I completely deleted the Globe7 (through using gksudo nautilus- deleting the actual files in the GUI)
2. And I did the same with the Firefox

I rebooted, and then reinstalled Firefox, and here I am, having the same exact problem.  I researched on Google, but couldn't seem to find a solution to my problem.

Please assist me in this.

Thank you.

---

### Post by khelben1979 on 2009-01-23
As a temporary solution you might be interested in installing [Seamonkey]("http://www.seamonkey-project.org/releases/") until your Firefox starts working again.

When it comes to Firefox I suspect that the package needs to be purged and not only uninstalled since all the configuration files remains if you don't.

---

### Post by nayeret43 on 2009-01-23
Ok, so how do I purge Firefox?  I am relatively new at this....

---

### Post by khelben1979 on 2009-01-23
From a text console with root priviliges (use sudo) you need to this:

**sudo root**

**apt-get purge firefox**

That should work. Then you can try installing firefox again the way you are used to. Also if you type: **man apt-get** you get a manual page for you on this matter.

---

### Post by sylvainrb on 2009-01-23
```
sudo apt-get remove --purge firefox
```

Restart your computer and reinstall firefox. If the problem persists you might have to delete some files (I don't know which though I have to check...).

You could also try with Synaptic and mark Firefox for complete removal.

---

### Post by northern lights on 2009-01-23
To have a chance of recovering your bookmarks, backup the configuration folder:```
cp -r ~/.mozilla ~/moz_bkup
```

Purge firefox```
sudo aptitude purge firefox && rm -rf ~/.mozilla
```(removal should be obsolete when purging, but run as above)

Subsequently, reinstall```
sudo apt-get install firefox
```

---

### Post by nayeret43 on 2009-01-23
Ok, I did everything as instructed and the terminal gives me this:

```

cp: cannot stat `/home/nayeret43/.mozilla': No such file or directory
nayeret43@root:~$ sudo apt-get remove --purge firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package firefox is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

However, Firefox still runs!  Even though it is not even on my operating system.  What should I do?

---

### Post by linux_tech on 2009-01-23
You can try removing the firefox folders in /usr/lib/
It looks like there is still some remnants, but it is broken.
First try searching and removing using synaptic, but if it won't remove
then manual removal may be your only way.
Usually by doing a manual uninstall , you may be able to reinstall it again

---

### Post by philinux on 2009-01-23
Agreed, as above. Need to find out where it is.

sudo updatedb

then

locate firefox

---

