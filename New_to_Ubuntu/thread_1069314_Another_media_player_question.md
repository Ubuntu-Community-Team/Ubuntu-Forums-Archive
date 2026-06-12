---
title: "Another media player question"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by nyvolvolvr on 2009-02-13
I've just started playing with Ubuntu and its a great OS.  Now the problem...

Situation:  Ubuntu is loaded on a laptop without internet access, downloaded mplayer .deb files onto usb drive and loaded to laptop.  Went to the terminal and navigated to the folder with the deb files and typed sudo dpkg -i *.deb.  It said the files were unpacking then I encountered the following errors:

libenca0 depends on libc6 (>=2.7-1); however
Package libc6 is not configured yet

or 

dpkg: error processing libfaac0 (--install)
dependcy problems - leaving uncofigured

I think this happens for every file.

Someone please help, I've been trying to get this to work for the past week and my computer is about to go through the window.

**Additional info**
I went to the website below and selected my Ubuntu version (8.04) and typed mplayer for the package and downloaded all of the urls.

[http://labs.fajran.web.id/p/apt-web/index.php](http://labs.fajran.web.id/p/apt-web/index.php)

---

### Post by Alterax on 2009-02-13
I'm assuming you're originally getting these from an Ubuntu desktop.  That being the case, I recommend using aptoncd to snag these packages (and their dependencies), then put them on a cd.

Then take the CD-rom to the laptop and do a "sudo apt-cdrom add".  Then use apt-get install to install the packages.

---

### Post by nyvolvolvr on 2009-02-13
Wow, thanks for the quick response.

I'm not sure I understand your question but here goes.  I downloaded the deb files onto a windows machine from the url give previosly, then moved them to my usb drive.

---

### Post by nyvolvolvr on 2009-02-14
I'm very new to this whole Ubuntu thing so any help would be great.  Please bear with me as I dont yet understand all of the sudo's and apt's and other keywords.

---

### Post by psychx on 2009-02-14
I know this won't necessarily help your problem, but I just starting tinkering with Ubuntu 8.10 on a desktop with a wired eth0 connection. I downloaded Songbird as a .deb package and installed it - works great! I really like Songbird, it is really fast, stable, and looks nice, too. Try giving it a try sometime.

---

### Post by nyvolvolvr on 2009-02-14
Thanks, where did you obtain the deb package?  Is it on the Songbird website?

---

### Post by psychx on 2009-02-14
[www.getdeb.net](www.getdeb.net) and search for whatever files you need, ie: Songbird

You should be able to download the .deb file and run it natively.

---

### Post by nyvolvolvr on 2009-02-15
I found songbird and it installed fine, however it doesnt play DVD's.  I tried to find mplayer on getdeb and found GNOME Mplayer.  I ran the dpkg line and it gave me more errors.  I dont think even debs will work for me.

---

### Post by sandyd on 2009-02-15
for each error, ill give an app thats missing (blablabla depends on blablabla)

download the app thats missing and install it ALL at once

its really hard to install stuff on ubuntu machines without internet though.

---

### Post by Orion8 on 2009-02-15
Can you move the laptop to a place where you can get it on the Internet?  A library, school, coffee shop?  It is generally really simple in install things in Ubuntu.  Internet helps not just for dependencies but for very useful trips to Google when things don't work out quite right!

---

