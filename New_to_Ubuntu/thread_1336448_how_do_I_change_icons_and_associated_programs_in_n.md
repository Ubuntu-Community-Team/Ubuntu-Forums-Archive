---
title: "how do I change icons and associated programs in nautilus"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by gatorbrit on 2009-11-24
I want to change the icons for some files.  For example: (see my screenshot)


*.dta files are stata data sets - I would like nautilus to say "Stata Data Set" under the "Type" column, rather than calling them programs.  Also I would like them to open with Stata when I click on them.

---

### Post by dca on 2009-11-24
You can right-click the files in nautilus and choose 'open with' tab, if program not listed, click the 'add' button. If not listed there, click 'use a custom command' option...

---

### Post by dca on 2009-11-24
Check this thread and see if that helps as well...
 
[http://ubuntuforums.org/showthread.php?t=656879](http://ubuntuforums.org/showthread.php?t=656879)

---

### Post by gatorbrit on 2009-11-24
> **dca said:**
> Check this thread and see if that helps as well...
 
[http://ubuntuforums.org/showthread.php?t=656879](http://ubuntuforums.org/showthread.php?t=656879)

Sort of worked.  I was able to change the file type description, but not the icon.   The thread above recommends a program called assogiate which works ok.   But the icon doesn't change.

If I right click on the file, and change the icon manually it only works for that file and not all files with the same extension.  

Thanks

---

### Post by dca on 2009-11-24
No problem, the change icon dealie (for individual files) works better when used with files that have generic extensions like:  .dat, .sh, .txt, etc etc
 
...your only other option is manually changing the icon in your /usr/share/icons/**whatever the icon package is**
 
For instance, the icon for most music files (mp3, m4a, wma) when using 'gnome' as your icon pack under desktop appearance themes is located in /usr/share/icons/gnome/**pick your size**/mimetypes/audio-x-generic.png
This would change how your music file icons in nautilus when you click on your 'My Music' directory
 
One caveat, it's easy to lose your place and screw things up...

---

### Post by MockY on 2009-11-24
```
sudo apt-get install assogiate
```
That program lets you set an icon for file types, system wide.

---

