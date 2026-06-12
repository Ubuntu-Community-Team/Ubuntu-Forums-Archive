---
title: "No wireless after 16.04 upgrade, Mediatek MT7630E"
date: 2016-09-01
forum: Networking &amp; Wireless
---

### Post by paul_b4 on 2016-09-01
My wireless isn't working anymore after 16.04 upgrade.  Before (with 15.10) when it stopped working, I followed these instructions [https://community.linuxmint.com/tutorial/view/1796](https://community.linuxmint.com/tutorial/view/1796) and it started working again.  Now I get this in the terminal:

```
make -C /lib/modules/`uname -r`/build M=/home/paul/Downloads/MT7630E-release/rt2x00 modules
make[1]: Entering directory '/usr/src/linux-headers-4.4.0-36-generic'
  CC [M]  /home/paul/Downloads/MT7630E-release/rt2x00/rt2x00config.o
/home/paul/Downloads/MT7630E-release/rt2x00/rt2x00config.c: In function &#8216;rt2x00lib_config&#8217;:
/home/paul/Downloads/MT7630E-release/rt2x00/rt2x00config.c:273:27: error: &#8216;struct ieee80211_conf&#8217; has no member named &#8216;max_sleep_period&#8217;
   autowake_timeout = (conf->max_sleep_period * beacon_int) - beacon_diff;
                           ^
scripts/Makefile.build:258: recipe for target '/home/paul/Downloads/MT7630E-release/rt2x00/rt2x00config.o' failed
make[2]: *** [/home/paul/Downloads/MT7630E-release/rt2x00/rt2x00config.o] Error 1
Makefile:1403: recipe for target '_module_/home/paul/Downloads/MT7630E-release/rt2x00' failed
make[1]: *** [_module_/home/paul/Downloads/MT7630E-release/rt2x00] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-36-generic'
Makefile:8: recipe for target 'all' failed
make: *** [all] Error 2
cp -v firmware/*/* /lib/firmware/
'firmware/BT/mt76x0.bin' -> '/lib/firmware/mt76x0.bin'
'firmware/Wi-FI/MT7650E234.bin' -> '/lib/firmware/MT7650E234.bin'
cp rt2x00/mt7630e.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/
cp btloader/mt76xx.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/
depmod
modprobe: ERROR: could not insert 'mt7630e': Exec format error
modprobe: ERROR: could not insert 'mt76xx': Exec format error

```

Thanks in advance!
Paul

---

### Post by wildmanne39 on 2016-09-01
Go into the directory that you tried to run make on that driver and failed then uninstall it completely.
Then do:
```
sudo apt-get install --reinstall git linux-headers-$(uname -r) build-essential dkms
git clone https://github.com/neurobin/MT7630E/
cd MT7630E/
make
sudo make install
```
watch for errors and post them here if there are any I suspect there will be.
Thanks

---

### Post by paul_b4 on 2016-09-02
Sorry, I'm not competent enough to know how to uninstall the driver where I tried to run make in the first place...  Can you tell me how to do that?

---

### Post by wildmanne39 on 2016-09-02
Please do:
```
cd ~/Downloads/MT7630E-release
sudo ./uninstall
```


This driver has been upgraded to work with kernel 4.0 so it may be your best chance to get your device working.

You will need to watch for errors through this whole process if there are any post them here.

If you have secure boot enabled you will need to disable it.
```
sudo mokutil --disable-validation
``` 
Please do:
```
cd
sudo apt-get install --reinstall git linux-headers-$(uname -r) build-essential dkms
```
Then do:
```
cd ~/Downloads/MT7630E-release
sudo chmod +x install
sudo ./install
```
let us know if it is working, since this driver is not being maintained by the maker I recommend that you put a hold on kernel upgrades because if the kernel gets upgraded it will break the wifi again.

---

### Post by paul_b4 on 2016-09-03
Unfortunately when I run```
sudo ./uninstall
``` I just get "command not found".  Do I need to have an internet connection to fix this?  Unfortunately I don't have a wired connection, and so I am using my Windows install to use the internet.

---

### Post by wildmanne39 on 2016-09-03
Make sure you are in the directory and try the command without sudo and see if that makes a difference.

Yes for the other commands you will need a internet connection, you can tether you cell phone to your computer that works nicely or take the computer somewhere you can plug it in.

---

### Post by paul_b4 on 2016-09-04
Ok, first I tried to do ./uninstall without sudo, and I got this ```
paul@paul-X555LAB:~/Downloads/MT7630E-release$ ./uninstall
bash: ./uninstall: Permission denied
``` 

