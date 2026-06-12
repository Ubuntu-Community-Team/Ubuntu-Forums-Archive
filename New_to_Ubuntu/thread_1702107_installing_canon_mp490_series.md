---
title: "installing canon mp490 series"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by bheadie on 2011-03-07
HI, so this is very confusing... I have read the other threads, tried what they said and all I get is wrong architecture message from the software center..

I am using 10.10 x64 downloaded from the thailand website, [http://support-th.canon-asia.com/contents/TH/EN/0100236305.html](http://support-th.canon-asia.com/contents/TH/EN/0100236305.html)  -I just don't get it, I tried every other possible printer driver as well 497 uk website has otherones I tried... always wrong architecture

---

### Post by bayan.rafeh on 2011-03-07
Wrong architecture means that you should be using 32 bit Ubuntu.

This is a bit of a roundabout solution but it should work.

Install oracle virtualbox from : [www.virtualbox.org](www.virtualbox.org)

Download 32 bit ubuntu.

Create a new virtual device in virtualbox and install Ubuntu 32 bit on it. Just follow the instructions.

Install it on the 32 bit machine and see if it works.

You could also try installing 32 bit Ubuntu on a separate partition.

---

### Post by maqtanim on 2011-03-07
If you try to use 32bit software in 64bit Ubuntu (or vice versa), you'll be shown a Wrong Architecture message. The software you are using its name is *cnijfilter-mp490series-3.20-1-i386-deb.tar.gz. *Mark the *i386* part in the name, it means it is 32 bit. You need software for 64 bit. 

By the way, did you try to install the printer from **System > Administration > Printing**?

---

### Post by WanderingAlbatross on 2011-03-24
It didn't look like this printer was supported by default in Ubuntu.  I had to go get drivers for it.  I am using 32-bit 10.04 myself, however.  I used the [Asian Canon website]("http://support-th.canon-asia.com/contents/TH/EN/0100236305.html").

For the 64-bit, try what was posted here:
[http://ubuntuforums.org/showthread.php?t=1673166&highlight=Canon+MP490](http://ubuntuforums.org/showthread.php?t=1673166&highlight=Canon+MP490)

---

