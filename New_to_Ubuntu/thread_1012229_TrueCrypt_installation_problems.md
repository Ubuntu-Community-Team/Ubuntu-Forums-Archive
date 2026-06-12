---
title: "TrueCrypt installation problems"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by ArcticWalrus on 2008-12-15
Could not open the file /home/***/.fr-AT2fAS/tru…ypt-6.1a-setup-ubuntu-x86.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

Character Coding: Current Locale (UTF-8)

...

I tried to Add other locals, such as all the Western ones and one with a Windows label. 

Any advice? 

This is a Ubuntu 8.10 32 bit system by the way. On the True crypt website [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php) it offers x86 and x64 and that's it.

---

### Post by Michaelg14 on 2008-12-15
Have you installed Truecrypt in your system?  If you have how are you trying to open it?

---

### Post by jbrown96 on 2008-12-15
Not sure if you have extracted the package yet, but try this. This assumes you downloaded the package to the desktop; substitute a different folder if it is another location. 

```
tar xvf ./Desktop/truecrypt-6.1a-ubuntu-x86.tar.gz
```

Then install with 
```
sudo dpkg -i ./truecrypt-6.1a-setup-ubuntu-x86
```

---

### Post by spy_1134 on 2008-12-15
Double click "truecrypt-6.1a-setup-ubuntu-x86" and when the prompt comes up click run

---

### Post by ArcticWalrus on 2008-12-15
> **Michaelg14 said:**
> Have you installed Truecrypt in your system?  If you have how are you trying to open it?

I downloaded the main file from the website using Firefox. I tried to click on it at the download location and in the 'Downloads' window in Firefox. Both resulted in that error. So it was never installed.

---

### Post by ArcticWalrus on 2008-12-15
> **jbrown96 said:**
> Not sure if you have extracted the package yet, but try this. This assumes you downloaded the package to the desktop; substitute a different folder if it is another location. 

```
tar xvf ./Desktop/truecrypt-6.1a-ubuntu-x86.tar.gz
```

Then install with 
```
sudo dpkg -i ./truecrypt-6.1a-setup-ubuntu-x86
```


***@desktop:~$ tar xvf ./Desktop/truecrypt-6.1a-ubuntu-x86.tar.gz
truecrypt-6.1a-setup-ubuntu-x86

***@desktop:~$ sudo dpkg -i ./truecrypt-6.1a-setup-ubuntu-x86
[sudo] password for ***: 
dpkg-deb: `./truecrypt-6.1a-setup-ubuntu-x86' is not a debian format archive
dpkg: error processing ./truecrypt-6.1a-setup-ubuntu-x86 (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 ./truecrypt-6.1a-setup-ubuntu-x86
***@desktop:~$ 


This is the error it returned

---

### Post by ArcticWalrus on 2008-12-15
> **spy_1134 said:**
> Double click "truecrypt-6.1a-setup-ubuntu-x86" and when the prompt comes up click run

No prompt comes up which says 'Run' I believe because my computer can't read the file which I was talking about in my first post.

---

### Post by Michaelg14 on 2008-12-15
Sounds like you may have had a bad download.  you should probably try it again.

If you download to your desktop you can double click on it, drag the file out, double click on it and choose run in a terminal.  It will open a menu that allows you to extract the correct file.

It takes longer to say it than it does to do it.

---

### Post by ArcticWalrus on 2008-12-15
OH wow I was so stupid... issue resolved thanks for your help.

---

