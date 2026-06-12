---
title: "Help in installing printer driver"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by pensioner77 on 2011-08-12
Some time ago I tried unsuccessfully to install a driver for my Canon printer on my laptop running 9.10. I am now trying to install it on my PC running 10.04. The download appears successfully to my doenload file but whereas other downloads such as VLC & IBM Symphony then install by a double click,when I do this with the canon driver all that happens is Archive Manager opens with the following 5 entries:
cnijfilter-common_2.80-1.tar.tar
cnijfilter-common_2.80-1_i386...
cnijfilter-ip4500series_2.80-1...
faq-pd-2.80-1.tar.tar
guideip4500series-pd-2.80-1.t...
The files1,4&5 are shown as Tar archives and 2 & 3 as Debian packages.
Can anyone tell me,a distinct novice at IT, what I have to do next to complete the install?:confused:

---

### Post by demonipuch on 2011-08-12
If you don't want to deal with these files and install your printer's drivers the easy way (by using the package manager) run this command :
```
sudo add-apt-repository ppa:michael-gruz/canon
```
This will add this [ppa]("https://launchpad.net/~michael-gruz/+archive/canon") to your repository list.

Now you can install the drivers with synaptic or in command line :
```
sudo apt-get update
sudo apt-get install cnijfilter-common cnijfilter-ip4500Series
```

Hope it helped

---

### Post by pensioner77 on 2011-08-12
Thanks Demonipuch. it all seemed to be going OK until the last entry when the following showes E:Invalid operation installer. You mentioned the easy way using the package installer--that was what I had hoped to do?

---

### Post by demonipuch on 2011-09-14
Sorry there was a typo in the last command. The command is
```
sudo apt-get install cnijfilter-common cnijfilter-ip4500Series
```

---

