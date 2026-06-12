---
title: "can't upgrade to 10.10"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by wordmaster on 2011-02-27
When I try to upgrade I get the following error:

Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

Please help.

---

### Post by Frogs Hair on 2011-02-27
Here is a related thread .[http://ubuntuforums.org/showthread.php?t=1591435](http://ubuntuforums.org/showthread.php?t=1591435)

---

### Post by wordmaster on 2011-02-27
> **Frogs Hair said:**
> Here is a related thread .[http://ubuntuforums.org/showthread.php?t=1591435](http://ubuntuforums.org/showthread.php?t=1591435)

When I try to do what that thread says, I get the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ppa-purge is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ppa-purge has no installation candidate

so that doesn't work either.

How do you repair broken packages?

---

### Post by sydbat on 2011-02-27
What version of Ubuntu are you running now?

Also, you can go into your Software Sources and disable all your PPA's manually. That might help.

---

### Post by ivanovnegro on 2011-02-27
> **wordmaster said:**
> When I try to do what that thread says, I get the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ppa-purge is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ppa-purge has no installation candidate

so that doesn't work either.

How do you repair broken packages?

Maybe the PPA's are making the problem while upgrading, I saw this often, disable them like said before and after the upgrade enable them again.
To repair broken packages you could go to Synaptic and choose Repair broken packages.

---

### Post by Frogs Hair on 2011-02-27
Try running these one at a time and check for errors.

```
sudo dpkg --configure -a
``` 

```
sudo apt-get install -f
```

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

---

### Post by wordmaster on 2011-02-27
> **ivanovnegro said:**
> Maybe the PPA's are making the problem while upgrading, I saw this often, disable them like said before and after the upgrade enable them again.
To repair broken packages you could go to Synaptic and choose Repair broken packages.

I am running 10.04. What are ppa's and how do you disable them? Also, I go to synaptic and click on broken packages and none are showing, but if they were, I see no option to fix them.

---

### Post by ivanovnegro on 2011-02-27
> **wordmaster said:**
> I am running 10.04. What are ppa's and how do you disable them? Also, I go to synaptic and click on broken packages and none are showing, but if they were, I see no option to fix them.

Ok, sorry, to not be precise enough.
Did you ever install something outside the official package manager?
Some things you can install are PPA's, unofficial packages for Ubuntu, normally you add them to your sources list. So, look in your sources list if you have some PPA's there. For example: Software Center-> Edit (I think, Im not a native English speaker)-> Software packages-> Other software. There you can disable them.  
If you want to repair anyway some packages please you use the command of Frogs Hair or from Synaptic-> Edit-> Repair packages.
Maybe you could also post here your sources list to see if something is avoiding the upgrade process.

---

### Post by bbd92b on 2011-02-28
Ok, I've exactly the same problem. I've tried cleaning up my ppa's, looked for broken packages with synaptic, used the terminal to try absolutely everything on this forum and I still get this:

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

This can be caused by:
* Upgrading to a pre-release version of Ubuntu
* Running the current pre-release version of Ubuntu
* Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.


I have to admit this is the first time I'm starting to have trouble with Ubuntu since I started using it last September on an Acer Aspire Timeline from 2009.
Somehow, trying all these things I've deleted a few programs like LibreOffice, Chrome and Grism, but when I installed Chrome again everything (bookmarks, passwords etc) was alright.
I seriously am starting to worry about what the hell is happening to my computer. Right now getting this machine upgraded is a matter of self-confidence!
Someone please help me before I get mad haha

---

