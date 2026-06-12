---
title: "How to install tar.bz2"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by MedeX on 2009-09-26
Can anyone tell me how to install tar.bz2?? i want to install firefox 3.5.3 and i even cant install a software... ah feels great!

---

### Post by dagoth_pie on 2009-09-26
It's most likely a source code file, unless you're wanting to learn to compile source code, then I'd suggest either managing with whats in the repositories, or trying to find a .deb package, possibly at getdeb.

Why is it that you're wanting a more recent version of FF?

---

### Post by nmccrina on 2009-09-26
Move the tar.bz2 to whatever directory you want to install it in (I suggest either /home/username/bin or /usr/local/bin; if the latter, just prefix all the following commands with sudo).

then
```
tar -xjvf whatever.tar.bz2
```

In the case of firefox, this is all you have to do. Just cd into the newly extracted directory and run ```
./firefox
```

Now, in order to be able to start firefox from anywhere, you should make a symlink to the firefox binary. For example, if your firefox directory is /home/username/bin/<firefox-folder-name>, cd to /home/username/bin and run
```
ln -sv ./<firefox-folder-name>/firefox ./firefox
```
Now, assuming that /home/username/bin is in your PATH (it should be), you could run firefox from any directory by typing
```
firefox
```

---

### Post by nmccrina on 2009-09-26
> **dagoth_pie said:**
> 
Why is it that you're wanting a more recent version of FF?

Because Firefox 3.5 is freakin' awesome!

> **dagoth_pie said:**
> It's most likely a source code file, unless you're wanting to learn to compile source code, then I'd suggest either managing with whats in the repositories, or trying to find a .deb package, possibly at getdeb.


Actually, if you go to the firefox site and hit the big green download button, you get a tar.bz2 which is entirely self-contained, no compiling or anything. Just extract it like above.

You can compile Firefox from scratch, but it is a major pain (as any project that size would be), and frankly if you're just an end user and not trying to roll your own variant or something I don't see going to the trouble of actually building it yourself. Just use the binaries you get from the main download page.

---

### Post by dagoth_pie on 2009-09-26
Alright then, I guess I forget you can put things besides source code into tarballs... :lolflag:

---

### Post by kansasnoob on 2009-09-26
> **MedeX said:**
> Can anyone tell me how to install tar.bz2?? i want to install firefox 3.5.3 and i even cant install a software... ah feels great!

Assuming you already have an older version of Firefox I'd just use Ubuntuzilla:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

Note: Be sure Firefox is closed when you run the script!

---

### Post by pedro3005 on 2009-09-26
I got it by going into Synaptic (System > Administration > Synaptic Package Manager) and searching for firefox-3.5, marking it for installation and clicking apply. Simple as that.

---

