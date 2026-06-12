---
title: "Belkin PCMCIA driver install problem"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by Bastun on 2009-03-15
Hi - I have never used a Unix OS before. I have installed Ubuntu 8.10 on a laptop. There is a Belkin PCMCIA F5D7010 attached but the new OS does not appear to have drivers for it. 
Following some online advice I downloaded the relevant Ubuntu driver for the card, a ZIP Broadcom_80211g_3_20_23_0.zip   and unzipped it to a folder on the Ubuntu box. I can see the .inf file bcmwl5.inf there.

The problem I am having now is in installing this driver. I downloaded UbuntuPocketGuide which advises checking if ndiswrapper is in the system.

After running:
$find /lib/modules/$(uname -r) -name "*ndiswrapper*"

...I get what appears to be conflicting info cos I get a path ending in .../ndiswrapper.ko..as follows\\\;
pete@pete-laptop:~$ find /lib/modules/$(uname -r) -name "*ndiswrapper*"
/lib/modules/2.6.27-7-generic/kernel/ubuntu/ndiswrapper
/lib/modules/2.6.27-7-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko

..which suggests that it is there, but...
$ ndiswrapper
...returns...
pete@pete-laptop:~$ ndiswrapper
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
pete@pete-laptop:~$ sudo apt-get install ndiswrapper-common
[sudo] password for pete: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-common
pete@pete-laptop:~$ 



Looking at the above, can anyone advise me if I have this ndiswrapper and basically, how I go about getting the Belkin PCMCIA to see the wireless network?

Cheers,

Bastun

---

### Post by taurus on 2009-03-15
Is your laptop even connected to the net?

---

### Post by Bastun on 2009-03-15
No!!!! Thats the problem! The network pcmcia is not seeing any networks! When Window XP was installed then the wireless network was available!!!!! I have now downloaded the supposedly correct drivers (via another box) and copied them across.

---

### Post by taurus on 2009-03-15
If your laptop is not connected to the net, no need to run **sudo apt-get install ndiswrapper-common** because that won't work.  You have to download the ndiswrapper-common.deb and install it by hand (or double-click it).

---

### Post by Bastun on 2009-03-16
I Have downloaded and have available on a USB-stick ndiswrapper-common_1.52-1ubuntu1_all.deb AND  ndiswrapper-utils-1.9_1.52-1ubuntu1_i386.deb. Can I confirm with you that I dont need to install these in any particular folder and then run 
$ sudo apt-get install ndiswrapper-common

...rather I can just double-click ndiswrapper-common_1.52-1ubuntu1_all.deb
...which will then install this "ndiswrapper" application after which I can use this to install the driver for the Belkin PCMCIA?

---

### Post by taurus on 2009-03-16
That's right.  Either double-click it or through a terminal.

```
sudo dpkg -i ndiswrapper-common_1.52-1ubuntu1_all.deb
```

---

