---
title: "WiFi driver not working on Ubuntu boot"
date: 2015-06-12
forum: Networking &amp; Wireless
---

### Post by roy27 on 2015-06-12
I'm trying to install Ubuntu on my desktop. I need to first make sure my hardware works before I install. My ASUS PCE-AC68 802.11ac Network Adapter doesn't work. It seems like the drivers are present, I even tried reinstalling them and it told me I already have them. I had the same problem when I was live booting Debian, the thing that fixed the problem is some deb files that a guy "rolled up" for me that I then installed, and then ran some code (I think to activate the modules), which gave me internet. By the way, I tried disabling/re-enabling/reinstalling drivers, nothing worked). The proprietary driver does in fact show up, and I enabled it, but it seems to be doing nothing.  Here is the code with the information:  [CODE] ubuntu@ubuntu:~$ apt-cache policy bcmwl-kernel-source bcmwl-kernel-source:   Installed: 6.30.223.141+bdcom-0ubuntu2   Candidate: 6.30.223.141+bdcom-0ubuntu2   Version table:  *** 6.30.223.141+bdcom-0ubuntu2 0         500 cdrom://Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)/ trusty/restricted amd64 Packages         500 http://archive.ubuntu.com/ubuntu/ trusty/restricted amd64 Packages         100 /var/lib/dpkg/status ubuntu@ubuntu:~$ apt-cache policy broadcom-sta-source  N: Unable to locate package broadcom-sta-source ubuntu@ubuntu:~$ lspci -vvnn | grep -A 9 Network 05:00.0 Network controller [0280]: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03) 	Subsystem: ASUSTeK Computer Inc. Device [1043:85df] 	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx- 	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- TAbort-

---

### Post by chili555 on 2015-06-13
With a temporary internet connection by ethernet or whatever means possible, please do:```
sudo apt-get update
sudo apt-get -y upgrade
```I suspect that the later version of bcmwl-kernel-source will install and work.

I believe this is the version you need: [http://packages.ubuntu.com/trusty-updates/bcmwl-kernel-source](http://packages.ubuntu.com/trusty-updates/bcmwl-kernel-source) You may need to download and install it yourself if *upgrade* doesn't help. Please post back if you need guidance on the exact steps.

---

### Post by roy27 on 2015-06-13
> **chili555 said:**
> With a temporary internet connection by ethernet or whatever means possible, please do:```
sudo apt-get update
sudo apt-get -y upgrade
```I suspect that the later version of bcmwl-kernel-source will install and work.

I don't have Ethernet internet access.

> **chili555 said:**
> 
I believe this is the version you need: [http://packages.ubuntu.com/trusty-updates/bcmwl-kernel-source](http://packages.ubuntu.com/trusty-updates/bcmwl-kernel-source) You may need to download and install it yourself if *upgrade* doesn't help. Please post back if you need guidance on the exact steps.

I think I tried installing that package, I think it told me the computer already had it (and it does have a package like that, that just doesn't connect to the internet). But I'll try it now.

---

### Post by chili555 on 2015-06-13
> I think it told me the computer already had it Your computer has:> Installed: 6.30.223.[COLOR="#FF0000"]141[/COLOR]+bdcom-0ubuntu2I linked, and suggest you install 6.30.223.[COLOR="#FF0000"]248[/COLOR]+bdcom-0ubuntu0.1.

Although they appear similar, they aren't the same.

---

### Post by roy27 on 2015-06-13
Okay, in live boot it worked.             :)                                                                                                                                                                                                                                                                                                                                                               However,  after I actually installed the OS on my hard drive, it stopped working (obviously) but it also won't let me use that same package!   "Dependency is not satisfiable: dkms" I also tried installing the wl packages and other packages and they all give me this error: "Dependency not satisfiable."                                                                                                                                                                                                                                                                                                                                                On top of this, I now can't even boot into my Windows because gru b doesn't feel like displaying it, and the possible fix to this (reinstalling grub) requires internet access. Edit: No matter how many spaces or paragraphs I make on this post, it still defaults and brings them back to nothing.

---

### Post by chili555 on 2015-06-13
Here is how you can get the files from the install DVD or USB: [http://askubuntu.com/questions/453252/ubuntu-cant-detect-wifi-networks-on-macbookpro-13-3/453669#453669](http://askubuntu.com/questions/453252/ubuntu-cant-detect-wifi-networks-on-macbookpro-13-3/453669#453669)

The device ID is different, however, the process to retrieve and install bcmwl-kernel-source and dkms are the same.

---

### Post by roy27 on 2015-06-13
thank you : )  Edit: If you could tell me why all the message I now edit on my computer take away all the spaces in between sentences, that would also be useful to know.

---

### Post by chili555 on 2015-06-13
> **roy27 said:**
> thank you : )  Edit: If you could tell me why all the message I now edit on my computer take away all the spaces in between sentences, that would also be useful to know.I haven't any idea. That's a different question that I suggest you post here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

