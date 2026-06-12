---
title: "How to remove with apt-get (questions)"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by Patrick Snyder on 2009-03-19
Hello all (^_^)/
I'm trying to get more comfortable with the command line, so please forgive some newbie questions.


I used:
sudo apt-get install (package name)
It said:
After this operation, **_356kB_** of additional disk space will be used.


And then tried:
sudo apt-get remove (package name)
It said:
After this operation, _**213kB**_ disk space will be freed.


**_Question 1:_**
How can I get it to remove *everything* it installed.  I'm guessing the 143kB is some sort of left over configuration.


**_Question 2:_**
I got the same text when I tried:
sudo apt-get purge (package name)

man apt-get said:
```
purge
     purge is identical to remove except that packages are removed and purged.
```

What does purge mean in this sense?


**_Question 3:_**
In Synaptic Package Manager:
What exactly is the difference between "Mark for Removal" and "Mark for Complete Removal"

*_Question 3.5:_*
Does "Mark for Complete Removal" get rid of every last kB that was installed during installation including dependencies and configuration files?



**_Question 4:_**
man apt-get says:
```
autoremove
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for some package and that are no more needed.
```

Is this safe to run by a newb like me?  If so, why doesn't this run each time a package is removed?


**_Sum up:_**
In the end I would like to be able to delete every last kB of data (including configuration files) of programs I uninstall.  I know this is often not necessary, but I do like to try a lot of programs and then delete them a week, a day, or a few minutes later.  

I don't want them leaving little bits of themselves, even if it doesn't fill up my harddrive.  I like to keep things clean in order to navigate through.



Anything you can tell me would be greatly appreciated!  (^_^)/
Best Wishes,
Patrick

---

### Post by binbash on 2009-03-19
purge also removes  configuration files.For question 4, it is not always safe.Google > apt-get vs aptitute for the answer.

---

### Post by yeats on 2009-03-19
> 
Question 1:
How can I get it to remove everything it installed. I'm guessing the 143kB is some sort of left over configuration.

Funny - this is something I've never even noticed before (the difference in kB)  I have enough disk space to be unconcerned about this...  I'm not sure of the exact answer here, but...

> What does purge mean in this sense?

Purge means that apt-get also removes configuration files (usually found in the /etc directory) when uninstalling.  By default it does not.

> In Synaptic Package Manager:
What exactly is the difference between "Mark for Removal" and "Mark for Complete Removal"

Mark for Removal = sudo apt-get remove

Mark for Complete Removal = sudo apt-get purge

> Question 3.5:
Does "Mark for Complete Removal" get rid of every last kB that was installed during installation including dependencies and configuration files?

Not sure about every last kB... Do you have limited disk space?

> Is this safe to run by a newb like me? If so, why doesn't this run each time a package is removed?

It is safe to run, yes.  Not sure why the packages are not removed by default, but I imagine the concept of choice/preference is involved, as that is a common theme in Linux in general (the system, unlike proprietary systems, leaves some of the decision-making to the user).

> Sum up:
In the end I would like to be able to delete every last kB of data (including configuration files) of programs I uninstall. I know this is often not necessary, but I do like to try a lot of programs and then delete them a week, a day, or a few minutes later.

I don't want them leaving little bits of themselves, even if it doesn't fill up my harddrive. I like to keep things clean in order to navigate through.

You can also do:

```
sudo apt-get autoclean
```

Which may do what you're attempting automatically.  As I said, this is not a huge concern for most users, so I've never investigated.

Hope that helps....

---

### Post by mocoloco on 2009-03-19
I've never noticed that either, good question! Would this have to do with apt's cache? All the .deb files are actually still kept in a cache after download, and they're not deleted even after remove or purge. The files are in /var/cache/apt/archives
Maybe see if the package in question is there and if it's size fits.
I've never really understood the point of keeping these files around, just taking up space, and I'll often configure synaptic not to keep them (Settings -> Preferences -> Files).  I'm sure there's a CLI way to clear them with apt-cache or something.

Anybody able to confirm if these files are the discrepancy, and while you're at it what the reason for keeping them in cache is?

---

### Post by dwasifar on 2009-03-19
When you *apt-get install [package]*, apt installs that package and all its dependencies (other packages required to make that package work).

When you *apt-get remove [package]*, apt removes just that package.  It does NOT remove the dependencies, because they could be in use by other packages too.

This is what probably accounts for the difference in size between what was installed and what was removed.

If you want to remove unneeded dependencies, the command is *sudo apt-get autoremove.*

---

### Post by MrWES on 2009-03-19
use 

sudo apt-get autoremove <packagename>

that will remove the dependenacies that were originally installed.

Bill

---

