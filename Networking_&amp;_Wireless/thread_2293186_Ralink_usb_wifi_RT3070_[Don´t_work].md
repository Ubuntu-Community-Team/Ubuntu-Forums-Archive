---
title: "Ralink usb wifi RT3070 [Don´t work]"
date: 2015-09-03
forum: Networking &amp; Wireless
---

### Post by lubuntwf on 2015-09-03
Can you help me please?
I´m new user of Lubuntu 15.04 (old user of Windows XP). Can you explain it step by step?

Lubuntu OS doesn´t recognize me Ralink usb wifi RT3070 (don´t work)
I have tested various forms but without success...

1) Download Linux driver from mediatek.com "RT8070/ RT3070/ RT3370/ RT3572/ RT5370/ RT5372/ RT5572 USB USB"

2) Decompress in desktop (DPO_RT5572_LinuxSTA_2.6.1.3_20121022.tar.bz2)
Delete the compressed archive. Leave only the unzipped folder on the desktop (without tar.bz2)

3) Open a terminal from previous folder,
> sudo apt-get install
It appears the following:
> Reading package lists ... Done
Building dependency tree
Reading state information ... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded 
The program isn´t installed...

I have also tried without success:
> ./configure ==> No such file or directory
> make ==> Try: sudo apt-get install <selected package>
> make install ==> command not found

Thanks! Regards.

---

### Post by howefield on 2015-09-03
Thread moved to the "*Networking & Wireless*" forum for better support.

---

### Post by chili555 on 2015-09-03
> DPO_RT5572_LinuxSTA_2.6.1.3_[COLOR="#FF0000"]2012[/COLOR]1022.tar.bz2That package is too old to compile correctly in 15.04.

