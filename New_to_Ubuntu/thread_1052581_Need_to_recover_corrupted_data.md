---
title: "Need to recover corrupted data"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by arashiko28 on 2009-01-27
My sister plugged her usb drive on several infected windows computers, and then she gave it to me. It had 4 virus, so I cleaned it by terminal. She's using Ubuntu too, so this is the weird part, in only half an hour her drive got infected again with 2 different virus than the ones I deleted and now all her data is corrupted. Is this normal? What just happened here? Can we recover the files?

---

### Post by handydan918 on 2009-01-27
Do a backup of the disk and PM me. I would love to see a virus that does what you say this did. I have test machines just waiting for this kind of abuse.

---

### Post by emarkd on 2009-01-27
Viruses are just software and Windows viruses don't work on Linux any better than Windows apps do.  Are you sure that's what happened?

---

### Post by bumanie on 2009-01-27
Your best bet to recover her files are via a program called photorec - despite the name, it recovers many more file types than just photos. Photorec is part of testdisk, therefore in terminal > sudo apt-get install testdiskTo run photorec > sudo photorecRead the documentation [here]("http://www.cgsecurity.org/wiki/TestDisk")Click on photorec in the top left hand box. Near the bottom of the page there is a step by step tutorial of how to use photorec. Good luck, if the files are corrupted, you may not find much of use, but if only the filesystem is corrupted, you have a good chance of recovering the files as photorec reads raw data off the disk, not the filesystem.

---

### Post by arashiko28 on 2009-02-10
I'm not sure about what happened, her best shot was to give it all for lost and format the disk.
Actually I'm being more careful now, because I used to plug anything, confident that no windows virus would mess around my computer.
I mean, even if I have wine, it's supposed to do harm only on the virtual disk that wine creates and if opened with it. I don't have it set to open anything automatically, so that's a long shot to be running through wine.

---

### Post by theozzlives on 2009-02-10
Wine don't use a virtual disk, it installs in your home folder. The only way to get a actual file that stores a virtual disk is to install a VM.

---

