---
title: "Installing a Belkin Wireless G F5D7010 Ver 7000uk"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by ThomasMarkas on 2008-02-20
Over the weekend I purchased a PCMCIA wifi card for my laptop. The previous one being borrowed permanently.  Having used Belkin F5D7010 Wireless G cards before and they normally working straight out the box. To my surprise the "ver 7000uk" did not.

I installed on my Toshiba Satellite 3000 running Ubuntu 7.10.

Oh well, no problem we would  use ndiswrapper. ndiswrapper and the supplied XP driver. To my continued surprise this did not work, but everything looked ok. Baffled I looked for guidance. I come to the conclusion that the version of ndiswrapper in Gutsy needed upgrading and after doing this and then installing the XP driver everything worked fine. 

Below is a summary of the steps I took to make my wifi pcmcia card work. There are other articles on how to do this on this and you may find them more suited to you. However, I post here as it may be useful to someone.

- From [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/) downloaded  ndiswrapper-1.52.tar.gz onto desktop.

- Extracted the tar.gz file and this gave me a folder on my desktop called ndiswrapper-1.52.

- From the supplied driver Cd copied the XP driver folder to the desktop. This contained 3 files blkwgnv7.cat  BLKWGNv7.inf  BLKWGNv7.sys. 

- In a terminal window the following commands installed the new version of ndiswrapper and the XP driver. Note the directory into which you extract the ndiswrapper will be different.

cd /home/mark/Desktop/ndiswrapper-1.52

sudo apt-get install build-essential linux-headers- uname -r
sudo make uninstall
sudo make
sudo make install


cd /home/mark/Desktop/WINXPDriverFromCD

sudo ndiswrapper -i BLKWGNv7.inf
sudo ndiswrapper -m

cd /etc
sudo gedit modules

- In the modules file I added ndiswrapper at the end of the "modules" file so it would be loaded at start up. See below for output of my copy of modules after modification.

- Then I rebooted the machine and hey presto, the card works.

- Below is my copy of modules with ndiswrapper added to the end to load it at startup time.

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
fuse
ndiswrapper
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

---

