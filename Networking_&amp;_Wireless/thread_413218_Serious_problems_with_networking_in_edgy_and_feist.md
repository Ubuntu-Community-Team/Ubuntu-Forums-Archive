---
title: "Serious problems with networking in edgy and feisty!"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by gsyoungblood on 2007-04-18
I'm hoping someone can point me to a resource to fix this problem. Earlier I installed 6.10 from CD immediately followed by an upgrade. My intent was to then upgrade to feisty, but that's where the fun began. See: [http://ubuntuforums.org/showthread.php?t=412795](http://ubuntuforums.org/showthread.php?t=412795)

At first I thought there was corruption with a couple of mirrors. Then it became obvious it was something wrong with the networking. Switching to wireless made things a little better, but not by much. I was able to upgrade to feisty, but installing mysql-server turned into a multi-hour ordeal.

To summarize the very painful process, I ran wget to get the packages for mysql-server-5.0 manually and then did an md5sum on the file and compared that with the value in the Packages file (/var/lib/apt/lists/...). They didn't match. I ran the exact same command again - 6 times. All 6 times the file had a different md5sum. Next, I switched to a different computer (connected to the same hub/router/network/isp/etc.) and ran the exact same wget command using the same mirror as my ubuntu installation. The md5sum on this computer matched the md5sum  in the packages file. The md5sum on the 6 tries from the laptop all had different values.

The laptop works fine with XP and with other distros. It's a problem that only appears with Ubuntu (edgy and feisty).

The laptop is an IBM Thinkpad T43p. Eth0 is using tg3 driver. I forget what the wireless driver is using. Problem exists on kernels 2.6.17-10-generic, 2.6.17-11-generic, and 2.6.20-15-generic. 

This is the first time I've seen problems like this. Judging by the threads in the install/upgrade forum, I'm not the only one seeing similar problems. A couple of other threads I know about: [http://ubuntuforums.org/showthread.php?t=410232](http://ubuntuforums.org/showthread.php?t=410232) and [http://ubuntuforums.org/showthread.php?t=412167](http://ubuntuforums.org/showthread.php?t=412167)

---

### Post by gsyoungblood on 2007-04-18
I guess it's possible that the problem is isolated to wget or something that wget relies on. That is, assuming the apt-get and update-manager processes rely on wget to retrieve files. Of course, that does not explain the malformed incoming MAC error SSH was returning earlier, though I don't know why SCP worked to copy files from one computer to the other computer. 

Any ideas are appreciated. Hopefully this can be fixed easily.

---

### Post by gsyoungblood on 2007-04-19
The problem is most definitely with ubuntu. I booted into Windows and have no problems.

The problem persists on wireless or wired network interfaces, only with ubuntu. Other machines on the network have no problems. Moving the ubuntu laptop to a different network (slower internet connection) seems to help, but it is not guaranteed. And, if I get a file from a local machine on the network, the problem remains.

The problem also is seen using ftp and not wget, so it's not wget. The problem is isolated to the ubuntu networking stack or something else within ubuntu. 

The Thinkpad T43p has Broadcom NetXtreme 10/100/1000 NIC and is using the tg3 (tigon3) driver. The link comes up as 100 full duplex, with tx and rx flow control enabled via autonegotiation. I've tried disabling flow control and that doesn't make a difference. The wireless interface is Intel 2200bg, and I don't know what driver it is using.

The initial wired and wireless network are using a Linksys wrt54g w/dd-wrt firmware. There are several other computers plugged into this network. None of the other systems, including the laptop while running windows instead of ubuntu, have any problems. The second network uses an actiontek dsl router plugged into a switch.

It seems whatever the problem is, it takes fast networks to see the problem. The first network is able to download mysql-server-5.0 (the test file, 25 megabytes) at about 1.5 m/s. The second network is about 1.5 k/s. The second network will still occasionally have problems, but not all the time. The faster, first network always has issues downloading that file. The wireless download speed is usually between 250 and 550 k/s.

I ran memtest for several hours, thinking the problem might be memory, but no errors were detected. I've copied the good file to/from the hard drive and no errors there. The only thing I can isolate it to is the networking stack itself on both 6.10 and 7.04.

---

### Post by gsyoungblood on 2007-04-22
I am returning to report that (at least in this case) the problem was hardware related. The drive and memory tested OK, but something is definitely wrong with the laptop I was using. Possibly cache or problems moving data around DMA channels, I don't know which.

I obtained a replacement laptop from the office identical to the one I was having problems with. This time I have had zero problems. Feisty is working just fine, including the ability to install packages from the network.

---