Then I remembered that I tried to install a [supposedly more updated driver]("https://github.com/neurobin/MT7630E/tree/e7130a42f8198cbf503a5a307175073c078bf340"), and that time the uninstall seemed to work ```
paul@paul-X555LAB:~/Downloads/MT7630E-e7130a42f8198cbf503a5a307175073c078bf340$ sudo ./uninstall
rm -vf /lib/firmware/mt76x0.bin /lib/firmware/MT7650E234.bin
removed '/lib/firmware/mt76x0.bin'
removed '/lib/firmware/MT7650E234.bin'
rm -vf /lib/modules/`uname -r`/kernel/drivers/net/wireless//mt7630e.ko
removed '/lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless//mt7630e.ko'
rm -vf /lib/modules/`uname -r`/kernel/drivers/net/wireless//mt76xx.ko
removed '/lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless//mt76xx.ko'
depmod

```

Then I ran ```
paul@paul-X555LAB:~$ sudo apt-get install --reinstall git linux-headers-$(uname -r) build-essential dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  dkms
0 upgraded, 1 newly installed, 3 reinstalled, 0 to remove and 18 not upgraded.
Need to get 3.077 kB/3.856 kB of archives.
After this operation, 265 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu xenial/main amd64 build-essential amd64 12.1ubuntu2 [4.758 B]
Get:2 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 dkms all 2.2.0.3-2ubuntu11.1 [66,2 kB]
Get:3 http://archive.ubuntu.com/ubuntu xenial/main amd64 git amd64 1:2.7.4-0ubuntu1 [3.006 kB]
Fetched 3.077 kB in 6s (495 kB/s)                                              
(Reading database ... 193844 files and directories currently installed.)
Preparing to unpack .../build-essential_12.1ubuntu2_amd64.deb ...
Unpacking build-essential (12.1ubuntu2) over (12.1ubuntu2) ...
Selecting previously unselected package dkms.
Preparing to unpack .../dkms_2.2.0.3-2ubuntu11.1_all.deb ...
Unpacking dkms (2.2.0.3-2ubuntu11.1) ...
Preparing to unpack .../git_1%3a2.7.4-0ubuntu1_amd64.deb ...
Unpacking git (1:2.7.4-0ubuntu1) over (1:2.7.4-0ubuntu1) ...
Preparing to unpack .../linux-headers-4.4.0-36-generic_4.4.0-36.55_amd64.deb ...
Unpacking linux-headers-4.4.0-36-generic (4.4.0-36.55) over (4.4.0-36.55) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up build-essential (12.1ubuntu2) ...
Setting up dkms (2.2.0.3-2ubuntu11.1) ...
Setting up git (1:2.7.4-0ubuntu1) ...
Setting up linux-headers-4.4.0-36-generic (4.4.0-36.55) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic

```

Then ```
paul@paul-X555LAB:~$ cd /home/paul/Downloads/MT7630E-release
paul@paul-X555LAB:~/Downloads/MT7630E-release$ sudo chmod +x install
paul@paul-X555LAB:~/Downloads/MT7630E-release$ sudo ./install
make -C /lib/modules/`uname -r`/build M=/home/paul/Downloads/MT7630E-release/rt2x00 modules
make[1]: Entering directory '/usr/src/linux-headers-4.4.0-36-generic'
  CC [M]  /home/paul/Downloads/MT7630E-release/rt2x00/rt2x00config.o
/home/paul/Downloads/MT7630E-release/rt2x00/rt2x00config.c: In function ‘rt2x00lib_config’:
/home/paul/Downloads/MT7630E-release/rt2x00/rt2x00config.c:273:27: error: ‘struct ieee80211_conf’ has no member named ‘max_sleep_period’
   autowake_timeout = (conf->max_sleep_period * beacon_int) - beacon_diff;
                           ^
scripts/Makefile.build:258: recipe for target '/home/paul/Downloads/MT7630E-release/rt2x00/rt2x00config.o' failed
make[2]: *** [/home/paul/Downloads/MT7630E-release/rt2x00/rt2x00config.o] Error 1
Makefile:1403: recipe for target '_module_/home/paul/Downloads/MT7630E-release/rt2x00' failed
make[1]: *** [_module_/home/paul/Downloads/MT7630E-release/rt2x00] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-36-generic'
Makefile:8: recipe for target 'all' failed
make: *** [all] Error 2
cp -v firmware/*/* /lib/firmware/
'firmware/BT/mt76x0.bin' -> '/lib/firmware/mt76x0.bin'
'firmware/Wi-FI/MT7650E234.bin' -> '/lib/firmware/MT7650E234.bin'
cp rt2x00/mt7630e.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/
cp btloader/mt76xx.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/
depmod
modprobe: ERROR: could not insert 'mt7630e': Exec format error
modprobe: ERROR: could not insert 'mt76xx': Exec format error

```

Again ```
paul@paul-X555LAB:~/Downloads/MT7630E-release$ cd /home/paul/Downloads/MT7630E-release
paul@paul-X555LAB:~/Downloads/MT7630E-release$ sudo ./uninstall
sudo: ./uninstall: command not found

```

