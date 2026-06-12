---
title: "Ubuntu as a VM with X on top of a Windows desktop?"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by sylvainrb on 2010-11-05
I read an interesting comment in an Ars article today where the person described their set up as follow:

"I run a Ubuntu VM on my Mac, but I use X to lay the windows on the Mac desktop."

The way I understand that is that I would have Ubuntu running in Virtualbox in the background and its X server being seemlessly "incorporated" within my Windows desktop... which would be awesome for me so I don't have to juggle between my Windows desktop and Virtualbox Linux desktop.

Is that possible? Easy to set up? I'm going to look it up but thought I'll post it here too just in case someone already did something similar...

Thanks!

---

### Post by ubudog on 2010-11-05
I don't believe that's possible.  There is however a seamless mode for VirtualBox.  It runs in fullscreen, and you can move your mouse cursor "seamlessly" into or out of it.  But, you cannot drag folders from the Ubuntu desktop on VirtualBox to your Windows desktop.  And it all depends on your system specs.  I have had many issues running VirtualBox on older PC's.

---

### Post by sylvainrb on 2010-11-05
> **ubudog said:**
> I don't believe that's possible.  There is however a seamless mode for VirtualBox.  It runs in fullscreen, and you can move your mouse cursor "seamlessly" into or out of it.  But, you cannot drag folders from the Ubuntu desktop on VirtualBox to your Windows desktop.  And it all depends on your system specs.  I have had many issues running VirtualBox on older PC's.

Yes I know. I'm already using the fullscreen seamless view with Virtualbox. I'm not really interested in the capability of dragging folders/files from the two desktops since I already have the two systems share parts of my HDDs. Just thought it'd be cool to have ubuntu windows floating around my Windows desktop... i.e. have a terminal in there without the whole Virtualbox window.

---

### Post by ubudog on 2010-11-05
> **sylvainrb said:**
> Yes I know. I'm already using the fullscreen seamless view with Virtualbox. I'm not really interested in the capability of dragging folders/files from the two desktops since I already have the two systems share parts of my HDDs. Just thought it'd be cool to have ubuntu windows floating around my Windows desktop... i.e. have a terminal in there without the whole Virtualbox window.

Ah, I see know.  Alas, I do not think that is possible.  The closest thing I think would be WUBI, but that's still different.

---

### Post by JustinR on 2010-11-05
> **sylvainrb said:**
> I read an interesting comment in an Ars article today where the person described their set up as follow:

"I run a Ubuntu VM on my Mac, but I use X to lay the windows on the Mac desktop."

The way I understand that is that I would have Ubuntu running in Virtualbox in the background and its X server being seemlessly "incorporated" within my Windows desktop... which would be awesome for me so I don't have to juggle between my Windows desktop and Virtualbox Linux desktop.

Is that possible? Easy to set up? I'm going to look it up but thought I'll post it here too just in case someone already did something similar...

Thanks!

[http://en.wikipedia.org/wiki/CoLinux](http://en.wikipedia.org/wiki/CoLinux)

It allows you to run Ubuntu and Window in cooperation with each other.

[img]http://en.wikipedia.org/wiki/File:Ubuntu_on_Windows_-_Firefox_vs_Firefox.png[/img]

---

### Post by ubudog on 2010-11-05
Interesting...:)

---

### Post by JustinR on 2010-11-05
> **ubudog said:**
> Interesting...:)

Definitely.

Its like running two operating systems on one machine though - so don't expect each OS to be as fast as they were before.

---

### Post by ubudog on 2010-11-05
An awesome tool indeed.  :)

---

### Post by sylvainrb on 2010-11-05
Found something similar...

[http://en.wikipedia.org/wiki/Xming]("http://en.wikipedia.org/wiki/Xming")

Gotta find use for these idle cores!

---

### Post by ubudog on 2010-11-05
> **sylvainrb said:**
> Found something similar...

[http://en.wikipedia.org/wiki/Xming]("http://en.wikipedia.org/wiki/Xming")

Gotta find use for these idle cores!

Lol.  Also looks like a good tool to have. :guitar:

---

