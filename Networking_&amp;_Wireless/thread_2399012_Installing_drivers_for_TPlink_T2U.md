---
title: "Installing drivers for TPlink T2U"
date: 2018-08-20
forum: Networking &amp; Wireless
---

### Post by poiseman on 2018-08-20
Hello,

I will try to make this quick, I am having big troubles with installing this ([https://github.com/ulli-kroll/mt7610u](https://github.com/ulli-kroll/mt7610u)) driver on ubuntu budgie. On linux lite 4.0 I can install it even via liveusb and it works. When I try to compile (using make on ubuntu budgie):

```
cc1: error: code model kernel does not support PIC mode
``` 

(Output is a little bigger, but this is the main information. It's hard to provide all outputs because linux has no internet connection for now)

I googled and found that I need to create patchfile but when I try to patch:

```
Hunk #1 FAILED at 608.
1 out of 1 hunk FAILED -- saving rejects to file Makefile.rej
```

Any ideas appreciated.

Greetings.

---

### Post by praseodym on 2018-08-20
[http://www.ubuntu-forum.de/artikel/65713/tp-link-ac600-t2uh-usb-adapter-probleme-mit-treiber-installation.html#post387218](http://www.ubuntu-forum.de/artikel/65713/tp-link-ac600-t2uh-usb-adapter-probleme-mit-treiber-installation.html#post387218)

What about this one?

---

### Post by poiseman on 2018-08-20
Do you mean this one? 
[https://www.tp-link.com/en/download/Archer-T2U.html#Driver](https://www.tp-link.com/en/download/Archer-T2U.html#Driver)

I have tried it on _different_ linux, without effect. After "make" I got:
```
make -C UTIL / osutil
make [1]: Catalog entry ‘/ home / seba / Programs / Archer_T2U_V2_Linux / Driver / UTIL’
cp -f os / linux / Makefile.6.util / home / seba / Programs / Archer_T2U_V2_Linux / Driver / UTIL / os / linux / Makefile
make -C /lib/modules/4.14.62-1-lts/build SUBDIRS = / home / seba / Programs / Archer_T2U_V2_Linux / Driver / UTIL / os / linux modules
make [2]: Catalog entry ‘/usr/lib/modules/4.14.62-1-lts/build’
make [2]: *** There are no rules to execute the ‘modules’ object. Stop.
make [2]: Exiting the ‘/usr/lib/modules/4.14.62-1-lts/build’ directory
make [1]: *** [Makefile: 528: osutil] Error 2
make [1]: Exiting the directory ‘/ home / seba / Programs / Archer_T2U_V2_Linux / Driver / UTIL’
make: *** [Makefile: 3: all] Error 2 
```

I googled that driver is outdated(Kernel version 2.6~3.16) and can't compile using newest kernels. Do you think tha should I even try with it on ubuntu?

---

### Post by chili555 on 2018-08-20
> Do you think tha should I even try with it on ubuntu?No. Please read post #18 here: [https://ubuntuforums.org/showthread.php?t=2367163&highlight=mt7610u](https://ubuntuforums.org/showthread.php?t=2367163&highlight=mt7610u)

---

### Post by poiseman on 2018-08-21
So, tell me why this driver WORKS on linux lite 4.0? I can browse pages and so on. It's even ubuntu distro

---

### Post by chili555 on 2018-08-21
> **poiseman said:**
> So, tell me why this driver WORKS on linux lite 4.0? I can browse pages and so on. It's even ubuntu distroWhat kernel version is being used?```
uname -r
```

---

### Post by poiseman on 2018-08-21
4.15.0-22-generic

proof that it works:
[IMG]http://i67.tinypic.com/2zh4c45.png[/IMG]

---

### Post by chili555 on 2018-08-21
I haven't any idea. Is the driver included or did you have to compile it?

Frankly, if Linux Lite meets your needs otherwise, I'd just go for it.

---

### Post by poiseman on 2018-08-21
I compiled it. Source: [https://github.com/ulli-kroll/mt7610u](https://github.com/ulli-kroll/mt7610u)
I guess that it will work on ubuntu (I also tried the normal one) but I can't even compile, when I type make:
```
cc1: error: code model kernel does not support PIC mode
```

What can I do with that? Maybe is it kernel version fault? As I remember Ubuntu Budgie uses 4.15.0-35-generic, Is there any option to downgrade?
Linux Lite seems to be good but sometimes it can completely freeze for a while, also turning off computer can take ages.

---

### Post by chili555 on 2018-08-21
It compiles for me without the error, albeit a few warnings.

What is the gcc version at LinuxLite?```
gcc --version
```As well as your Ubuntu install?

My result is:```
gcc (Ubuntu 7.3.0-16ubuntu3) 7.3.0
```If, in Ubuntu, you have an earlier version, we may find that this gcc version allows successful compilation.

---

### Post by poiseman on 2018-08-22
Linux Lite:
```
gcc (Ubuntu 7.3.0-16ubuntu3) 7.3.0
```

I'm not sure, I think that could be version 6+ (something like that). Does gcc updates with "sudo apt-get update"? Can we check that gcc version for fresh install somewhere online? or Do I have to install fresh ubuntu to check it?

---

### Post by chili555 on 2018-08-22
>  Can we check that gcc version for fresh install somewhere online? or Do I have to install fresh ubuntu to check it?I thought you already had it installed; no??> When I try to compile (using make on ubuntu budgie):

```
cc1: error: code model kernel does not support PIC mode
```

---

### Post by poiseman on 2018-08-22
It's a long story, I have uninstalled budgie for a while (Just to test this wi-fi card on linux lite 4.0). I have installed it again with gcc 7.3 and I can compile the driver! But, there is a problem. When I unload the driver, network manager says: Device not managed. The easiest way to fix this was typing into terminal:
```
sudo service network-manager restart
```
On linux lite, it worked perfectly, but here on budgie network manager freeze completely. Is there anything I can do?

Also, I have spotted on both systems (linux lite and budgie), that when I unload the driver, computer have huge problem with shutting down. It can't make it.

---

### Post by chili555 on 2018-08-22
> When I unload the driver, network manager says: Device not managed.When you *load* the driver or when you unload the driver?

Did you see what was written in README.md?> **NOTES**  

The original driver is **PITA**  
Both mt7610u and mt7612u <u>can</u> work with the same driver.  
**but currently dont't**  

Code which is missing in one driver, may found in the other driver.  
i.e STA, AP, Monitor, RSSI, LED handling stuff  

**STATUS**  
[COLOR="#FF0000"]Driver works fine (some sort of)  [/COLOR]
Most of the work is done is cleaning the driver and make this mess **readable** 
  for conversion.  
Updates for wireless-ext/cfg80211  are not accepted.  
The only solution is uptream and this is mac80211 support.  
As I said previously, I suspect it compiles and yet doesn't work properly. My opinion is unchanged.

---

### Post by poiseman on 2018-08-22
My fault, when I load by:
```
sudo insmod mt7610u.ko
```

---

### Post by poiseman on 2018-09-16
[SLOUTION]

If you have ubuntu or some offical flavor you will probably need an ethernet cable. This solution works on Linux Lite 4.0(It is based on ubuntu 18.04 or 16.04) and I did not require ethernet cable. I can connect even to 5GHz networks. My kernel: 4.15.0-22-generic

1. Make sure if you have installed "make"
```
sudo apt-get install make
```

2. Download ZIP [https://github.com/bbczeuz/mt7610u_wifi_sta_v3002_dpo_20130916](https://github.com/bbczeuz/mt7610u_wifi_sta_v3002_dpo_20130916)

3. Extract that folder somewhere 

4. Open that folder, right-click somewhere and click "open terminal here"

5.```
sudo make
```

6.```
make install
```

7.```
mkdir -p /etc/Wireless/RT2870STA
```

8.```
sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat
```

9. Reboot

Work like a dream for me. Can somebody pin this post somewhere? There are a lot of trouble with this chipset (mt7610).

---

