---
title: "LibreOffice Constantly Crashing"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by wpwend42 on 2011-08-03
Almost every time I open LibreOffice, it crashes the first time I try to save the file I am working with. This happens with word processing, spreadsheets, and presentations. Sure, I can recover the files fine, but this is getting extremely annoying and cutting into my productivity. The software is basically unusable if I let a file sit for a few minutes. The next time I try to type, it crashes. 

Are there any know solutions for this problems?

---

### Post by skatinjj on 2011-08-03
Can you run it from the terminal with this:

```
gnome-terminal -e libreoffice
```

and post any error messaages from the terminal here?

---

### Post by wpwend42 on 2011-08-03
No errors come up when I put that into the terminal.

---

### Post by skatinjj on 2011-08-03
Run libreoffice from the terminal then try to open and save a document.

Are there any errors in the terminal after the program crashes?

---

### Post by wpwend42 on 2011-08-03
The terminal doesn't show any errors after it crashes.

---

### Post by amjjawad on 2011-08-03
> **wpwend42 said:**
> The terminal doesn't show any errors after it crashes.

Are you using 11.04? are you logging in to Unity?

Try to Login to Classic with no effect session and see if that makes any difference.

---

### Post by wpwend42 on 2011-08-03
Oh, I'm not on 11.04/Unity. I can't think of anything else that could be wrong? This is extremely frustrating and really killing my productivity.

---

### Post by skatinjj on 2011-08-03
What version of Ubuntu are you running?

---

### Post by wpwend42 on 2011-08-03
Could a fresh install of LibreOffice help?

I just noticed that it doesn't seem to happen with .txt files, but doesn't .odt, .odp, etc

---

### Post by skatinjj on 2011-08-03
It might, you would have to try it and find out.

---

### Post by The Cog on 2011-08-03
It might be worth downloading and installing version 3.4.2, released a few days ago. It contains bug fixes.

---

### Post by vanquishedangel on 2012-02-08
I am aswell having this issue in Lubuntu oneric oncelot. I went into the terminal and typed sudo apt-get build-dep libreoffice, and it is installing all of this...


ant ant-optional automoc bsh dctrl-tools default-jdk devscripts dmake
  fastjar fdupes firefox firefox-dev gir1.2-ebook-1.2 gir1.2-edataserver-1.2
  gir1.2-gconf-2.0 gperf javahelper kdelibs-bin kdelibs5-dev kdoctools
  libamd2.2.0 libarchive-zip-perl libatk1.0-dev libattica0 libblas-dev
  libboost-dev libboost1.46-dev libbtf1.1.0 libcairo-script-interpreter2
  libcairo2-dev libcamd2.2.0 libcamel-1.2-29 libcamel1.2-dev libccolamd2.7.1
  libcholmod1.7.1 libclucene0ldbl libcommons-codec-java
  libcommons-httpclient-java libcommons-lang-java libcommons-logging-java
  libcppunit-1.12-1 libcppunit-dev libcsparse2.2.3 libcxsparse2.2.3 libdb-dev
  libdb5.1-dev libdbusmenu-qt2 libdlrestrictions1 libebook1.2-12
  libebook1.2-dev libedataserver1.2-15 libedataserver1.2-dev libexiv2-10
  libfftw3-dev libgconf2-dev libgdk-pixbuf2.0-dev libgmp-dev libgnomevfs2-0
  libgnomevfs2-common libgnomevfs2-dev libgtk2.0-dev libhunspell-dev
  libhyphen-dev libicu-dev libidl-dev libidl0 libiodbc2 libjline-java
  libkactivities5 libkcmutils4 libkde3support4 libkdeclarative5 libkdecore5
  libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4 libkemoticons4 libkfile4
  libkhtml5 libkidletime4 libkimproxy4 libkio5 libkjsapi4 libkjsembed4
  libklu1.1.0 libkmediaplayer4 libknewstuff2-4 libknewstuff3-4
  libknotifyconfig4 libkntlm4 libkparts4 libkprintutils4 libkpty4
  libkrosscore4 libkrossui4 libktexteditor4 libkunitconversion4 libkutils4
  liblapack-dev libldl2.0.1 liblpsolve55-dev libmdds-dev libmysqlclient-dev
  libmysqlcppconn-dev libmysqlcppconn5 libmythes-dev libneon27-gnutls-dev
  libnepomuk4 libnepomukquery4a libnepomukutils4 liborbit2 liborbit2-dev
  libpango1.0-dev libphonon-dev libphonon4 libplasma3 libpoppler-dev libpq-dev
  libpq5 libpulse-mainloop-glib0 libqca2 libqt4-designer libqt4-dev
  libqt4-help libqt4-opengl libqt4-qt3support libqt4-scripttools libqt4-svg
  libqt4-test libqtwebkit4 libraptor2-dev librasqal3-dev librdf0-dev
  libselinux1-dev libsepol1-dev libsolid4 libsoprano-dev libsoprano4
  libsqlite3-dev libstreamanalyzer0 libstreams0 libsuitesparse-dev
  libtextcat-dev libthreadweaver4 libumfpack5.4.0 libvigraimpex-dev
  libvigraimpex2 libwpd-dev libwpg-dev libwps-dev libxaw7-dev
  libxcb-render0-dev libxcb-shm0-dev libxft-dev libxmu-dev libxmu-headers
  libxpm-dev libxtst-dev libyajl-dev openjdk-6-jdk phonon-backend-null
  python-dev python2.7-dev qt4-linguist-tools qt4-qmake soprano-daemon
  x11proto-record-dev


it is 123 mb of stuff and will take up 1/2 gig of space and after that i may try a re-install of libre office.

did that fix it for you?

---

