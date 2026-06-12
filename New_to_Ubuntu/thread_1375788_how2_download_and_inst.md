---
title: "how2 download and inst"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by ricky rodgers on 2010-01-08
hi all my question is how do you download an application from the Internet and then install it in plane language ie for a nob like me
Richard;)

---

### Post by warfacegod on 2010-01-08
The most straight forward method would be to find an app with .deb at the end of the file name. .deb works sort of like a Windows .exe file. Good luck.

---

### Post by Darce on 2010-01-08
The easiest way is to download using the software centre ( Karmic ) or Synaptic Package Manager.

---

### Post by mlentink on 2010-01-08
Hors Competition:
[https://help.ubuntu.com/9.10/add-applications/C/index.html](https://help.ubuntu.com/9.10/add-applications/C/index.html)

Number 1:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
Runner up:
[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

---

### Post by FaizanKazi on 2010-01-08
> **ricky rodgers said:**
> hi all my question is how do you download an application from the Internet and then install it in plane language ie for a nob like me
Richard;)

you have 3 basic options:

1) find .deb files which can be installed with just a few clicks of the mouse, like exe files. [www.getdeb.net/](www.getdeb.net/) distributes deb (debian) installer files.

2) use the synaptic package manager which shows a listing of all available software from the default servers. System menu >> Administration >> Synaptic Package Manager.

3) use the command line.... Sudo apt-get install something somethingElse
Use tab completion (pressing the tab key once or twice quickly) to try completing your queries
like if i write: "sudo apt-get install pidg" and double-click the Tab button it'll either give me some options, one of which will be "pidgin", or it'll just autocomplete the word because thats the only option.

good luck! :)

---

### Post by warfacegod on 2010-01-08
> The easiest way is to download using the software centre ( Karmic ) or Synaptic Package Manager.


Not everyone's S.C. is working. Synaptic is not easy (normally) for a noob. Assuming you don't already know, could you tell me what simple-ccsm was? Or dpkg?

Double clicking .deb files is very easy. Later on, with more experience, comes synaptic, tarballs, apt-get install, or compiling from source.


ricky rodgers:

Assuming that your ubuntu software center is working, I would suggest using it install Add/Remove Applications. It's more simple than ubuntu S.C.

---

### Post by bodhi.zazen on 2010-01-08
If at all possible , use the Ubuntu repositories. The repositories are quite large and this is a huge advantage of Ubuntu.

[InstallingSoftware - Community Ubuntu Documentation]("https://help.ubuntu.com/community/InstallingSoftware") 

If you wish to install an application outside of the repos, well installation will vary. Personally I advise you learn to compile from source code and would caution you of two things :

1. Only install applications from trusted sources. There was a recent malicious .deb in Gnome Look.

2. Just because it is a .deb does NOT mean it is compatible with Ubuntu.

---

### Post by ricky rodgers on 2010-01-08
ok thanks for all the help now the thing is i am running ubuntu .9.10 and the file i want to get is called  campcaster now this is the files on the site
 
