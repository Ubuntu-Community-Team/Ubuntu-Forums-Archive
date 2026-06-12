---
title: "usb wifi causes kernel panic with Gutsy"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by 1feistymedic on 2007-11-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/162653](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/162653) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have a Linksys wusb54g usb wifi adapter that worked fine under Feisty. I did a fresh install on another desktop with Gutsy and followed the same directions that I used for Feisty and got it to work perfectly. Once I rebooted the system the following occurred:

I get a flashing keyboard and the system wont finish booting.

I did a hard shutdown and on the next restart did the following:

Hit escape and booted into Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode).

If wifi dongle plugged in at boot, boot stops and gives this error message:

```
[ 82.325884] Kernel panic &#8211; not syncing: Creation of kmalloc slab kmalloc_dma-2 size=2 failed.

[ 82.325886]
```

If I boot in recovery mode without the dongle plugged in I get a normal recovery boot and a root prompt. Once I plug it in, I immediately get the following error message:
```

root@ubuntuserver1:~# [ 75.112448] rt73: Firmware not load
```

With either way, I get the two lights on the keyboard (next to the num lock light) flashing and the system locks up.

If I allow the system to do a normal boot it boots fine. As soon as I plug in the dongle, the keyboard flashes and the system locks up, even after a normal boot.

In order for the card to work again, I have to do a hard shutdown, unplug the dangle, do a normal boot, go through the whole setup procedure and reinsert the card.  Then the card works fine. Once I reboot, the problem repeats.

I used the directions found at the following link to set up the card:

[COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=512647&highlight=1feistymedic&page=4](http://ubuntuforums.org/showthread.php?t=512647&highlight=1feistymedic&page=4)[/COLOR]

Any suggestions? Wired ethernet does not cause this problem.

---

### Post by rustybronco on 2007-11-14
> **1feistymedic said:**
> 				I have a Linksys wusb54g usb wifi adapter that worked fine under Feisty. What version v1,v2,v4 ?

---

### Post by 1feistymedic on 2007-11-14
Network manager no longer shows in the panel now.  But I can still log on if I manually go into system, administration and network and enable it.  Somehow the settings were lost.

---

### Post by 1feistymedic on 2007-11-14
I am not sure of the version.  It does not state on the dongle.  Should it matter since I don't use the drivers that came with it (a-la Ndiswrapper)?

---

### Post by rustybronco on 2007-11-14
> **1feistymedic said:**
> I am not sure of the version.  It does not state on the dongle.  Should it matter since I don't use the drivers that came with it (a-la Ndiswrapper)? The version is on the bottom of the adaptor and yes there are different chipsets for each version. v1=prisim v4=rt2500usb v2=?

---

### Post by 1feistymedic on 2007-11-14
I am looking at the bottom.  It does not state. But I am 100% certain it is the rt73 chipset.  It was working flawlessly with the rt73 serialmonkey driver.  It still works on my Feisty machine no problem.  Just not Gutsy.

---

### Post by rustybronco on 2007-11-14
lsusb should tell you the chipset.
Please excuse my ignorance, just trying to help.
you may have to blacklist a driver if it is trying to use two drivers in  /etc/modprobe.d/blacklist
did you look at the dmesg output?

---

### Post by 1feistymedic on 2007-11-14
I did blacklist the usual modules.  It is the rt73 chipset.  Kevdog helped me the last time.  I followed his previous instructions to the t and it worked, just not on reboot.

Refer to the following post

[http://ubuntuforums.org/showthread.php?t=512647&highlight=1feistymedic&page=4](http://ubuntuforums.org/showthread.php?t=512647&highlight=1feistymedic&page=4)

---

### Post by rustybronco on 2007-11-14
v1=prisim chipset, v2=prisim gt? chipset, v4=rt2570 chipset (I have the wusb54gv4) rt73 drivers don't make sense
that post started with a wusb54gc which may use the rt73 drivers but you have a wusb54g...

---

### Post by kevdog on 2007-11-14
RustyBronco 

Changed the avatar from the pumpkin -- hardley recognized it was you!!!

Can you catch me up to speed.  Just quickly you are using a rt73 chipset.  Did you compile the cvs serial monkey drivers and install them and blacklist the builtin rt73 kernel modules??

Is anything working for you??  From an informal poll that was ongoing, I finding the rt drivers shipped with Gusty do seem to be causing a lot of people problems, so the old fallback method of source compiling and installation seems currently to be the most reliable option.

---

### Post by rustybronco on 2007-11-14
kevdog, I had to change it, halloween done gone. 
looked for a avatar for a blue 1982 gs850g but I couldn't find one, so for now a 1969 shelby gt350 (same color as mine), at least its the same color as the pumpkin.

---

### Post by rustybronco on 2007-11-14
Kevdog,
Up to speed, I'm trying to find out if he has a wusb54g (v1-v2-v4) or a wusb54gc (gs?) at this point.

---

### Post by 1feistymedic on 2007-11-14
It is the wusb54gc card and it uses the RT73 chipset.  I did the following in terminal:

```
cd /usr/src
```

```
sudo wget http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz -O /usr/src/rt73-cvs-daily.tar.gz
```

```
sudo tar –xvzf rt73-cvs-daily.tar.gz
```

```
sudo aptitude install build-essential linux-headers-`uname -r`
```

```
cd /usr/src/rt73-cvs-2007111213/Module
```

```
sudo make
```

```
sudo strip -S rt73.ko 
```


sudo make install

```
sudo ifconfig wlan0 down
```

```
sudo modprobe -r rt73usb
```

```
sudo modprobe -r rt2570
```

```
sudo modprobe -r rt2500usb
```

```
sudo modprobe -r rt2x00lib
```

```
xhost +
```

```
gksu gedit /etc/modprobe.d/blacklist
```

```
paste after last line:

# Blacklist rt73usb, as it is a non-functional beta module which conflicts with the working rt73 module.
blacklist rt73usb
# Blacklist rt2570, as it causes conflicts with rt73
blacklist rt2570
# Other modules that break rt73
blacklist rt2500usb
blacklist rt2x00lib
```

```
sudo modprobe –v rt73
```

```
sudo ifconfig wlan0 down
```

```
sudo ifconfig wlan0 down
```

```
sudo iwconfig wlan0 essid "my essid"
```

```
sudo iwconfig wlan0 mode managed
```

```
sudo dhclient wlan0
```

```
sudo aptitude update
```

```
sudo aptitude upgrade
```

```
sudo aptitude install wpasupplicant libgtk2.0-dev
```

```
wpa_passphrase <SSID of my router> <my password>
```

```
gksu gedit /etc/network/interfaces
```

```
pasted:

# The primary network interface

auto wlan0
iface wlan0 inet static
address 192.168.1.112
netmask 255.255.255.0 
gateway 192.168.1.1 
dns-nameservers 68.87.87.12
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid "my ssid"
pre-up iwconfig wlan0 mode managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set WPAPSK="pasted psk info from two steps above"
pre-up iwpriv wlan0 set EncrypType=TKIP
```

After doing this it worked great, just like in Feisty.  Until I rebooted.  Then it broke.  I can't even insert the card now to print out any info because as soon as I insert it, the system freezes up and does not unfreeze even after removing the card.

---

### Post by rustybronco on 2007-11-14
> **1feistymedic said:**
> 				I have a Linksys wusb54g usb wifi adapter  I can't help much with the wusb54gc i have no experience with it, sorry.

---

### Post by 1feistymedic on 2007-11-14
No problem.  Kevdog, diepruis, and noob12 helped me before.  

I am still waiting for an answer to the bug I filed.  I guess this is a long process.  

The only good thing is that I did not upgrade to Gutsy on my ***primary*** machine and only did it on my ***test*** machine.  Actually, the test machine did the same thing as an upgrade so I reinstalled as a fresh install and it still did the same.

---

### Post by 1feistymedic on 2007-11-14
> No problem.  Kevdog, diepruis, and noob12 helped me before.  

Where are you?:confused:

---

### Post by 1feistymedic on 2007-11-15
Still no takers?[-o<

---

### Post by 1feistymedic on 2007-12-09
Hello Ubuntu world...Has anyone come up with a solution to this problem yet?  Thanks:confused:

---

### Post by diepruis on 2007-12-15
From the error messages, it could be the case that the firmware isn't being loaded. Could you check the output of

```

find /lib/firmware/`uname -r`/ -name rt*.bin

```

Have you tried using a newer CVS version from serialmonkey? Remember that this driver is still in beta, so often times things break horribly.

---

### Post by Rplus9 on 2007-12-18
I was having a similar problem with my Gutsy install.  I was stoked to start playing WoW on Ubuntu (so very close to kicking the M$ addiction)

I'd get the random double blinky keyboard lights of doom and no input short of a reset button would do anything.

I learned that this was called kernel panic.  It was only happening when I was using my USB wireless (linksys) wusb54gsc.

{odd note, I found I could keep the kernel from panic if I kept it really busy.  Basically if I was doing something that used up a lot of CPU it would not crash.  I used that kernelcheck software to get the newest kernel (2.6.23) and I figured out that if I made the chess game play against itself (several games!) if would fend off panic long enough to finish the kernel install}

I had a lot of experience with ndiswrapper and I had no issues installing the hardware on the 2.6.22-14-generic kernel.

So as a fix I learned that maybe a new kernel would jive better, so now I have a new kernel, BUT when I go through the hoops to install my USB wireless I get to the;

$ modprobe ndiswrapper
FATAL: Module not found

before you ask:
$ ndiswrapper -l
checks out good (I forget the feedback but it's good)

the /etc/modprobe.d/ndiswrapper
shows all the right signs.

however, I cannot find a ndiswrapper.ko file anywhere.  I don't know what it is, but I have a feeling it's important.

I've tried some other things but my notes are not at hand.  Would anyone have some advice? 

I'm still a linux learner, having explinations along with syntax is really helpful.

Thanks!

---

