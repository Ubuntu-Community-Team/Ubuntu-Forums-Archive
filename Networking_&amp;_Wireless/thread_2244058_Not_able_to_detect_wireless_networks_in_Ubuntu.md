---
title: "Not able to detect wireless networks in Ubuntu"
date: 2014-09-13
forum: Networking &amp; Wireless
---

### Post by abhijits on 2014-09-13
Hi all,
I've been trying to install Ubuntu on my dell laptop. I already have Windows 8 on this laptop. I created the bootable Ubuntu disk. When I boot from this disk Ubuntu starts up fine but when I click on the networking icon at the top right hand corner of the screen it does not detect any wireless network. However, I am able to connect to the internet using a wired network cable. I am able to detect and connect to my wireless network from windows 8 on the same machine. Any ideas about where the problem may be and how to fix it?

---

### Post by bell1996 on 2014-09-13
You going to need to add drivers for that wireless card. There are a lot of links on how to do that. Just google it or search in this forum (I use the forum a lot).
Please post your network hardware info using this command: lshw -class network

---

### Post by Hadaka on 2014-09-13
Hi, please post the output of..
```
lspci -nn | egrep '0200|0280'
lsmod | grep wl
rfkill list all
```
thanks

---

### Post by abhijits on 2014-09-14
Hi,
Thank you for the quick responses. Below is the information:

lspci -nn | egrep '0200|0280':

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
03:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0036] (rev 01)

lsmod | grep wl:

(No result.)


rfkill list all:

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no










lshw -class network: 

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 07
       serial: b8:2a:72:b4:42:f1
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.36 latency=0 multicast=yes port=MII speed=100Mbit/s
       resources: irq:79 ioport:d000(size=256) memory:fe500000-fe500fff memory:d0800000-d0803fff
  *-network UNCLAIMED
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:fe400000-fe47ffff memory:fe480000-fe48ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

Do let me know what steps to take further. Thanks.

---

### Post by varunendra on 2014-09-14
Hello Abhijit!

It seems you are using an outdated version of Ubuntu, because all the supported versions have the required driver within the kernel.

Please show us the outputs of -
```
uname -mr
lsb_release -d
```

If it is older than 12.04.4, it is highly recommended to download and install either 14.04 or 12.04.4.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by abhijits on 2014-09-14
Hi Varun,
Below is the output:

ubuntu@ubuntu:~$ uname -mr
3.2.0-23-generic x86_64

ubuntu@ubuntu:~$ lsb_release -d
Description:    Ubuntu 12.04 LTS

For some reason, I am not able to boot from a DVD containing Ubuntu 14.04. I get just a blinking cursor when I try to boot from the DVD. So I don't have any choice but to use 12.04 LTS.

---

### Post by varunendra on 2014-09-14
Yes, indeed you have an outdated kernel and release version. Even though 12.04 is still supported (and will be, upto April 2017), its current "Point-Release" is 12.04.4 which contains one of the latest kernels. You have plenty of options, of which I think trying out the 12.04.4 Live DVD (just because you said 14.04 is having issues) in Live mode, and if it works, do a fresh install of it.

Other options that you have are -

**1)** Upgrade your Hardware Enablement Stack manually. Basically it will upgrade you to 12.04.4, with the benefit that your installed programs and settings will be retained, but also with the potential risk of breaking/losing some functionalities.

**2)** Upgrade just your kernel. Easier, and less likely to break anything.

