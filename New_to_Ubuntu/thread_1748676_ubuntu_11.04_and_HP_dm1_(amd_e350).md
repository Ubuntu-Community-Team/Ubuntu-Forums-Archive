---
title: "ubuntu 11.04 and HP dm1 (amd e350)"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by pft0 on 2011-05-03
Tried 11.04 for a few day, finally it installed not like 10.10 or 10.04, but the mouse pad, wifi and bluetooth does not work, is there anyone know how to get driver for the wifi?

---

### Post by Apperature_Science on 2011-05-05
Hello, I too have the HP dm1. If you figure this out please let me know.

the touch pad is horrible, I can't right click, and the wireless does not work.  I would love to get this computer working with ubuntu. If it helps you I found this website. [http://www.6by9.net/b/2011/04/25/hp-dm1z-laptop-running-ubuntu-1010](http://www.6by9.net/b/2011/04/25/hp-dm1z-laptop-running-ubuntu-1010)

But nothing on there has worked for me so far. To be honest, I don't know if I'm even running ubuntu in 64 bit mode or not. I have no idea how to check. I have no idea which versions of stuff to get.

pft0, did the wireless and touch pad work when you were in ubuntu 10? if so maybe we should just stick to that.

---

### Post by Apperature_Science on 2011-05-05
Someone please help us. I have no idea what to do.  Its getting increasingly difficult to use with the mouse pad messed up like this.

---

### Post by doulos115 on 2011-05-06
Hi!

I am trying to install Ubuntu 11.04 as well. I tried the LIVE version, and I like it. And I DID find a web page which can install WiFi driver for Ubuntu 11.04. 

[http://ubuntuforums.org/showpost.php?p=10661914&postcount=21](http://ubuntuforums.org/showpost.php?p=10661914&postcount=21)

Please, if you are able to do this, please give a detailed instruction here. I am a newbie and I don't fully understand.

---

### Post by Redblade20XX on 2011-05-07
For the wifi fix, you can either try the rt5390 manual fix or wait for kernel 2.6.39 release which should have the driver built in. 

Here's the link for the manual fix (see pg 6 or 7): [http://ubuntuforums.org/showthread.php?t=1600498&highlight=rt5390](http://ubuntuforums.org/showthread.php?t=1600498&highlight=rt5390)

---

### Post by pendragyn on 2011-05-10
[http://ubuntuforums.org/showthread.php?t=1645716&page=9](http://ubuntuforums.org/showthread.php?t=1645716&page=9)
On page 9 there are some good directions for the manual fix for the wifi card. It does take messing with the terminal so you might need to look up some of the commands and what the terminal prompts will look like. If you keep looking through the forums here for terms like ralink rt5390 there are lots of posts about this topic.

I got my touchpad working by going into the package manager Synaptic and doing a search for touchpad. I am using kde-config-touchpad and it is working great so far. I do not use gestures so much, but it does let me do 1, 2, and 3 finger taps. It does not recognise the buttons as being 2 buttons but with the synapiks config too (the one I mention getting above) you can tell it that tapping in a corner counts and a mouse button click. It also lets the pad be turned off temporarily for typing and how long a delay to enact before it come back on.

I don't have any solutions for the Bluetooth yet, but I am hoping something will come up soon. 

Good luck!

---

### Post by T0OL on 2011-05-16
I've been running 11.04 for a week or two, everything seems fine. I fixed my wifi the manual way and only have one problem.

I can connect to hidden ssid's. I get an ip address but thats it. I am unable to surf the internet or even ping anything outside of my machine.

anybody else experiencing this particular wifi problem.

---

### Post by doulos115 on 2011-05-23
So did new kernel 2.6.39 fix wifi driver for dm1-3020us (amd e350)? Please let us know.

---

### Post by kibaya on 2011-05-23
Hi guys,
Have you tried just to run the update manager then install the updates and then reboot. If the mouse doesn't work try using an external usb mouse till you run the updates.

---

### Post by Redblade20XX on 2011-05-23
> **doulos115 said:**
> So did new kernel 2.6.39 fix wifi driver for dm1-3020us (amd e350)? Please let us know.

No it didn't. Just installed it and it only added "experimental" support. lol. Guess you'll have to do the manual fix.:(

---

### Post by nefan on 2011-05-24
The kernel driver works for me with 2.6.39 and the patch from here [http://rt2x00.serialmonkey.com/pipermail/users_rt2x00.serialmonkey.com/2011-May/003786.html](http://rt2x00.serialmonkey.com/pipermail/users_rt2x00.serialmonkey.com/2011-May/003786.html)

---

### Post by doulos115 on 2011-05-24
> **nefan said:**
> The kernel driver works for me with 2.6.39 and the patch from here [http://rt2x00.serialmonkey.com/pipermail/users_rt2x00.serialmonkey.com/2011-May/003786.html](http://rt2x00.serialmonkey.com/pipermail/users_rt2x00.serialmonkey.com/2011-May/003786.html)

How do I apply the patch? I am a newbie at this. Do I just execute the .bin file? Please help. Thanks.

---

### Post by nefan on 2011-05-25
This is what I've done for using the rt2800pci module for the rt539f card on Natty. The steps below involve compiling a new kernel so every warning against doing this applies. It's written from the top of my head so please ask if it doesn't work. And please note that I use the latest rt2x00 drivers from their git repository. That step might be unnecessary.

1. Get the ubuntu kernel code from git repository: git clone git://kernel.ubuntu.com/ubuntu/ubuntu-oneiric.git

2. Get the rt2x00 code : git clone git://git.kernel.org/pub/scm/linux/kernel/git/ivd/rt2x00.git

3. Remove the rt2x00 from the ubuntu kernel and add the rt2x00 code: something like 'rm -rf ubuntu-oneiric/drivers/net/wireless/rt2x00' and 'cp -R rt2x00/drivers/net/wireless/rt2x00 ubuntu-oneiric/drivers/net/wireless

(note: step 2. and 3. might be (are probably) unnecessary and might even break things. It's a hack which worked for me)

4. Apply patch to make rt2800pci recognice rt539f: the quick way. Find the lines
#ifdef CONFIG_RT2800PCI_RT53XX
    { PCI_DEVICE(0x1814, 0x5390) },
#endif
around line 1160 in ubuntu-oneiric/drivers/net/wireless/rt2x00/rt2800pci.c and replace with
#ifdef CONFIG_RT2800PCI_RT53XX
    { PCI_DEVICE(0x1814, 0x5390) },
    { PCI_DEVICE(0x1814, 0x539F) },
#endif

5. Kernel configuration: copy /boot/config-2.6.38-8-generic to ubuntu-oneiric/.config. cd to ubuntu-oneiric. Run 'make oldconfig'. After that, make sure 
CONFIG_RT2800PCI_RT53XX is set. I.e., edit .config and replace the line containing CONFIG_RT2800PCI_RT53XX with the line CONFIG_RT2800PCI_RT53XX=y

6. Compile and install kernel, [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

7. After boot, modprobe rt2800pci

---

