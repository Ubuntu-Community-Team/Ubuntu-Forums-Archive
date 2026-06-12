---
title: "video problems"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by kapi on 2008-12-31
Hi there, hoping someone can help. After finally getting Ubuntu lopaded, it seems to be great, love it in fact! However when I try to play dvds none of the players appear to work. tried loading the libstdc++5 file with another to no avail. hope someone could shed some light and help. Many thanks

Kapi

---

### Post by LowSky on 2008-12-31
you need libdvdcss2, copy and past this code into a terminal (applications> Accessories> Terminal)
```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
```

What version 8.04(LTS) or 8.10?

check out this link
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Pat Benson on 2008-12-31
Im new as well but I got DVDs working, in Dragonplayer.

I followed this [guide]("http://www.videolan.org/vlc/download-ubuntu.html") to get VLC player. I just tried VLC with a DVD and it didn't work to well. 

However it will install the correct codecs to run a DVD on your system **(or so I assume)**.

Follow the guide and then use Dragonplayer(or equivalent in Ubuntu) and I think it may work

Hope that could be of some help :)

---

### Post by kapi on 2008-12-31
Thank you all very much, I followed the advice and went to the VLC link where thye suggested installing packages from the synaptic package manager, I just selected everything that included the title dvd and it seems to work fine in dragon player. Totem seems to just sit there and not play but hey at least dragon player is working. Many thanks again all, your help is very much appreciated

Kapi

---

### Post by cariboo on 2008-12-31
@LowSky is correct, you need to install the libdvdcss2 library from the Medibuntu repositories. I would suggest installing the ubuntu-restricted-extras meta package as well. To install the meata package go to System--Administration--Synaptic Package Manager and search for ubuntu-restricted-extras and install it. The ubuntu restricted-extras package will install most of the codecs needed to play most audio/video files, as well as flash, java and mscorefonts. 

To enable the Medibuntu repositories go [here]("http:///help.ubuntu.com/community/Medibuntu"), and follow the instructions for you version, scroll down and install the gpg key. Once you have setup the repositories, go back to synaptic and install libdvdcss2 and w32codec. You should now be ready to play almost any type of media you run into.

Jim

---

