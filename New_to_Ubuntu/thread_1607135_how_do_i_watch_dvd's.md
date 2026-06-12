---
title: "how do i watch dvd's"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by icemaster3850 on 2010-10-27
i recently changed my laptop to ubuntu netbook remix 10.10 but i cant play any dvds on it at all is there any way of fixing this or do i have to use another computer with micros**t on it

---

### Post by Verbeck on 2010-10-27
if thats a clean install, you'll need to follow the instructions at :
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

here's the snip you need from that page
open a terminal and enter the following:[FONT=monospace]
[/FONT]```
sudo apt-get install ubuntu-restricted-extras
```

after it has completed then run :
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by Silent Warrior on 2010-10-27
DVD-decryption isn't quite free stuff - the Linux implementation of it is apparently illegal in some parts of the world. If you believe you're in the clear (or 'don't care all that much, anyway, I wantz teh DVD!'), installing ubuntu-restricted or something with a similar name should be enough. Also make sure you have a media-player that plays video... (Like Totem, VLC, etc.)

---

### Post by uRock on 2010-10-27
icemaster1350,

Hello and Welcome.

To watch DVDs you will need to install a package from the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository. Open a terminal and copy and paste this command into it.

For 32bit```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
```For 64bit ```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
```

---

