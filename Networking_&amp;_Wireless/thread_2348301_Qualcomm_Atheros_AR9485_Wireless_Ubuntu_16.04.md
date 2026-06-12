---
title: "Qualcomm Atheros AR9485 Wireless Ubuntu 16.04"
date: 2017-01-02
forum: Networking &amp; Wireless
---

### Post by Tarhawk on 2017-01-02
I thought I would start a new thread on my particular problem with this wireless card.  I have seen other problems with this particular card but so far none of the workarounds seem to work and the problems have been with older versions of Ubuntu and none specific to Toshiba Satellite notebooks.

Here is the problem.

Recently upgraded to U 16.04.  Wireless connects and works just fine when I boot up and start my initial session.  However, when I close the laptop and it goes to sleep then turn it back on it will not recognize the particular wireless network I am connected to.  Oddly, it recognizes other wireless networks, just not mine.  I have to restart the computer to get it to connect to my wireless.  It is not a problem with the router or signal, my other devices connect fine when this one is not connecting after coming awake from sleep mode.

Running Ubuntu 16.04 on a Toshiba Satellite C55 B5196

Thank you in advance for the help.

Here is some output of the wireless card when it is not connecting after waking up from sleep mode.

Output from [COLOR=#000000][FONT=verdana]iwconfig:
[/FONT][/COLOR]
```
[COLOR=#2f2213][FONT=Consolas, Lucida Console, Monaco, monospace]lo       no wireless extensions.[/FONT][/COLOR]


[COLOR=#2f2213][FONT=Consolas, Lucida Console, Monaco, monospace]wlan0    IEEE 802.11bgn  ESSID:off/any  [/FONT][/COLOR]
[COLOR=#2f2213]          [FONT=Consolas, Lucida Console, Monaco, monospace]Mode:Managed Access Point: Not-Associated   Tx-Power=16 dBm   [/FONT][/COLOR]
[COLOR=#2f2213]          [FONT=Consolas, Lucida Console, Monaco, monospace]Retryshort limit:7   RTS thr:off   Fragment thr:off[/FONT][/COLOR]
[COLOR=#2f2213]          [FONT=Consolas, Lucida Console, Monaco, monospace]PowerManagement:off[/FONT][/COLOR]
[COLOR=#2f2213]          [/COLOR]
[COLOR=#2F2213][FONT=Consolas]eth0     no wireless extensions.[/FONT][/COLOR]
```

Output from [COLOR=#2F2213][FONT=Consolas]lspci | grep Wireless[/FONT][/COLOR]

```

[COLOR=#2F2213][FONT=Consolas]02:00.0Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter(rev 01)[/FONT][/COLOR]
```

---

### Post by jeremy31 on 2017-01-02
Please open terminal and run ```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info
```
Then put it in sleep mode and wake, then
```
./wireless-info
```
When you get back online post the contents of the wireless-info.**txt** file or attach the tar.gz file that is created

---

### Post by Tarhawk on 2017-01-02
Attached is the tar.gz wireless info file.

Oddly enough, after I put in the code then put it to sleep and ran the wireless info command the connection reestablished.  That is a first since I updated the ubuntu release.  I would still like to make sure the issue is resolved and possibly what the problem was in case others with this card and similar laptop run into this issue.

---

### Post by jeremy31 on 2017-01-02
You are still using Ubuntu 15.10 and should upgrade to 16.04
For the wireless I would change settings on the wireless router, set it on channel 9 and change encryption to WPA2-AES, WPA2-PSK, or WPA2 only depending on what router you have

I say to use channel 9 because at the time the script was run the channel had no other access points.  You appear to be in Spain and the router may have been on auto channel and it is likely capable of channels 1-14 in Spain but the wifi card is only capable of channels 1-11

iw reg get from your results
```
country ES: DFS-ETSI
	(2400 - 2483 @ 40), (N/A, 20), (N/A)
```
Channel list from wifi card
```
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
```

---

### Post by Tarhawk on 2017-01-02
I recently upgraded to 16.04, not sure why it would say I am still on 15.10.  System info also shows that I am on 16.04.

I used to live in Spain and have recently moved back stateside to US territories.

I am not sure how I could affect an update of either of those two bits of information in my wireless output?  Any suggestions would be appreciated.

---

### Post by jeremy31 on 2017-01-02
What happens when you ```
sudo apt-get update
```

---

### Post by Tarhawk on 2017-01-02
Update seems to run fine, pulling from 16.04 US based sources.  Output below.  

The only strange thing I notice, though I am a total linux novice, is the last line:  **N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension**


```
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InReleaseIgn:2 http://dl.google.com/linux/chrome/deb stable InRelease
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Hit:4 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:5 http://archive.canonical.com/ubuntu xenial InRelease                     
Get:6 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  
Get:8 http://us.archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu xenial-proposed InRelease [253 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [302 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [183 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [121 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [145 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [2.520 B]
Get:15 http://us.archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [212 B]
Get:16 http://us.archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64 DEP-11 Metadata [212 B]
Get:17 http://us.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [208 B]
Get:18 http://us.archive.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [68,2 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [43,0 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [19,4 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [25,6 kB]
Get:22 http://us.archive.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata [212 B]
Get:23 http://us.archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 DEP-11 Metadata [10,2 kB]
Get:24 http://us.archive.ubuntu.com/ubuntu xenial-proposed/universe DEP-11 64x64 Icons [10,9 kB]
Get:25 http://us.archive.ubuntu.com/ubuntu xenial-proposed/multiverse amd64 DEP-11 Metadata [212 B]
Get:26 http://us.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 DEP-11 Metadata [36,5 kB]
Get:27 http://us.archive.ubuntu.com/ubuntu xenial-proposed/main DEP-11 64x64 Icons [18,0 kB]
Fetched 1.547 kB in 2s (771 kB/s)                                        
Reading package lists... Done
N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension



```

---

### Post by jeremy31 on 2017-01-02
Definitely strange as updating to xenial should have replaced /etc/lsb-release with the correct info for 16.04 and the script result showed you were using the 3.19 kernel that is EOL
Post results for ```
dpkg -s linux-image-generic
```

---

### Post by Tarhawk on 2017-01-02
Here is the output:

```
Package: linux-image-genericStatus: install ok installed
Priority: optional
Section: kernel
Installed-Size: 12
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux-meta
Version: 4.4.0.58.61
Depends: linux-image-4.4.0-58-generic, linux-image-extra-4.4.0-58-generic, linux-firmware
Recommends: thermald
Description: Generic Linux kernel image
 This package will always depend on the latest generic kernel image
 available.



```

---

### Post by jeremy31 on 2017-01-02
Do you have a second linux distro installed, perhaps since the Ubuntu install?

---

### Post by Tarhawk on 2017-01-02
I am pretty sure that I don't. I never installed a different distribution side by side.  I do run windows as a dual boot but really don't use it.  Attached is a picture of the grub menu upon startup, pretty sure there is just one distribution installed.

---

### Post by jeremy31 on 2017-01-02
I would start a thread in the Installation subforum if you check ```
cat /etc/lsb-release; uname -a
```
and you don't see info about Ubuntu 16.04 and kernel 4.4.0-58-generic.

---

### Post by Tarhawk on 2017-01-02
I just want to be sure I understand the issue.  The kernel is out of date or EOL.  Which kernel should 16.04 be operating on at this point?

---

### Post by jeremy31 on 2017-01-02
According to the info you posted the uname -a command should say 4.4.0-58-generic and not 3.19.0-?

---

### Post by Tarhawk on 2017-01-02
Well this is a strange indeed.  I read over the wireless info file and indeed it shows 15.10 and 3,19 kernel however when I run the last code you gave me this is what it comes up with.
Is this something I should even bother with, will it effect the performance of the system or cause update problems?

```

DISTRIB_ID=UbuntuDISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS"
Linux B 4.4.0-58-generic #79-Ubuntu SMP Tue Dec 20 12:12:35 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux



```

---

### Post by jeremy31 on 2017-01-02
Run the wireless script again and post results

---

### Post by Tarhawk on 2017-01-02
Hmm. Odd indeed.  Release info seems to be updated.  Looks to be resolved.

```


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-58-generic #79-Ubuntu SMP Tue Dec 20 12:12:35 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7
```

---

### Post by Tarhawk on 2017-01-04
I unmarked this thread as solved because the original problem has returned.  It should be noted, that I really did not change anything originally to affect a change in wireless functionality, it just started working correctly for the last two days.  Now though, when I close the laptop or put it to sleep it wont recognize the network I was connected to though it is there.  Wireless card recognizes other networks upon waking up, just not my default.  Thanks for the help in advance.

---

### Post by jeremy31 on 2017-01-04
Did you ever change the router to use channel 9?  If you brought the router with you from Spain, it is likely able to use channels higher than 11 in 2.4 GHz which won't work with the AR9485 and using channels higher than 11 in the US is illegal

If you did change to channel 9, then the next time the issue happens run ```
./wireless-info
```
And post the new results

---

### Post by Tarhawk on 2017-01-04
The router is American, I did not bring it from Spain and the laptop is an American laptop.  I don't think it is the router because with 15.10 it was working fine, the problem began after I upgraded the OS.   Attached is the latest wireless info from the last incident.  What is strange is when I wake the laptop it does not recognize the wireless.  But when I entered wireless info code it reconnected and functions normally.

---

