---
title: "Make won't build my WLAN driver!"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by SunshineSmile on 2006-11-18
I follow [these instructions]("http://www.ubuntuforums.org/showthread.php?t=106328") to install my USB Wlan adapter, but I get the following feedback:

make

***no rule to make target 'modules'. Stop.

rt2570.ko failed to build

Anybody have a clue what might be wrong?

uname-r
2.6.12-9-386
I have build-essential installed
I downloaded and installed kernel headers using the command:
sudo apt-get install linux-headers-2.6.12-9-386

It still doesn't work. I so need to get my wireless up and running..

---

### Post by huygens on 2006-11-18
Where did you get the rt2570-1.1.0-b2.tar.gz that you use for compiling?
You can go on this page to download the latest version of the driver: [http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)

If you download the file rt2570-1.1.0-b2.tar.gz from the link I mention. Then the installation instruction would be (I assume that you have downloaded the file to /tmp and that you are on Ubuntu 6.10 Edgy Eft):
```
cd /tmp
tar zxf rt2570-1.1.0-b2.tar.gz
cd rt2570-1.1.0-b2/Modules
make
sudo make install
```So it is installed, now you need to "remove" the old driver. Type the following:
```
sudo modprobe -r rt2570
sudo cp /lib/modules/`uname -r`/extra/rt2570.ko /lib/modules/`uname -r`/kernel/drivers/usb/net/rt2570/
```Now you can load the driver:
```
sudo modprobe rt2570
```Modify the /et/network/interfaces as suggested in the post you used before. And you should be done.

Huygens

---

### Post by SunshineSmile on 2006-11-18
I am actually on the Breezy, cuz I had some trouble with the video input signals with the Edgy Eft.

Anyway, I have this feeling the driver ain't the problem. Because I am using the rt2750-1.1.0-b2.tar.gz, and it is on my desktop.

Problem is that when I am in the Module folder, typing make doesn't work for me!

---

### Post by huygens on 2006-11-19
> **SunshineSmile said:**
> Problem is that when I am in the Module folder, typing make doesn't work for me!

Could you send the output (complete) when you type 'make' and could you attached the Makefile file?

Huygens

---

### Post by NetworkGuy on 2006-11-19
Have you installed the build-essentials package from Synaptic?

---

### Post by huygens on 2006-11-19
> **NetworkGuy said:**
> Have you installed the build-essentials package from Synaptic?

He said so in his original e-mail:
> **SunshineSmile said:**
>  I have build-essential installed
I downloaded and installed kernel headers using the command:
sudo apt-get install linux-headers-2.6.12-9-386

---

