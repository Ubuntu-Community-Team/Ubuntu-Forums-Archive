---
title: "A few beginner problems."
date: 2009-11-03
forum: New to Ubuntu
---

### Post by RileyRandom on 2009-11-03
Hello this is my second attempt to try with ubuntu. this time with 9.10
Anyway, here are my two problems; i can't seem to get adobe flash plugin to work.
my second problem is ubuntu is running insanely slow. How do i fix this?

third problem is how do i play my ipod on ubuntu

---

### Post by Raistlin355 on 2009-11-03
Are you running 32bit or 64bit?  What kind of hardware do you have? i.e. cpu, RAM.  What Gen iPod do you have?

---

### Post by QIII on 2009-11-03
Did you install Karmic, or are you running it from the LiveCD?

---

### Post by Roinator on 2009-11-03
> Hello this is my second attempt to try with ubuntu. this time with 9.10
Anyway, here are my two problems; i can't seem to get adobe flash plugin to work.
my second problem is ubuntu is running insanely slow. How do i fix this?

third problem is how do i play my ipod on ubuntu 

To install flash and a bunch of other restricted extras use Ubuntu Software Center to install "Ubuntu restricted extras".  If you just want flash support though, you can install it using synaptic (System->Administration->Synaptic Package Manager), or you can open up a terminal and:

```
sudo apt-get install adobe-flashplugin
```

Also, you may want to remove other flash players from your system if they are already installed.

Your computer running slowly could be a result of any number of problems.  You could try to narrow it down by opening up the System Monitor (System->Administration-> System Monitor) and seeing what is taking so many resources.

To use your iPod on ubuntu you can use one of many different programs/media players.  I am almost assuredly in a minority, but I like Banshee.  Alternatives include Rhythmbox, Amaraok, Songbird, and Exaile.  Also, if you don't want a media player, and just want iPod support you can use gtkpod.  You can install all of those apps through the Ubuntu Software Center.

---

### Post by Raistlin355 on 2009-11-04
> **Roinator said:**
> To install flash and a bunch of other restricted extras use Ubuntu Software Center to install "Ubuntu restricted extras".  If you just want flash support though, you can install it using synaptic (System->Administration->Synaptic Package Manager), or you can open up a terminal and:

```
sudo apt-get install adobe-flashplugin
```

This has changed.  It is now:
```
sudo apt-get install flashplugin-installer
```
I'm not being a jerk, just trying to help a newbie.

---

### Post by nhasian on 2009-11-04
first of all you need to check with you are using 32bit or 64bit ubuntu as it makes a difference in this case. if you are using 32bit ubuntu simply open up a terminal (applications->accessories->terminal) and type:

```
sudo apt-get install flashplugin-nonfree
```

viola! your done. you will need to close firefox and restart if it was running.

If your using 64bit ubuntu on the other hand using the above method will only install the 32bit version of adobe flash. you want the 64 bit version from:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

extract the libflashplayer.so file from the tar archive and then you need to copy it to /usr/lib/mozilla/plugins/ with the following command:

```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
```

---

