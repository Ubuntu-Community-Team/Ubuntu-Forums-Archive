---
title: "Problem running minitube"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by shankhs on 2009-10-22
hi,
I installed minitube [http://flavio.tordini.org/minitube]("http://flavio.tordini.org/minitube") and all the codecs neccessary but when I am trying to run it the error pops up:

```
(<unknown>:17544): libsoup-CRITICAL **: soup_message_queue_destroy: assertion `queue->head == NULL' failed
"http://www.youtube.com/get_video?video_id=NCPDiEz-GcE&t=vjVQa1PpcFO_wZnazyZ0Oo3T0jMfmGNtVqs_eY1Opr0=&eurl=&el=detailpage&ps=default&fmt=18" 
GET "http://gdata.youtube.com/feeds/api/videos?q=hi&max-results=1&start-index=19" 
Phonon error: "A required codec is missing. You need to install the following codec(s) to play this content: text/html" 2 

```

How do I install text/html!!!?
I am behind proxy if that might cause the error.
Anybody here have any idea where is minitube installed?
How to know where any app in ubuntu installs itself?(the apps in linux never asks for the place to get installed!!!)
Thank You
-shankhs

---

### Post by cariboo on 2009-10-22
I'm not sure about the missing codec, but all properly packaged programs are located in /usr/bin. To find where all the files are located open an Applications-->Accessories-->Termianl and type:

```
locate <packagename>
```

where <packagename> is the name of the package you are looking for. If you were looking for minitube the command would be:

```
locate minitube
```

---

### Post by OpenGuard on 2009-10-22
```
sudo apt-get install html2text

```

---

### Post by jmszr on 2009-10-22
shankhs,

You can install minitube with a .deb, if you'd prefer: [http://www.getdeb.net/search.php?keywords=MINITUBE](http://www.getdeb.net/search.php?keywords=MINITUBE) .

---

### Post by shankhs on 2009-10-22
> **OpenGuard said:**
> ```
sudo apt-get install html2text

```
html2text is already installed.

and 

> **cariboo907 said:**
> I'm not sure about the missing codec, but all properly packaged programs are located in /usr/bin. To find where all the files are located open an Applications-->Accessories-->Termianl and type:

```
locate <packagename>
```

where <packagename> is the name of the package you are looking for. If you were looking for minitube the command would be:

```
locate minitube
```

```
shankhs@shankhs-desktop:~$ locate minitube
shankhs@shankhs-desktop:~$ 

```
locate mintube isnt giving anything.I am completely lost its installed and can open minitube then why locate isnt returning anything?
Anyways /usr/bin does contain the minitube exe but there might be some config file to let me enter the http proxy stuffs,I couldn't find those files.

> **jmszr said:**
> shankhs,

You can install minitube with a .deb, if you'd prefer: [http://www.getdeb.net/search.php?keywords=MINITUBE](http://www.getdeb.net/search.php?keywords=MINITUBE) .

I have installed minitube using .deb only.

Than You for your time and useful advices.

---

### Post by varsamakos on 2009-11-17
I'm trying minitube 0.8 but I can't watch any video.
For some reason, playback is not starting.

---

### Post by eagle06 on 2009-12-03
same problem text/html error

---

### Post by oracle2b on 2009-12-19
I installed minitube like this.

sudo apt-get install qt4-dev-tools

sudo apt-get install phonon-backend-gstreamer gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad

sudo ln -s /usr/lib/kde4/plugins/phonon_backend /usr/lib/qt4/plugins

grab the deb and install it.

[https://launchpad.net/~neversfelde/+archive/ppa/+files/minitube_0.8.1-0ubuntu1~karmic1~ppa2_i386.deb]("https://launchpad.net/~neversfelde/+archive/ppa/+files/minitube_0.8.1-0ubuntu1~karmic1~ppa2_i386.deb") (for x86 pc's)

[https://launchpad.net/~neversfelde/+archive/ppa/+files/minitube_0.8.1-0ubuntu1~karmic1~ppa2_amd64.deb]("https://launchpad.net/~neversfelde/+archive/ppa/+files/minitube_0.8.1-0ubuntu1~karmic1~ppa2_amd64.deb") (fo x64 pc's

---

