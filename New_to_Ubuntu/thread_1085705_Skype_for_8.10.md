---
title: "Skype for 8.10"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by js@lloyd on 2009-03-03
I'd like to set up Skype, but the option on their site is Ubuntu 7.04-8.04 . Which version do I need for 8.10?  

Thanks,

---

### Post by gandaran on 2009-03-03
add the [medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository then install skype from synaptic, I would recommend the static version.

---

### Post by MrWES on 2009-03-03
> **js@lloyd said:**
> I'd like to set up Skype, but the option on their site is Ubuntu 7.04-8.04 . Which version do I need for 8.10?  

Thanks,

[http://ubuntu-tutorials.com/2008/11/16/install-skype-20-on-ubuntu-810-intrepid-ibex/]("http://ubuntu-tutorials.com/2008/11/16/install-skype-20-on-ubuntu-810-intrepid-ibex/")

---

### Post by js@lloyd on 2009-03-10
Thanks. Sorry for all the questions. Can anyone elaborate on what I need to do from here?  I don't want to mess this one up.

[IMG]http://i728.photobucket.com/albums/ww284/jsinlloyd/Screenshot-SoftwareSources.png[/IMG]

---

### Post by cmay on 2009-03-10
[PHP]#! /bin/bash
#
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
#
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
#
sudo apt-get install skype [/PHP]
this script is something i just made by copying the instructions from mediubuntu-link as posted above. for it to work you need to place it in the homefolder. open terminal and use the command chmod 755./scriptname and then run it wiht the command ./scriptname

it takes very little time to make those scripts and you can save them for anohter time when you need them.  you may use this one above or even better try making your own .
its really a good thing to learn to use script for these things as many things can be done very much faster.

---

### Post by hyper_ch on 2009-03-10
or use the repogenerator in my signature.

---

### Post by LowSky on 2009-03-10
you uncheck the medibuntu source files I doubt you will ever need that

Hyper_ch that Repo Gen is cool

---

### Post by js@lloyd on 2009-03-11
Thanks for the help on the install.  I use a plantronics headset and mic (audio 400 dsp) with Skype, but skype doesn't show it as a option to use in the options.  Assuming there's an easy fix.  As always, the assistance is appreciated.

---

