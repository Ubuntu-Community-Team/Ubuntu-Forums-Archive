---
title: "Internet no longer working after upgrading from Ubuntu 18.04 to 20.04"
date: 2020-06-21
forum: Networking &amp; Wireless
---

### Post by abdullahtrees on 2020-06-21
Let's cut to the chase... TL;DR I'm a long time Windows user and am new to Linux. I do not really think highly of Linux because of its complexities and hard to use/repair situations such as these ones. I upgraded from Ubuntu 18.04 to 20.04 using `do-release-upgrade`, and it went quite smoothly, preserving my GRUB boot menu and software settings, but the upgrade has rendered my system completely unable to use the Internet. How bad is it? **The network activity lights next to my LAN port don't light up at all, as if the network wire was disconnected**... I actually initially thought the network adapter on my laptop got fried or something, but it works perfectly fine on other OS's (I am currently triplebooting 3 OS's, Internet works fine on the other two)


Here is the inxi output for some hardware info: Keep in mind this was done back when I still had Linux Mint(which I don't have anymore),so some information, especially software-related, maybe wrong but hardware info should be pretty much the same. ```
inxi -Fxz
System:
  Host: HP-ENVY-m6-Notebook-PC 
  Kernel: 4.15.0-20-generic x86_64 bits: 64 compiler: gcc v: 7.3.0 
  Desktop: Cinnamon 4.0.8 Distro: Linux Mint 19.1 Tessa 
  base: Ubuntu 18.04 bionic 
Machine:
  Type: Laptop System: Hewlett-Packard product: HP ENVY m6 Notebook PC 
  v: <filter>  serial: <filter> 
  Mobo: Hewlett-Packard model: 18A6 v: 74.52 serial: <filter> 
  UEFI [Legacy]: Insyde v: F.11 date: 08/15/2012 
CPU:
  Topology: Quad Core model: AMD A10-4600M APU with Radeon HD Graphics 
  bits: 64 type: MCP arch: Piledriver rev: 1 L2 cache: 2048 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm 
  bogomips: 18363 
  Speed: 1405 MHz min/max: 1400/2300 MHz Core speeds (MHz): 1: 1445 2: 1445 
  3: 1865 4: 2213 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Hewlett-Packard driver: r8169 v: 2.3LK-NAPI port: 2000 
  bus ID: 01:00.2 
  IF: eno1 state: down mac: <filter> 
Drives:
  Local Storage: total: 698.64 GiB used: 13.48 GiB (1.9%) 
  ID-1: /dev/sda vendor: Toshiba model: MQ01ABD075 size: 698.64 GiB 
Partition:
  ID-1: / size: 49.21 GiB used: 13.48 GiB (27.4%) fs: ext4 dev: /dev/sda3 
Sensors:
  System Temperatures: cpu: 39.6 C mobo: N/A gpu: radeon temp: 37 C 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 180 Uptime: 1m Memory: 3.33 GiB used: 606.0 MiB (17.8%) 
  Init: systemd runlevel: 5 Compilers: gcc: 7.3.0 Shell: bash v: 4.4.19 
  inxi: 3.0.27 


```

And here is the lspci output as well
```
HP-ENVY-m6-Notebook-PC:~$ lspci -knn00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Complex [1022:1410]
    Subsystem: Hewlett-Packard Company Family 15h (Models 10h-1fh) Processor Root Complex [103c:18a6]
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller [1022:780b] (rev 14)
    Subsystem: Hewlett-Packard Company FCH SMBus Controller [103c:18a6]
    Kernel modules: i2c_piix4, sp5100_tco
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller [1022:780d] (rev 01)
    Subsystem: Hewlett-Packard Company FCH Azalia Controller [103c:18a6]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 4 [1022:1404]
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 5 [1022:1405]
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411 PCI Express Card Reader [10ec:5289] (rev 01)
    Subsystem: Hewlett-Packard Company RTL8411 PCI Express Card Reader [103c:18a6]
    Kernel driver in use: rtsx_pci
    Kernel modules: rtsx_pci
01:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    DeviceName: Hanksville Gbe Lan Connection
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:18a6]
    Kernel driver in use: r8169
    Kernel modules: r8169
```

So my suspicions are that the Ubuntu upgrade somehow removed some of the drivers for the hardware in the system, and the Ethernet controller was one of them. Without it, the system is unable to dial a PPPOE connection, and hence I can't use the internet. 

I ask the Ubuntu experts for help on this matter...
Thanks in Advance!
AbdullahTrees

---

### Post by TheFu on 2020-06-21
Can you **ping 1.1.1.1**?
If you can, then it is just a DNS problem, not a network problem.

---

### Post by abdullahtrees on 2020-06-28
> **TheFu said:**
> Can you **ping 1.1.1.1**?
If you can, then it is just a DNS problem, not a network problem.

Hi! Sorry for replying late, but I was very busy. Looks like I'll need to recreate this thread soon to get some help again... 

Anyways, as I've already mentioned in my post, the network indicators near the LAN ports are not lighting up at all, which indicates that this is not just a simple DNS/network configuration issue. I still tried out your ping command, and of course, it didn't work at all. 

```
ping 1.1.1.1
ping: connect: Network is unreachable
```

---

### Post by TheFu on 2020-06-28
```
Kernel driver in use: r8169
```
shows the expected driver is loaded, which is why i ignored the prior driver comment as a non sequitor. if the lspci output isn't recent from the Ubuntu 20.04, that's bad. Unhelpful.

 i missed the PPOE comment. Cannot help with that sort of connection, sorry.  Everywhere I’ve been the last 30 yrs had a router that managed upstream connectivity that wasn't dialup.  Never did any dialup stuff on Linux.

BTW, sometimes a light that doesn't come on is just a broken light or a driver initialization problem.

The ping was requested to see if it was something simple.  Clearly not that  and not very important based on the delay.

---

### Post by abdullahtrees on 2020-06-29
> **TheFu said:**
> ```
Kernel driver in use: r8169
```
shows the expected driver is loaded, which is why i ignored the prior driver comment as a non sequitor. if the lspci output isn't recent from the Ubuntu 20.04, that's bad. Unhelpful.

 i missed the PPOE comment. Cannot help with that sort of connection, sorry.  Everywhere I’ve been the last 30 yrs had a router that managed upstream connectivity that wasn't dialup.  Never did any dialup stuff on Linux.

BTW, sometimes a light that doesn't come on is just a broken light or a driver initialization problem.

The ping was requested to see if it was something simple.  Clearly not that  and not very important based on the delay.

Thanks, but the lspci out is definitely from Ubuntu 20.04, so that's why I put it there, 
So it is interesting to see that lspci reports the network driver is installed, but the lights on the network card are not working: I booted up into the other OS's and the lights are working perfectly fine, so it's probably the latter.

Thank you for your help. Looks like I'll have to reinstall Ubuntu 20.04 from scratch.

---

### Post by TheFu on 2020-06-29
> **abdullahtrees said:**
>  
Thank you for your help. Looks like I'll have to reinstall Ubuntu 20.04 from scratch.

Have you not found other threads in these forums with the same card and similar issues that have been marked as "SOLVED?"  
Did none of those solutions work?

Trouble with realtek NICs happens much more than it should. When the same NIC in my system started having dropped packets, I put a $10 NIC that was laying around in and started using it instead. My issue was different from yours (16.04, not 20.04 and not total failure, just dropped+resent packets). Realtek has a problem with using the same drivers for different cards and versions of cards that show up with the same name. This leads to confusion and issues.

No sure how reinstalling the OS will fix this. If you have other issues with 20.04, that's one thing. But if this is the only problem, I'd search the forums for solutions and try those out, taking careful notes of everything done. Chilli has a good track record posting solutions that solve the realtek issue.

---

### Post by praseodym on 2020-06-29
Can you connect via cell phone tethering? If yes, run
```

sudo apt install build-essential dkms r8168-dkms
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.

If not, download this file (somehow) and save it in your /home folder. [http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.048.00-1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.048.00-1_all.deb) 

Now run in a new terminal

```
sudo dpkg -i *.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
and reboot

---

### Post by TheFu on 2020-06-29
How do we know when the use r8169 or r8168 driver?
How to know when the included kernel driver is fine and when a driver from github is needed? 
Does the identifier 103c:18a6 denote that or can the version of the card as shown by lshw be used?

---

### Post by abdullahtrees on 2020-06-30
> **praseodym said:**
> Can you connect via cell phone tethering? If yes, run
```

sudo apt install build-essential dkms r8168-dkms
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.

If not, download this file (somehow) and save it in your /home folder. [http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.048.00-1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.048.00-1_all.deb) 

Now run in a new terminal

```
sudo dpkg -i *.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
and reboot

I tried installing the package which you mentioned, but sadly, I couldn't connect the laptop to the internet, even with cellphone tethering via Android phones. The laptop was connected briefly to the internet, but the connection was jittery and super-unstable to the point where it was impossible to get the 'sudo apt install build-essential dkms r8168-dkms' command to successfully complete.

Then I tried downloading that .deb installer to try and install that package, but I ran into this dependency error. I'm totally new to Linux, and all of this seems very inconvenient and difficult to understand, so if I could have help on just how to get this running, it'd be great. I'm especially not good with CMD-line, and never was...

```
Selecting previously unselected package r8168-dkms.(Reading database ... 157320 files and directories currently installed.)
Preparing to unpack r8168-dkms_8.048.00-1_all.deb ...
Unpacking r8168-dkms (8.048.00-1) ...
dpkg: dependency problems prevent configuration of r8168-dkms:
 r8168-dkms depends on dkms (>= 2.1.0.0); however:
  Package dkms is not installed.


dpkg: error processing package r8168-dkms (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 r8168-dkms

```

It is extremely sad, but I don't know why Ubuntu 20 is doing this, I never had this problem with Ubuntu 18 and it even supported PPPOE (had a nice little CMD-line wizard for creating a PPPOE connection, called 'pppoeconf', this command doesnt even exist anymore in Ubuntu 20). So I kind of regret upgrading to Ubuntu 20 now... Hope you guys don't get offended or anything, just sharing a noob's thoughts. Thank you so much for your patronage

---

### Post by TheFu on 2020-06-30
> **abdullahtrees said:**
>   So I kind of regret upgrading to Ubuntu 20 now... Hope you guys don't get offended or anything, just sharing a noob's thoughts. Thank you so much for your patronage

No offence taken. We understand the frustration due to poor vendor support.  Realtek is to blame here by not having clear drivers for specific versions of their hardware.

installing a $25 intel PRO/1000 Nic makes this and all future realtek issues go away.

---

### Post by abdullahtrees on 2020-07-01
> **TheFu said:**
> No offence taken. We understand the frustration due to poor vendor support.  Realtek is to blame here by not having clear drivers for specific versions of their hardware.

installing a $25 intel PRO/1000 Nic makes this and all future realtek issues go away.

Yeah but this is a laptop, and one does not simple install an NIC card into a laptop

What I find most intriguing is that this issue was completely nonexistent in Ubuntu 18, and Internet on Ubuntu 18 worked perfectly fine. This leads me to believe that this is a flaw in Ubuntu 20 with them either dropping support for my network card.

---

### Post by TheFu on 2020-07-01
Does the _Try Ubuntu_ environment running 20.04 booted from a flash drive work with the networking? 

if it does, then you can setup a chroot environment for the installed on disk 20.04 then reinstall the build-essential dkms r8168-dkms packages.

---

### Post by abdullahtrees on 2020-07-03
> **TheFu said:**
> Does the _Try Ubuntu_ environment running 20.04 booted from a flash drive work with the networking? 

if it does, then you can setup a chroot environment for the installed on disk 20.04 then reinstall the build-essential dkms r8168-dkms packages.

After booting from Ubuntu 18 and 20 using a USB flash drive, I see that Internet works perfectly once I set an PPPOE connection using ```
sudo pppoeconf
```
[[img]https://i.postimg.cc/Lnx63KPw/image.png[/img]](https://postimg.cc/Lnx63KPw)

However, this command simply doesn't exist on Ubuntu 20. Looks like Ubuntu 20 does not have support for PPPOE connections, so reinstalling Ubuntu 18 is guaranteed to fix this issue. It is in times like these that Windows outshines Linux as they are not so quick to drop features from their OS's, especially something like PPPOE which was probably not something that would've needed much effort anyway. I will now look into ways to get a PPPOE connection running in Ubuntu 20 (although atm Google is not yielding any helpful results for Ubuntu 20, it is too new of an OS)

---

### Post by TheFu on 2020-07-03
When I run pppoeconf on a 20.04 desktop, I see ... 
```
Looking for PPPoE Access Concentrator on ens3...
```
So it seems to be something related to how 20.04 was installed.  I'm running 
```
$ lsb_release -a                                      
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04 LTS
Release:        20.04
Codename:       focal
```

The Ubuntu-Mate spin.

---

### Post by abdullahtrees on 2020-07-06
> **TheFu said:**
> When I run pppoeconf on a 20.04 desktop, I see ... 
```
Looking for PPPoE Access Concentrator on ens3...
```
So it seems to be something related to how 20.04 was installed.  I'm running 
```
$ lsb_release -a                                      
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04 LTS
Release:        20.04
Codename:       focal
```

The Ubuntu-Mate spin.

This is very wierd. I am running Ubuntu 20.04 off the 'Try Ubuntu' Option from Ubuntu Setup and ran the same commands, but I don't have pppoeconf.


[IMG]https://i.postimg.cc/WbjvJfV6/Virtual-Box-3-JXS4-Vhmo-D.png[/IMG]

[IMG]https://i.postimg.cc/qMLdcXMf/Virtual-Box-Uav-Ijqw11a.png[/IMG]

---

### Post by TheFu on 2020-07-06
Please don't post images when they aren't needed.  Text, always.  Let's not waste bandwidth unless necessary.

> After booting from **Ubuntu 18 and _20_** using a USB flash drive, I see that Internet works perfectly once I set an PPPOE connection using
```
sudo pppoeconf
```

So it does work on 20.04?

---

### Post by abdullahtrees on 2020-07-07
> **TheFu said:**
> Please don't post images when they aren't needed.  Text, always.  Let's not waste bandwidth unless necessary.



So it does work on 20.04?

Do you have images disabled or something? I apologize, but I didn't think saving bandwidth was an issue in this forum, never really got told this in other forums.

I booted up both Ubuntu 18 and 20. The images show clearly that Ubuntu 20.04 has the pppoeconf command missing, but it works on 18.04. Hence I can connect to the Internet on Ubuntu 18.04 Live CD but not on Ubuntu 20.04 Live CD.

---

### Post by abdullahtrees on 2020-07-12
Anyways. update time... I managed to restore Internet connection to the Laptop without having to reinstall by getting my hands on a WiFi Dongle and connecting to WiFi to install pppoeconf again. I had no idea how it got lost/removed and how it didn't work. but when I installed it and ran pppoeconf again, I was able to connect to the Internet using ethernet/PPPoE once more. Thank you guys a lot for dealing with me and helping me out... This problem is solved as of now.

---

