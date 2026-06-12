---
title: "How to get madwifi source"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by PaulFXH on 2007-10-14
I'm using a new MacBook (C2D, 2.16 GHz) with three Linux OSes installed (Ubuntu Feisty, Sidux 2007-3 and OpenSUSE).
Wireless works fine on the first two OSes (as well as in OSX) but I'm having big trouble in OpenSUSE (OK, I know this is a Ubuntu forum but in my view there's a lot more knowledge here than in other forums :grin:).
My intention is to build the madwifi drivers based on my kernel (2.6.18.2-34-default) but when I try to get the sourec code from
```
svn checkout http://svn.madwifi.org/trunk madwifi
```
I get this message
```
svn: URL 'http://svn.madwifi.org/trunk' doesn't exist
```
What alternatives exist for me?

Thanks
Paul

---

### Post by kevdog on 2007-10-14
I think it is the following:

```
svn co http://svn.madwifi.org/madwifi/trunk madwifi
```

---

### Post by PaulFXH on 2007-10-14
Thanks kevdog
That works perfectly.
Now to see if I can get this driver actually built and working but at least I'm over the first obstacle.

---

### Post by kevdog on 2007-10-14
I just did it yesterday. 

make 
sudo make install
sudo modprobe ath_pci
sudo ifconfig ath0 up

Also take down anywired connection if you have any
sudo ifconfig eth0 down

That should make the card up and ready to connect.  Either connect manually or through Network Manager/WICD should be all there is to it!  Dont even need to reboot!

---

### Post by PaulFXH on 2007-10-14
OK, didn't take me long to reach the next problem.
Here it is: when I download all the stuff I need (based on this [guide]("http://www.gareth.fiford.com/index.php?m=08&y=07&entry=entry070828-220320")) and then type "make clean" I get this
```
Makefile.inc:91: *** KERNELCONF: /lib/modules/2.6.18.2-34-default/build/.config does not exist..  Stop.
``` 
Indeed, although /lib/modules/2.6.18.2-34-default/build exists, it doesn't contain any .config file.
Any ideas what I should do next?

---

### Post by kevdog on 2007-10-14
Forget the make clean statement.  You just downloaded it -- its never been built before -- there is nothing to clean.

---

### Post by PaulFXH on 2007-10-14
Yes, but I get the exact same error using just "make".

---

### Post by kevdog on 2007-10-14
Did you install the build-essential package along with the linux headers for your kernel??

sudo aptitude install linux-headers-`uname -r`

---

### Post by PaulFXH on 2007-10-14
Actually, no.
I tried to install build-essential but it didn't seem to be available in the OpenSUSE repository. At least in the ones I was using.
But, yeah, I need to get all that stuff installed before complaining any further.
Thanks for the reminder.

---

### Post by kevdog on 2007-10-14
Google around and see what actually files are in the build essential package and then you could just install them individually. You definitely need the header files however.  I know it seems like kind of a pain, but it shouldnt take you all that long to do.

---

### Post by PaulFXH on 2007-10-14
OK, I eventually found that what I needed were the gcc++  and kernel sources packages.
Then everything went fine with the compilation.
Nevertheless, still can't get wireless to work in OpenSUSE.
But, one step at a time, I guess. It just wouldn't be fun if it were too easy.
Thanks for all your help.

---

