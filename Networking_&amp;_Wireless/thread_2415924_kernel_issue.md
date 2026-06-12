---
title: "kernel issue"
date: 2019-04-02
forum: Networking &amp; Wireless
---

### Post by j3984 on 2019-04-02
is there now or will there be soon an iso for Ubuntu that has the BCM wifi driver in the live session files so you dont have to download it everytime  you do a live session?
this is a major pita. Needs to be fixed.

---

### Post by chili555 on 2019-04-03
In order to be labeled Open Source and therefore subject to the GPL, the Ubuntu iso must contain no proprietary software. Unfortunately, Broadcom consider its STA driver and its firmware as proprietary and subject to license restrictions and not the GPL. Therefore, Ubuntu, who wish to remain free and open source, may not include any proprietary software in its iso.

Obviously, if we the end users wish to add proprietary software to our systems, we are free to do so. 

I don’t believe the Broadcom software is going to be included any time soon.

---

### Post by kc1di on 2019-04-03
+1 to what chili555 said.  But you should know that the broadcom drivers are included on the install .iso they are just not installed in many cases you can install them from the usb/Dvd.  In the live session all you need to do is go to a terminal and type```
sudo apt install bcmwl-kernel-source
``` this will load the driver. 
and it should work for you.  (**Note:** b43 firmware was also included and can be installed, for those with cards requiring it.)  If you have done an install to the hard drive you can in a lot of cases, not all install bcmwl-kernel source from the install media by navigating to the correct folder on the media and using software installer or in the terminal dpkg to install it.  no need most of the time to be connected to do it.  You must install it's dependencies first though and they are on the install media also.  Good luck. (**Note:** Of course you will loose the driver if you reboot and will have to install it again, in the live instance.)

---

### Post by j3984 on 2019-04-03
are you sure of that? I thought I had to go out to the repos to get it..but I hope not....
btw ..is it possible to use an editor and go into the kernel and change it to load the bcm driver automatically on boot? I know Ubuntu cant do that legally but can we??
Where would I find out how to do it via terminal/command line..?

---

### Post by kc1di on 2019-04-04
The problem would be that the kernel module is built by DKMS at the time it's installed.  So there is no Kernel module to load until it's built and in the live session all that is lost when you reboot.  Only thing I can think of is to install bcmwl and then remaster the .iso with it enabled that can be done. [This page]("https://help.ubuntu.com/community/LiveCDCustomization") may be of help with that.
It will install from the Dvd/usb as long as all other dependencies are met.  I've never had a problem installing it on my live ISO's here. Good Luck. 
If you need to install this driver on an already installed system without internet acess you have to plug in the usb/DvD and use the file manager to navigate and install the files via software installer. or use dpkg in a terminal.  The address is as follows /pool/main/g/glibc/ you need to install ```
/pool/main/g/glibc/libc-dev-bin_2.27-3ubuntu1_amd64.deb
``` first then install ```
/pool/main/g/glibc/libc6-dev_2.27-3ubuntu1_amd64.deb  
```Then navigate to /pool/restricted/b/bcmwl and install ```
bcmwl-kernel-source
```.  it has to be done in that order.

---

### Post by tea for one on 2019-04-04
> **j3984 said:**
> is there now or will there be soon an iso for Ubuntu that has the BCM wifi driver in the live session files so you dont have to download it everytime  you do a live session?
this is a major pita. Needs to be fixed.

Is there a reason why you do not want to make a live usb with persistence?

If you add persistence, you can install your Broadcom driver and it will be available when you reboot.

The package **mkusb** will help you do this.

Whoops, I've just realised that this will **not** work on reboot because the persistence only recognises files saved in **user home** as opposed to saving system files.

---

### Post by chili555 on 2019-04-04
Possibly helpful: [https://askubuntu.com/questions/1069550/unable-to-use-wifi-card-16-04-macos-dual-boot/1069949#1069949](https://askubuntu.com/questions/1069550/unable-to-use-wifi-card-16-04-macos-dual-boot/1069949#1069949) Indeed, the package and its dependencies are all on the install DVD, USB or other. However, the free and open source default installation doesn't quickly and easily install them.

---

### Post by tea for one on 2019-04-04
> **j3984 said:**
> is there now or will there be soon an iso for Ubuntu that has the BCM wifi driver in the live session files so you dont have to download it everytime  you do a live session?
this is a major pita. Needs to be fixed.

An alternative suggestion (although not strictly a **live** session):-

Prepare a usb stick with a live Ubuntu iso
Boot the live session
Install the OS to another usb device (say 16GB) complete with user and log in password etc (ensure that grub is installed on the 16GB stick)
Reboot the installed system and add the Broadcom driver

I tested this with an Ubuntu Minimal installation onto a Sandisk Ultra 16GB and have rebooted a couple of times to double check the driver.

All in all, not bad.

Here is the output to show the driver in use:-

```
test@test:~$ lspci -vvnn | grep -A 9 Network
02:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [103c:804a]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at 91000000 (64-bit, non-prefetchable) [size=32K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: bcma, wl
test@test:~$ 
```

---

### Post by j3984 on 2019-04-04
thanks

---

