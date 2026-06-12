---
title: "automatix"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by darvina on 2009-09-24
Hi i am new to unbuntu and really want to succeed with this application just to stick 2 fingers up at microcrap.

Being used to gui interface i need help with automatix so this app installs all my plugins

the website is down is this a normal occurence 

what is automatix equailvent if automaix is no longer avaible.

also how do i configure by pc to use the respositires and what are the address 

thanks 

sorry for the spelling typing to fast;)

---

### Post by ibuclaw on 2009-09-24
Automatix is not supported here. [This blog post ought to explain why.]("http://mjg59.livejournal.com/77440.html")

If you want some nice restricted features/codecs, your best bet is here: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by doas777 on 2009-09-24
automatix is not recomended for ubuntu.
what plugins do you need?

if you just need codecs try pasting this into a terminal:
```

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update;
sudo apt-get install ubuntu-restricted-extras libdvdcss2 vlc mplayer
```

then depending on wether you have 32 or 64 bit ubuntu, run one of the following lines:
```

sudo apt-get install w64codecs
sudo apt-get install w32codecs

```

that will give you DVD playback, Sun java, Adobe Acrobat/Flash, playback for most windows video formats, and 2 additional media players (vlc and mplayer).

hope that helps.

---

### Post by Sef on 2009-09-24
```
automatix is not recomended for ubuntu.
what plugins do you need?

if you just need codecs try pasting this into a terminal:
Code:
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update;
sudo apt-get install ubuntu-restricted-extras libdvdcss2 vlc mplayer
then depending on wether you have 32 or 64 bit ubuntu, run one of the following lines:
Code:
sudo apt-get install w64codecs
sudo apt-get install w32codecs
that will give you DVD playback, Sun java, Adobe Acrobat/Flash, playback for most windows video formats, and 2 additional media players (vlc and mplayer).

hope that helps.
```

Except for DVD playback, the rest can be installed from the respositories via Add/Remove. (Applications > Add/Remove)

---

