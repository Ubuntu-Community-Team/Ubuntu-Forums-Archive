---
title: "incredibly strange behavior in firefox"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by yakinikku on 2011-02-28
Hi guys,  I hope you are able to help me out on this as it is a problem I have never seen before.  Last night firefox started acting funny, what it's doing is, in the bookmarks toolbar I have something like 6 bookmarks all with the titles removed so as to only see the favicon.  Last night these started constantly shuffling around as if someone were moving them around, but no one was doing anything of the sort.  While they are shuffling, the bookmarks are also being overwritten.  So the 6 become 4 of the same and 2 of the same, etc.  Once I open firefox I can see it starting, you can sit and watch them move around, it's incredibly strange.  I loaded firefox in safe mode and it didn't appear to happen in safe mode.  Any thoughts?

---

### Post by seawolf167 on 2011-02-28
That's quite weird and I kind of want to see it actually happen. I have no idea what's causing it aside from some addon incompatibility.

I have two suggestions

1. Remove/disable your addons, then install/enable them one at a time and see if one of them is causing it

2. Try reinstalling firefox

Back up your bookmarks (yes even though thats where you are noticing the strange behavior - the bookmarks exported file is saved as an html file so that should be ok)

Then do

```
sudo apt-get purge firefox
sudo apt-get install firefox
```

---

### Post by yakinikku on 2011-02-28
> **seawolf167 said:**
> That's quite weird and I kind of want to see it actually happen. I have no idea what's causing it aside from some addon incompatibility.

I have two suggestions

1. Remove/disable your addons, then install/enable them one at a time and see if one of them is causing it

2. Try reinstalling firefox

Back up your bookmarks (yes even though thats where you are noticing the strange behavior - the bookmarks exported file is saved as an html file so that should be ok)

Then do

```
sudo apt-get purge firefox
sudo apt-get install firefox
```

i will try to take a video of whats happening, give me a few minutes.  there are only 2 add ons installed on that computer, ad block plus and compact toolbar (i think thats what its called, its the one that collapses the file, edit, etc menus into an icon).  its really odd.  let me do a screengrab and post it.

---

### Post by yakinikku on 2011-02-28
here is a video of what happens.  as you can see a lot of the favicons are already the same, what i did was restored the bookmarks, opened firefox and tried to record it using istanbul but was having issues so i used GTK-recordmydesktop instead.  thats why they are already the same, but you can see how they are moving around on their own.  

[http://tinypic.com/r/25fq5bd/7](http://tinypic.com/r/25fq5bd/7)

very odd.

edit:  I just did the purge/install and the problem is still there, I think firefox needs to be completely removed and reinstalled (this includes the hidden folder, etc).  rm -rf .mozilla did not fix it either.  any other suggestions guys?

---

### Post by Rubi1200 on 2011-03-01
It could be an addon or a corrupted profile.

Start here:
[http://www.webgapps.org/blogs/firefox-tutorials](http://www.webgapps.org/blogs/firefox-tutorials)

(courtesy of forum member lovinglinux)

---

### Post by yakinikku on 2011-03-01
> **Rubi1200 said:**
> It could be an addon or a corrupted profile.

Start here:
[http://www.webgapps.org/blogs/firefox-tutorials](http://www.webgapps.org/blogs/firefox-tutorials)

(courtesy of forum member lovinglinux)

I did what this guy did

[http://aeric.poon.my/index.php/tag/desktop-couch-scratch/](http://aeric.poon.my/index.php/tag/desktop-couch-scratch/)

and it solved the problem.

---

### Post by frogotronic on 2011-07-12
Ive got this same problem - will try to disable bindwood.

- CH

---

### Post by frogotronic on 2011-07-15
> **cement_head said:**
> Ive got this same problem - will try to disable bindwood.

- CH

Disabling bindwood solved the issue.

Bug Report filed: [https://bugs.launchpad.net/ubuntu/+source/bindwood/+bug/811098](https://bugs.launchpad.net/ubuntu/+source/bindwood/+bug/811098)

---

