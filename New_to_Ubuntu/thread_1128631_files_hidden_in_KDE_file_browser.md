---
title: "files hidden in KDE file browser"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by qwertyuiop96 on 2009-04-17
I used the .hidden file in Nautilus to make files hidden without changing their names.  However, this doesn't work in whatever KDEs manager is.  Anything like the .hidden for KDE?  If so, what?

---

### Post by qwertyuiop96 on 2009-04-18
Bump

---

### Post by Chemical Imbalance on 2009-04-18
."file name" should hide any file on linux regardless of file manager.  Are you asking how to show these hidden files?  

[http://www.felgall.com/lincmd5.htm](http://www.felgall.com/lincmd5.htm)

> Linux provides a vary simple way of "hiding" a file. All that you need to do when you create the file is to add a period to the front of the filename.

---

### Post by mgranet on 2009-04-18
Just put a dot (.) before the filename. 
```
.fileyouwanttohide
```

---

### Post by qwertyuiop96 on 2009-04-18
Prob is, these are config files for programs, if I put a dot in front the name isn't the same and the program errors, can't find file.

---

### Post by qwertyuiop96 on 2009-04-19
Anyone?

---

### Post by mikechant on 2009-04-20
Not sure if this is what you are looking for, but read this
[http://www.kdedevelopers.org/node/2231](http://www.kdedevelopers.org/node/2231)
particularly part 1 of 'what I did'.
However, this relates to Konquerer; I've got a feeling that Dolphin is the KDE file manager now (use Gnome myself so I'm not sure) so this may not apply.

Edit: Found this:
[https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/129796](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/129796)
So I guess it won't work - shame they din't explain why the feature was removed and just closed the bug report as invalid!

---

### Post by SuperSonic4 on 2009-04-20
.file works for me in kde and it works in both dolphin and konqueror

---

### Post by qwertyuiop96 on 2009-04-20
The .filewanthide works, its just that then the programs don't recognize the . files and error.

---

### Post by qwertyuiop96 on 2009-04-29
> **mikechant said:**
> Not sure if this is what you are looking for, but read this
[http://www.kdedevelopers.org/node/2231](http://www.kdedevelopers.org/node/2231)
particularly part 1 of 'what I did'.
However, this relates to Konquerer; I've got a feeling that Dolphin is the KDE file manager now (use Gnome myself so I'm not sure) so this may not apply.

Edit: Found this:
[https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/129796](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/129796)
So I guess it won't work - shame they din't explain why the feature was removed and just closed the bug report as invalid!

Ah well.  BTW< KDE 4 has both Konqueror and Dolphin- Dolphin default.  Konqueror is ported as primarily a web browser.  Konqueror doesn't recognise the .hidden file either.

---

### Post by NightwishFan on 2009-04-29
It should recognize it. Did you call the file with the . in front where it is not recognized?

---

### Post by qwertyuiop96 on 2009-04-29
I THINK you misunderstood me.  In nautilus you can create a file called .hidden and list the files you want hidden in it, and those files will be hidded.  Is there any eq for this in Dolphin?

---

### Post by NightwishFan on 2009-04-29
Ah, I see. That is... interesting. That sounds like a GVFS thing actually, and likely is unique to nautilus.

---

### Post by qwertyuiop96 on 2009-05-02
> **NightwishFan said:**
> Ah, I see. That is... interesting. That sounds like a GVFS thing actually, and likely is unique to nautilus.

That's what I was afraid of.  Oh well.:(

---

