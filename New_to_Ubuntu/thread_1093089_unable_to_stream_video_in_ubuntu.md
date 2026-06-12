---
title: "unable to stream video in ubuntu"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by leeds on 2009-03-11
Hi - I recently installed Ubuntu 8.10 however I am unable to view any embedded video (youtube, etc) from my browser (Firefox or Opera). Within Firefox I appear to have installed all the plug-ins which include: DivX, QuickTime, Shockwave, Totem, VCL and Windows Media. I also recently installed the Gstreamer plug-in (although I cannot see this within Firefox > Tools > "add-ons > "Plugins") and Medibuntu. Still no luck. I'm not sure if installing multiple players is actually causing the conflict and if a fresh install is required. Please help. Just one point - please give me step-by-step instructions as I'm new to Linux.

---

### Post by skymera on 2009-03-11
You need to install Flash player.

```
 sudo apt-get install flashplugin-nonfree 
```

---

### Post by RyanVanDiemen on 2009-03-11
best thing to do right after system installation is to install ubuntu-restricted-extras package (or kubuntu-restricted-extras / xubuntu-restricted-extras if you use KDE or Xfce) it will install all necessary packages for running multimedia. you need to add medibuntu repository if you haven`t yet first:

```

sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install w32codecs

```

I`m not sure if w32codecs (windows video codecs) package is part of restricted extras so you need to add this separately

---

### Post by billgoldberg on 2009-03-11
When I do a fresh Ubuntu install, I always use this command to install all available codecs and flash, java, ...

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

If after this you can't play the video from firefox, no one can.

---

### Post by gn2 on 2009-03-11
Do you have 32-bit or 64-bit Ubuntu installed?

---

### Post by RyanVanDiemen on 2009-03-11
> **gn2 said:**
> Do you have 32-bit or 64-bit Ubuntu installed?

That`s a good question of course. If you run 64-bit version, you can pretty much forget (or better modify) most of the commands above...

---

### Post by leeds on 2009-03-11
Thank you for all the responses.

I'm running 32 bit.

Tried everything mentioned in this thread - now, Youtube video has started working but lacks clarity (i.e. runs slow) and tried BBC iPlayer which does not work. Sorry, but please let me know if I can try something else?

---

### Post by parkinrg on 2009-03-14
I was having similar problems but
the code suggested by billgoldberg earlier in this thread solved it for me
Thanks billgoldberg

---

### Post by leeds on 2009-03-14
Thank you all. I did a fresh install of Ubuntu and installed Adobe Shockwave player (in addition to the default add-ons already included with Firefox and Ubuntu 8.10). There might have been some conflicts in my previous installation. Videos are streaming as normal now.

---

### Post by unicornlover442 on 2009-04-09
Please accept my apologies if I'm doing this incorrectly. Have never posted on a thread b4---I tried to do the commands that 
RyanVanDiemen  suggested on his thread posted 4 wks ago 	
At 617a.m. When i did the 2nd line of the command (sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update) I get an error message as follows:W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Can someone please help me??? Does this error message mean that I already have some other type of application already using it??? If so, how do I find out which one it is??
Thanks for ANY help you can suggest.

---

### Post by leeds on 2009-04-11
Sorry if this does not help, I'm also new to Linux. Just a few thoughts - was this a temporary problem that has corrected itself now? You may be able to try the other codes provided above. In my case, all of the above codes worked perfectly. However I may have made some other mistake during installation or with the settings on my system, I had to do a fresh install of ubuntu to correct the streaming and sound issues.

---

### Post by funky_uncle on 2009-04-13
> **unicornlover442 said:**
> E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Can someone please help me??? Does this error message mean that I already have some other type of application already using it??? If so, how do I find out which one it is??I think that means that you have another package manager running, like Synaptic. If you do, close it and try again.

---

