---
title: "Anyone worked with the Adobe Flash 64 bit alpha?"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by pablolie on 2008-12-06
They have now an alpha version of Adobe Flash in 64 bit!

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

However, I was wondering whether anyone has used it with Ubuntu 8.10 64 bit and what their experiences have been. The package doesn't seem to be designed for Ubuntu (it is a tar.gz file).

I am very happy now - after some persistence I have Vista 64 and Ubuntu 8.10 64 dual booting off the same mirrored RAID drive. :-)

---

### Post by jbrown96 on 2008-12-06
It works flawlessly in Firefox for everything I've tried. It does not work in Konqueror though, although I haven't really tried anything to get it working.

To install it do the following in a terminal:

1) Remove current flash if installed
```
sudo apt-get remove flashplugin-nonfree
```
2) extract the package ```
tar xvf ./FLASH_PACKAGE
``` I don't remember the exact name of the package so replace it with whatever it is.
3) move the .so file into the plugin folder
```
mkdir ./.mozilla/plugins && mv ./libflashplayer.so ./.mozilla/plugins
```

---

### Post by drs305 on 2008-12-06
Simple to install, as jbrown96 documented, and I've had no problems using it with Firefox 3.0.4 and Intrepid 64-bit. My previous issue of having to restart FF every few hours to re-enable flash is a thing of the past.

---

### Post by pablolie on 2008-12-06
> **jbrown96 said:**
> It works flawlessly in Firefox for everything I've tried. It does not work in Konqueror though, although I haven't really tried anything to get it working.

To install it do the following in a terminal:

1) Remove current flash if installed
```
sudo apt-get remove flashplugin-nonfree
```
2) extract the package ```
tar xvf ./FLASH_PACKAGE
``` I don't remember the exact name of the package so replace it with whatever it is.
3) move the .so file into the plugin folder
```
mkdir ./.mozilla/plugins && mv ./libflashplayer.so ./.mozilla/plugins
```

Thanks a bunch. Where does the mozzila folder have to be created though? I am just afraid to break something, so I want to make sure.

---

### Post by pablolie on 2008-12-06
Wow - it all works!

Thank you so much!

I found the mozilla plugins folder in /usr/lib/mozilla/plugins, and then simply copied the file over as you said (well, with sudo), and now flash is working nicely. This is an alpha? It is great.

Will it update automatically as Adobe issues updates?

Thanks again...pablo

---

### Post by Skripka on 2008-12-06
> **drs305 said:**
> Simple to install, as jbrown96 documented, and I've had no problems using it with Firefox 3.0.4 and Intrepid 64-bit. My previous issue of having to restart FF every few hours to re-enable flash is a thing of the past.

Yep.  Flash10 64-bit is ANYTHING but what I would expect out of "alpha" quality software. 

Updates will NOT be automatically prompted or install.  You have to do that manually-until Flash10 64bit comes out as a final stable release-the install that like you would flashplugin-nonfree.

---

### Post by doorknob60 on 2008-12-06
Works great for me in Arch 64 bit.

---

### Post by wirelessmonkey on 2008-12-06
Works much better than 9 on my 64bit 8.10 install.

---

### Post by pablolie on 2008-12-06
> **Skripka said:**
> ...  You have to do that manually-until Flash10 64bit comes out as a final stable release-the install that like you would flashplugin-nonfree.

Will we have to manually uninstall the current version at that point in time? Just want to make sure I am ready to avoid a conflict at that point in time, although it seems as easy as deleting the .so file in the mozilla plugins...

---

### Post by Skripka on 2008-12-06
> **pablolie said:**
> Will we have to manually uninstall the current version at that point in time? Just want to make sure I am ready to avoid a conflict at that point in time, although it seems as easy as deleting the .so file in the mozilla plugins...

Odds are not....I installed the debian package for Flash10 on i386 *buntu, without removing Flash9, and things went fine.

But I'd delete it by hand just the same, restart your browser, to make sure it is aware that the browser doesn't get too confused.

---

