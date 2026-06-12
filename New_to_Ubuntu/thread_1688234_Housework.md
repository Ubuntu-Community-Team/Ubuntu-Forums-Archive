---
title: "Housework"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by PhilRogers34 on 2011-02-15
Ok so when i was using xp every couple of weeks i would run the ' disc cleanup' tool, dfrag the hard drive, delete all the temporary files and clean the mru, to try and stop the system getting clogged up and slowing down.

can i do the same in ubuntu? how do i locate these tools and how do i use them? is there an application that can do these or will i need to use the terminal?   i would prefer apps first then the terminal


Thanks

---

### Post by Hippytaff on 2011-02-15
In System > preferences (or administration) there is dic janitor (or some thing like that, at wotk so can't check the specifics) that where you can to some house-keeping) though defragging tends to be mainly a windows bain.
 
There are commands for the terminal such as 
```

sudo apt-get autoclean

```
 
etc

---

### Post by Paqman on 2011-02-15
> **PhilRogers34 said:**
> Ok so when i was using xp every couple of weeks i would run the ' disc cleanup' tool, dfrag the hard drive, delete all the temporary files and clean the mru, to try and stop the system getting clogged up and slowing down.

can i do the same in ubuntu?


You can, but you'll find you don't really need to. Ubuntu doesn't slow down over time. Cleaning out some junk will free up disk space, but that's all.

There's no need to actively defrag Linux filesystems. As long as they aren't run at over about 80% capacity they don't really fragment to any degree that would ever affect performance.

Temporary files are deleted every boot, so you don't need to worry about that either.

> 
how do i locate these tools and how do i use them? is there an application that can do these or will i need to use the terminal?   i would prefer apps first then the terminal


You could try Bleachbit. It will get in and clean out the caches of all sorts of apps. As I said above, this won't improve performance, but will free up space.

Some other things you could do would be open up Synaptic or Ubuntu Software Centre and delete any unused kernels. Search for "linux-image" and delete all of them except the current one and the linux-image-generic metapackage. Doing so frees up abut 100MB per kernel, which is nice.

---

### Post by Paqman on 2011-02-15
> **Hippytaff said:**
> 
There are commands for the terminal such as 
```

sudo apt-get autoclean

```


Yep, this one gets rid of all obsolete .deb files in the package manager's cache.

There's also:
```
sudo apt-get autoremove
```

Which looks for packages that were installed to satisfy a dependency of another package, and removes them if they're no longer required.

---

### Post by Hippytaff on 2011-02-15
> **Paqman said:**
> You can, but you'll find you don't really need to. Ubuntu doesn't slow down over time. Cleaning out some junk will free up disk space, but that's all.
 
And that's one of the many reason I prefer the superior linux os ;-)

---

### Post by Paqman on 2011-02-15
> **Hippytaff said:**
> And that's one of the many reason I prefer the superior linux os ;-)

Totally. People always accuse Linux of being a tinkerer's OS, but I spent far more time nursing the OS along on Windows. That was on XP though, I believe recent versions of Windows have got a bit better.

---

### Post by Hippytaff on 2011-02-15
> **Paqman said:**
> Totally. People always accuse Linux of being a tinkerer's OS, but I spent far more time nursing the OS along on Windows. That was on XP though, I believe recent versions of Windows have got a bit better.
 
since I rid myself of windows and the more I become familiar with linux the more baffled I am about why people buy windows, but there you go.
 
The linux is feared - though I have managed to convert 3 people so far :-)

---

### Post by waynefoutz on 2011-02-15
+1 on Bleachbit. Ubuntu Tweak  is a great tool as well. Stay away from the "Computer Janitor" application, I would suggest even uninstalling it, because it has the potential to break things.

---

### Post by waynefoutz on 2011-02-15
> since I rid myself of windows and the more I become familiar with linux the more baffled I am about why people buy windows, but there you go.


Because that's what comes installed on most computers, most people have no idea there is an alternative. Of those that do, Linux is perceived to most of them as a hard to use OS for nerds who prefer typing at a Unix command line.

---

### Post by Paqman on 2011-02-15
> **Hippytaff said:**
> the more baffled I am about why people buy windows

There's lots of good reasons to use Windows dude. What's right for you isn't necessarily the same for others.

[/offtopic]

---

### Post by Hippytaff on 2011-02-15
> **Paqman said:**
> There's lots of good reasons to use Windows dude. What's right for you isn't necessarily the same for others.
 
[/offtopic]
 
Actually I have to admit to keeping one laptop with windopws on it, for certain occasions
 
I'll stop hijacking the thread

---