Let's start by identifying the device in question. Please open a terminal and run and post:```
lsusb
```If you wish, you may omit everything but the USB wireless device.

---

### Post by lubuntwf on 2015-09-03
USB wireless device
> Bus 001 Device 003: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter

Thanks! ):P

---

### Post by chili555 on 2015-09-03
Your device is supposed to work with the driver rt2800usb. Is it loaded?```
lsmod | grep rt2
```Is there a wireless interface, ideally wlan0, here?```
iwconfig
```Are there any clues in the log?```
dmesg | grep rt2
```

---

### Post by lubuntwf on 2015-09-03
[FONT=&amp]> **chili555 said:**
> Your device is supposed to work with the driver rt2800usb. Is it loaded?```
lsmod | grep rt2
```

> rt2800usb 28672 0 
rt2x00usb 20480 1 rt2800usb
rt2800lib 90112 1 rt2800usb
rt2x00lib 49152 3 rt2x00usb,rt2800lib,rt2800usb
mac80211 626688 3 rt2x00lib,rt2x00usb,rt2800lib
crc_ccitt 16384 1 rt2800lib
cfg80211 462848 2 mac80211,rt2x00lib

> **chili555 said:**
> Is there a wireless interface, ideally wlan0, here?```
iwconfig
```

Nothing appears

> **chili555 said:**
> Are there any clues in the log?```
dmesg |  grep rt2
```

> 0x07 failed for offset 0x101c with error -110
[ 274.879422] ieee80211 phy0: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110
[ 274.983429] ieee80211 phy0: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110
[ 274.983563] ieee80211 phy0: rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x0000101c, value=0xffffffff
[ 275.087445] ieee80211 phy0: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110
[ 275.191339] ieee80211 phy0: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110
...

Thanks! ):P[/FONT]

---

### Post by chili555 on 2015-09-03
Wow!> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110 I suggest you try the fix at post #22 here: [http://ubuntuforums.org/showthread.php?t=2276483&page=3](http://ubuntuforums.org/showthread.php?t=2276483&page=3)

---

### Post by lubuntwf on 2015-09-04
Bad news...
> sudo apt-get install build-essential linux-headers-generic
> Reading package lists ... Done
 Building dependency tree
 Reading state information ... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

> cd ~/Desktop/backports-4.1-rc1-1 
make defconfig-wifi        (second)
make        (third)
sudo make install        (fourth)
second and third ==> see next quote
fourth ==> sudo: make: command not found
> The program 'make' can be found in the following packages:
 * make
 * make-guile
Try: **_sudo apt-get install_** <selected package> **I write in the terminal**

> Reading package lists ... Done
Building dependency tree
Reading state information ... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

Reboot the computer and doesn´t work USB wireless device...
What can I do?

Thanks! ):P

---

### Post by chili555 on 2015-09-04
> sudo apt-get install build-essential linux-headers-generic
Reading package lists ... Done
Building dependency tree
Reading state information ... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
Please start with:```
sudp apt-get update
```And then try again. If there is any error, stop and post it as all further steps will also be ineffective.

---

### Post by lubuntwf on 2015-09-04
```
sudo apt-get update
```
I'm not getting on the Internet.
Where can I download the packages? (from another computer)
> Err [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security InRelease
  
Err [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security Release.gpg
  Temporary failure to resolve "security.ubuntu.com"
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) vivid InRelease
  
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) vivid-updates InRelease
  
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) vivid-backports InRelease
  
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) vivid Release.gpg
  Temporary failure to resolve "es.archive.ubuntu.com"
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) vivid-updates Release.gpg
  Temporary failure to resolve "es.archive.ubuntu.com"
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) vivid-backports Release.gpg
  Temporary failure to resolve "es.archive.ubuntu.com"
Reading package lists ... Done
W: Failed to get [http://es.archive.ubuntu.com/ubuntu/dists/vivid/InRelease](http://es.archive.ubuntu.com/ubuntu/dists/vivid/InRelease)

W: Failed to get [http://es.archive.ubuntu.com/ubuntu/dists/vivid-updates/InRelease](http://es.archive.ubuntu.com/ubuntu/dists/vivid-updates/InRelease)

W: Failed to get [http://es.archive.ubuntu.com/ubuntu/dists/vivid-backports/InRelease](http://es.archive.ubuntu.com/ubuntu/dists/vivid-backports/InRelease)

W: Failed to get [http://security.ubuntu.com/ubuntu/dists/vivid-security/InRelease](http://security.ubuntu.com/ubuntu/dists/vivid-security/InRelease)

W: Failed to get  [http://security.ubuntu.com/ubuntu/dists/vivid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/vivid-security/Release.gpg)  Temporary failure to resolve "security.ubuntu.com"

W: Failed to get  [http://es.archive.ubuntu.com/ubuntu/dists/vivid/Release.gpg](http://es.archive.ubuntu.com/ubuntu/dists/vivid/Release.gpg) Temporary  failure to resolve "es.archive.ubuntu.com"

W: Failed to get  [http://es.archive.ubuntu.com/ubuntu/dists/vivid-updates/Release.gpg](http://es.archive.ubuntu.com/ubuntu/dists/vivid-updates/Release.gpg)  Temporary failure to resolve "es.archive.ubuntu.com"

W: Failed to get  [http://es.archive.ubuntu.com/ubuntu/dists/vivid-backports/Release.gpg](http://es.archive.ubuntu.com/ubuntu/dists/vivid-backports/Release.gpg)  Temporary failure to resolve "es.archive.ubuntu.com"

W: Failed to download some index files are omitted, or old ones used instead.


I've also tried without success:
```
sudo apt install build-essential
```
> Reading package lists ... Done
 Building dependency tree
 Reading state information ... Done
 Package build-essential is not available, but is Referred to by another package.
 This May Mean That the package is missing, you has-been obsoleted, or
 is only available from another source

 E: 'build-essential' Package has no installation candidate

Thanks! ):P

---

### Post by chili555 on 2015-09-04
> I'm not getting on the Internet.That is why you are unable to install the packages.

Here is how you install it in about five minutes.

Lubu: "Hey, friend, can I borrow your ethernet connection for just a few minutes? I brought along six of your favorite beverage."

Friend: "Sure, Lubu, glad to help you! Let me put a couple of those beverages on ice."

You then open a terminal and do:

```
sudo apt-get install linux-headers-generic build-essential 
wget https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.1-rc1/backports-4.1-rc1-1.tar.gz
tar -zxvf backports-4.1-rc1-1.tar.gz
cd backports-4.1-rc1-1
make defconfig-wifi
make
sudo make install
```
Reboot.

Your wireless should now be working. Detach the ethernet, thank the friend and enjoy!

Here is how to do it in about five days...maybe.

Go here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Select Vivid in the drop-down box. Search for linux-headers-generic and build-essential. Be sure to locate their dependencies and the dependencies of the dependencies. Be sure to download the correct version, either 32- or 64-bit. Once you've download about fifteen or so packages on another computer, transfer them with a USB stick or similar to the desktop of your Ubuntu computer. Open a terminal and install them:

```
cd ~/Desktop
sudo dpkg -i *.deb

