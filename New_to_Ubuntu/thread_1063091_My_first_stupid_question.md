---
title: "My first stupid question"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by paulkruger on 2009-02-07
I am new to linux and have a question...it is probably simple but the responses I find assume I know more than I do.

I have installed Ubuntu inside win2K.  It is in "D" drive which is NTFS. My C Drive is NTFS and I can view all the files there without a problem.

I am on a network and I can view the contents of NTFS drives on other computers in Ubuntu so I assume it has what it needs to see these partitions.

Problem is on the local machine I cannot see any files on this "D" drive at all except those related to Ubuntu?

My windows programs are here and I want to try WINE but none of the programs on this drive seem to be visible to Ubuntu?

I don't want to mess around with things like ntfs-3g as it appears Ubuntu can already see these files everywhere else.  ( Not to mention that the installation instructions for this is Greek to me at this point )

Any hints as to what I need to do so I can access files on the local machine other than those on C drive?:(

---

### Post by eddietours on 2009-02-07
did you use wubi?

---

### Post by avtolle on 2009-02-07
Take a look at [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?) to see if this answers your question.

---

### Post by paulkruger on 2009-02-07
> **eddietours said:**
> did you use wubi?

I told you I was new ! :p

What's a wubi ?

Is it part of the Ubuntu standard installation or do I need a .deb package to install this?

Not sure this is what I need? seems to be a windows installer for Ubuntu. I already have Unbutu installed.

My problem is in being able to see my D drive and windows application files.

---

### Post by hyper_ch on 2009-02-07
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by avtolle on 2009-02-07
paulkruger, you mentioned that you had installed Ubuntu "inside win2k" which indicated you had installed using Wubi, and had not done an install of Ubuntu on a dedicated partition, thus the question and link.

---

### Post by paulkruger on 2009-02-07
> **avtolle said:**
> paulkruger, you mentioned that you had installed Ubuntu "inside win2k" which indicated you had installed using Wubi, and had not done an install of Ubuntu on a dedicated partition, thus the question and link.


I assume WUBI was the program that came with the ubuntu distribution I downloaded. I just chose the option to install Ubuntu withinn windows but don't recall it stating that WUBI was then being used.  I just followed the prompts.

So I guess I must have used WUBI although I was not aware of it nor did I download it as a separate installation.:p

---

### Post by avtolle on 2009-02-07
When you go to Places and open Nautilus by clicking on, say, your home folder, in the left hand side showing the various places on your computer, do you see something named "host"? If so, that's your Windows partition, and by opening it, you should see the various files, etc., within the partition.

---

### Post by paulkruger on 2009-02-09
> **avtolle said:**
> When you go to Places and open Nautilus by clicking on, say, your home folder, in the left hand side showing the various places on your computer, do you see something named "host"? If so, that's your Windows partition, and by opening it, you should see the various files, etc., within the partition.

Nope...no such option as "host"
Here is what I have:

HOME FOLDER
DESKTOP
DOCUMENTS
MUSIC
VIDEO
COMPUTER CD/DVD CREATOR ( [COLOR="DarkRed"]DON'T NEED NO BURNER[/COLOR] )
8.5 GB MEDIA ([COLOR="DarkRed"] This is the C:/ drive and I can view those files fine so I know it can view NTFS partitions but I can't see the other partitions. [/COLOR])
CD-ROM
NETWORK
CONNECT TO SERVER
SEARCH FOR FILES
RECENT DOCUMENTS

And that is the entire contents of the menu.

---

