---
title: "Guide for remastering LiveCD lacking some steps"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by Squba on 2010-05-18
Goes without saying but I am very new to Linux and Ubuntu.

For several years I have had the idea that I would like to create my own "laptop" using a liveCD with the applications I need.

Tried to follow this guide: [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

My first goal was the following:

1. Delete some language packs I do not need
2. Install Google Chrome as a browser

Basically I do a couple of: **aptitude purge language-pack-de-base**
and then: **sudo apt-get install chromium-browser** (this require some extra steps, but I get a feeling that it works because I can start the browser from my work directory.

I do the cleanup steps and create my ISO... it end at 23Mb.

Running the tests I DO get the splash screen and can select to start liveCD. This gives me a black screen with a flashing cursor in the top left corner.

Obviously something is missing? Do I have to install everything I want on the CD? I thought starting from an existing ISO like in the guide I would keep everything that I do not remove?

---

### Post by ubunterooster on 2010-05-18
I like liveUSBs because they can be added to as if they were a regular install.

---

### Post by Squba on 2010-05-18
I have been thinking about using USB version but I am not sure all the machines where I will need to use my "laptop" are able to boot off of a USB. 
Besides I should be able to get a simple mod like this to work :)

---

### Post by qyot27 on 2010-05-18
That looks like far more trouble than it's worth, IMO.  And ending up at just 23MB means you probably don't have any of the system utils installed, which means you pretty much created a coaster with a splash screen.

What you probably should look at, is [Ubuntu Customization Kit](http://uck.sourceforge.net/) (UCK).  If you've done slipstreaming on Windows, this is basically what UCK does for Ubuntu - you can have the disc's packages updated, add repositories/software/customization, trim unneeded language packs, and repackage the ISO.  I've used it before to include mencoder and the Medibuntu repositories on a 9.10 disc.

---

### Post by ubunterooster on 2010-05-18
you can set your exsisting install to be what you want and use [remastersys]("http://www.geekconnection.org/remastersys/index.html") to make it a live CD

---

