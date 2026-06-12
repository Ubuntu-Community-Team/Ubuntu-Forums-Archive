---
title: "Sound Issue"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by Nemix on 2008-12-28
I can get sound say if im on youtube and other web site (flash player things normally have sound for me) but the sound is low. If i get onto my window partition i watch say the same youtube vid i have the sound level at like half as what i need it on Ubuntu (ive tried setting all my settings to max). 

Another sound issue i have is when i try opening say a mp3 file or other media files i can see visual just cant hear anything, not even something faint.

---

### Post by billgoldberg on 2008-12-28
I'm guessing you are on Ubuntu 8.10

Let's start by making sure you those codecs installed.

Open up a terminal (applications -> accessories -> terminal) and copy/paste this:

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2 gnome-alsamixer
```

press enter.

Type in your password (you won't see any indication you are typing) and hit enter.

When it is finished, go to "applications -> sound and video -> gnome alsamixer" and max everything out.

---

### Post by jyaan on 2008-12-28
Yea, I would check out that the mixer has the correct settings. If you have some experience with Linux, you probably already know this though. One other thing could be an incorrect/incomplete driver. Some chipsets are very similar, and therefore will still give the general functionality. However, there will be a few issues.

I would type ```
lspci | grep -i audio
``` at the command line, and then do a search on the driver name along with Linux &/or Ubuntu. There might be a guide regarding a few tweaks you can add to the sound configuration files.

edit: If you don't know what the command means : lspci means 'list pci'; grep means search, -i is the flag for case-insensitivity.

---

### Post by Nemix on 2008-12-28
i ran that in terminal to get the codecs, waited awhile for it to run through then came back and had this java licensing page up and couldn't do anything, couldnt accept so i closed it now i cant update anything.

i get this when i run that line in terminal again.

```
Fetched 192B in 5s (35B/s)
W: GPG error: http://wine.budgetdedicated.com intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

---

### Post by linux_tech on 2008-12-28
> **Nemix said:**
> 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


In the terminal, type 
```
dpkg --configure -a
```

---

### Post by linux_tech on 2008-12-28
Gnome-alsamixer is easier to use than alsamixer. Try installing and running it it first
```
sudo apt-get install gnome-alsamixer

``` 
To open gnome-alsamixer type


```
gnome-alsamixer

```
check all settings, make sure nothing is muted; 
make sure front and headphone is checked


If you havn't already installed these under Intrepid, installing these next they will probably improve your sound

```

sudo apt-get install alsa-oss

sudo apt-get install libasound2

sudo apt-get install libasound2-plugins

```

To open volume control type:
```
gnome-volume-control

```

---

### Post by Nemix on 2008-12-28
ok thank it seems to be working =D
:KS:KS:KS

i love these forums :KS

---

