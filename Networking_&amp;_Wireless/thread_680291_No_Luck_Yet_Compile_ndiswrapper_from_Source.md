---
title: "No Luck Yet? Compile ndiswrapper from Source"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by buccaneere on 2008-01-27
[HTML]chuckhp@chuckhp-laptop:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf
couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper line 219.
chuckhp@chuckhp-laptop:~/bcm43xx$ 
[/HTML]

What's wrong here?

Help?

---

### Post by kevdog on 2008-01-27
Ok, you have to make sure the bcmwl5.inf file and corresponding .sys file (lsbcmds.sys -- this is just a guess) are in the same directory where you are issuing the command.

---

### Post by buccaneere on 2008-01-27
> **kevdog said:**
> Ok, you have to make sure the bcmwl5.inf file and corresponding .sys file (lsbcmds.sys -- this is just a guess) are in the same directory where you are issuing the command.

Makes sense, but at what point in this sequence do I change directories?
-------------------------------------------------------------
Remove Stock ndiswrapper

sudo modprobe -r ndiswrapper
sudo ndiswrapper -r bcmwl5
sudo apt-get remove ndiswrapper-utils 
sudo rm -r /etc/ndiswrapper/ 
sudo rm -r /etc/modprobe.d/ndiswrapper

--------------------------------------------------------

Compile and Install New ndiswrapper

    *

      Nov 29, 2007: Instructions now point to newly-released ndiswrapper version 1.50
    *

      Dec 09, 2007: Instructions now point to newly-released ndiswrapper version 1.51

sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
mkdir -p ~/bcm43xx/ndiswrapper; cd ~/bcm43xx/ndiswrapper
sudo wget [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.51.tar.gz](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.51.tar.gz) -Ondiswrapper.tar.gz
tar xvzf ndiswrapper.tar.gz
cd ndiswrapper*
make distclean
make
sudo make install


-----------------------------------------------------------


Redo Some Steps That Were Undone by ndiswrapper Compilation/Installation

cd ~/bcm43xx **[COLOR="Red"]<--- should I not have changed directory here???[/COLOR]**
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo modprobe ndiswrapper
sudo ndiswrapper -m

---

### Post by kevdog on 2008-01-27
Those directories you mentioned are kind of strange.  The bcm43xx driver is totally different (and the anti-solution for ndiswrapper with broadcom chipsets).  

The particularly directory you are in doesnt matter.  You only need to go into the directories where your windows xp drivers are located for your broadcom card -- specifically the directory where your bcmwl5.inf and xxxxxx.sys file are located.  This could be in any directory.

---

