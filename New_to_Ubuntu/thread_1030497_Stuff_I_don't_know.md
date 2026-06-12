---
title: "Stuff I don't know"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by cymbalguy on 2009-01-04
I didn't see this mentioned anywhere. I bet this is easy for those who know. 

How does Ubuntu handle things like temporary internet files, cookies,registry entries (like in windows)?
you periodically have to defrag and decrapify the drive to get rid of all the build up with a windows based system.
Does the same thing apply to Ubuntu?
If so, how is it accomplished?

Also How can I make the mouse pointer bigger?
Thanks

---

### Post by steveneddy on 2009-01-04
Firefox, or whatever browser you use, takes care of the temp internet files and cookies.
Ubuntu doesn't have anything to do with that.

In Firefox, go to Edit --> Preferences --> Privacy

You can choose to delete individual cookies or all of them.

To make the mouse pointer bigger, go to the Desktop (minimize all windows)

right click the desktop

select change desktop background

click the theme tab on top

click the customize button

select the pointer tab

change the pointer if necessary and there is a slider at the bottom....slide right for a larger pointer.

---

### Post by sydbat on 2009-01-04
> **cymbalguy said:**
> I didn't see this mentioned anywhere. I bet this is easy for those who know. 

How does Ubuntu handle things like temporary internet files, cookies,registry entries (like in windows)?
you periodically have to defrag and decrapify the drive to get rid of all the build up with a windows based system.
Does the same thing apply to Ubuntu?
If so, how is it accomplished?

Also How can I make the mouse pointer bigger?
ThanksTemporary Internet files are handled through Firefox (or whichever browser you use). In Firefox, under Edit > Preferences > Privacy, you can choose to keep or automatically remove cookies, etc when you close Firefox.

You do not have to defrag your HDD with Linux...as long as you are using ext3 (ext2 also, I believe). This file system handles file blocks (or whatever they are called) differently than NTFS or other Windows based file systems.

And you shouldn't have to decrapify your HDD either. Most of what bogs down a Windows based system is the registry. Linux does not use anything like that. If you install then uninstall an application, it goes away completely. Occasionally, there are 'orphaned' files (files no longer used by any app), but these do not impact your system performance.

About the pointer - you can choose one of many different pointers via System > Preferences > Appearance. Under the Theme tab you can Customize your current theme by clicking the Customize button near the bottom and choosing the Pointer Tab. Some pointers cannot be changed in size, but several can be manipulated. I use one that I have made bigger in this manner.

---

### Post by stderr on 2009-01-04
Hi cymbalguy

Temporary interney files and cookies are handled by Firefox in Ubuntu, what with it being the default internet browser. You can change handling behaviour in Firefox's preferences (Edit -> Preferences). Check under the Privacy tab.

Linux doesn't use a Registry like Winblows (thank goodness). Things are typically configured with textual configuration files, although some of these settings can be changed with Ubuntu's stuff under System ->Preferences, ->Administration. Many of the configuration files are under /etc and (hidden) dotfiles under ~

As for defragmenting, not really, if you're using ext3 as the filesystem, which I presume you are... if you don't know  run the following in a Terminal (Applications -> Accessories)

```
mount | grep "/ "
```

and look for ext3, ext2, ntfs... something like that. That's the filesystem on your root device. Typically, you don't defrag extX filesystems. I think there do exist some sort of defrag tools somewhere, but it's not necessary as with Windows filesystems such as FATXX/NTFS. I don't bother, and I would imagine most people using Ubuntu don't bother - in fact, I'm not sure what it would do, or if it would help much. 

As for the build up of crap, there's not much to clean up... occasionally running things like

```
sudo apt-get autoremove
```

may free a few MBs or tens of MBs. *shrug*. The buildup of crap is more Windows-specific ;)

edit: I should mention, (sort of) recently GNOME has started using GConf, which is quite like the Winblows registry in some ways. Try doing (Alt + F2, gconf-editor) to have a look. Be careful ;)

---

### Post by jimmy the saint on 2009-01-04
If you know what you are doing, you can try a program like fslint.  It will look for such things as duplicate files and other "file system lint" that can eat up space.

---

### Post by Nepherte on 2009-01-04
There's no registry either. Instead, each program has its own configuration file. System wide configuration files are in /etc, user only configuration files are hidden files in the home directory.

---

