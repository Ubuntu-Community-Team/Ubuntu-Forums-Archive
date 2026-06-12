---
title: "Flash problem with jaunty 64"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by Omegaxis on 2009-05-02
I have no flash video in Firefox (not even a grey box)
Also in the plugin menu in firefox version 9 of shockwave is still there after I installed version 10.

---

### Post by 123456789123456789123456 on 2009-05-02
Try this, My friend found out that flash is not installed automatically, in Ubuntu.
You can get it, at least part of it, by going to hulu.com
It will direct you to download the deb file, install the file.
You will need some extra files, if the computer does not prompt you to get the files automatically, go to synaptic, search for flash, and choose all the flash plugins you find, and apply changes.
After you apply all the flash changes, flash should work.

---

### Post by nhasian on 2009-05-02
the one you want in synaptic is flashplugin-nonfree.  you can also easily install it in a terminal by typing:

```
sudo apt-get install flashplugin-nonfree
```

or easier still, just click [HERE]("apt:flashplugin-nonfree") to have it installed automatically

---

### Post by Omegaxis on 2009-05-02
I already have all of the needed files installed.
I just reinstalled them all to be sure.

---

### Post by arashiko28 on 2009-05-02
Go the x86 64bit part of the forum, there's a sticky, by following it, I have flash and java working like a charm.

---

### Post by inobe on 2009-05-02
> **Omegaxis said:**
> I have no flash video in Firefox (not even a grey box)
Also in the plugin menu in firefox version 9 of shockwave is still there after I installed version 10.

if you have **swfdec-mozilla** installed remove it.

---

### Post by Racecar56 on 2009-05-02
by the way...
flash != shockwave

---

### Post by presence1960 on 2009-05-02
> **Omegaxis said:**
> I have no flash video in Firefox (not even a grey box)
Also in the plugin menu in firefox version 9 of shockwave is still there after I installed version 10.

[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490) for adobe flash

[http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59) for 64bit mozilla java plugin

Works all the time for me in Hardy, Intrepid and now Jaunty.

---

### Post by Omegaxis on 2009-05-02
> **inobe said:**
> if you have **swfdec-mozilla** installed remove it.

That did the trick, thank you very much!

---

### Post by inobe on 2009-05-02
i struggled for a "week" and removing that took merely a minute.

---

