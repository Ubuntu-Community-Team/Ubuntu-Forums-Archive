---
title: "Nepomuk and GNOME"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by Cleveland Rock on 2010-04-22
Sorry for all the posting I've been doing lately, but Nepomuk is driving me crazy and I figured it would be best if I started a new thread.

Let me bring you up to speed:

[LIST]
[*]I wanted image-tagging software, so I downloaded digiKam.
[*]After having problems with digiKam, someone suggested using Gwenview, since digiKam was for photos and I wasn't tagging photos.
[*]After having trouble with Gwenview, I was informed that I could enable the image-tagging part of the software by running the program "nepomukserver" in a terminal. This part was apparently necessary because I use GNOME.
[*]However, I cannot *search* for tags I've added to pictures (it either gives me no results or crashes somehow), and I don't know how to delete unused tags, so the program doesn't remember them.
[/LIST]
It seems like this has been going on for months, and it's driving me crazy! Can anybody help me?

---

### Post by mgranet on 2010-04-22
Your insanity is being caused by trying to run core KDE software in a Gnome environment. It's the old square peg in a round hole scenario. Your best bet is to either find Gnome-oriented image tagging software, or run KDE.

---

### Post by Cleveland Rock on 2010-04-22
Aw, that bites. Does anyone know of an alternative I could use?

---

### Post by NightwishFan on 2010-04-22
F-spot, Gthumb?

---

### Post by Cleveland Rock on 2010-04-22
I think F-Spot will work, although the lack of a customizable slideshow feature is a bummer. Thanks.

Sorry for trying to put a square peg in a round hole, but that's why I'm in Absolute Beginner Talk.

---

### Post by NightwishFan on 2010-04-22
KDE programs generally should work, just some are designed to integrate more with KDE.

---

### Post by alex.nucleo on 2011-03-22
Sorry for resurrecting the thread, but I have similar problems. Under Ubuntu I tired of Nautilus, which is too slow, when I manage a collection of files larger than 100 items. It is also a pure file manager and doesn't allow me to organize my files in a "semantic" way.

I tried Dolphin, it is awesome and also following the suggestion of **Cleveland Rock** I started Nepomuk under Gnome with "nepomukserver" command. First there were some errors and it crashed several times. Then I selected only the folders I need it to index through its GUI. Now I'm almost happy, because all my tags, including ID3 tags are visible in Dolphin's side panel and the collection of files is opened almost immediately.

The only problem I have is that documents from Nepomuk watched folders are not indexed by full text. I have only meta-attributes and file names in my search results, but content of the files (particularly, PDFs) is not searchable. For instance I tried Meta Tracker - it does index full text. 

I'm sure Strigi must also search over all files, here is an excerpt from strigi-utils package description:
> 
This package is part of Strigi Desktop Search, it contains utilities powered
by Strigi:
...
deepgrep, an enhanced version of grep. It searches in binary files like
   OpenOffice files, mp3s, Microsoft office files, pdfs and also in files
   embedded in other files like .deb, .rpm, .tar.gz, email attachments, pdf
   and other files.
...
So obviously it's me who's missed something. I suppose I have to do something to enable full-text search in Nepomuk/Strigi? Has anybody ran Nepomuk under Gnome successfully with all its capabilities?

---