[**Download Now!** campcaster-1.4.0.tar.bz2 (12.6 MB]("http://ubuntuforums.org/projects/campcaster/files/campcaster/1.4.0-beta3/campcaster-1.4.0.tar.bz2/download")
 
and
 
[_[COLOR=#0000ff]campcaster-libs_1.4.0-3beta3_i386.deb_[/COLOR]]("http://ubuntuforums.org/projects/campcaster/files/campcaster/1.4.0-beta3/campcaster-libs_1.4.0-3beta3_i386.deb/download") 1.7 MB 2009-05-04 1,940 [_[COLOR=#0000ff]campcaster-studio_1.4.0-3beta3_i386.deb_[/COLOR]]("http://ubuntuforums.org/projects/campcaster/files/campcaster/1.4.0-beta3/campcaster-studio_1.4.0-3beta3_i386.deb/download") 734.5 KB 2009-05-04 1,485 [_[COLOR=#0000ff]campcaster-station_1.4.0-3beta3_i386.deb_[/COLOR]]("http://ubuntuforums.org/projects/campcaster/files/campcaster/1.4.0-beta3/campcaster-station_1.4.0-3beta3_i386.deb/download") 1.1 MB 2009-05-04 1,618 [_[COLOR=#0000ff]campcaster-libraries-1.4.0.tar.bz2_[/COLOR]]("http://ubuntuforums.org/projects/campcaster/files/campcaster/1.4.0-beta3/campcaster-libraries-1.4.0.tar.bz2/download") 2.3 MB 2009-05-04 957 [_[COLOR=#0000ff]campcaster-1.4.0.tar.bz2_[/COLOR]]("http://ubuntuforums.org/projects/campcaster/files/campcaster/1.4.0-beta3/campcaster-1.4.0.tar.bz2/download") 12.6 MB 2009-05-04 2,493
 
so do i just downloade the top one if so where to
 
or do i download the bottom files  if so where to  and how do i open it and install ????
richard.

---

### Post by FaizanKazi on 2010-01-08
> **warfacegod said:**
> Not everyone's S.C. is working. Synaptic is not easy (normally) for a noob. Assuming you don't already know, could you tell me what simple-ccsm was? Or dpkg?


really? its "not easy"? there are explanations for each software package... :s

its also easy to search by key words: searching for "compiz" brings up simple-ccsm. searching for stuff on the net can be confusing, and then there's just SO much reading. not to mention there may be outdated packages or complicated installation techniques listed, and possibly malicious code.

also, the screenshots add-on was great. Linux Mint had implemented it earlier and they still do it better.

anyway, its concise, its safe (if using default repositories) and its easy. thats Synaptic Package manager.

---

### Post by FaizanKazi on 2010-01-08
> **ricky rodgers said:**
>  
[**Download Now!** campcaster-1.4.0.tar.bz2 (12.6 MB]("http://ubuntuforums.org/projects/campcaster/files/campcaster/1.4.0-beta3/campcaster-1.4.0.tar.bz2/download")
 
and
 
[_[COLOR=#0000ff]campcaster-libs_1.4.0-3beta3_i386.deb_[/COLOR]]("http://ubuntuforums.org/projects/campcaster/files/campcaster/1.4.0-beta3/campcaster-libs_1.4.0-3beta3_i386.deb/download") 

The second url is the link you should use.
its a link to the DEB file.

have you not been reading what people have written for you?

---

### Post by bodhi.zazen on 2010-01-08
> **ricky rodgers said:**
> ok thanks for all the help now the thing is i am running ubuntu .9.10 and the file i want to get is called  campcaster now this is the files on the site
 
[**Download Now!** campcaster-1.4.0.tar.bz2 (12.6 MB]("http://ubuntuforums.org/projects/campcaster/files/campcaster/1.4.0-beta3/campcaster-1.4.0.tar.bz2/download")
 
and
 
[_[COLOR=#0000ff]campcaster-libs_1.4.0-3beta3_i386.deb[/COLOR]_]("http://ubuntuforums.org/projects/campcaster/files/campcaster/1.4.0-beta3/campcaster-libs_1.4.0-3beta3_i386.deb/download") 1.7 MB 2009-05-04 1,940 [_[COLOR=#0000ff]campcaster-studio_1.4.0-3beta3_i386.deb[/COLOR]_]("http://ubuntuforums.org/projects/campcaster/files/campcaster/1.4.0-beta3/campcaster-studio_1.4.0-3beta3_i386.deb/download") 734.5 KB 2009-05-04 1,485 [_[COLOR=#0000ff]campcaster-station_1.4.0-3beta3_i386.deb[/COLOR]_]("http://ubuntuforums.org/projects/campcaster/files/campcaster/1.4.0-beta3/campcaster-station_1.4.0-3beta3_i386.deb/download") 1.1 MB 2009-05-04 1,618 [_[COLOR=#0000ff]campcaster-libraries-1.4.0.tar.bz2[/COLOR]_]("http://ubuntuforums.org/projects/campcaster/files/campcaster/1.4.0-beta3/campcaster-libraries-1.4.0.tar.bz2/download") 2.3 MB 2009-05-04 957 [_[COLOR=#0000ff]campcaster-1.4.0.tar.bz2[/COLOR]_]("http://ubuntuforums.org/projects/campcaster/files/campcaster/1.4.0-beta3/campcaster-1.4.0.tar.bz2/download") 12.6 MB 2009-05-04 2,493
 
so do i just downloade the top one if so where to
 
or do i download the bottom files  if so where to  and how do i open it and install ????
richard.

You can try the .deb There are many ways to install it, Personally I would download all 3 .deb (-libs, -studio, and -station) to your Desktop.

(assume the .deb is downloaded to Desktop)

```
cd ~/Desktop
sudo dpkg -i ./campcaster-libs*
sudo dpkg -i campcaster-station*
sudo dpkg -i campcaster-studio*
```

Post back if you have problems, but as this app is not supported by Ubuntu you may also want to ask on the campcast site :

[http://www.campware.org/en/camp/campcaster_news/649/](http://www.campware.org/en/camp/campcaster_news/649/)

---

### Post by ricky rodgers on 2010-01-08
the thing is a have downloaded all this lot and still no program on the pc i have about 20 downloads on the pc and no program running in windows you do it once and it is there .??????

---

### Post by bodhi.zazen on 2010-01-08
> **ricky rodgers said:**
> the thing is a have downloaded all this lot and still no program on the pc i have about 20 downloads on the pc and no program running in windows you do it once and it is there .??????

Remove all the downloads.

download each .deb once, why do you keep downloading and working with the tar.gz ? 

rather then telling us it is not working you will need to describe the problem. What is happening,? Can not install the .deb ? what command did you run ? Can't start the program , what error message did you get ?

---

