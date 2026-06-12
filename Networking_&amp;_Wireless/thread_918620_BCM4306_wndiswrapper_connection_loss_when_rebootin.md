---
title: "BCM4306 w/ndiswrapper connection loss when rebooting..."
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2008-09-13
Hardy fresh install


I have a working connection with Ndiswrapper, with WPA (using XP 32bit bcmwl5.inf).


My problem...I lose the connection after a reboot. Seems like a problem with the "ssb" module loading, rather than "ndiswrapper".


To get the wlan0 connection up (from "network down") I run these in order....

 
sudo rmmod b43

sudo rmmod b44

sudo rmmod b43legacy #this step added Apr 27 2008

sudo rmmod ssb

sudo rmmod ndiswrapper

sudo modprobe ndiswrapper

sudo modprobe ssb

sudo modprobe b44 #this step added May 1 2008


echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper 

sudo /etc/init.d/networking restart


After the above, I now have my internet up!!! 


According to lshw -C network...
Seems like a problem with "ssb" loading as my BCM4306 module at start, rather than "ndiswrapper". After running the above commands, the module shows as "ndiswrapper", therefor a simple network restart takes car of business.



So, how can I get Ndiswrapper, not ssb, to stick to my Broadcom interface???

---

### Post by DapperMe17 on 2008-10-06
Anyone? 

Half the battle is done!!! 

How about the "ssb" loading issue?

---

### Post by Ayuthia on 2008-10-06
To start things off, do you need the b44 module?  To figure this out, you need to check lshw -C network.  If your wired card is using the b44 module, you will need it (it should be something like a Broadcom 44xx series card).  

The b44 module does need to have the ssb module, but the ssb module has to be loaded after ndiswrapper or else it(ssb) will take hold of your wirless device.  So if you don't use the b44 module, the script is not necessary.  However if you do need the b44 module, you will have to use the script to make it work.  In my opinion, instead of using the script, it would be better to add the information in /etc/modprobe.d/blacklist.  The howto for this is found [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Version%200.3").  I prefer this route because the steps are only run when you load the ndiswrapper module.  However the the route that you are using will always load the script even if you remove ndiswrapper.

If you don't need to b44 module, you should just need to blacklist the b43 and ssb modules in /etc/modprobe.d/blacklist and then run:
```
sudo update-initramfs -u
```

Most likely what is happening is that you have already blacklisted b43 and ssb but it is still coming back when you reboot.  The initramfs has not been updated so it still sees that it needs to load the b43 and/or ssb modules.  The update should fix this problem.

From the man pages of update-initramfs:
```
The  initramfs  is  a gzipped cpio archive.  At boot time, the kernel unpacks that archive into RAM disk, mounts and uses it as initial root file system. All finding of the root  device  happens  in  this  early userspace.
```
If you take a look at the gzipped file, you will see that it has its own set of blacklist files.  My understanding is that update-initramfs updates that blacklist file.

---

### Post by DapperMe17 on 2008-10-07
Thanks for your reply!

I've since solved the "ssb" issue, with a small script. Absolutely, it was an ordering issue & I also found very little need to blacklist anything. 

Too bad it takes a rocket scientist to figure this card out, but what a great way to learn something about Linux...even at the expense of a little hairloss!  

You can see my tutorial at...

[http://ubuntuforums.org/showthread.php?t=939658](http://ubuntuforums.org/showthread.php?t=939658)

:popcorn:

---

### Post by zeddock on 2008-11-07
> **DapperMe17 said:**
> Thanks for your reply!

I've since solved the "ssb" issue, with a small script. Absolutely, it was an ordering issue & I also found very little need to blacklist anything. 

Too bad it takes a rocket scientist to figure this card out, but what a great way to learn something about Linux...even at the expense of a little hairloss!  

You can see my tutorial at...

[http://ubuntuforums.org/showthread.php?t=939658](http://ubuntuforums.org/showthread.php?t=939658)

:popcorn:


I may be having same problem but not as skilled as you. Also, need to keep this system working for my son's schooling.

I am on the 8.10 release. Confirmed 4306/version 3.
Seems to work after HARD power off... at least sometimes.

Noted your script includes things for WPA, which will not be a part of our home network. How can I implement a fix without WPA then please?

Thanx for you'r work on this!

zeddock

---

### Post by DapperMe17 on 2008-11-08
Glad it worked for you...somewhat

Just skip steps 18-20. 

It will be easy without WPA encryption.

You should also just be able to use Network Manager, or WICD, to set your internet connection preferences, rather than manually editing the interfaces file.

I have the same instructions over a Linux Mint. Their interface is easier on the eyes!
[http://linuxmint.com/forum/viewtopic.php?f=53&t=17688](http://linuxmint.com/forum/viewtopic.php?f=53&t=17688)

---