Then I tried the other driver again ```
paul@paul-X555LAB:~/Downloads/MT7630E-release$ cd /home/paul/Downloads/MT7630E-e7130a42f8198cbf503a5a307175073c078bf340
paul@paul-X555LAB:~/Downloads/MT7630E-e7130a42f8198cbf503a5a307175073c078bf340$ sudo chmod +x install
paul@paul-X555LAB:~/Downloads/MT7630E-e7130a42f8198cbf503a5a307175073c078bf340$ sudo ./install
make -C /lib/modules/`uname -r`/build M=/home/paul/Downloads/MT7630E-e7130a42f8198cbf503a5a307175073c078bf340/rt2x00 modules
make[1]: Entering directory '/usr/src/linux-headers-4.4.0-36-generic'
  CC [M]  /home/paul/Downloads/MT7630E-e7130a42f8198cbf503a5a307175073c078bf340/rt2x00/rt2x00config.o
/home/paul/Downloads/MT7630E-e7130a42f8198cbf503a5a307175073c078bf340/rt2x00/rt2x00config.c: In function ‘rt2x00lib_config’:
/home/paul/Downloads/MT7630E-e7130a42f8198cbf503a5a307175073c078bf340/rt2x00/rt2x00config.c:273:27: error: ‘struct ieee80211_conf’ has no member named ‘max_sleep_period’
   autowake_timeout = (conf->max_sleep_period * beacon_int) - beacon_diff;
                           ^
scripts/Makefile.build:258: recipe for target '/home/paul/Downloads/MT7630E-e7130a42f8198cbf503a5a307175073c078bf340/rt2x00/rt2x00config.o' failed
make[2]: *** [/home/paul/Downloads/MT7630E-e7130a42f8198cbf503a5a307175073c078bf340/rt2x00/rt2x00config.o] Error 1
Makefile:1403: recipe for target '_module_/home/paul/Downloads/MT7630E-e7130a42f8198cbf503a5a307175073c078bf340/rt2x00' failed
make[1]: *** [_module_/home/paul/Downloads/MT7630E-e7130a42f8198cbf503a5a307175073c078bf340/rt2x00] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-36-generic'
Makefile:8: recipe for target 'all' failed
make: *** [all] Error 2
cp -v firmware/*/* /lib/firmware/
'firmware/BT/mt76x0.bin' -> '/lib/firmware/mt76x0.bin'
'firmware/Wi-FI/MT7650E234.bin' -> '/lib/firmware/MT7650E234.bin'
cp rt2x00/mt7630e.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/
cp: cannot stat 'rt2x00/mt7630e.ko': No such file or directory
Makefile:16: recipe for target 'install' failed
make: *** [install] Error 1
modprobe: ERROR: could not insert 'mt7630e': Exec format error
modprobe: ERROR: could not insert 'mt76xx': Exec format error

```

Finally, ```
paul@paul-X555LAB:~$ sudo mokutil --disable-validation
sudo: mokutil: command not found

``` (my secure boot was already disabled though).

---

### Post by chili555 on 2016-09-04
> paul@paul-X555LAB:~$ cd /home/paul/Downloads/MT7630E-release
paul@paul-X555LAB:~/Downloads/MT7630E-release$ sudo chmod +x install
paul@paul-X555LAB:~/Downloads/MT7630E-release$ sudo ./installPlease stop. I do not understand why you are trying to install and then uninstall the same thing that you complained would not compile in your original post. If it didn't compile three days ago, it won't compile today.

If it didn't build and didn't load, there is no need to uninstall it. Stop.

Please do:```
cd
git clone https://github.com/neurobin/MT7630E.git
cd MT7630E
make
sudo make install
```Reboot.

On my 16.04 system, this 'makes' without error, without warning and without drama. I'm sure it will for you, too.

---

### Post by blurryface on 2016-12-22
Hello there, Im a noob to linux but Im not new to ubuntu.
I am using an asus k555lf laptop which came with the MT7630e wifi+bluetooth combo card.
I was having a plethora of issues to get the wireless to work but i did  my research and this method is sure to work on your card if you follow  every condition to boot.

here goes, Im using ubuntu- Gnome 16.04 but it should work for your build regardless of the desktop environment.
Try to go with a clean install for better results.
you will need ethernet of course.
after installation, you should update your build and you can do that by navigating to the software updater app.

next up run this command 
```
sudo apt-get install linux-headers-generic build-essential git
```

let the terminal do it's magic 

after its done downloading, run this command 
```
sudo apt-get install dkms
```

let the terminal do it's magic

next up youre gonna want to navigate to

```
https://github.com/neurobin/MT7630E/releases
``` 
and download the source code.zip of the latest release in your home folder also extract it .

navigate into the extracted folder and open a terminal there
run 
```
[FONT=arial] chmod +x install test uninstall bpatch[/FONT] 
```

the run 
```
[FONT=arial]
sudo ./install[/FONT]
```

or run 
```
sudo make dkms
```

to install with dkms.

your wireless should be working and the drivers will load at startup. 

cheers :grin:

---

