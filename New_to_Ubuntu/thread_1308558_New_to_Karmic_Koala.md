---
title: "New to Karmic Koala"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by infernus_crusher on 2009-10-31
Hi,

I just installed Karmic from scratch and found out that things weren't working as expected. I'd like to know how I can fix these problems:
1. Adobe Flash Player plugin not installed in Firefox. (`sudo apt-get install adobe-flashplugin` doesn't work)
2. How to install libqtdbus4 for Skype.
3. Enabling all Jaunty repositories (cos I can't `sudo apt-get install rails`)
4. I want Pidgin back. Empathy isn't as fun to use.

If there's anything I might need to know, please feel free to add. Thanks.

---

### Post by Buuntu on 2009-10-31
1) You can download the .deb package from here -> [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
2) Not sure about this one, I'll try to see if I can find something
3) System > Administration > Software Sources.  From there you can check the repositories you would like to download from (I assume you want universe and multiverse mainly)
4) ```
sudo apt-get install pidgin
```
and if you want to remove empathy:
```
sudo apt-get remove empathy
```
You can also do the above from Synaptic Package Manager (System > Administration > Synaptic Package Manager) if you prefer an interface.

---

### Post by infernus_crusher on 2009-10-31
For the repository list, I'm not sure what line to add to the Other Software tab in Software Sources. Currently I have two:
1. [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
2. [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner (Source Code)

---

### Post by dj-toonz on 2009-10-31
To install flash, just type sudo apt-get install ubuntu-restricted-extras , the same as under Jaunty and it installs flash & all the other codecs all together

---

### Post by ikisham on 2009-10-31
You may install Pidgin but leave Empathy alone since it's integrated with Gnome and can't be removed by itself.
rails is in the repos in Karmic. Try ```
sudo apt-get update
``````
sudo apt-get install rails
```

---

### Post by mikewhatever on 2009-10-31
sudo apt-get install adobe-flashplugin

Something might be wrong with the repositories or the sources. Please post the output of that command.

---

### Post by dj-toonz on 2009-10-31
> **mikewhatever said:**
> sudo apt-get install adobe-flashplugin

Something might be wrong with the repositories or the sources. Please post the output of that command.


he doesn't need to do that, easier way & this installs every codec under the sun to play or view anything even dvd's (ubuntu-restricted-extras has the flash plugin and others)

sudo apt-get install ubuntu-restricted-extras sun-java6-jre sun-java6-plugin sun-java6-fonts msttcorefonts non-free-codecs libdvdcss2 w32codecs **copy & paste the whole part from sudo ** (make sure medibuntu repo is enabled first to install the non-free-codecs, Libvdcss2 & w32codecs)

---

### Post by Dougie187 on 2009-10-31
> **mikewhatever said:**
> sudo apt-get install adobe-flashplugin

Something might be wrong with the repositories or the sources. Please post the output of that command.

The package name isn't even adobe-flashplugin. It's flashplugin-nonfree, but it's better to install it through ubuntu-restricted-extras because they would get more codecs and stuff like java.

---

### Post by juraj.pelikan on 2009-10-31
2) sudo apt-get install libqt4-dbus

if you want all dependencies: sudo apt-get build-dep skype

---

### Post by kevdog on 2009-10-31
With the pidgin demand, I would install from ppa to get the latest/greatest version with all the features:

Here's the PPA page:

[https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)

---

### Post by mikewhatever on 2009-10-31
> **dj-toonz said:**
> he doesn't need to do that, easier way & this installs every codec under the sun to play or view anything even dvd's (ubuntu-restricted-extras has the flash plugin and others)

sudo apt-get install ubuntu-restricted-extras sun-java6-jre sun-java6-plugin sun-java6-fonts msttcorefonts non-free-codecs libdvdcss2 w32codecs **copy & paste the whole part from sudo ** (make sure medibuntu repo is enabled first to install the non-free-codecs, Libvdcss2 & w32codecs)

Well, if there is a problem with either the repositories or the sources, ubuntu-restricted-extras wouldn't install. On the other hand, not every one wants 'every codec under the sun' plus java. I've installed ubuntu-restricted-extras a few times in the past, only to find out I never use half of what it pulls in. These days, I just click a file to play, and Ubuntu searches and installs the codecs by itself.

---

### Post by sdpiowa on 2009-10-31
If you are trying to install flash player on a 64 bit version of Ubuntu, see here:
[http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/](http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/)

I do not know if you are using a 64 bit version of the OS, but if you are, the link should help.

---

### Post by infernus_crusher on 2009-11-01
Okay, why can't apt-get fetch anything? Whatever I downloaded just stayed at 0% and connection timed out minutes later.

I had similar problem with Firefox before, but I went into its config and disabled IPv6 as instructed, and now it works.

FYI, I'm using a 32-bit Karmic Koala on a 3 year old laptop.

---

