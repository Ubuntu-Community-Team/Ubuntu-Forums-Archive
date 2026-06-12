---
title: "Video resolution"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by navaneethan on 2009-03-13
I have installed hardy
in my hardy thera are problems to play video it is not rendering smoothly
it runs under low resolution & low quality i want to play it as in high quality what i have to do

---

### Post by martrn on 2009-03-13
Presuming you have installed Hardy and the rest of your X11 or Xorg is working fine you would need to install the codecs.

You need to add the following lines to /etc/apt/sources.list file or you need to make sure you have enabled Universe and multiverse repositories in /etc/apt/sources.list file

```
sudo gedit /etc/apt/sources.list
```

Make sure you have the following two lines (uncommented and with no ## before them), and save your file.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe multiverse

Now you need to update the source list

sudo apt-get update
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

```
sudo apt-get install mplayer
sudo apt-get install medibuntu-keyring
sudo apt-get update
sudo apt-get install w32codecs libdvdcss2
sudo apt-get update && sudo apt-get upgrade
```

If you want to install Mplayer with plug-in for Mozilla Firefox run the following command:

sudo apt-get install mozilla-mplayer

---

