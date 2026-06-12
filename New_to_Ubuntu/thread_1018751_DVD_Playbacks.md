---
title: "DVD Playbacks"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by johndingli on 2008-12-22
I am having problems when playing dvd's.I am using totem movie player.I am seeing the dvd but with strange colours.Like red becomes green the colour of people is like black and white and all those strange colours.I have installed all the codecs in mediubuntu and the extra package.Sound is ok any help please:confused:

---

### Post by taurus on 2008-12-22
Have you tried another player like vlc?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install vlc
```

---

### Post by johndingli on 2008-12-22
yes i did try vlc but still the same.I also used kaffeine but with no luck

---

### Post by khelben1979 on 2008-12-22
You could also check if you have [libdvdcss]("http://en.wikipedia.org/wiki/Libdvdcss") in the system over there. It's a critical component which must be installed.

[VLC]("http://en.wikipedia.org/wiki/Vlc") is a good player, but you can also check out [mplayergui]("http://sourceforge.net/search/?type_of_search=soft&words=mplayergui").

---

### Post by johndingli on 2008-12-22
I have vlc installed and has the same problem i have also installed libdvdcss but nothing is helping

---

### Post by khelben1979 on 2008-12-22
I suggest you try with MPlayer instead and make sure the codecs are installed which you'll find [here]("http://www.mplayerhq.hu/design7/dload.html").

Make sure to read the README file which comes with the archive.

The codec package which VLC uses doesn't sound to work very well over there, so you could give a [Mplayer]("http://en.wikipedia.org/wiki/Mplayer") a try until you know how to resolve the problem you have with VLC.

---

### Post by LowSky on 2008-12-22
have you rebooted the machine after installing the codecs?

here are the files you need form medibuntu

sudo apt-get install libdvdcss2
sudo apt-get install w32codecs

if those cammands don't work you somehow messed up installing the medibuntu repos, no worries you can get dvd playback and codec support  by using these commands in a terminal just copy and paste them
```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
```
```
wget -c http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb
sudo dpkg -i w32codecs_20071007-0medibuntu2_i386.deb
```

---

