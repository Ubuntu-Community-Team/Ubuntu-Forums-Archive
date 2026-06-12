---
title: "Personal Dictionary"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by Bouldaire on 2009-03-30
I have a Dell mini 9 w/ubuntu 8.10.  In anticipation of the 9.10 release I would like to copy the dictionary file since I have added numerous words related to my business/industry.  I don't know how to copy it to my USB flash drive.  Yes, I am a novice since December of '08.  Thanks for your interest in this thread.  Bouldaire

---

### Post by spiderbatdad on 2009-03-30
The recommended way of upgrading from 8.10 is to open your terminal and type:
```
update-manager -d
```Your settings and files will be saved. I just did this on a new Acer Aspire One with 8.10 installed. The upgrade was flawless and I did not have to rebuild sound module and wireless module again.
Sorry don't know how to approach the usb question.

---

### Post by Bouldaire on 2009-03-30
> **spiderbatdad said:**
> The recommended way of upgrading from 8.10 is to open your terminal and type:
```
update-manager -d
```Your settings and files will be saved. I just did this on a new Acer Aspire One with 8.10 installed. The upgrade was flawless and I did not have to rebuild sound module and wireless module again.
Sorry don't know how to approach the usb question.

Thanks!!  I presume this is B4 the upgrade?  Bouldaire

---

### Post by aeiah on 2009-03-30
> **Bouldaire said:**
> Thanks!!  I presume this is B4 the upgrade?  Bouldaire

update-manager -d **is** the upgrade.


im not familiar with the directory program you're using but your saved data will be in a corresponding file in a hidden folder in your home directory.

config files and saved data for mplayer are in ~/.mplayer. deluge saves its data and config settings in ~/.config/deluge

usually one of the two formats will have your data.

---

### Post by spiderbatdad on 2009-03-30
when you run that command, update manager will run and show any updates avaialble. At the top of the list of updates will be a small block telling you a distribution upgrade 9.04 is available. Do you want to install it?

It is the beta release, so updates will follow for the next few weeks. Of course waiting until the final release means waiting and waiting while the servers are clogged to the max. Read the page here for possible issues with your hardware. Scroll down to "Known Issues." As I said, I couldn't be happier with the performance so far.
[http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)

---

### Post by Bouldaire on 2009-03-30
> **Bouldaire said:**
> Thanks!!  I presume this is B4 the upgrade?  Bouldaire

Thanks so much.  I'll use that B4 my upgrade in late April.  -Bouldaire

---

### Post by mkvnmtr on 2009-03-30
Before I do an upgrade I back up the hidden files in my home folder to another drive. Things like the folder .mozilla and .mozilla-thunderbird. For you that would include your dict file. They are usually small enough that just drag and drop does it very quickly. That way if I do something wrong I don't lose them.

---

