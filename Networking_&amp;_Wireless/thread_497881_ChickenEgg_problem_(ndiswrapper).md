---
title: "Chicken/Egg problem (ndiswrapper)"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by hauger on 2007-07-10
Okay, I'm not exactly a noob with Linux, but I am a noob when it comes to Wireless Laptops on Linux.  As far as I can tell, 7.04 has installed nicely and correctly identified my wireless (I think anyways, it's identified as a "Broadcom Corp Dell Wireless 1390 WLAN Mini-PCI Card" which is odd given that I'm using a HP Pavilion DV2404 laptop).

Anyways, from what I can gleam from around the net is to get the indentified hardware running, I need to run ndiswrapper.  Odd.  Why would this be odd?  Well, I have access pretty much only to wireless (long story), meaning I don't have the ability to apt-get ndiswrapper and install it since I need it to run the wireless.

So, what do I do?  Is there a way around this?

---

### Post by spd106 on 2007-07-10
First try the bcm43xx way.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/)
[http://linuxwireless.org/en/users/Drivers/bcm43xx](http://linuxwireless.org/en/users/Drivers/bcm43xx)

Download this driver [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o) and this package [http://packages.ubuntu.com/feisty/utils/bcm43xx-fwcutter](http://packages.ubuntu.com/feisty/utils/bcm43xx-fwcutter)

Then install the bcm43xx-fwcutter by double clicking on it or use this command.
```
sudo dpkg -i bcm43xx-fwcutter_006-1_i386.deb

```

Now extract the firmware from the driver straight into the correct folder with this command.
```
sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r` wl_apsta.o
```

If that doesn't work then try ndiswrapper.
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by kevdog on 2007-07-10
Yea installing ndiswrapper when you dont have an internet connection can be a b**ch!

Here is how to do it, its not very hard but you do need another computer with an internet connection and a trusty USB stick for the file transfer

Get ready to compile the source ndiswrapper files, all commands typed at command prompt:
1. Stick ubuntu installation cd into drive, wait for it to become ready
2. sudo apt-cdrom add
3. sudo aptitude update
4. sudo aptitude install build-essential

cd ~
mkdir ndiswrapper
cd ndiswrapper

Great, now download the ndiswrapper sources (ndiswrapper-1.47.tar.gz) and make the transfer to via USB stick. Place the tar.gz file in ~/ndiswrapper. [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

Extract the archive
tar -zxvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47

Lets compile and install the ndiswrapper utility:
make distclean
make
sudo make install

Ok to see if everything was done correctly
ndiswrapper -v

ndiswrapper installed -- now you just need to install the driver!

---

### Post by hauger on 2007-07-11
Thanks for all the replys....one of the main reasons I love using linux is the community support.

Alright, I found an "easy" solution, I've gone to a friends and pluged a wired connection in.  That's the good news.  I've apt-get'ed and installed ndiswrapper-common/utils, and the graphical front end (although that refuses to start, no real issue though, I'm comfortable in the command line).  I found the wireless chipset on the NDISwrapper site.  It's claims no problems and even provides a link to the driver.

Here in lies the problem.

Given the driver is a windows driver, HP has ever so nicely provided a nicely packaged, consumer friendly .exe file.  All the ndiswrapper install docs I find need this file unwrapped, providing .ini and .sys components.  

Never mind, I just ran the file in Vista and what'd'ya know, it self extracts to it's sub components.  Wish me luck installing it.

---

### Post by tjduavis on 2007-09-15
Hauger... how did that installation go? Were you able to get your wireless working on the HP Paviilion dv2404? 

I have recently purchased that laptop and I am having troubles getting the wireless to work.

Could you please assist me?

---

