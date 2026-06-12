---
title: "Netgear A6100 USB mini adapter"
date: 2014-07-22
forum: Networking &amp; Wireless
---

### Post by JP_Keenan on 2014-07-22
Hello,
I'm brand new to Ubuntu and testing it on an older machine to see if I want to install it instead of windows on some other computers.
I am trying to install my Netgear A6100 USB mini adapter and can't get it working, I've read through some pages so I hope I am providing the right information to start people off helping me
```
jpkeenan@test1:~$ lsusb
Bus 001 Device 006: ID 0846:9052 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0461:0010 Primax Electronics, Ltd HP Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```

Thanks is advance and am looking forward to learning how to solve this

JP

---

### Post by Hadaka on 2014-07-22
Hi, your device...
Bus 001 Device 006: ID 0846:9052 NetGear, Inc. 

led me to.
[http://forum.ubuntu-fr.org/viewtopic.php?id=1572411](http://forum.ubuntu-fr.org/viewtopic.php?id=1572411)
and this led to..
[https://wikidevi.com/wiki/Netgear_A6100](https://wikidevi.com/wiki/Netgear_A6100)
Which shows your device 0846:9052 NetGear
has the rtl8812au chip
and finally the chilli555 fix can be found,,
Please first do..
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
```
Then go here ..
[http://askubuntu.com/questions/368015/problem-with-building-compiling-a-driver-for-edimax-wireless-adapter-ew-7822uac](http://askubuntu.com/questions/368015/problem-with-building-compiling-a-driver-for-edimax-wireless-adapter-ew-7822uac)

---

### Post by JeQhdMD on 2014-07-23
If you don't want "relatively" complex drivers to "build" . . . just get a plug and play wireless adapter.  TP-Link 822-N, or 722N or Panda Ultra 150 b/g/n are 3 proven ones.  Just search on amazon or similar tech site.  The Panda device is great for laptops as it's super small.

---

### Post by JP_Keenan on 2014-07-23
Thanks Hadaka.
That worked like a charm. 


Now where do I find that handy solved button....

---

### Post by Bucky Ball on 2014-07-23
Follow the second link in my signature for solved button. Enjoy the OS and the learning curve. ;)

Take note of this part from the chili's original fix on that link:

> Whenever a later kernel version, also known as linux image is installed by Update Manager, after you reboot, you will need to re-compile the driver:

```
cd Downloads/rtl8812AU_8821AU_linux-master
make clean
make
sudo make install
sudo modprobe 8812au
```

(The above presumes the driver you downloaded is in the Downloads folder.) Meaning that if you do an update and the kernel is updated you may need to run the above to get things working again, so keep that in a safe place. With any luck the driver will be included in the kernel before long so you don't need to do this.

---

### Post by JP_Keenan on 2014-07-23
Great,
1 more quick question, how often is a new kernel released and is it generally a big deal, or will I just wake up and my wifi will have stopped working?

---

### Post by Hadaka on 2014-07-23
Hi, Glad that worked for you !
yeah, pretty much, if you have your updates
on auto mode,,thats what will happen. so be
sure to make a file with the reload commands
that bucky made mention of in chilli's guide.
to mark solved  go here
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by laymansnerd on 2015-02-11
YES!!! This just worked for me too! I'm running Linux Mint 17 and had no problems!! Mind if I publish these instructions on my blog?

---

