---
title: "Installing songbird via script"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by CaptainMark on 2009-11-16
I tried installing songbird via scripts as per instructions here [https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird) after following the instructions i get the message that songbird has been installed but when i click on it in the Sound & Video menu is get an error reading "Could not launch songbird music player, failed to execute child process "Songbird" no such file or directory exists." Heres the terminal output when i try to install, it looks like its not finding any files online```
mark@mark-desktop:~$ Desktop/installsongbird.sh 

(zenity:4530): Gtk-WARNING **: Theme directory scalable/stock of theme Minty has no size field

0
--2009-11-16 12:52:17--  http://www.xs4all.nl/~mgj1/Songbird/64.bit
Resolving www.xs4all.nl... 194.109.6.92
Connecting to www.xs4all.nl|194.109.6.92|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-11-16 12:52:18 ERROR 404: Not Found.

head: cannot open `64.bit' for reading: No such file or directory
head: cannot open `64.bit' for reading: No such file or directory
rm: cannot remove `64.bit': No such file or directory
tar: : Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
mv: cannot stat `Songbird': No such file or directoryrm: cannot remove `Songbird*.tar.gz': No such file or directory
rm: cannot remove `/usr/bin/Songbird': No such file or directory
(zenity:4565): Gtk-WARNING **: Theme directory scalable/stock of theme Minty has no size field

```


Edit: I wanted to use scripts over getdeb so i can autoupdate songbird once it is installed

---

### Post by soapytheclown on 2009-11-16
```
mark@mark-desktop:~$ Desktop/installsongbird.sh 

--2009-11-16 12:52:17--  http://www.xs4all.nl/~mgj1/Songbird/64.bit
Resolving www.xs4all.nl... 194.109.6.92
Connecting to www.xs4all.nl|194.109.6.92|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-11-16 12:52:18 ERROR 404: Not Found.


```

your problem lies here,

wget [http://www.xs4all.nl/~mgj1/Songbird/64.bit](http://www.xs4all.nl/~mgj1/Songbird/64.bit)

in that script doesnt exist, so it cant continue, If you really want cutting edge stuff id suggest you use this ppa:

[https://launchpad.net/~songbird-daily/+archive/ppa](https://launchpad.net/~songbird-daily/+archive/ppa)

---

### Post by CaptainMark on 2009-11-16
okay, so i needed a quick fix to sort out my ipod earlier today so used getdeb, if i add the daily builds ppa will i need to uninstall the getdeb version or will the ppa just update automatically

---

