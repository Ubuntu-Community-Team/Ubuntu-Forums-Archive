---
title: "Trouble with modem detection"
date: 2004-11-25
forum: Networking &amp; Wireless
---

### Post by dhamil on 2004-11-25
After reading a review of ubuntu in a linux format magazine floating around work I downloaded 4.10 to give it a go. This is my first time using linux, everything ran smooth until I tried to set up an internet connection.

In the hardware manager it detects there is a modem there but in the gnome networking application it cannot detect it. I only know about the linux file system what I read in the mag but I have no /dev/modem entry if that means anything. 

Not being able to use the internet  is making this new adventure very frustrating. **Please help me kick windows to the curb.** ;p

_Modem:_ Intel 536EP V.92 (that is what ubuntu detects it as)

---

### Post by az on 2004-11-25
Your modem is a software modem.  It needs drivers. 

You can get drivers from the intel website:
[http://linmodems.technion.ac.il/packages/Intel/536/intel-536EP-2.56.76.0.tgz](http://linmodems.technion.ac.il/packages/Intel/536/intel-536EP-2.56.76.0.tgz)

(From the readme)
steps to install
   1. login as ROOT 
   2. extract the archive into a directory with "tar -zxvf <archivename>.tgz"
   3. cd into the directory it created.
   4. Type: make clean
   5. Type: make 536
   6. Type: make install
This will create a /dev/modem device file. This file is used as an interface to 
modem by all applications: minicom, kpppd, efax, etc. Please configure the applications
to use /dev/modem if neccessary.

--
To compile the drivers you will need to install some packages.  Go into synaptic and install build-essential and linux-headers-2.6 (They are on your cd)




-or-

An easier way:

It is reported that most of these modems will work with the sl-modem driver.  You can download the modules here (I compiled them with the afformentioned kernel-headers)

[http://www.vif.com/users/mzajac/sl-modem-modules-2.6.8.1-3-386_2.9.9-1_i386.deb](http://www.vif.com/users/mzajac/sl-modem-modules-2.6.8.1-3-386_2.9.9-1_i386.deb)

You will also need the sl-modem-daemon package.
[http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-daemon_2.9.9-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-daemon_2.9.9-1_i386.deb)

So either you make the intel driver yourself or you download the two packages to a floppy and install them.  



Post back how it went.

---

### Post by dhamil on 2004-11-26
Thank you very much for your quick reply. Nice to see such a supportive community.

I tried the  first solution but after typing "make install" alot of text appears with

unknown distrubution. no boot scripts installed
make: *** [install] Error 1

at the end. There is no /dev/modem after this.

I would love  to try  the other method but I have absolutely no idea what to do with a .deb file. My lackof knowledge astounds even me.

Thanks in advance for any further help.


EDIT: RTFM dhamil! Found a work around in the readme that came with the intel drivers. Thanks for  the help azz. :)

---

### Post by az on 2004-11-26
The second way would be the easier one.

cd to the directory where you put them and

sudo dpkg -i *.deb




I just read your edit!

You are using ubuntu - it is debian.  It is not installing the debian init scripts because it does not know what ubuntu is...   Maybe you could find the workaround and post it.

Also, (if you dare) would you make uninstall (or whatever, RTM) and try the second method.  It would be nice to compare one driver with the other.

i would understand if you just want to stop now that it works...  (It does work, right?)

---

### Post by dhamil on 2004-11-26
Ok, so I tried the .deb files (thanks for telling me how to use them) and they didn't seem to work. Went back to the old way (method 1) and everytime I turn on the computer I have to:


   1.  	insmod -f Intel536.ko

   2. 	hamregistry &

   3.   rm /dev/536ep

   4.   mknod /dev/536ep c 240 1

   5.   ln -s /dev/536ep /dev/modem


before it will work (this is based on whats in the readme). I have 2 questions:

1.) What does this do? O.o

2.) Is there an easier way? (As in can I automate this)

At least it works but I will be damned if it isn't the untidiest feeling doing it this way.  :wink:

---

### Post by az on 2004-11-27
The package provides a script for debian.  Ubuntu is debian, but the package does not know that.  Are you able to find a hack to install it (using the makefile or configure options?)

I will download the package and look at it when I have more time.
Basically, if you add the module name to /etc/modules it will get loaded on boot.  As for creating the device node, it is probably necessary, but maybe not.

Also, I realise the reason why the other way failed is right off the bat, sl-modem-daemon depends on sl-modem-source so you will get an error message when you install them alone from a floppy.

[http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-daemon_2.9.9-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-daemon_2.9.9-1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-source_2.9.9-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-source_2.9.9-1_i386.deb)


Try the two sl-modem packages (daemon and source) by default, it will try to use the GPL alsa driver for the intel chipset) 
sudo  dpkg -i sl-modem*.deb
It will complain about missing dependancies.  (build-essential and so forth)
You then do:
sudo apt-get -f install 
and eveything else needed is found on your cd.


You may need to edit /etc/default/sl-modem-daemon to specify the device if 'auto' fails.

SLMODEMD_DEVICE=hw:0 #(or hw:1depends on your soundcard, I guess)

If it still don't work, download and install the modules (or make them youself...)
[http://www.vif.com/users/mzajac/sl-modem-modules-2.6.8.1-3-386_2.9.9-1_i386.deb](http://www.vif.com/users/mzajac/sl-modem-modules-2.6.8.1-3-386_2.9.9-1_i386.deb)

Then reconfigure sl-modem-daemon to use the slarm modules instead of the snd_intel8x0m module...
sudo dpkg-reconfigure sl-modem-daemon


All that just may be easier than using the intel tarball...
Sorry for the mistake on my part...

---

### Post by dhamil on 2004-11-27
I followed your instructions for getting it going the non-intel tarball way. I made an impressive mess of it and it took me a good hour to get it back the old intel tarball way. I am afraid I may have understated my complete lack of linux knowledge.  :-? 

Finding a hack to install it (using the makefile or configure options?) is beyond me I'm afraid but adding the module name to /etc/modules seems within my grasp. However, I am not sure what the module name is? Is it Intel536? How would I find this out?

Thanks for all your efforts. Sorry I'm not much help but everyones has gotta start somewhere ah.  :wink:

---

