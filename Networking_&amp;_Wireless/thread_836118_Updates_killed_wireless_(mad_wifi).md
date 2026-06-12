---
title: "Updates killed wireless (mad wifi)"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by Midwest-Linux on 2008-06-21
I have Hardy 8.04 on my Compaq HP 700 laptop. I finally got the Atheros 5007 wireless working the other day. I saw there was updates to be installed. There were 187 updates, I allowed the updates and installation and then rebooted. And the wireless (mad wi-fi) stopped working. 

 So I went back to the terminal and re did the script. 

sudo apt-get install build-essential

wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

tar xfz madwifi-ng-r2756+ar5007.tar.gz

cd madwifi-ng-r2756+ar5007

sudo make 

sudo make install

sudo modprobe ath_pci

sudo reboot


 It would not install, I checked and the mad wifi site is down. Is there another script I can use from another site not connected to Mad Wi-Fi ? Or do I need to wait for the site to come back up?


So just a word of warning that Updates can kill the wireless. Hopefully it can be fixed and I'll try to get back later if I get it back up and running. Earlier (before the updates) I had some problems with gDesklets freezing and had to reboot to get out of Hardy and then remove the gDesklets. Hopefully the two are not related...or maybe they are?

---

### Post by flyinggreg on 2008-06-21
I know this post won't really help you...sorry...but, the updates are killing networking in general it seems.  I have a wired connection and ran an update and lost all networking capability.  I have to run windoze to get on the internet right now - have another post asking for help.  Seems like when you update the kernel, it's killing the network connection.  Hopefully someone will submit the course of action to reconnect for us.

---

### Post by daRealScanMan on 2008-06-21
The wifi modules are related to the kernel - so if you upgrade the kernel they need to be rebuilt.

See my post:  [http://ubuntuforums.org/showpost.php?p=5175481&postcount=134](http://ubuntuforums.org/showpost.php?p=5175481&postcount=134)

The madwifi site was down but it's up now.  Also, you might consider using 3366 module.

[http://snapshots.madwifi.org/special/madwifi-ng-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r3366+ar5007.tar.gz)

---

### Post by Midwest-Linux on 2008-06-21
I solved the problem (even when madwifi.org was down). I started another thread with the solution. [http://ubuntuforums.org/showthread.php?t=836177](http://ubuntuforums.org/showthread.php?t=836177)




Moderators please delete this thread. Thanks

---

