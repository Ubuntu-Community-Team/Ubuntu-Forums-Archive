---
title: "getting wireless to work without ethernet acess"
date: 2007-07-14
forum: Networking &amp; Wireless
---

### Post by DWRZ on 2007-07-14
**Hardware:** HP zd8000 Notebook [P4 @ 2.8 Ghz, 512 RAM, HD ~60Gb, Realtek8139/810x (Ethernet), Broadcom 802.11 b/g WLAN].
**OSes:** Windows XP SP2, Ubuntu Feisty 7.04

I need a creative, cohesive and intelligent solution to an unusual problem.

My Ethernet has stopped working. I still have functional wireless access from WinXP SP2, but no wireless on Ubuntu. Back when I was on Ubuntu Edgy I had wireless working with no problems.

I want to get Ubuntu running wireless. Obviously, I can't go through the normal setup process because Ubuntu is not connected through Ethernet. So... is there any way to do this with what I've got?

Here's what I'm thinking:
1. Use WinXP SP2 to download drivers, software, anything Ubuntu needs to set wireless up.
2. Transfer to USB stick.
3. Boot Ubuntu, transfer files and proceed to set up wireless as if I had just downloaded the same files straight through LAN.
4. Wireless works in Ubuntu.

Is this a feasible solution? Any limitations/possible problems/good guides? Other solutions?

I would _really_ appreciate any help... please, I can't stand XP anymore. :(

Also, for a long term solution, any advice on a good Ethernet card replacement?

Thanks/danke/grazie/merci/&#35874;&#35874; in advance...

---

### Post by ub52 on 2007-07-14
I too would like a solution to this as I have the exact same system. My ehternet card is working, however access to a wired network connection is limited. I've been booting back and forth between XP and Linux trying to find a solution, but no luck as yet

-ub52

---

### Post by DWRZ on 2007-07-14
Ub52, I think our problems are different as I have no ethernet at all. With ethernet it should be just a matter of download and configure straight from Ubuntu. Sorry this is not more helpful.

---

### Post by compwiz18 on 2007-07-15
Alright.  First you need to download/install ndiswrapper.  ndiswrapper can be downloaded from the site below.  You will need both ndiswrapper-utils and ndiswrapper-common.  Once these are installed, you can try my script again if you want (link in my sig)

ndiswrapper-common: [http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.38-1ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.38-1ubuntu1_all.deb)
ndiswrapper-utils: [http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb)
script: link in sig (you will have to download the script, you may also want to download/print/memorize the instructions)

Download them both, and save them somewhere you can access from Ubuntu (a flash drive, c: on windows), anywhere handy.  Reboot into Ubuntu.  Install both ndiswrapper-utils and ndiswrapper-common, and then run the script.  With some luck, you should be all set :D

---

### Post by DWRZ on 2007-07-16
Thank you, thank you, thank you.

What I needed were the .deb packages as I didn't know how to install from source. With those everything went smooth and I am _finally_ back on Ubuntu!!! Wh00t!!! Everything is running great.

Really impressed by your tutorial and dedication. Really helps us new people out. Can't thank you enough, you have no idea how great it is to be on a functional distro again. :D

---