```
It may complain that a package is missing a dependency. If so, download that and add it to the desktop and try again.

Write many posts on the forum to tell old Chili how you're stuck. Rinse and repeat.

Once that's all done, get this: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.1-rc1/backports-4.1-rc1-1.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.1-rc1/backports-4.1-rc1-1.tar.gz)  Download it and then transfer it to your desktop, too. Right-click it and select 'Extract Here.' Now, back to the terminal.

```
cd ~/Desktop/backports-4.1-rc1-1
make defconfig-wifi
make
sudo make install
```

Your wireless should now be working.

In either event, when Update Manager installs a later kernel, known as linux-image, after the requested reboot, you must recompile:

```
cd ~/Desktop/backports-4.1-rc1-1
make clean
make defconfig-wifi
make
sudo make install
```Reboot.


Please retain the files and these instructions for that time.

---

### Post by lubuntwf on 2015-09-05
Still doesn´t work...

```
Reading package lists ... Done
Building dependency tree
Reading state information ... Done
You might want to run 'apt-get -f install' to correct it.
The following packages have unmet dependencies:
 build-essential: Depends: libc6-dev but it is not installable or
                            libc-dev but it is not installable
                   It Depends: gcc (> = 4: 4.4.3) but it is not installable
                   Depends: g ++ (> = 4: 4.4.3) but it is not installable
                   Depends: make but it is not installable
                   It Depends: dpkg-dev (> = 1.13.5) but it is not installable
 linux-generic: Depends: linux-headers-generic (= 3.19.0.15.14) but 3.19.0.26.25 is installed
 linux-headers-generic: Depends: linux-headers-generic-3.19.0-26 but it is not installable
E: unmet dependencies. Try again using -f.
@: ~ / Desktop / backports-4.1-RC1-1 $ apt-get -f install
+ E: Could not open the lock file "/ var / lib / dpkg / lock" - open (13: Permission denied)
E: Could not lock the administration directory (/ var / lib / dpkg /), is it as root?
```

---

### Post by chili555 on 2015-09-05
> You might want to run 'apt-get -f install' to correct it.By all means, please do so.>   + E: Could not open the lock file "/ var / lib / dpkg / lock" - open (13: Permission denied)
E: Could not lock the administration directory (/ var / lib / dpkg /), is it as root?              Is some other process sitting open? Synaptic? Update Manager?? Please close it or them and try again.> The following packages have unmet dependencies:
 build-essential: Depends: libc6-dev but it is not installable or
                            libc-dev but it is not installable
                   It Depends: gcc (> = 4: 4.4.3) but it is not installable
                   Depends: g ++ (> = 4: 4.4.3) but it is not installable
                   Depends: make but it is not installable
                   It Depends: dpkg-dev (> = 1.13.5) but it is not installable
 linux-generic: Depends: linux-headers-generic (= 3.19.0.15.14) but 3.19.0.26.25 is installed
 linux-headers-generic: Depends: linux-headers-generic-3.19.0-26 but it is not installableRemeber I talked about the dependencies of the dependencies? This message is telling you more you need. Go get them and try again.

---

### Post by lubuntwf on 2015-09-06
I only see the networks, but I can´t connect.

I leave it as impossible...

Any OS alternative? More easier and simpler?
Not having to install anything or only install Linux drivers from Mediatek
[http://www.mediatek.com/en/downloads1/downloads](http://www.mediatek.com/en/downloads1/downloads)

Thanks.

---

### Post by RichardET on 2015-09-06
since it's a usb wireless, why not research what is compatible, buy one, then use the new device?  why all this stress?

---

### Post by deadflowr on 2015-09-07
```
Reading package lists ... DoneBuilding dependency tree
Reading state information ... Done
You might want to run 'apt-get -f install' to correct it.
The following packages have unmet dependencies:
 build-essential: Depends: libc6-dev but it is not installable or
                            libc-dev but it is not installable
                   It Depends: gcc (> = 4: 4.4.3) but it is not installable
                   Depends: g ++ (> = 4: 4.4.3) but it is not installable
                   Depends: make but it is not installable
                   It Depends: dpkg-dev (> = 1.13.5) but it is not installable
 linux-generic: Depends: linux-headers-generic (= 3.19.0.15.14) but 3.19.0.26.25 is installed
 linux-headers-generic: Depends: linux-headers-generic-3.19.0-26 but it is not installable
E: unmet dependencies. Try again using -f.
@: ~ / Desktop / backports-4.1-RC1-1 **$ apt-get -f install**
+ E: Could not open the lock file "/ var / lib / dpkg / lock" - open (13: Permission denied)
E: Could not lock the administration directory (/ var / lib / dpkg /), is it as root?
```

From the bolded part, you ran this as a normal user, so the error response is typical.
Add sudo to the front of the command.
And the command should run as expected, without those errors.

---

