---
title: "file cleaner for ubuntu/linux"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by scorpian81 on 2010-11-19
Hi, I was just wondering if there is a file cleaner like ccleaner for ubuntu/linux users?

---

### Post by NightwishFan on 2010-11-19
Linux handles most of the garbage cleaning itself with scripts, but for user stuff, like uneeded caches and private data you can use bleachbit. Click below to install:
[apt://bleachbit]("apt://bleachbit")

[http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

---

### Post by santosh83 on 2010-11-19
> **scorpian81 said:**
> Hi, I was just wondering if there is a file cleaner like ccleaner for ubuntu/linux users?

What about 'KleanSweep' and 'BleachBit'? Check out their descriptions in Synaptic. But personally I haven't used them.

---

### Post by Rubi1200 on 2010-11-19
Be aware that tools like Bleachbit can remove more than you want and cause problems.

There is little or no "junk" accumulated in Linux the way there is in Windows.

For general "cleaning" tips using the built-in tools in Ubuntu:
[http://ubuntuforums.org/showpost.php?p=800462&postcount=1](http://ubuntuforums.org/showpost.php?p=800462&postcount=1)

---

### Post by scorpian81 on 2010-11-19
Thanks for the replies and advice. That's a relief as I remember how quickly windows got full of junk so i shall just use the terminal/sudo things to clean up in the future.

---

### Post by Andrew.Z on 2010-11-27
> **Rubi1200 said:**
> Be aware that tools like Bleachbit can remove more than you want and cause problems.

You should never check options you don't understand, but each option is clearly labeled with a name and a verbose description.  Options that are most likely to cause regret (e.g., removing the Firefox places database) even have popup warnings.  Do any of the options in BleachBit remove more than what is described, or do you think users are easily confused?

> There is little or no "junk" accumulated in Linux the way there is in Windows.

Here is an article that has some counterexamples [Myth: Linux Doesn't Need a Registry Cleaner ](http://bleachbit.blogspot.com/2008/12/linux-registry-cleaner-myth.html).  I would say BleachBit itself (and all its options) is a counterexample. 

> **scorpian81 said:**
> Thanks for the replies and advice. That's a relief as I remember how quickly windows got full of junk so i shall just use the terminal/sudo things to clean up in the future.

A novice browsing the file system with the terminal and sudo is more likely to get into trouble than using an application (i.e., BleachBit) that organizes, identifies, and describes the files you are most likely want to remove.

---

