---
title: "WIFI problems on Fujitsu Amilo Li2727"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by foo-monger on 2008-10-24
Hello, I hope someone can help me with this problem. 
I have just got a Fujitsu Amilo Li2727 laptop which is running Vista. I know its not the best spec and would like to run Ubuntu as I think that it would run faster using this OS. 
I have managed to install everything and the wizard recognizes my wifi card but I cant turn on wifi reception. In windows wifi is turned on by pressing fn + f1. Im a total noob in linux and need leading through this by the nose please. I hope someone can help me. 

Thanks in anticipation.

---

### Post by Fuzis on 2009-10-29
Hi there, which version of Ubuntu are you using? The wifi activation is greatly different depending on whether you're using Jaunty/Intrepid or Karmic.

If you're using Karmic, her'es the setup : 

If you had madwifi installed, check if ath5k is not blacklisted in /etc/init/madwifi.conf. If so, comment this line.
Normally, the ath5k driver - that works for your wifi card - should be installed with karmic . You can verify that this driver is installed by typing
  ifconfig
and looking for a device called wlan0 . If you have it, jump to the end of this post to switch the wifi on. If you don't have it, first try a simple
  sudo modprobe ath5k

Again, check your devices using ifconfig. If that doesn't work or if youhave an error message saying that ath5k doesn't exist on your system you'll have to install it.
The easier way is to install the modules of the ubuntu CD : 
   sudo apt-get install linux-backports-modules-karmic

If that doesn't work neither, you can build the driver from the compat-wireless package found here :  [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download) . Again, it's pretty easy : download the tarball "compat-wireless-version.tar.bz2" , uncompress it from the folder where you downloaded it : 
   tar -xvf compat-wireless-version.tar.bz2

Enter the folder compat-wireless-version and run the configuration script from there : 
   ./scripts/driver-select ath5k

Then, build the driver (make) and install it (sudo make install). 
When it's installed, you can load the driver whether using
   sudo athload ath5k
or
   sudo modprobe ath5k

Normally, your wifi card should be recognized by your system (it appears in ifconfig and as a wireless device in iwconfig).


To switch on the card, just type

sudo modprobe acer-wmi

Your DEL turns green, and the wifi should be working by now.

---

### Post by foo-monger on 2009-11-02
Hi,

Thanks for the reply.  Im really new to linux, can you go explain what I need to type step by step please?

Thank you

---

### Post by Fuzis on 2009-11-03
Ok, so step by step.

First, open your terminal (Kickoff > Applications > System > Konsole) and log into root by typing 

   sudo -s

You'll have to enter your password after that. You'll be logged into root and your prompt changes from $ to # .

To enable the wifi you first need the correct drivers. The wifi card on your amilo li2727 needs ath5k (it's an atheros chipset), which is normally provided with Karmic. To check if your wifi card is recignized as such, type

  ifconfig

There should be three devices : l0, eth0 and wlan0. If wlan0 doen't appear, that means you don't have the correct drivers.
You should get them by typing 

   apt-get install linux-backports-modules-karmic

and then (maybe optional)

  sudo modprobe ath5k 

Than again, look for you wifi card with *ifconfig*, it should appear now. If not, you'll need to install ath5k drivers from sources but I'll assume this method is enough. Post again if you have any problems.


Once your wifi card is recognized by your system, you have to switch it on. On a Windows system, you can do that with the combination "Fcn+F1" but that won't work on Linux. We'll use the acer-wmi module to take care of this. 
In your terminal, type

   modprobe acer-wmi 

and your wifi led should turn green, indicating it's switched on. To check if your wifi card is actually working go to System configuration > Network configuration , the "Wireless" thumbnail should be accessible. Click "Add",  "Scan networks" (or something like this). If your scan doesn't show any results, that means you still have some issues. If you can find wifi networks, configure yours and that should work now. 

If your connection works, you may want to switch on your wifi card automatically when your system boots. To do so, type 

   touch /etc/modules

then

   kate /etc/modules

and add the line

   acer-wmi.

---

### Post by foo-monger on 2009-11-03
Thank you so much.  Ive managed to get the wifi up and running.  I cant get it to turn on from boot but Im just glad to be back on line.

Thanks again,

Ben.

---

### Post by Fuzis on 2009-11-04
Neat!

You can try another way to switch your wifi card on boot : in terminal, as root, type

   touch /etc/rc2.d/S19Wifi

then

  kate /etc/rc2.d/S19Wifi

and add
```

   #! /bin/sh

   modprobe acer-wmi
```That's what I did on mine and it actually works.

---

### Post by Rankin1 on 2011-07-06
Hey just wondering if anyone could update the terminal commands for the new Ubuntu 11.04? sorry linux newbie.

---

