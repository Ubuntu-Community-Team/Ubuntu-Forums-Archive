---
title: "Installing Linux Wireless OR Ndiswrapper without Internet connection"
date: 2014-02-04
forum: Networking &amp; Wireless
---

### Post by MercuriusAurelio on 2014-02-04
Let me just preface this by saying I'm generally a cool-headed, patient guy, and I don't bother people about my problems if I know I can probably find the answer to them myself. With that said, I've been using Ubuntu for about 6 months, and this is exactly what I do 100% of the time and I haven't had such a problem until today/several days ago when my laptop's wireless adapter died.

 I'm aware this/general wireless issues are often quite the problem for ubuntu users, but looking for answers has made it at least 10 times as frustrating. Knowing I would have to deal with enraging grapplings, I bought a Belkin USB wifi adapter from wal-mart, and initially tried to install/run the accompanying software using wine. This, obviously, was entirely useless. Silly me. So I took to the googles looking for any possible substitute drivers. What I found was Ndiswrapper, in other user's words, is for "trying to force-fit the square Windows driver into the round Linux hole". Sounds decent enough to me though I know most disagree, I just need an internet connection to do my work. I also came Across Linux Hybrid Wireless Driver, which also sounded worth a shot. It all sounded good on paper. The problem is, every single set of instructions, for either, even on those threads posted by users in my exact situation, seemed to include terminal installation commands that by default, involve.....erm. an INTERNET connection. Sorry for the sarcasm, but can ANYONE spot the fundamental problem with this. As if that wasn't frustrating enough, I have downloaded different versions of Ndiswrapper, and The Linux Hybrid driver, and with all the different sets of instructions on how to implement them, transferred them to a USB flashdrive to linux machine, and am still a complete loss, didn't get past the first or second step in all cases. Even the instructions on transferring the install package via USB give terminal commands, and those commands herald results implying that the file or directory does not exist, and "unable to locate package ___" "couldn't find any package by regex 'ndiswrapper-1.59" etc.... Now maybe this is because I'm an ubuntu noob making an a$s of himself and doesn't know jack about how the terminal or how the commands you put in it work, but can anyone give good advice on how to install either Ndiswrapper or Linux Hybrid Wireless Driver? That doesn't involve Terminal Commands that implement an internet connection? I know there must be some commands I can run that will help install them, but for the love of **** no more "sudo apt-get install _______" commands that typically initiate a download. Just keep in mind, this machine has NO METHOD of connecting to the internet, at all right now. I've also ran all these commands as root to no avail.

I'm currently Running:

Ubuntu 13.10 
on Toshiba Satellite L505 

Trying to install the packages either
ndiswrapper-1.59
or hybrid-v35_64-nodebug-pcoem-6_30_223_141

In order to use
Belkin N450 DB/N600 (F9L4500) Wifi USB adapter (as of yet unlisted on [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:Belkin](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:Belkin) and similar lists) If it doesn't work, I'll get over it, but I haven't even been able to determine that in any official capacity yet.

both of these packages are located in my home directory, so what is the best, specific advice to installing these?

---

### Post by chili555 on 2014-02-04
Let's start by identifying your device. Please open a terminal and run and post:```
lsusb
```It's fine to trim away everything that isn't your Belkin wireless before you post it.

---

### Post by MercuriusAurelio on 2014-02-04
this turns up "Bus 002 Device 018: ID 050d:110a Belkin Components"

---

### Post by chili555 on 2014-02-04
The short version is that the device Device 018: ID [COLOR="#FF0000"]050d:110a[/COLOR] Belkin Components uses the relatively new driver 8192du. The instructions you will hate to see are here: [http://ubuntuforums.org/showthread.php?t=2153777&p=12688576#post12688576](http://ubuntuforums.org/showthread.php?t=2153777&p=12688576#post12688576) 

If you could beg, borrow or steal an ethernet connection from a friend, you could be done in two minutes. If you can't, and must download all on some other computer and transfer on a USB stick or similar, it will be arduous and I'll need to postpone my May trip to Cape Cod. In anticipation of your answer, I will pour a ... beverage.

Just to give you a preview, for example, *build-essential* has dependencies that also must be downloaded and installed. And the dependencies have dependencies.

---

### Post by MercuriusAurelio on 2014-02-04
^%$$ goodie. well I suppose I could find one as it seems it might be LESS out of the way. Is each line a separate command?

---

### Post by chili555 on 2014-02-04
> it seems it might be LESS out of the way.Woo hoo! I'll tell Mrs. Chili and Travelocity we are go for Cape!

Each command is a separate command followed by Enter. Some will do little and some will churn away for a few moments. I compiled this on my own system and it should do so with a few warnings but no error and, as I said, in about two minutes. If you have any other questions, I'm here.

---

### Post by MercuriusAurelio on 2014-02-04
Well, I got the connection finally, thank you kindly for all your help, enjoy your vacay, haha.

---

### Post by chili555 on 2014-02-04
> **MercuriusAurelio said:**
> Well, I got the connection finally, thank you kindly for all your help, enjoy your vacay, haha.Awesome! Great job.

You have compiled the driver for the currently running kernel version only. When Update Manager offers a newer version, also known as linux-image, after reboot, recompile:```
cd ~/rtl8192du
[COLOR="#FF0000"]make clean[/COLOR]
make
sudo make install
sudo modprobe 8192du
```Please retain the file and these instructions for that time.

Please use thread tools at the top to mark Solved.

---

