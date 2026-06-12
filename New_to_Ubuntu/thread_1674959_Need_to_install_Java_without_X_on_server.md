---
title: "Need to install Java without X on server"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by ben.blank on 2011-01-24
I'm just setting up a new server, and using Ubuntu for the very first time, on the recommendation of a friend.  Unfortunately, this means I am a *rank amateur* with apt-get! :)

After a bit of struggling, I have modified my /etc/apt/sources.list to include the "partner" repo and apt-get is willing to install sun-java6-jre.  However, the "extra packages" to be installed (dependencies, I assume) include X11 packages like gsfonts-x11 and x11-common.  Checking openjdk-6-jre, I see it wants to install X11 as well.

How can I install Java without installing X11?  I neither need, nor want, a graphical interface on server which I will be administering exclusively with SSH! ;)

**EDIT:**

I suppose I should have included the apt-get command I'm running and its output!

```
bblank@sectoid:/home/bblank$ sudo apt-get install sun-java6-bin
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  avahi-daemon consolekit dbus gsfonts gsfonts-x11 java-common libasound2 libavahi-common-data libavahi-common3 libavahi-core7 libck-connector0 libdaemon0 libeggdbus-1-0 libfontenc1 libice6 libltdl7 libnss-mdns libpam-ck-connector
  libpolkit-gobject-1-0 libpython2.6 libsm6 libxfont1 libxi6 libxt6 libxtst6 odbcinst odbcinst1debian2 sun-java6-jre unixodbc x11-common xfonts-encodings xfonts-utils
Suggested packages:
  avahi-autoipd dbus-x11 default-jre equivs libasound2-plugins binfmt-support sun-java6-plugin ia32-sun-java6-plugin sun-java6-fonts ttf-baekmuk ttf-unfonts ttf-unfonts-core ttf-kochi-gothic ttf-sazanami-gothic ttf-kochi-mincho
  ttf-sazanami-mincho ttf-arphic-uming libmyodbc odbc-postgresql tdsodbc unixodbc-bin
The following NEW packages will be installed:
  avahi-daemon consolekit dbus gsfonts gsfonts-x11 java-common libasound2 libavahi-common-data libavahi-common3 libavahi-core7 libck-connector0 libdaemon0 libeggdbus-1-0 libfontenc1 libice6 libltdl7 libnss-mdns libpam-ck-connector
  libpolkit-gobject-1-0 libpython2.6 libsm6 libxfont1 libxi6 libxt6 libxtst6 odbcinst odbcinst1debian2 sun-java6-bin sun-java6-jre unixodbc x11-common xfonts-encodings xfonts-utils
0 upgraded, 33 newly installed, 0 to remove and 86 not upgraded.
Need to get 42.3MB of archives.
After this operation, 117MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
```
```
bblank@sectoid:/home/bblank$ sudo apt-get install openjdk-6-jre
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  ca-certificates-java defoma fontconfig hicolor-icon-theme icedtea-6-jre-cacao java-common libaccess-bridge-java libaccess-bridge-java-jni libasound2 libatk1.0-0 libatk1.0-data libavahi-client3 libavahi-common-data libavahi-common3
  libcups2 libdatrie1 libflac8 libfontenc1 libgdk-pixbuf2.0-0 libgif4 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libice6 libjasper1 libjpeg62 liblcms1 libnspr4-0d libnss3-1d libogg0 libpango1.0-0 libpango1.0-common libpulse0
  libpython2.6 libsm6 libsndfile1 libthai-data libthai0 libtiff4 libvorbis0a libvorbisenc2 libx11-xcb1 libxcb-atom1 libxcomposite1 libxcursor1 libxdamage1 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1 libxrandr2 libxtst6
  openjdk-6-jre-headless openjdk-6-jre-lib shared-mime-info ttf-dejavu-extra tzdata tzdata-java x-ttcidfont-conf x11-common xfonts-encodings xfonts-utils
Suggested packages:
  defoma-doc psfontmgr dfontmgr libfont-freetype-perl default-jre equivs libasound2-plugins cups-common librsvg2-common gvfs libjasper-runtime liblcms-utils ttf-japanese-gothic ttf-japanese-mincho ttf-thryomanes ttf-baekmuk
  ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-gkai00mp ttf-arphic-bkai00mp pulseaudio icedtea6-plugin libnss-mdns sun-java6-fonts ttf-sazanami-gothic ttf-kochi-gothic ttf-sazanami-mincho ttf-kochi-mincho ttf-wqy-microhei
  ttf-wqy-zenhei ttf-indic-fonts-core ttf-telugu-fonts ttf-oriya-fonts ttf-kannada-fonts ttf-bengali-fonts
The following NEW packages will be installed:
  ca-certificates-java defoma fontconfig hicolor-icon-theme icedtea-6-jre-cacao java-common libaccess-bridge-java libaccess-bridge-java-jni libasound2 libatk1.0-0 libatk1.0-data libavahi-client3 libavahi-common-data libavahi-common3
  libcups2 libdatrie1 libflac8 libfontenc1 libgdk-pixbuf2.0-0 libgif4 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libice6 libjasper1 libjpeg62 liblcms1 libnspr4-0d libnss3-1d libogg0 libpango1.0-0 libpango1.0-common libpulse0
  libpython2.6 libsm6 libsndfile1 libthai-data libthai0 libtiff4 libvorbis0a libvorbisenc2 libx11-xcb1 libxcb-atom1 libxcomposite1 libxcursor1 libxdamage1 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1 libxrandr2 libxtst6
  openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib shared-mime-info ttf-dejavu-extra tzdata-java x-ttcidfont-conf x11-common xfonts-encodings xfonts-utils
The following packages will be upgraded:
  tzdata
1 upgraded, 63 newly installed, 0 to remove and 85 not upgraded.
Need to get 47.7MB of archives.
After this operation, 131MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
```

---

### Post by ben.blank on 2011-01-24
Eureka!  I now feel even more foolish for answering my own question, but here it is: I needed to install openjdk-6-jre**-headless**

While working on another part of the server, I found myself in the folder containing the .jar file and typed "java" out of sheer perversity.  Needless to say, it listed out a number of -headless packages I could install to get Java working. :D

---

### Post by Lunarll on 2011-01-24
On a side note... a command you might find useful is
```

apt-cache search <search_item>
apt-cache search <search_item> | grep <some_specific_thing>

```

In case you're ever looking for any other packages.
"grep" is useful if you ever want to narrow your search down but don't know the exact package name. The lists for searching can get seriously long sometimes. x.x

---

