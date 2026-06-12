---
title: "How to Play Video in Firefox?"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by h2o4444 on 2009-03-28
I just recently did a fresh install of Ubuntu on my computer and Firefox can't seem to play any of the videos on hulu.com, casttv.com, or youtube.com.

All of the error messages told me to install Flash and I installed the latest Flash 10 but the error is still evident when I go on these sites after the fact. In Synaptics both "adobe-flashplugin" and "flashplugin-nonfree" are installed.

As for the Plugins under Add-ons in Firefox itself, I have the Default Plugin, Demo Print Plugin for unix/linux, and Shockwave Flash. I even completely removed Firefox then reinstalled it with Synaptic but the problem is still there.

How do I make Firefox play the videos on those sites?

---

### Post by germanix on 2009-03-28
Run this command in a terminal;

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2

This will add the medibuntu repository and install codecs for xvid, divx and a number of other video codecs, audio codecs, flash, java, commercial dvd playback, ...

Just copy/paste the command, press enter, enter your password (you won't see what or how many letters you type) and press enter again.

During installation a EULA for Java will pop up,press tab and press enter to agree.

This should solve the problem.

---

### Post by gandaran on 2009-03-28
> **h2o4444 said:**
> I just recently did a fresh install of Ubuntu on my computer and Firefox can't seem to play any of the videos on hulu.com, casttv.com, or youtube.com.

All of the error messages told me to install Flash and I installed the latest Flash 10 but the error is still evident when I go on these sites after the fact. In Synaptics both "adobe-flashplugin" and "flashplugin-nonfree" are installed.

As for the Plugins under Add-ons in Firefox itself, I have the Default Plugin, Demo Print Plugin for unix/linux, and Shockwave Flash. I even completely removed Firefox then reinstalled it with Synaptic but the problem is still there.

How do I make Firefox play the videos on those sites?
do you have flashblock addon installed?
you don't need two flash packages installed! this will just complicate things for firefox, remove one either adobe-flashplugin or flashplugin-nonfree, both install exactly the same adobe flash plugin and make sure you don't have any open source flash installed like gnash or swfdec too.
also it's very important to have the system fully updated, there have been some system changes and flash mite not work if ubuntu is not fully updated.

---

### Post by h2o4444 on 2009-03-28
I do not have flashblock addon installed.

I removed flashplugin-nonfree since it's an installer, according to the Synaptic description. The problem still persisted. But a simple search of "flash" in Synaptics turned out to be helpful because "swfdec-mozilla" was installed. After I removed it the videos worked, at least for now.

My system is updated to the latest Ubuntu and its packages.

Thank you very much for helping me.

---

