---
title: "kde screen saver"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2010-04-08
how to disable kde screensaver and enable xscreensaver????

---

### Post by undecim on 2010-04-08
Installing kscreensaver-xsavers should allow you to use screensavers from xscreensaver in kscreensaver.

---

### Post by 1991sudarshan on 2010-04-09
> **undecim said:**
> Installing kscreensaver-xsavers should allow you to use screensavers from xscreensaver in kscreensaver.

no!!!!!! i installed the the kanjisaver but that screensaver is not available in the list of ksreensaver and how to make xscreensaver the default screensaver ??

---

### Post by ankspo71 on 2010-04-09
Here's a tutorial for setting the xscreensaver application as default in Kubuntu 9.10. [http://www.mangrums.net/content/kubuntu-karmic-koala-and-xscreensaver](http://www.mangrums.net/content/kubuntu-karmic-koala-and-xscreensaver)

I noticed that a couple of xscreensavers aren't available in gnome screensaver's gui too.

---

### Post by 1991sudarshan on 2010-04-09
> **ankspo71 said:**
> Here's a tutorial for setting the xscreensaver application as default in Kubuntu 9.10. [http://www.mangrums.net/content/kubuntu-karmic-koala-and-xscreensaver](http://www.mangrums.net/content/kubuntu-karmic-koala-and-xscreensaver)

I noticed that a couple of xscreensavers aren't available in gnome screensaver's gui too.

i was successful upto few steps after that i got this error message in the terminal

[B]kevin@sreenivassudarshan-desktop:/usr/lib/kde4/libexec$ sudo mv kscreenlocker kscreenlocker.bak
mv: cannot stat `kscreenlocker': No such file or directory
[/B]

---

### Post by ankspo71 on 2010-04-09
> **1991sudarshan said:**
> i was successful upto few steps after that i got this error message in the terminal

[B]kevin@sreenivassudarshan-desktop:/usr/lib/kde4/libexec$ sudo mv kscreenlocker kscreenlocker.bak
mv: cannot stat `kscreenlocker': No such file or directory
[/B]

Hmm, that's odd. The file exists on my system. Did you uninstall kscreensaver? It looks as if kscreensaver needs to be installed (or at least libkscreensaver because that is all I have installed) for this screenlocker part of the tutorial to work. Can you verify the kscreenlocker file exists by typing...
```
ls -a
```
if you are still in the same directory, or
```
ls -a /usr/lib/kde4/libexec
```
?

If it still doesn't exist with kscreensaver installed, I'm sure you could skip that part create a new kscreenlocker file like it says in the next step.

---

### Post by 1991sudarshan on 2010-04-09
> **ankspo71 said:**
> Hmm, that's odd. The file exists on my system. Did you uninstall kscreensaver? It looks as if kscreensaver needs to be installed (or at least libkscreensaver because that is all I have installed) for this screenlocker part of the tutorial to work. Can you verify the kscreenlocker file exists by typing...
```
ls -a
```
if you are still in the same directory, or
```
ls -a /usr/lib/kde4/libexec
```
?

If it still doesn't exist with kscreensaver installed, I'm sure you could skip that part create a new kscreenlocker file like it says in the next step.

only the kscreenlocker.bak exists that file also was creates in that process

---

### Post by ankspo71 on 2010-04-09
well, I installed xscreensavers and followed the tutorial, and installed kangisaver, but kanjisaver would not show up in kscreensaver settings or xscreensaver settings. According to several claims on the internet, kanjisaver doesn't display in the screensaver settings of KDE 4.xx, but it used to show up in 3.5xx. Here is someone's Ubuntu bug report stating this...
[https://bugs.launchpad.net/ubuntu/+source/kanjisaver/+bug/399016](https://bugs.launchpad.net/ubuntu/+source/kanjisaver/+bug/399016)
I added myself to the "this effects me too" list.

Kanjisaver man page: (which wasn't found in my kubuntu version):
[http://manpages.ubuntu.com/manpages/karmic/man6/kanjisaver.kss.6.html](http://manpages.ubuntu.com/manpages/karmic/man6/kanjisaver.kss.6.html)

---

### Post by ankspo71 on 2010-04-09
I finally got it to work (sort of).

In a nutshell, in the /usr/bin directory, I made a backup of kblankscrn.kss first, then replaced kblankscrn.kss with kanjisaver.kss
(This can be done by running dolphin as kdesudo, of course)

So, to enable the "kanjisaver" screensaver (by commands)
```
sudo mv /usr/bin/kblankscrn.kss  /usr/bin/kblankscrn.kss.bak
sudo mv /usr/bin/kanjisaver.kss  /usr/bin/kblankscrn.kss

```
You should now be able to select "blank screen" screensaver to use the kanjisaver. (see screenshot)

To restore the original "blank screen" screensaver:
```
sudo mv /usr/bin/kblankscrn.kss /usr/bin/kanjisaver.kss
sudo mv /usr/bin/kblankscrn.kss.bak /usr/bin/kblankscrn.kss
```

This can be done with no xscreensavers or extra kscreensaver packages installed in Kubuntu with KDE4

So if this works, then there must be a simple explanation somewhere as to why 
kanjisaver (and kannasaver) is not registering as a screensaver.

---

### Post by 1991sudarshan on 2010-04-09
thank you so much!!!

---

