---
title: "frustrated with opera/adobe"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by hubcity on 2009-02-18
i've been searching threads for a couple days, and trying all the tips...

i just upgraded to hardy heron, and ff broke...(something about a lost child)  so i downloaded and installed opera 9.6.  i like hulu.  it tells me to download adobe...i click on download, and the package installer tells me i already have it.  but i can't find it anywhere...

i am enjoying ubuntu, but am getting overwhelmed by the technical end of things.  if someone could please just give me a walkthrough...i've read psychocats manual a few times, but i still can't seem to watch hulu.  i'm afraid i'm going to go through all of  this when i try to install realplayer as well...

as i said, ibetter at using the programs than knowing how they work...please be gentle... ;)

---

### Post by hubcity on 2009-02-18
so every time i click on hulu, it tells me i have to download adobe.  but when i go to the adobe site and click on 8.4 deb, the screen thet pops up tells me it's already installed.  when i go to add remove programs, it's not listed, but when i go into synaptic package manager, its listed as installed.  what am i missing?

---

### Post by wolfen69 on 2009-02-18
download the tar.gz from [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) and right click>extract here. then open the folder and copy the libflashplayer.so file. then do 
```
gksudo nautilus
```
navigate to /usr/lib/opera/plugins and paste it there.

---

