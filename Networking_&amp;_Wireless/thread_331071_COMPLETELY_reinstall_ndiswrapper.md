---
title: "COMPLETELY reinstall ndiswrapper?"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by aberry5555 on 2007-01-04
Right, I just installed my copy of ubuntu on to my pc last night, working absolutely brilliantly after a little fiddling, bar one thing. I used Ndiswrapper with a driver from the ASUS website which, unfortunately, made my pc crash and not work properly until I'd removed it. I tried to remedy this by using different drivers. These drivers gave a parsing error but they still loaded and, when I checked, it still said that the driver was loaded and the hardware was present but it wouldn't show up in the network manager, even when I installed the driver with ndiswrapper and checked that everything was ok by typing the following commands:

modprobe ndiswrapper
 modprobe wlan0
 ndiswrapper -l
ndiswrapper -m (alias already installed and still valid)

All of these commands show up as they should, but when I type iwconfig no wireless is detected. I tried switching back to the old drivers, simply to check if they were at least recognised, but they weren't either. Apparently the first drivers I installed are a known incompability with ubuntu and I've read that it "screws up your system" though no one elaborated more than that :S

Tonight I'm either gonna start again from scratch or, if someone can help explain to me how to properly remove ndiswrapper ( I have a feeling the "complete" removal in synaptic isn't as complete as it could be) and how to reset any other settings that might have gone awry, I will do that.

Cheers

---

### Post by halfmanhalfbug on 2007-01-04
Hi aberry5555
I just finished a complete reinstall of ndiswrapper on my Edgy 64bit configuration (I'm a new refugee from Fedora...so many discs!). I found that even with a completely new version of ndiswrapper I still had to make a few changes for wlan0 to show up:
1)blacklist your old driver so that it does not get loaded. Edit the file /etc/modprobe.d/blacklist and add the following line:
blacklist nameofyourolddriver
2) add ndiswrapper to the list of modules to be loaded at startup. Edit the file /etc/modules and add the following line:
ndiswrapper
3)add the wlan0 interface to the list of interfaces in /etc/network/interfaces. Add the following lines:
auto wlan0
iface wlan0 inet dhcp

I woud say try the above changes first and see if they fix the problem. Restart your computer and see if you find wlan0. I found that the 1.18 version of ndiswrapper simply would not work with the 64bit 2.6.17-10-generic kernel and a Broadcom 4318 chipset (the worst of the worst from what I understand) even with the above modifications so I installed the latest version from source.
First remove the old ndiswrapper and ndiswrapper-utils with Synaptic. You will also need to remove the directory /etc/ndiswrapper and the file /etc/modprobe.d/ndiswrapper by hand. To compile ndiswrapper:
1) go to [http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net) and download the latest version (currently 1.33)
2) unpack it: tar -xzvf ndiswrapper-1.33.tar.gz
3)  enter the unpacked directory: cd ndiswrapper-1.33
4) remove the old precompiled ndiswrapper module that came with Edgy: sudo make clean.
5) remove any other old stuff: sudo make uninstall
6) compile the new version: make
If you get a lot of errors saying files such as errno.h could not be found you need to install the C programming libraries. Use Synaptic to install libc and libc-dev then try "make" again.
7) install the new version: sudo make install

Now the usual. Load your driver: ndiswrapper -i path/to/driver.inf
Make sure it recognizes the driver and hardware: ndiswrapper -l
You should see your driver and hardware present.
Write the new module configuration: sudo ndiswrapper -m
And update your module dependencies: sudo depmod -a
Restart your computer and see if you can find wlan0, if ndiswrapper is loaded (lsmod), and if your old driver is loaded (lsmod). If no wlan0, make the edits to /etc/modprobe.d/blacklist, /etc/network/interfaces, and /etc/modules and restart.

I think Ubuntu needs to update the ndiswrapper package to at least version 1.25 (the current version for Fedora Core 6. Apparently it work for kernels up to 2.6.18) cuz I've seen a LOT of grief in these forums trying to configure wireless.
Good Luck,
hmhb

---

### Post by lorenzo on 2007-01-04
I had the same problem too. My wireless card works only installing ndiswrapper from scratch. If you had it already installed from synaptic you have to remove it first.

I also have to reinstall it whenever the kernel changes.

---

### Post by theblackgecko on 2007-03-13
This got my Broadcom 4318 working (although I haven't been able to do a proper test, because the antenna is short).

I had to use the command below to get the make working.
```
sudo aptitude install linux-headers-`uname -r`
```

Also, when Ubuntu is loading, it says basic networking ... failed. But, my wireless is working just fine. Any suggestions?

---

