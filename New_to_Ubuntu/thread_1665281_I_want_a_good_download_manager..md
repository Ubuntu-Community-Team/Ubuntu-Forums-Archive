---
title: "I want a good download manager."
date: 2011-01-12
forum: New to Ubuntu
---

### Post by jijiisme on 2011-01-12
I really need a good download manager.
In window I used IDM. but now I move to the ubunut.
I can't choose the right one. pls suggest me.

---

### Post by jijiisme on 2011-01-12
now i am testing Uget.:)

---

### Post by gradinaruvasile on 2011-01-12
Multiget. Uses multiple simultaneous connections.

---

### Post by godspeedmav on 2011-01-12
If you use firefox, try using "downthemall" just like IDM. :D

here is the link; [https://addons.mozilla.org/en-US/firefox/addon/201/](https://addons.mozilla.org/en-US/firefox/addon/201/)

---

### Post by feistybird on 2011-03-15
> **jijiisme said:**
> now i am testing Uget.:)

**[SIZE="4"]uget[/SIZE]** +1 
(**[http://urlget.sourceforge.net/](http://urlget.sourceforge.net/)**)

It now supports Aria2 plugin meaning that it is able to make multi-segment downloads! uget is a fully functional GTK download manager with graphical interface, it has its own downloader based on curl, but supports aria2 plugin as well. and unlike other aria2 frontends, the uget also supports some basic command line control itself.

The author is busy working on the next version support Ubuntu indicators for Natty! See: **[https://launchpad.net/~plushuang-tw](https://launchpad.net/~plushuang-tw)**

Download deb files here: 

[COLOR="Blue"]i386
[https://launchpad.net/~ferramroberto/+archive/maverick/+files/uget_1.7.2-1~lffl~maverick~ppa_i386.deb](https://launchpad.net/~ferramroberto/+archive/maverick/+files/uget_1.7.2-1~lffl~maverick~ppa_i386.deb)

amd64
[https://launchpad.net/~ferramroberto/+archive/maverick/+files/uget_1.7.2-1~lffl~maverick~ppa_amd64.deb](https://launchpad.net/~ferramroberto/+archive/maverick/+files/uget_1.7.2-1~lffl~maverick~ppa_amd64.deb)[/COLOR]

[COLOR="Red"]*** Note  *** For Ubuntu 10.10 users, please upgrade Aria2 to v1.10.9+ [/COLOR] : **[https://launchpad.net/~t-tujikawa/+archive/ppa/+buildjob/2157226](https://launchpad.net/~t-tujikawa/+archive/ppa/+buildjob/2157226)** or the aria2 plugin may crash! although the default curl plugin should work anyway...

The uget's default download plugin is curl, If you want to use aria2 as the default downloader, You will have to manually enable the aria2 plugin after installation:

[IMG]http://wowubuntu.com/wp-content/uploads/2011/03/20110314_002.png[/IMG]
Picture source: [WOW!Ubuntu]("http://wowubuntu.com/") 

**[https://launchpad.net/~t-tujikawa/+archive/ppa/+buildjob/2157226](https://launchpad.net/~t-tujikawa/+archive/ppa/+buildjob/2157226)**

uget is already supported by the flashgot extension of Firefox.

For Google Chrome, it is recommended to use the latest[SIZE="4"] "Chrome Download Assistant"[/SIZE] - a flashgot equivalent extension provided by Google:
Picture source: [WOW!Ubuntu]("http://wowubuntu.com/") 

 [B][http://code.google.com/p/chrome-download-assistant/](http://code.google.com/p/chrome-download-assistant/)
[/B]
[IMG]http://wowubuntu.com/wp-content/uploads/2011/03/20110311_004.png[/IMG]

Picture source: [WOW!Ubuntu]("http://wowubuntu.com/") [http://wowubuntu.com/](http://wowubuntu.com/)

---

### Post by SuperBo on 2011-03-28
I use uGet 1.7.3 with aria2 1.10.0 but aria2 plugin dont work.
```
aria2.addUri response fault
```

---

### Post by Enigmapond on 2011-03-28
JDownloader just made a PPA for Linux version. This is, by far, the most efficient I have found.

```
sudo add-apt-repository ppa:jd-team/jdownloader
sudo apt-get update && sudo apt-get install jdownloader
```

Good Luck!

---

### Post by jijiisme on 2011-05-23
Now I found the best download program " axel "
that is command line tools, it support up to 256 thread of one download. 
to add this simply type 
> sudo apt-get install axelto download with multiple thread 
just type 
> axel -n <number of thread up to 256> <download link>not include < > to want more info just call man.

it is not a perfect download program but it is really powerful.

axel is not a long sword, its like a dagger. :)

---

### Post by jtarin on 2011-05-23
> **Enigmapond said:**
> JDownloader just made a PPA for Linux version. This is, by far, the most efficient I have found.

```
sudo add-apt-repository ppa:jd-team/jdownloader
sudo apt-get update && sudo apt-get install jdownloader
```

Good Luck!
I vote overwhelmingly for jDownloader. The best downloader I've ever used in over 15 years.Runs on any operating system. I can download in Linux and the reboot into Windows and resume my download.

---

### Post by jijiisme on 2011-05-23
ok thank for you suggestion I will try now. :)

---

### Post by jijiisme on 2011-05-23
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv B305FC46C55F531512AFA579D6B6DB186A68F637
gpg: requesting key 6A68F637 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

---

### Post by jijiisme on 2011-05-23
this is not the first time error
I think my country is block some port and some link , url " I hate access denied"
this is not your fault.:)
Is there another way to download package form http server?

---

### Post by jtarin on 2011-05-23
> **jijiisme said:**
> this is not the first time error
I think my country is block some port and some link , url " I hate access denied"
this is not your fault.:)
Is there another way to download package form http server?What's the url?
Try using ["wget"]("http://ubuntuforums.org/archive/index.php/t-644915.html").

---

### Post by jijiisme on 2011-05-23
no no i didn't mean like that, I mean to show me where I can download .deb package.

---

