---
title: "Help with project playlist"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by zabien1970 on 2009-02-17
When I go on my project playlist page my songs no longer appear or play, I borrowed a friends computer running windows and it worked there so that eliminates the site, it was working last month.
 I did run 2 commands (can't remember if it was before or after I had problems)

 ```
sudo apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar 
```

 ```
 sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2 libdvdnav4 gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 libdvdread3
```

 Im running 8.04

---

### Post by cariboo on 2009-02-17
You may want to install the ubuntu-restricted-extras meta package, to reinstall the codecs you removed.

Jim

---

### Post by zabien1970 on 2009-02-17
How would i do that? I mostly copy and paste commands, I just found them by going through my history in terminal

edit: basically what is the terminal command to reinstall the codecs I removed?

---

