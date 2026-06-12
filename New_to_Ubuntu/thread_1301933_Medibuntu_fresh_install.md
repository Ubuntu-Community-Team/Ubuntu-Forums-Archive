---
title: "Medibuntu fresh install?"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by shnurui on 2009-10-26
How to install Medibuntu, preferably using the synaptic sources instead of the detailed, yet fail, sudo on the front page.

Running Ubuntu Jaunty 9.04

DVD still failing, Segmented read Fail with Gxine.

---

### Post by fancypiper on 2009-10-26
Have you tried this command?

# Add medibuntu sources latest release
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

Also, see [Comprehensive Multimedia & Video Howto ]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by arochester on 2009-10-26
Instructions for installing Medibuntu here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

NOTE! It is a 2 part installation 1) Install Repository 2) Get GPG key (through Terminal)

---

### Post by jmszr on 2009-10-26
shnurui,

As part of installing Medibuntu be sure to install:  

```
sudo apt-get install libdvdcss2
```

Also I would suggest the VLC media player:

```
sudo apt-get install vlc
```

---

### Post by shnurui on 2009-10-27
Hmm, it appears all I was missing was the reboot.

Going to try the medibuntu install after I get the updates done.

---

### Post by shnurui on 2009-10-27
> **arochester said:**
> Instructions for installing Medibuntu here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

NOTE! It is a 2 part installation 1) Install Repository 2) Get GPG key (through Terminal)

Those instructions are GIGo on 9.04

---

### Post by shnurui on 2009-10-27
> **fancypiper said:**
> Have you tried this command?

# Add medibuntu sources latest release
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

Also, see [Comprehensive Multimedia & Video Howto ]("http://ubuntuforums.org/showthread.php?t=766683")

100100001001
File Not found

404 error

---

### Post by mkvnmtr on 2009-10-27
Google medibuntu.  In the first few entries you will see the community support. Click on that and you will find the simplest instructions around to enable the medibuntu repository. Follow the instructions and then go to your package manager and install the programs you think you might need.

---

### Post by shnurui on 2009-10-28
> **mkvnmtr said:**
> Google medibuntu.  In the first few entries you will see the community support. Click on that and you will find the simplest instructions around to enable the medibuntu repository. Follow the instructions and then go to your package manager and install the programs you think you might need.

No, just use the "brute force" manual method listed in the other thread, link above.

---

