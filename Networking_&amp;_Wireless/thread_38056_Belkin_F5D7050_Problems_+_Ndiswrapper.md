---
title: "Belkin F5D7050 Problems + Ndiswrapper"
date: 2005-05-29
forum: Networking &amp; Wireless
---

### Post by abandonedhero on 2005-05-29
I have installed Hoary on my PC. Hoary can tell that my USB wireless card is connected. The problem is, I have found no way to configure it. It's not listed on any of ubuntu's hardware lists, so I've tried to use Ndiswrapper. Second problem - Ndiswrapper doesn't like the Windows XP driver, and results with an error.  I've seen somewhere that someone extracted a driver for Windows 9x, and got it to work, but I haven't found a way to extract the .inf and .sys files for Windows 9x out of the .cab file. I've tried WinZip, Windows XP, and a few different ubuntu extraction utilities, none of which recognized the type of .cab file. 

Now for my question. Is there a way that I could get the card to work in ubuntu without Ndiswrapper, as I've tried to get it to work in SuSE as well (and failed)?

Second question. If I am forced to use Ndiswrapper, how can I extract the .inf and .sys files out of the .cab?

Buying a different wireless card isn't an option.

---

### Post by abandonedhero on 2005-05-29
Here is some additional information that may be useful.

while in the terminal as root,

```
ndiswrapper -i bknUSB.inf
```

returns

```
CP: Cannot stat 'bknUSB.inf': No Such File or Directory
```

Am I just missing a file in the /etc/ndiswrapper/ directory?
I've copied:

bknUSB.inf
prismaxp.sys

to the directory.

Any ideas?

---

### Post by kadissie on 2005-05-30
I'm just browsing ubuntuforums for info about wireless cards, because tomorrow I'm going to purchase and install one for a friend whom I've introduced to Ubuntu.

So I don't have any direct experience of the particular Belkin card that you're using, but that's the one I'm going to buy.

But... excuse me if this is something obvious, but I believe when using the "ndiswrapper -i <foo>" command, the path <foo> needs to be the full path to the driver file, doesn't it?  So if you just type the name of the file it doesn't look in /etc/ndiswrapper, it looks in the current directory or something like that.  What happens if you issue the command
```
ndiswrapper -i /etc/ndiswrapper/bknUSB.inf
```

As for extracting files from M$ cabinet archives, a search of Synaptic's packages turns up cabextract and orange, both of which promise to do exactly that.

Robert.

---

### Post by alastair lewis on 2005-05-30
```
sudo ndiswrapper -i bknUSB.inf
```

creates /etc/ndiswrapper/ and installs the drivers

---

### Post by alastair lewis on 2005-05-30
[QUOTE=alastair lewis]```
sudo ndiswrapper -i bknUSB.inf
```

creates /etc/ndiswrapper/ and installs the drivers[/QUOTE]
 Also, after 'ndiswrapper-l' to confirm you have installed correctly
you also need to run 'modprobe ndiswrapper' as root as well.

---

