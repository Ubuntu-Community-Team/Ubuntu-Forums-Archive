---
title: "3Com 3CRWE154g72 Not Working under Ubuntu 6.10"
date: 2006-12-11
forum: Networking &amp; Wireless
---

### Post by Flumuxed on 2006-12-11
I had the version 2 PCMCIA card 3CRWE154G72 set up and working using ndiswrapper under 6.06 Dapper.  Having recently installed 6.10 Edgy, the damn thing no longer works and having spent days googling and searching the forums I've failed to find any answers (at least non that work!!).  As a last resort, from the various attempts to make it work, I've wiped the hard drive and reinstalled 6.10.  Could anybody offer some guidance on getting this up and running?


Thanks

---

### Post by FrodoB on 2006-12-11
Getting the latest version of ndiswrapper which is up to 1.31 and compiling from source has done wonders for me in the past:

[http://sourceforge.net/projects/ndiswrapper](http://sourceforge.net/projects/ndiswrapper)

---

### Post by FrodoB on 2006-12-11
DO NOT INSTALL THE OLD NDISWRAPPER THAT IS IN THE EDGY REPOSITORY BEFORE DOING THIS.

Prepare the Linux build environment

You will need to install the essential build files to compile the driver:

user@ubuntu:~$ sudo apt-get update 
user@ubuntu:~$ sudo apt-get install build-essential

Install the correct headers for your version of Ubuntu: (don't worry if it tells you that yours are up to date.)

user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r` 
user@ubuntu:~$ sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build



Download the latest version of the ndiswrapper driver

Download the latest version of the ndiswrapper from sourceforge:

 [http://sourceforge.net/projects/ndiswrapper](http://sourceforge.net/projects/ndiswrapper)


It should be noted that as the ndiswrapper is further developed it could be the case that any particular NDIS driver compatibility could become broken for awhile.


Extract and install the ndiswrapper using make

Using tar extract the archived driver and change directories into the build area.

user@ubuntu:~$ tar xvzf ndiswrapper-1.31.tar.gz 
user@ubuntu:~$ cd ndiswrapper-1.31

Make the driver with the commands "make distclean", "make", and "make install":

user@ubuntu:~/ndiswrapper-1.31$ make distclean
user@ubuntu:~/ndiswrapper-1.31$ make
user@ubuntu:~/ndiswrapper-1.31$ sudo make install

The make process will take several minutes to complete.

You can now check the ndiswrapper to see that it is installed correctly. You should see something similar to:

user@ubuntu:~/ndiswrapper-1.31$ ndiswrapper -v
utils version: 1.9
driver version:        1.31
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1

Now go ahead and install your NDIS driver files as normal.

---

### Post by Flumuxed on 2006-12-12
FrodoB, thanks for that - your instructions were really really clear and easy to follow.  Unfortunately, being the newb that I am, I'm now having difficulty with installing the driver with Ndiswrapper.

So far, I've blacklisted the Prism54 driver and run a ndiswrapper -i 3c154g72.inf.  Now when I do ndiswrapper -l, I get the following:

mad@mad-laptop:~$ ndiswrapper -l
3c154g72 : driver installed
        device (10B7:6001) present (alternate driver: prism54

by doing iwconfig, I get:

mad@mad-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      NOT READY!  ESSID:"Flumuxed"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=31 dBm   Sensitivity=0/200  
          Retry min limit:0   RTS thr=0 B   Fragment thr=0 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I set the ESSID by using: 'iwconfig eth1 essid Flumuxed'

Currently neither of the two lights on the PCMCIA card are lit, not even flashing.   Also, with regards my router, it is set not to broadcast ESSID and it is using WPA encryption.

If you could provide some guidance it would be much appreciated!!

Thanks

---

### Post by FrodoB on 2006-12-12
I don't have a prism54 device to check with.  Run lsmod and look for the complete name of the driver and blacklist that. Hopefully it is just something minor.

---

### Post by Flumuxed on 2006-12-15
Prism54 is the correct driver to blacklist but unfortunately, even having blacklisted it, it hasn't got the card working.........

---

### Post by FrodoB on 2006-12-15
Search the ndiswrapper compatibility list for success reports and use their drivers:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)


Good luck, I'm on vacation for a while.

---

