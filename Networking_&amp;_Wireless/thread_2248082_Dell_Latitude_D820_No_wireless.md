---
title: "Dell Latitude D820 No wireless?"
date: 2014-10-12
forum: Networking &amp; Wireless
---

### Post by chance5 on 2014-10-12
I have a Dell Latitude D820 with Windows XP Pro Service Pack 3. The wireless works great on it, but as soon as I switched over to Ubuntu 
(I also tried Mint), it wouldn't even recognize that I have a wireless chip. It only lets me select from wired connections. I'm new to Ubuntu so I don't know how to install the drivers necessary to allow my laptop to find wi-fi with Ubuntu or Mint. And how do I download them if I can't connect to wi-fi? Also will I be able to get the wi-fi drivers installed if I don't have Ubuntu installed and I'm just working off of the DVD boot? Thanks for the help in advance, and sorry if this was answered in the sticky, I didn't quite understand the sticky.

---

### Post by chili555 on 2014-10-12
Let's start where the sticky starts. Please open a terminal and identify your wireless card with this command:```
lspci -nn | grep 0280
```That funny pipe symbol | is on the right side of my US keyboard on the same key with \.

Post the result and we'll proceed.

---

### Post by chance5 on 2014-10-12
> **chili555 said:**
> Let's start where the sticky starts. Please open a terminal and identify your wireless card with this command:```
lspci -nn | grep 0280
```That funny pipe symbol | is on the right side of my US keyboard on the same key with \.

Post the result and we'll proceed.
I get this out of terminal:

Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (Rev 01)

---

### Post by chili555 on 2014-10-12
If you can hook up the ethernet for a few moments, please open a terminal and do:```
sudo apt-get update
sudo apt-get install firmware-b43-installer
```If you have no, none, zero connectivity, even after you asked your neighbor and friends for a two-minute session, you can get the firmware on some other computer as here: [http://ubuntuforums.org/showthread.php?t=2098717&p=12426843#post12426843](http://ubuntuforums.org/showthread.php?t=2098717&p=12426843#post12426843)

Then reboot.

Post back if you need additional guidance.

---

### Post by chance5 on 2014-10-13
> **chili555 said:**
> If you can hook up the ethernet for a few moments, please open a terminal and do:```
sudo apt-get update
sudo apt-get install firmware-b43-installer
```If you have no, none, zero connectivity, even after you asked your neighbor and friends for a two-minute session, you can get the firmware on some other computer as here: [http://ubuntuforums.org/showthread.php?t=2098717&p=12426843#post12426843](http://ubuntuforums.org/showthread.php?t=2098717&p=12426843#post12426843)

Then reboot.

Post back if you need additional guidance.

I just got back to try what you said. I hooked the ethernet from the modem directly into the ethernet port on my laptop. It registered that there was an ethernet port, but refused to connect. It just won't connect even through a wired connection

EDIT: I figured out how to get the wired connection to work

EDIT2: When typing "sudo apt-get install firmware-b43-installer" I get the error "E: unable to locate package firmware-b43-installer". I did the sudo apt-get update first and that ran perfectly fine

---

### Post by chili555 on 2014-10-13
Which Ubuntu version are you using?```
lsb_release -d
```

---

### Post by chance5 on 2014-10-13
Ubuntu 14.0.1 LTS

If it helps, i haven't installed Ubuntu yet and am still strictly working off of the Disk boot. I'm afraid to completely wipe XP from this laptop until I'm positive I can get this to work.

---

### Post by jeremy31 on 2014-10-13
> **chance5 said:**
> Ubuntu 14.0.1 LTS

If it helps, i haven't installed Ubuntu yet and am still strictly working off of the Disk boot. I'm afraid to completely wipe XP from this laptop until I'm positive I can get this to work.

There should be the option to install along with windows or similar when you choose to install, but do a full backup of your windows install and make recovery disks before trying in case a mistake is made

---

### Post by chili555 on 2014-10-13
The package is most certainly available in 14.10: [http://packages.ubuntu.com/trusty/firmware-b43-installer](http://packages.ubuntu.com/trusty/firmware-b43-installer)

Would you please humor an old man and try once again in case there was a typo? I know, I know.

Your device will certainly work in Ubuntu 14.10 with no issues once the needed firmware is installed.

---

### Post by chance5 on 2014-10-13
Could it be that I don't have Ubuntu installed? Or should it still work off of a boot disk? I even tried to do the manual installation of the package in the previous link you provided but when i chose to save the file to my desktop it didn't show up on my desktop at all. But if it should work off of a boot disk then I'll try again and update you.

---

### Post by chance5 on 2014-10-14
I'll go ahead and paste exactly what I get out of terminal while I'm in Linux:
```

ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease                                 
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/main Translation-en_US
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/main Translation-en
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/restricted Translation-en_US
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [59.7 kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release.gpg [933 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release                    
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release [59.7 kB]               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted i386 Packages
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [142 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages [333 kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [14 B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [72.4 kB] 
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted i386 Packages [5,820 B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en [151 kB]   
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en [14 B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en [1,736 B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en_US
Fetched 827 kB in 3s (259 kB/s)
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-installer

```

---

### Post by chili555 on 2014-10-14
It should work perfectly well off the boot disk, as far as I know.

---

### Post by chance5 on 2014-10-15
> **chance5 said:**
> I'll go ahead and paste exactly what I get out of terminal while I'm in Linux:
```

ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease                                 
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/main Translation-en_US
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/main Translation-en
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/restricted Translation-en_US
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [59.7 kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release.gpg [933 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release                    
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release [59.7 kB]               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted i386 Packages
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [142 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages [333 kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [14 B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [72.4 kB] 
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted i386 Packages [5,820 B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en [151 kB]   
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en [14 B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en [1,736 B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en_US
Fetched 827 kB in 3s (259 kB/s)
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-installer

```


Nothing seems unusual here? I plan on buying a new laptop soon if this doesn't work. Probably a Lenovo Z50 since this Dell Latitude is old and just not worth it

---

### Post by chili555 on 2014-10-15
I think I see the problem here. You are using the repositories for main and restricted only:> Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages [333 kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [14 B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [72.4 kB] 
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted i386 Packages [5,820 B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en [151 kB]   
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en [14 B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en [1,736 B]What we are not seeing is the repository where firmware-b43-installer is located; it's called multiverse.> Package firmware-b43-installer

trusty (14.04LTS) (kernel): firmware installer for the b43 driver [[COLOR="#FF0000"]multiverse[/COLOR]] 
1:018-2: allPlease go to Software and Updates and check the 'multiverse' box to include those packages. Then re-run:```
sudo apt-get update
sudo apt-get install firmware-b43-installer
```I think we are almost there!

---

### Post by chance5 on 2014-10-16
So I did exactly what you said, and it installed the b43 installer, however I now see this [http://i.imgur.com/abYuqZV.jpg](http://i.imgur.com/abYuqZV.jpg) Where it says "Broadcom Xtreme BCM5752" That is blacked out and I cannot click on it. I tried rebooting, but when I turned my computer back on the b43 drivers weren't installed anymore and after reinstalling i got the same problem.

---

### Post by chili555 on 2014-10-16
Let's look for clues in the log:```
dmesg | grep -e wlan -e b43
rfkill list all
```Very interesting!

---

