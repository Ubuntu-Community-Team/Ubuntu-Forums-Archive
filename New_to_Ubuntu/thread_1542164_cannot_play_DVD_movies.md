---
title: "cannot play DVD movies"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by kbrittt on 2010-07-30
I'm running Lucid Lynx on a ASUS ul-8o laptop and cannot play DVD movies, cd's with pictures work fine but cannot play dvd's

---

### Post by aidenscool09 on 2010-07-30
Have you installed VLC media player? Try installing it if you haven't and then go to Media>Open Disk in VLC. Give that a try and if that doesn't work you need to install libdvdcss by doing ```
wget http://ftp.yi.se/pub/software/videolan/libdvdcss/1.2.8/deb/libdvdcss2_1.2.8-1_i386.deb -c
wget http://ftp.yi.se/pub/software/videolan/libdvdcss/1.2.8/deb/libdvdcss2-dev_1.2.8-1_i386.deb -c
sudo dpkg -i *.deb
```in a terminal.

---

### Post by mapes12 on 2010-07-30
VLC media player +1

You will need the none free codecs to play DVD's:-

1. In synaptic search for ubuntu-restricted-extras and install it
2. Go to [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and follow the terminal commands to install these codecs as well

You should then be good to go with DVD's

Mark

---

### Post by WRDN on 2010-07-30
Assuming the multiverse repositories are enabled, open the Terminal and type:

```
sudo apt-get install ubuntu-restricted-extras &&  sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

