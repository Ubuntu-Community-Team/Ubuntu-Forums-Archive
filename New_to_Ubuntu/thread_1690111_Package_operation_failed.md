---
title: "Package operation failed"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by J4G on 2011-02-17
Hi! I'm completely new to Ubuntu, so please bear with me. :) I've been having trouble installing programs for a short time. Specifically I'm trying to install SciTE. Whenever I do so, however, I get the following error.

[B]Package Operation Failed
[/B]
The installation or removal of a software package failed. 

installArchives() failed: dpkg: parse error, in file '/var/lib/dpkg/available' near line 9316 package 'gvfs-backends': 
 `Depends' field, missing package name, or garbage where package name expected

Before trying to install this program, all other installations went fine. Any help would be appreciated...

---

### Post by J4G on 2011-02-17
[SIZE=3]**Update:**[/SIZE]
I tried to install Google Chrome. This time I got this message:

[I]
**An unhandlable error occured**

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.[/I]


I wonder why there are spelling errors...?

---

### Post by J4G on 2011-02-17
*bump*

---

### Post by outskut on 2011-02-17
You kindof have to get used to the software installation methods with ubuntu.  There are three main ways of installing software by one counting of it.  You can download packages from websites and run them with a dpkg manager (10.04 LTS and several releases before it had a good fast one, I think the developers have started experimenting with another one for 10.10 that I don't like so far just considering how slow it is).  Any package you download online has a chance of being incorrectly put together, but dpkg usually takes care of all the dependencies for the program automatically, which is nice.  You are usually downloading .deb or .rpm files right now, download the .deb files just because dpkg deals with them more easily.  If one source isn't working, find another source for the package you're trying to download

The most reliable way by far to install software is to use the synaptic package manager [System>Administration>Synaptic Package Manager] which searches through a list of websites called repositories, (listed with "$ cat /etc/apt/sources.list | less").  If you know the name of a program from a repository use the command "$sudo apt-get install ___ " where ___ is the package.

The most complicated way to install regular software is by source-code, downloading a directory with a ton of files in it.  To do that go into the directory and type:
$./configure
$make
$sudo make install

This will attempt to install this one package.  You'll probably then fail the installation with a list of dependencies to satisfy, you'll have to track down each of these dependencies and install them in sequence before your package will compile.

You'll get used to it all.  This is really more of an open-ended question, and I just rambled for a while.  I haven't found any single place yet where this is all really explained...


edit:  btw source code will probably be bundled together and compressed.

---

### Post by Dutch70 on 2011-02-17
which method are you using to install the packages 
...synaptic? software center? or the command line (terminal)
(software center is easiest for beginners)

or try running the following code in terminal to install uhhmmm...a linux version of google chrome.

```
sudo apt-get install chromium-browser
```

 Also, you didn't give any info about what distro you're using, or how you're trying to install anything.
 It would be beneficial for you to read [*[COLOR="Red"]_this_[/COLOR]*]("http://ubuntuforums.org/showthread.php?t=1422475")

Regards
Dave

---

### Post by J4G on 2011-02-17
Thanks for your patience and sorry for my ignorance. I've been using the Software Center on Ubuntu 10.10. I want to be able to download software from there again, but I keep getting the error listed in the first post (the Chrome post is irrelevant, I realize now).

installArchives() failed: dpkg: parse error, in file '/var/lib/dpkg/available' near line 9316 package 'gvfs-backends': 
 `Depends' field, missing package name, or garbage where package name expected

How can I fix this?

---

### Post by J4G on 2011-02-17
UPDATE:

I tried to install Chrome via the terminal. I got a similar-looking error message.

dpkg: parse error, in file '/var/lib/dpkg/available' near line 9316 package 'gvfs-backends':
 `Depends' field, missing package name, or garbage where package name expected
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by grahammechanical on 2011-02-18
Try this

Load software centre. Go to Edit>Software Sources. Select the Other software tab and see what is listed there. You may want to remove the tick marks against some of the entries. Do not worry. You will not lose what is written there unless you choose to select a line and then click Remove. Do not do that. Just remove the tick marks against some of the lines. 

Leave ticked Canonical Partners, Canonical Partners (Source code), Independent, and Independent (Source code). Select Close. Give the program a few seconds to adjust itself and then try to install a program from the Software Centre. If this fixes things you can go back into the Software Centre and put the tick mark back on those lines that you removed it from.

I had to do this the other day when some of the Updates failed to update. There was some sort of conflict with some of the sources of programs that I had listed. After the update had completed successfully, I restored the tick marks to those sources that I had removed them from.

Regards.

---

### Post by J4G on 2011-02-18
Thanks for your help. It didn't work though. :( 

Any other ideas? The error seems pretty specific and direct, but I'm not experienced enough to go diving into the source and program files yet.

---

### Post by J4G on 2011-02-18
When I looked further, I saw that the problem was probably the package "gvfs-backends". I tried to remove it with the software center, but I got the error again!  :mad: 

](*,)

---

### Post by J4G on 2011-02-18
Here's what it says about the package in /var/lib/dpkg/ under the file available.

```