**3)** Install just a newer driver from the backports. Easy enough and safe too. Method is here : [http://ubuntuforums.org/showthread.php?t=2190930&p=12866455#post12866455](http://ubuntuforums.org/showthread.php?t=2190930&p=12866455#post12866455) . As you would notice on the backports package page, the package version suggested in that post doesn't exist there anymore. So try a newer one, and change the package name, directory names in the commands accordingly.

But again, doing a fresh install of 12.04.4 would be best in my opinion.

---

### Post by abhijits on 2014-09-14
How about doing an update to 12.10 through update manager. Would that solve the problem?

---

### Post by varunendra on 2014-09-14
No it won't. Not only 12.10 is dead (was an interim release, with much shorter support life), the kernel it had (3.5 series) didn't have the driver version that started supporting your card. Support for your card, if I remember correctly, was included since kernel 3.8 series.

---

### Post by praseodym on 2014-09-14
I recommend 12.04.5 with kernel 3.11 or 14.04

---

### Post by abhijits on 2014-09-14
Okay, I tried upgrading to 14.04.1 but I got the message "Running the 'unity' desktop environment is not fully supported by your graphics hardware. You will maybe end up in a very slow environment after the upgrade. Our advice is to keep the LTS version for now. For more information see [https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D](https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D) Do you still want to continue with the upgrade?" . So I decided not to go ahead with the upgrade. 
I would like to avoid doing a fresh install of 12.04.4 or 12.04.5 as this would entail downloading a new ISO image, burning it on a DVD and reinstalling the OS again. Is there some way of directly upgrading to 12.04 or 12.05 without having to reinstall the OS? What is my easiest option right now and how to go about doing it?

---

### Post by praseodym on 2014-09-14
Which VGA card is in use?
```

lspci -nnk | grep -iA2 VGA
```

---

### Post by abhijits on 2014-09-15
Hi,
Below are the results:

lspci -nnk | grep -iA2 VGA:

00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Device [1002:9851]
    Subsystem: Dell Device [1028:0658]
00:01.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Device [1002:9840]

---

### Post by praseodym on 2014-09-15
Now run:

```
sudo apt-get install fglrx
```
and reboot

---

### Post by abhijits on 2014-09-15
Hi,
My objective is not really to fix the graphics or video card. This is a secondary objective. My main objective is to fix the wireless networking problem where the wireless networks are not being detected. Can you suggest some solution for that?
> **praseodym said:**
> Now run:

```
sudo apt-get install fglrx
```
and reboot

---

### Post by praseodym on 2014-09-15
Check this command:

```
sudo apt-get -s install --install-recommends linux-generic-lts-trusty linux-image-generic-lts-trusty linux-headers-generic-lts-trusty xserver-xorg-lts-trusty libgl1-mesa-glx-lts-trusty 
```
This will not install it, but checking if its working. If no errors occur, then run it without "-s". Remember the VGA driver afterwards.

---

### Post by abhijits on 2014-09-15
> **praseodym said:**
> Check this command:

```
sudo apt-get -s install --install-recommends linux-generic-lts-trusty linux-image-generic-lts-trusty linux-headers-generic-lts-trusty xserver-xorg-lts-trusty libgl1-mesa-glx-lts-trusty 
```
This will not install it, but checking if its working. If no errors occur, then run it without "-s". Remember the VGA driver afterwards.

praseodym - You are a genius! It worked! Thank you very much!

---

### Post by varunendra on 2014-09-16
Basically, you upgraded your Hardware Enablement Stack which supports your card natively.

If the performance is satisfactory, please mark the thread as [SOLVED] using "Thread Tools" link above the top post. Thanks!

---

### Post by sheldon-corey on 2014-09-17
what was the error code from wallsplash on that 14.04 live install and though this may seem trivial did a md5sum /path/to/iso match the provided one from canonical?   if not re-d/l  the 14.04.x (.1 atm iirc) iso and retry also if you have a machine with an irc client installed (or that gets installed) feel free to visit any of the following freenode channels (also available from SOME web chat clients like [http://kiwiirc.com](http://kiwiirc.com) ) ##linux-wireless ##ubuntu   #ubuntu-wireless ##linux or even on the spot chat server where I personally also live along with Freenode lol....  my guess is that its a efi or gfx issue causing the blinking cursor ...



pls provide current systems output for these cmds please (using "code" tags)

lsmod |grep video 
inxi -SsNGxx   (install if needed  via   sudo apt-get install -y inxi)


Corey   (IRC - Corey84)

---

