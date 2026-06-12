---
title: "Cisco AM10 wifi adapter not working on Ubuntu 20.04"
date: 2020-04-27
forum: Networking &amp; Wireless
---

### Post by vishnumrao on 2020-04-27
I booted up the liveUSB with Ubuntu 20.04 on my desktop with a Cisco AM10 USB wifi adapter plugged in. But looks like the wifi adapter is not detected. 

Its weird since I previously had 18.04 running on this machine, and I was using this AM10 USB adapter. To confirm I also booted a liveUSB with 18.04.1 and it clearly detects the AM10 as a wifi adapter and is able to connect to my wireless network. 

Anyone know if Ubuntu has removed support for this wifi adapter? Anyone any ideas?

---

### Post by vishnumrao on 2020-05-10
Bump. anyone have any insights?

---

### Post by chili555 on 2020-05-10
Please run and post: ```
lsusb
```  ...with the device inserted, of course.

---

### Post by vishnumrao on 2020-05-10
Maybe I should have thought about posting it in the first place. 

```
ubuntu@ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0930:6544 Toshiba Corp. TransMemory-Mini / Kingston DataTraveler 2.0 Stick
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 1307:1169 Transcend Information, Inc. TS2GJF210 JetFlash 210 2GB
Bus 001 Device 005: ID 1307:0169 Transcend Information, Inc. Cisco AM10 USB Hub
Bus 001 Device 009: ID 05ac:12a8 Apple, Inc. iPhone5/5C/5S/6
Bus 001 Device 007: ID 058f:6364 Alcor Micro Corp. AU6477 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 002: ID 05e3:0616 Genesys Logic, Inc. hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 003: ID 0b05:1852 ASUSTek Computer, Inc. 802.11ac NIC
Bus 008 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ubuntu@ubuntu:~$ 
```


Note I also have a Asus [USB-AC68]("https://www.asus.com/us/Networking/USB-AC68/") adapter. I will like to get that working as well.  But thats a separate discussion in itself, because it requried some custom steps on 18.04 as well. But this Cisco AM10 worked out of the box on 18.04.

---

### Post by chili555 on 2020-05-10
> 
0b05:1852 ASUSTek Computer, Inc. 802.11ac NIC
The correct driver is 8814au. Please do:

```
sudo apt update
sudo apt install git dkms
git clone https://github.com/zebulon2/rtl8814au.git
sudo dkms add ./rtl8814au
sudo dkms install rtl8814au/4.3.21
```
Reboot and your USB wireless should now be working.

---

### Post by vishnumrao on 2020-05-10
I haven't installed 20.04 yet. This desktop is cant be wire connected. And both the wireless adaptes that I have are not supported out of the box in 20.04. I haven't installed so far due to another [issue]("https://ubuntuforums.org/showthread.php?t=2442434"). 

Thanks for the help to locate the drivers. On a different system with 18.04, I was using this driver from [github]("https://github.com/nazar-pc/RTL8814AU"). If I install 20.04 I will use your since it seems more current. It talks about "Updated with support for kernels >= 4.14.". 

But back to the original purpose of this thread, how can I get the Cisco AM10 working with Ubuntu 20.04?

---

### Post by chili555 on 2020-05-11
The original question wasn't clear that you needed to install the driver without any working internet access. Sorry if I misunderstood.

The USB or DVD from which you install Ubuntu 20.04 contains the packages build-essential and dkms and their prerequistes. Simply set the DVD as a source in Software and Updates and install them both:

```
sudo apt update
sudo apt install dkms build-essential
```I am not aware of any way to use the USB as a source, although you could tediously drag and drop the deb files and all their dependencies to your desktop and install them:

```
cd ~/Desktop
sudo dpkg -i *.deb
```Then get the zip file from the github site: [https://github.com/zebulon2/rtl8814au/archive/master.zip](https://github.com/zebulon2/rtl8814au/archive/master.zip) Transfer it to your desktop on a USB key or similar and do:

```
cd ~/Desktop
unzip master.zip
sudo dkms add ./rtl8814au-master
sudo dkms install rtl8814au/4.3.21
sudo modprobe 8814au
```

Your wireless should then be working.

---

### Post by vishnumrao on 2020-05-16
Hello there. Its been a busy few days at work. I put this off for the weekend. 

I have tried your instructions. I did not need to copy from another machine. I ended up usb tethering my phone for internet connectivity and download the driver source from github. But unfortunately the zebulon2 driver did not work for me. The machine would hang at a poweroff. 

So I decided to go back to stable 18.04 where both my AM10 and the USB-AC68 work. The driver I use for my USB-AC68 is this one: [https://github.com/nazar-pc/RTL8814AU](https://github.com/nazar-pc/RTL8814AU). Works great. I did not try on 20.04 though. 

For now  I need a stable system for some work. So going to stick to 18.04 for now. But thanks for your efforts. I greatly appreciate your time and effort to help me.

---

