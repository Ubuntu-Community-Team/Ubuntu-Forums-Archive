---
title: "APT URI scheme not working in Chrome"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by hdstur on 2010-04-07
Just wanted to install Flash, and I noticed that Adobe's site has an option for Ubuntu 9 that uses a special URI to download and load the package.  See what I'm talking about here:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

When I try to open the link in Chrome, it asks if I want to launch an external program.  Even if I click 'yes', it does nothing.  Not sure if I don't have something installed.

I have a minimal install of Ubuntu 10.04.

- Henson

---

### Post by OriginalName on 2010-04-07
Can't you download it using Firefox? It should install system wide so flash will work in whichever browser you're using.

I'd guess it's a chrome / adobe / linux combination that they haven't done properly on their website.

---

### Post by tom.swartz07 on 2010-04-07
> **hdstur said:**
> Just wanted to install Flash, and I noticed that Adobe's site has an option for Ubuntu 9 that uses a special URI to download and load the package.  See what I'm talking about here:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

When I try to open the link in Chrome, it asks if I want to launch an external program.  Even if I click 'yes', it does nothing.  Not sure if I don't have something installed.

I have a minimal install of Ubuntu 10.04.

- Henson

If worse comes to worst, you could just manually enter the command. When you mouse over the link, you will see that it says ```
apt:adobe-flashplugin?channel=$distro-partner
```

All that means is it will open Synaptic and install the package adobe-flashplugin.

You could manually install the package by entering in the terminal
```
sudo apt-get install adobe-flashplugin
```

---

### Post by hdstur on 2010-04-07
> **tom.swartz07 said:**
> You could manually install the package by entering in the terminal
```
sudo apt-get install adobe-flashplugin
```
I think that may be the problem, I don't see any package named "adobe-flashplugin" when I run apt-cache search.  What repository is it in?

---

### Post by tom.swartz07 on 2010-04-08
> **hdstur said:**
> I think that may be the problem, I don't see any package named "adobe-flashplugin" when I run apt-cache search.  What repository is it in?

A-HA! Thats it- you need to enable the MediBuntu repos. If you open up software sources, you could enable the 'restricted' and otherwise closed source programs. After that, just reload your data and you could install it!

Alternatively, you could also just install the # ubuntu-restricted-extras # package and it will grab all of the things that you most likely are looking for, (Flash, Java, TrueType fonts, etc)

---

