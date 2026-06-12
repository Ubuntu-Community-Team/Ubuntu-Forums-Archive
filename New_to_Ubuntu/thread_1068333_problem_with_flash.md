---
title: "problem with flash"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by anico on 2009-02-12
Ok so i've installed java and flash successfully .. or so i'm told by my computer..

alexander@alexander-laptop:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for alexander: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  libboost-date-time1.34.1 libboost-thread1.34.1 openssh-blacklist
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

alexander@alexander-laptop:~$ java -version
java version "1.5.0_16"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_16-b02)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_16-b02, mixed mode)

yet whenever i enter a site that requires flash..firefox will let me know that i need to install missing plugin... i accept to download flash plugin but it says it's already clearly installed...

What is going on? Any help will be greatly appreciated (also i'm very very new to ubuntu.. please write as if i were 7 :) )

thanks in advance!

---

### Post by RomeReactor on 2009-02-12
Hi. in Firefox's address bar, write:
```
about:plugins
```
and press ENTER; scroll down and see how many entries you have for "Shockwave Flash", and post them here.

---

### Post by anico on 2009-02-12
Shockwave Flash

    File name: /usr/lib/swfdec-mozilla/libswfdecmozilla.so
    Shockwave Flash 9.0 r100

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Adobe Flash movie 	swf 	Yes
application/futuresplash 	FutureSplash movie 	spl 	Yes

---

### Post by roshanjose on 2009-02-12
thats not latest...

install flash 10 rom the adobe

---

### Post by anico on 2009-02-12
i know but i thought this version could work too. When i go to the flash site to download the .deb file.. i get an error saying "Error: Wrong architecture 'i386' "

---

### Post by RomeReactor on 2009-02-12
> **anico said:**
> Shockwave Flash

    File name: /usr/lib/swfdec-mozilla/libswfdecmozilla.so
    Shockwave Flash 9.0 r100

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Adobe Flash movie 	swf 	Yes
application/futuresplash 	FutureSplash movie 	spl 	Yes
Looks like you have **swfdec-mozilla** installed; if you have the **gnome** package installed, removing swfdec-mozilla will also uninstall the gnome metapackage, but not the rest of the packages themselves. Note that having the Gnome package installed is not the same as the Ubuntu desktop package.

> i know but i thought this version could work too. When i go to the flash site to download the .deb file.. i get an error saying "Error: Wrong architecture 'i386' "
You seem to be running Ubuntu 64 bit; to make sure, open a terminal (Applications->Accessories->Terminal), paste the following there:
```
uname -m
```
and if the result is x86_64, you have a 64 bit installation.

Ether way, you can uninstall the swfdec-mozilla package and install flashplugin-nonfree (close Firefox first):
```
sudo aptitude purge swfdec-mozilla && sudo aptitude install flashplugin-nonfree
```
Reopen Firefox, and Flash should be working.

---

### Post by anico on 2009-02-13
So it appears i do have the 64 version.. what is the difference?? 
I used the code you gave me and still no luck with flash... how does the gnome package differ from ubuntu package??? I am really lost! thanks

---

### Post by 3rdalbum on 2009-02-13
Flash 10 for 64-bit is still in development stage but it is available from [http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")  right at the bottom of the page.

---

### Post by RomeReactor on 2009-02-13
> **anico said:**
> So it appears i do have the 64 version.. what is the difference??
There was no 64 bit version of Flash until recently, as 3rdalbum pointed out.

> I used the code you gave me and still no luck with flash...
Did you restart Firefox after purging swfdec-mozilla?

> how does the gnome package differ from ubuntu package??? I am really lost! thanks
The gnome package isn't installed by default, whereas if you installed Ubuntu, you get the ubuntu-desktop package by default. In other words, you must manually install the gnome package; otherwise, it won't be installed on your system.

As 3rdalbum says, there's now a 64 bit version of the flash plugin, and it seems to perform better than the 32 bit version with a wrapper. If you wish to install it, open a terminal and run:
```
gedit Flash64
```
When Gedit opens, paste this into it:
```
#!/bin/bash
aptitude -y purge flashplugin-nonfree nspluginwrapper swfdec-mozilla gnash mozilla-plugin-gnash gnash-common
updatedb
for x in `locate libflashplayer.so`; do rm $x; done
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz
tar -xvzf libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz
cp ~/libflashplayer.so /usr/lib/mozilla/plugins
rm ~/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz
rm ~/libflashplayer.so
```
This will make sure your system doesn't have any conflicting libflashplayer.so files, and it will install the plugin, essentially copying the file to **/usr/lib/mozilla/plugins**, so it is available systemwide; now save the file, close Gedit, and make the file executable:
```
chmod +x Flash64
```
Close Firefox, then run the script using sudo:
```
sudo ./Flash64
```
Now open Firefox again, and Flash should be working.

---

### Post by anico on 2009-02-13
I followed the procedure but it seems as though mozilla didn't recognize it as a plugin :( i went on about:plugins and there was nothing from flash there.I may have made a mistake as the file is in my home folder..although this one seems to be here:


alexander@alexander-laptop:~$ ls -al /usr/lib/mozilla//plugins/
total 9328
drwxr-xr-x 2 root root    4096 2009-02-13 21:16 .
drwxr-xr-x 4 root root    4096 2009-01-20 05:12 ..
-rwxr-xr-x 1 root root 9526312 2009-02-13 21:16 libflashplayer.so

i don't know if i should reinstall it and save it in /urs/lib/mozilla/plugins folder?

sorry to bother you this way! i'm so close to get it!!

Thanks so much!
:)

---

### Post by RomeReactor on 2009-02-13
Did you restart Firefox after installing the plugin? If so, close Firefox and delete the xpti.dat file in ~/.mozilla/firefox/*default:
```
rm ~/.mozilla/firefox/*default/xpti.dat
```
Open Firefox again and see if it now lists the plugin. What version of Ubuntu do you have?

---

### Post by anico on 2009-02-13
i typed in the code.. is it normal that nothing happened as a result of typing that in terminal?
ugh.. it's still not showing anything in firefox..


i have ubuntu 8.04 Hardy Heron...

---

