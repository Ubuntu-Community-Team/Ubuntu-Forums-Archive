---
title: "Complete remove and reinstall firefox"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by grobar87 on 2010-05-17
Complete remove and reinstall will fix my firefox problems?If yes, how to do that?
Thanks

---

### Post by Calash on 2010-05-17
Depends on what problems you are having.

I believe the following command lines will do it for you.

```

sudo apt-get purge firefox 
sudo apt-get install firefox

```

This will get rid of everything, including bookmarks if I remember correctly.

---

### Post by grobar87 on 2010-05-17
I try that...but still the same,firefox crash....

---

### Post by grobar87 on 2010-05-17
In terminal:

```
(firefox-bin:6213): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:6213): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:6213): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:6213): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:6213): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:6213): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:6213): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:6213): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:6213): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:6213): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:6213): Gdk-WARNING **: XID collision, trouble ahead
Segmentation fault

```

---

### Post by jerome1232 on 2010-05-17
Can you copy paste terminal output when launching it from a terminal? maybe there's a clue there.

Just pop open a terminal and type

```
firefox
```

Copy and paste the text that gets dumped at you. please put ```
 
``` tags around it to keep it readable.

edit: Looks like you beat me to it.

Have you fully updated your system? I see a bug mentioned in launchpad but it was for the RC of 10.04 and shows as fixed.

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/401823](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/401823)

---

### Post by grobar87 on 2010-05-17
> **jerome1232 said:**
> Can you copy paste terminal output when launching it from a terminal? maybe there's a clue there.

Just pop open a terminal and type

```
firefox
```Copy and paste the text that gets dumped at you. please put  tags around it to keep it readable.

in my previous post...

---

### Post by RiceMonster on 2010-05-17
If you're trying whipe the settings and addons and return to the default setup, you can do this:
```
mv ~/.mozilla ~/.mozilla.bak
```

If you want to get your settings back afterwards, you can do this:
```
mv ~/.mozilla.bak ~/.mozilla
```

---

### Post by grobar87 on 2010-05-17
> **RiceMonster said:**
> If you're trying whipe the settings and addons and return to the default setup, you can do this:
```
mv ~/.mozilla ~/.mozilla.bak
```If you want to get your settings back afterwards, you can do this:
```
mv ~/.mozilla.bak ~/.mozilla
```


i just want to be able to open all sites with firefox,but on some pages firefox crash...and i dont know how to fix this,so i think reinstallation will help :confused:

---

### Post by Calash on 2010-05-17
> **grobar87 said:**
> i just want to be able to open all sites with firefox,but on some pages firefox crash...and i dont know how to fix this,so i think reinstallation will help :confused:


You did a reinstall and it did not help, so we need to look at other possible problems.  Try what RiceMonster posted and see if that helps.  Also make sure your system is up to day by checking the update manager.

---

### Post by uRock on 2010-05-17
I wonder if the crashes are being caused by flash and not having enough RAM.

---

### Post by uRock on 2010-05-17
You can also give Chromium a try. It is in the repos, so installing is easy. ```
sudo apt-get install chromium-browser
```

---

### Post by grobar87 on 2010-05-17
```
mv ~/.mozilla ~/.mozilla.bak
```

This solve the problem i think..thanks RiceMonster and thanks to all for help!
I try chromium it's ok.
Thanks again :)

---

### Post by lovinglinux on 2010-05-17
> **grobar87 said:**
> ```
mv ~/.mozilla ~/.mozilla.bak
```

This solve the problem i think..thanks RiceMonster and thanks to all for help!
I try chromium it's ok.
Thanks again :)

I don't like to recommend that. It is certainly easy to fix problems by renaming your .mozilla folder, but then you will have to restore or re-enter all your Firefox settings, extensions, passwords, and so on. Additionally, you don't know what was causing the problem and it might come back. It could be an extension, some settings messing with Firefox or a corrupted file in your profile.

So I would recommend trying to find the culprit before doing the mozilla renaming. See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

I would start removing libmoon. Although it doesn't show up the terminal output, it is known to be causing Firefox to crash on Lucid.

---