Package: gvfs-backends
Priority: optional
Section: libs
Installed-Size: 2160
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: i386
Source: gvfs
Version: 1.6.4-0ubuntu1.1
Depends: libarchive1 (>= 2.2.3), libavahi-client3 (>= 0.6.16), libavahi-common3 (>= 0.6.16), libavahi-glib1 (>= 0.6.16), libbluetooth3 (>= 4.40), libc6 (>= 2.7), libcdio-cdda0, libcdio-paranoia0, libcdio10, libdbus-1-3 (>= 1.1.1), libdbus-glib-1-2 (>= 0.78), libexpat1 (>= 1.95.8), libgconf2-4 (>= 2.31.1), libglib2.0-0 (>= 2.24.0), libgnome-keyring0 (>= 2.20.3), libgphoto2-2 (>= 2.4.3), libgphoto2-port0 (>= 2.4.3), libgudev-1.0-0 (>= 147),(libgvfscommon0 (>= 1.1.7), libimobiledevice1 (>= 0.9.7), libplist1 (>= 0.13), libsmbclient (>= 2:3.3.1), libsoup-gnome2.4-1 (>= 2.27.4), libsoup2.4-1 (>= 2.26.1), libxml2 (>= 2.7.4), gvfs (= 1.6.4-0ubuntu1.1)

```

---

### Post by J4G on 2011-02-18
Reinstalled the package with Synaptic Package Manager... Didn't work. Completely removed it. Didn't work. I'm at a loss as to what to do here... If I can't change any programs, how on earth am I supposed to FIX one?!?!

---

### Post by J4G on 2011-02-19
*bump-a-dee-bump-bump*

PLEASE  help me... This is driving me insane.

---

### Post by J4G on 2011-02-19
HAHAHA! I FIXED IT BY BREAKING ONE OF MY SACRED RULES!
(Which is- Never mess with the source if you don't know what you're doing.

I opened something called Nautilus which I saw on another forum topic, went to the "available" file, and deleted gvfs-backends  from it (it was read-only without Nautilus open)!

Thanks for your help! :D

---

### Post by Dutch70 on 2011-02-19
> **J4G said:**
> HAHAHA! I FIXED IT BY BREAKING ONE OF MY SACRED RULES!
(Which is- Never mess with the source if you don't know what you're doing.

I opened something called Nautilus which I saw on another forum topic, went to the "available" file, and deleted gvfs-backends  from it (it was read-only without Nautilus open)!

Thanks for your help! :D

Glad to hear you got it figured out J4G.

Dont forget to mark your thread solved so others can find it when they have the same problem.

---

### Post by outskut on 2011-02-23
okay, first absolutely try Dave's suggestion.  Open a terminal window, that is   "Alt-F2" then type "gnome-terminal" and press enter, or find it in the applications menu.
Second type "sudo apt-get install chromium-browser" return

if it tells you that it can't find the package, type "sudo gedit /etc/apt/sources.list"

that file will have lines beginning with "##", "#" and deb-...   You can uncomment some of the lines at the bottom that begin with only 1 #.   Then try your sudo apt-get install chromium browser again.

Also, tell us what version of Linux you're using and more details about what you're doing to try to use to install this.  If you can, copy and paste the paragraph surrounding line 9316 of /var/lib/dpkg/available, that is into a terminal window type:
gedit /var/lib/dpkg/available
and scan to line 9316.  Now, if you change your repository list (sources.list) be aware that /var/lib/dpkg/available might change.
if that happens just find the line starting with
Package: gvfs-backends
and copy everything after that.

Submit more information about what you're trying to do though.  Are you just trying to install chromium-browser, or are you trying to do something different.

---

### Post by frotzed on 2011-02-23
> **J4G said:**
> HAHAHA! I FIXED IT BY BREAKING ONE OF MY SACRED RULES!
(Which is- Never mess with the source if you don't know what you're doing.

I opened something called Nautilus which I saw on another forum topic, went to the "available" file, and deleted gvfs-backends  from it (it was read-only without Nautilus open)!

Thanks for your help! :D

This is full of awesome.  Seeing how you took a risk, did some trouble-shooting and solved the issue yourself, I have no doubt that you'll have a long and happy life with Ubuntu :D  I believe a congratulations is in order!

---

