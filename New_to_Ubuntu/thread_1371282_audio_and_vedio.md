---
title: "audio and vedio"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by saman6015 on 2010-01-03
hello everybody i am new with ubundu i am having ubundu 8.04 in that video and audio is not suporting if i play it showing u didnt installed appropriate plug- in code i am very confused and alaso i dont have any internet connection how can i insatall audio and video player without  internet connection
 
 
 please anybody solve this problem

---

### Post by mac9416 on 2010-01-03
Hey, saman6015,

To get sound and video working properly in Ubuntu, you need to install ubuntu-restricted-extras. Since the computer you are working on is offline, you should use [Keryx]("http://keryxproject.org") to download the .debs to a flash drive for installation on the offline machine. 
To get started, check you the [Keryx tutorial]("http://crashsystems.net/2009/01/keryx-tutorial/").

Let me know if you need anything clarified. Good luck!

---

### Post by sandyd on 2010-01-03
ok, ive posted this again.... and again....
so im simply going to link to ->
[http://ubuntuforums.org/showthread.php?p=8598363#post8598363](http://ubuntuforums.org/showthread.php?p=8598363#post8598363)

or just run all of this stuff....
```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update[FONT=monospace]
[/FONT]sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
sudo apt-get install libdvdcss2 libdvdread4 ubuntu-restricted-extras flashplugin-nonfree libfaac0 libfaad0 libavcodec-extra-52 libavdevice-extra-52 libavformat-extra-52 gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse

```for 32 bit
```

sudo apt-get install w32codecs

```for 64 bit 
```

sudo apt-get install w64codecs
```

---

### Post by mac9416 on 2010-01-03
carlee, did you notice when saman6015 said:

> i dont have any internet connection how can i insatall audio and video player without internet connection

Though yours is a very elegant solution, I don't believe it will help saman if he does not have an Internet connection on the target computer. Am I mistaken?

---

### Post by sandyd on 2010-01-03
->apt-on-cd

---

### Post by mac9416 on 2010-01-03
Yes, that would work, assuming his online computer is Ubuntu 8.04 and knows how to use APTOnCD.

saman6015, if your online computer is running Ubuntu 8.04, you can run carlee's commands to install those plugins. Then you can use [APTOnCD]("http://aptoncd.sourceforge.net/") to create a CDROM repository of the packages that were downloaded and install them on the offline computer.

If you are not on Ubuntu 8.04, you should use [Keryx]("http://keryxproject.org"). Check out this page for an explanation of the differences between Keryx and APTOnCD: [http://keryxproject.org/wiki/index.php?title=Keryx_vs_APTonCD](http://keryxproject.org/wiki/index.php?title=Keryx_vs_APTonCD)

---

