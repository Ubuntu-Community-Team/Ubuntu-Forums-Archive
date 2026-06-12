---
title: "Very Weak WiFi With Ubuntu, And Previous Suggestions Aren't Working"
date: 2016-06-24
forum: Networking &amp; Wireless
---

### Post by Lupus_Aviculae on 2016-06-24
Hi there! Oh boy, I am very nervous. I'll try to be as concise as possible. I'm an absolute beginner with Ubuntu or any Linux-based. I've learned a lot by pouring through the forums, but my skills are about at "Open Terminal, Paste Kind-Hearted-User's Suggestion, Pray" level.

I'm having trouble with WiFi connection. I get 1 or 2 bars anywhere in the house, and never more than 2 even sitting right next to the router. My hard drive is partitioned, Ubuntu and Windows 10. I can jump over to Windows 10 right now, and my WiFi will be full bars, very fast and strong anywhere in the house.

I'm really sorry to be asking this question, I've seen a LOT of other users ask the exact same question, but I've tried those fixes to the best of my ability, and nothing seems to be working. I love Ubuntu, I really don't want to go back to Windows, but I can't use Ubuntu and all its glory if I'm tethered to my Ethernet cord.

(Oh, my TX is 20dBm. I'm not sure exactly what that means, but I found a thread where someone suggested "sudo iwconfig" and checking to make sure TX was between 15 and 20)

A quick rundown of what I've tried: 

```
sudo apt-get install linux-headers-generic
sudo apt-get install bcmwl-kernel-source
```

```
iwconfig wlan0 power off
```

```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl

sudo su
echo 'wl' >> /etc/modules
```

```
sudo modprobe -r rt2800pci
sudo modprobe -v rt2800 pci nohwcrypt=1
```

```
sudo rmmod iwlwif
sudo modprobe iwlwifi 11n_disable=1
```

I'm sorry if this post is too long. I just want to be clear that I'm not running to make a new thread on my first day. I've been reading through the forums for a few days now, and I just want to be able to use my fancy new operating system.

The issue is that I see experienced Linux users asking for technical specs at the start of some threads, but not knowing if my specs match or are even similar, I'm throwing code at my terminal pretty blindly, hoping that someone else's fix works for me. I really hope I haven't mucked anything up in there with all my failed attempts.

I've really fallen in love with the Ubuntu community, I'm hoping someone can help. And please, if there's anything in this post I can add or cull to make it more helpful and easy on the eyes, let me know. Thank you in advance, I'll be waiting with bated breath. :)

-- Lupus

---

### Post by grahammechanical on 2016-06-24
Hi. And welcome

We prefer people to start their own threads and we do not mind if they have the same problem as someone else. Your setup may not be exactly the same as the other person's. And your problem might not be exactly the same either. We can learn a lot from following other people's threads. I have learned a lot that way.

If you are able to make a WiFi connection to the router then we know that the WiFi adapter is switched on and Ubuntu has a driver module for that model of WiFi adapter and is using it. With certain WiFI adapters there may be an alternative driver that will work better. We do not know if that is the case.

My machine is a few feet from my router and I have Tx-Power=20 dBm. So, if you are getting that same Decibel to milliwatt power ratio, then I conclude that the problem is not caused by a lack of transmitting power. Tx = transmitting Rx = receiving. As for dBm, well, wikipedia has a an article on it. That is how I found out what dBm means.

It would be useful if you told us what version of Ubuntu you are using. Sometimes things change from version to version. It would also be useful if you ran this command and posted the information that is relevant to the network wireless interface.

```
sudo lshw -C network
```

This is what I see

>   *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlx0015af0e9be0
       serial: 00:15:af:0e:9b:e0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=4.4.0-25-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg



From that we see that there is a driver and the WiFi adapter is working. broadcast=yes & mulitcast=yes gives us that information. My WiFi is a Realtek (rtl8187 is the clue). What WiFi adapter do you have. You only need a bcmwl driver if you have a Broadcom WiFi adapter. and there is something else. rt2800pci is Ralink WiFi adapter. It looks to me that you are running commands relating to two different WiFi adapters.

It is nice that you tell us the commands that you ran but without the printouts from those commands we do not learn anything.

Regards.

---

### Post by wildmanne39 on 2016-06-24
Hello, looks like you may be doing things that we will have to fix besides the original issue.
Please click on the wireless script in my signature and follow the directions for posting the file it creates here using code tags.
Thanks

---

### Post by wildmanne39 on 2016-06-24
Moved to networking for better support!

---

### Post by praseodym on 2016-06-25
Please run the wireless-script from the sticky thread of the networking section and show the outputs

---

### Post by Lupus_Aviculae on 2016-06-25
[SIZE=2][FONT=arial]Thank you guys so much for your help! I'm already feeling the love. :-)
Quick to business: 
Ubuntu Version 16.04

Wild Man's suggestion: Thank you very much for directing me to another thread, I hadn't found that one yet, as well as for moving my question to networking. I entered the commands you suggested and built the .tar.gz file you asked for. It's attached below. 
The results of
```
sudo apt-get update
```
were: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [94.5 kB]
Hit:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease 
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease 
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [222 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [219 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [99.9 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [97.0 kB]
Fetched 732 kB in 1s (415 kB/s) 
Reading package lists... Done

I saved the results of
```
sudo apt-get dist-upgrade
```
I haven't included it here because it was very long (about 26 pages according to LibreOffice Writer), but I have it if you want/need it.[/FONT][/SIZE]
[SIZE=2][FONT=arial]
 [/FONT][/SIZE]
[SIZE=2][FONT=arial]As for how it worked, I got very excited when I rebooted the laptop, I had 3 bars of WiFi sitting right next to the router, instead of 2. It dropped back down to 2 later, but it’s at 3 again now. It’s still not as strong as I’d hope it would be sitting where I am, but it’s better than it was! So thank you! :-)

Grahammechanical: Firstly, thank you for your kind welcome into the community. I'm glad to be here, and I appreciate the community's "no stupid questions" attitude. Back to the code!

```
sudo lshw -c network
```[/FONT][/SIZE]
[SIZE=2][FONT=arial]*-network 
[/FONT][/SIZE]
[SIZE=2][FONT=arial]description: Wireless interface[/FONT][/SIZE]
[SIZE=2][FONT=arial]product: RTL8723BE PCIe Wireless Network Adapter[/FONT][/SIZE]
[SIZE=2][FONT=arial]vendor: Realtek Semiconductor Co., Ltd.[/FONT][/SIZE]
[SIZE=2][FONT=arial]physical id: 0[/FONT][/SIZE]
[SIZE=2][FONT=arial]bus info: pci@0000:02:00.0[/FONT][/SIZE]
[SIZE=2][FONT=arial]logical name: wlo1[/FONT][/SIZE]
[SIZE=2][FONT=arial]version: 00[/FONT][/SIZE]
[SIZE=2][FONT=arial]serial: d8:5d:e2:42:9f:3d[/FONT][/SIZE]
[SIZE=2][FONT=arial]width: 64 bits[/FONT][/SIZE]
[SIZE=2][FONT=arial]clock: 33MHz[/FONT][/SIZE]
[SIZE=2][FONT=arial]capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless[/FONT][/SIZE]
[SIZE=2][FONT=arial]configuration: broadcast=yes driver=rtl8723be driverversion=4.4.0-24-generic firmware=N/A ip=***.***.*.** latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn[/FONT][/SIZE]
[SIZE=2][FONT=arial]resources: irq:34 ioport:3000(size=256) memory:f0a00000-f0a03fff[/FONT][/SIZE]
[SIZE=2][FONT=arial]
 [/FONT][/SIZE]
[SIZE=2][FONT=arial]Hopefully that gives you the information you need, between that printout and the .tar.gz file below. You asked for the results of the other terminal commands, so I’ll list them here:[/FONT][/SIZE]
[SIZE=2][FONT=arial]
 [/FONT][/SIZE]
[SIZE=2][FONT=arial]```
sudo apt-get install-headers-generic
```[/FONT][/SIZE]
[SIZE=2][FONT=arial]Reading package lists... Done[/FONT][/SIZE]
[SIZE=2][FONT=arial]Building dependency tree        [/FONT][/SIZE]
[SIZE=2][FONT=arial]Reading state information... Done[/FONT][/SIZE]
[SIZE=2][FONT=arial]linux-headers-generic is already the newest version (4.4.0.24.25).[/FONT][/SIZE]
[SIZE=2][FONT=arial]0 upgraded, 0 newly installed, 0 to remove and 208 not upgraded.[/FONT][/SIZE]
[SIZE=2][FONT=arial]
 [/FONT][/SIZE]
[SIZE=2][FONT=arial]```
sudo apt-get install bcmwl-kernel-source
```[/FONT][/SIZE]
[SIZE=2][FONT=arial]Reading package lists... Done[/FONT][/SIZE]
[SIZE=2][FONT=arial]Building dependency tree        [/FONT][/SIZE]
[SIZE=2][FONT=arial]Reading state information... Done[/FONT][/SIZE]
[SIZE=2][FONT=arial]bcmwl-kernel-source is already the newest version (6.30.223.248+bdcom-0ubuntu8).[/FONT][/SIZE]
[SIZE=2][FONT=arial]0 upgraded, 0 newly installed, 0 to remove and 208 not upgraded.[/FONT][/SIZE]
[SIZE=2][FONT=arial]
 [/FONT][/SIZE]
[SIZE=2][FONT=arial]```
iwconfig wlan0 power off
```[/FONT][/SIZE]
[SIZE=2][FONT=arial]Error for wireless request "Set Power Management" (8B2C) :[/FONT][/SIZE]
[SIZE=2][FONT=arial]    SET failed on device wlan0 ; Operation not permitted.[/FONT][/SIZE]
[SIZE=2][FONT=arial]
 [/FONT][/SIZE]
[SIZE=2][FONT=arial]```
sudo apt-get install linux-headers-generic
```[/FONT][/SIZE]
[SIZE=2][FONT=arial]Reading package lists... Done[/FONT][/SIZE]
[SIZE=2][FONT=arial]Building dependency tree        [/FONT][/SIZE]
[SIZE=2][FONT=arial]Reading state information... Done[/FONT][/SIZE]
[SIZE=2][FONT=arial]linux-headers-generic is already the newest version (4.4.0.24.25).[/FONT][/SIZE]
[SIZE=2][FONT=arial]0 upgraded, 0 newly installed, 0 to remove and 208 not upgraded.[/FONT][/SIZE]
[SIZE=2][FONT=arial]
 [/FONT][/SIZE]
[SIZE=2][FONT=arial]```
sudo apt-get install –reinstall bcmwl-kernel-source
```[/FONT][/SIZE]
[SIZE=2][FONT=arial]Reading package lists... Done[/FONT][/SIZE]
[SIZE=2][FONT=arial]Building dependency tree        [/FONT][/SIZE]
[SIZE=2][FONT=arial]Reading state information... Done[/FONT][/SIZE]
[SIZE=2][FONT=arial]0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 208 not upgraded.[/FONT][/SIZE]
[SIZE=2][FONT=arial]Need to get 0 B/1,515 kB of archives.[/FONT][/SIZE]
[SIZE=2][FONT=arial]After this operation, 0 B of additional disk space will be used.[/FONT][/SIZE]
[SIZE=2][FONT=arial](Reading database ... 204480 files and directories currently installed.)[/FONT][/SIZE]
[SIZE=2][FONT=arial]Preparing to unpack .../bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu8_amd64.deb ...[/FONT][/SIZE]
[SIZE=2][FONT=arial]Removing all DKMS Modules[/FONT][/SIZE]
[SIZE=2][FONT=arial]Done.[/FONT][/SIZE]
[SIZE=2][FONT=arial]Unpacking bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu8) over (6.30.223.248+bdcom-0ubuntu8) ...[/FONT][/SIZE]
[SIZE=2][FONT=arial]Setting up bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu8) ...[/FONT][/SIZE]
[SIZE=2][FONT=arial]Loading new bcmwl-6.30.223.248+bdcom DKMS files...[/FONT][/SIZE]
[SIZE=2][FONT=arial]Building only for 4.4.0-24-generic[/FONT][/SIZE]
[SIZE=2][FONT=arial]Building for architecture x86_64[/FONT][/SIZE]
[SIZE=2][FONT=arial]Building initial module for 4.4.0-24-generic[/FONT][/SIZE]
[SIZE=2][FONT=arial]Done.[/FONT][/SIZE]
[SIZE=2][FONT=arial]
 [/FONT][/SIZE]
[SIZE=2][FONT=arial]wl:[/FONT][/SIZE]
[SIZE=2][FONT=arial]Running module version sanity check.[/FONT][/SIZE]
[SIZE=2][FONT=arial] - Original module[/FONT][/SIZE]
[SIZE=2][FONT=arial]   - No original module exists within this kernel[/FONT][/SIZE]
[SIZE=2][FONT=arial] - Installation[/FONT][/SIZE]
[SIZE=2][FONT=arial]   - Installing to /lib/modules/4.4.0-24-generic/updates/dkms/[/FONT][/SIZE]
[SIZE=2][FONT=arial]
 [/FONT][/SIZE]
[SIZE=2][FONT=arial]depmod....
[/FONT][/SIZE]
[SIZE=2][FONT=arial]
 [/FONT][/SIZE]
[SIZE=2][FONT=arial]DKMS: install completed.[/FONT][/SIZE]
[SIZE=2][FONT=arial]modprobe: ERROR: could not insert 'wl': Required key not available[/FONT][/SIZE]
[SIZE=2][FONT=arial]update-initramfs: deferring update (trigger activated)[/FONT][/SIZE]
[SIZE=2][FONT=arial]Processing triggers for initramfs-tools (0.122ubuntu8) ...[/FONT][/SIZE]
[SIZE=2][FONT=arial]update-initramfs: Generating /boot/initrd.img-4.4.0-24-generic[/FONT][/SIZE]
[SIZE=2][FONT=arial]
 [/FONT][/SIZE]
[SIZE=2][FONT=arial]```
sudo modprobe wl
```[/FONT][/SIZE]
[SIZE=2][FONT=arial]modprobe: ERROR: could not insert ‘wl’: Required key not available[/FONT][/SIZE]
[SIZE=2][FONT=arial]
 [/FONT][/SIZE]
[SIZE=2][FONT=arial]```
sudo su
```[/FONT][/SIZE]
[SIZE=2][FONT=arial]Here it printed out “root@{my computer name}:/home/{my name}#”[/FONT][/SIZE]
[SIZE=2][FONT=arial]```
echo ‘wl’ >> /etc/modules
```[/FONT][/SIZE]
[SIZE=2][FONT=arial]It produced the same “root@” line with no change. When I tried to close the terminal, it said “Close this terminal? There is still a process running in this terminal. Closing the terminal will kill it.”[/FONT][/SIZE]
[SIZE=2][FONT=arial]
 [/FONT][/SIZE]
[SIZE=2][FONT=arial]```
sudo modprobe -r rt2800pci
```[/FONT][/SIZE]
[SIZE=2][FONT=arial]{produced no text}[/FONT][/SIZE]
[SIZE=2][FONT=arial]
 [/FONT][/SIZE]
[SIZE=2][FONT=arial]```
sudo modprobe -v rt2800 pci nohwcrypt=1
```[/FONT][/SIZE]
[SIZE=2][FONT=arial]modprobe: FATAL: Module rt2800 not found in directory /lib/modules/4.4.0-24-generic[/FONT][/SIZE]
[SIZE=2][FONT=arial]
 [/FONT][/SIZE]
[SIZE=2][FONT=arial]```
sudo rmmod iwlwif
```[/FONT][/SIZE]
[SIZE=2][FONT=arial]rmmod: ERROR: Module iwlwif is not currently loaded[/FONT][/SIZE]
[SIZE=2][FONT=arial]
 [/FONT][/SIZE]
[SIZE=2][FONT=arial](I ran the command again using “iwlwifi”, just in case my source had made a typo)[/FONT][/SIZE]
[SIZE=2][FONT=arial]```
sudo rmmod iwlwifi
```[/FONT][/SIZE]
[SIZE=2][FONT=arial]rmmod: ERROR: Module iwlwifi is not currently loaded[/FONT][/SIZE]
[SIZE=2][FONT=arial]
 [/FONT][/SIZE]
[SIZE=2][FONT=arial]```
sudo modprobe iwlwifi 11n_disable=1
```[/FONT][/SIZE]
[SIZE=2][FONT=arial]{produced no text}[/FONT][/SIZE]
[SIZE=2][FONT=arial]
 [/FONT][/SIZE]
[SIZE=2][FONT=arial]Thanks again for your help guys![/FONT][/SIZE]
[SIZE=2][FONT=arial]
 [/FONT][/SIZE]
[SIZE=2][FONT=arial]-- Lupus
[/FONT][/SIZE]

---

### Post by praseodym on 2016-06-25
No need for guessing. Please run

```
sudo apt-get remove --purge bcmwl-kernel-source
echo "options rtl8723be swenc=1 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Reboot. If its not enough, update the driver and switch the antenna (only the new driver can do so:

```
sudo apt-get install git build-essential 
git clone https://github.com/lwfinger/rtlwifi_new 
cd rtlwifi_new
make
sudo make install
sudo depmod -a
sudo update-initramfs -u 
echo "options rtl8723be swenc=1 fwlps=0 ips=0 [COLOR="#FF0000"]ant_sel=1[/COLOR]" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Reboot

---

### Post by Lupus_Aviculae on 2016-06-26
Hey guys. First off, thank you everyone for your help and support. Secondly, I'm sorry it takes me so long to respond. 3am is about the only window I have to work on personal projects. I feel bad because everyone is responding so promptly, but that's the best I can do.

Next: I'm some kind of idiot. I don't know how I managed to screw up cutting and pasting, but I did something and now my computer isn't seeing any wireless networks at all. Here's the new results of some of the code you've asked for in the past. I don't know what's wrong, but hopefully this is the information that will help. If there's something else you guys need, I'm at your command.

```
sudo lshw -c network
```
 *-network UNCLAIMED     
       description: Network controller
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:f0a00000-f0a03fff

I've also attached the new result of
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```
at the bottom as wireless-info.txt

Again, I'm really sorry guys. I know your time and patience are not infinite, and I feel like an idiot for managing to mess up what should have been an easy fix. I hate asking other people to clean up my mistakes. That said, if you have time, I'd really appreciate the help. 

All of my documents are saved to an external hard drive, so if I have to reset this baby to factory default, it's not the end of the world. If that happens, I'll still redownload Ubuntu and work on this until it's perfect. I love this system and I love this community, I don't want to give up on this just because I failed once.

Thanks again guys (and gals). Fingers crossed for an easy solution!

-- Lupus

---

### Post by praseodym on 2016-06-26
Obviously, the driver is not loaded:
```

sudo modprobe -v rtl8723be
dmesg | grep rtl8
iwconfig
```

---

### Post by Lupus_Aviculae on 2016-06-26
Thank you so much for your help, Praseodym. I'm very glad to hear that it's an easy fix. It's still not working for me, and I think the offending line is 

```
sudo modprobe -v rtl8723be
```
insmod /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko 
modprobe: ERROR: could not insert 'rtl8723be': Required key not available

Doing a quick bit of research, it appears this may be a secure boot issue. Unfortunately I'm running to work right now, so I don't have time to play with it at the moment. I should be back in about 12 hours or so. If you have any suggestions, I'd still love to hear them. If not, I'll continue working with it, see if disabling secure boot will help.

Not only do I appreciate everyone's help, but I'm really grateful to have a small issue my first time around. I feel like I'm learning a lot about the system and my computer. It's a lot of fun (even if I'm pulling my hair out occasionally.)

-- Lupus

---

### Post by praseodym on 2016-06-26
Deactivate secure boot in your (U)EFI

---

### Post by jeremy31 on 2016-06-26
An alternative to disabling Secure Boot is [http://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-dkms-modules-in-ubuntu-16/762255#762255](http://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-dkms-modules-in-ubuntu-16/762255#762255)

---

### Post by Lupus_Aviculae on 2016-06-27
I could simply kiss all of you. Thank you so much! It's perfect. My wifi is faster and stronger than ever. You guys are all incredible.

Jeremy31, I tried the mokutil fix, but it was still giving me the modprobe error.

Praseodym, I disabled secure boot, ran the three lines of code, and the problem is fixed. You are a wizard.

One last question before I go, are there any downsides to disabling secure boot? I tried to do some research and the results were very mixed. My hard drive is partitioned, Windows 10 with Ubuntu 16.04. I was planning on using Ubuntu for nearly everything, and Windows 10 only for the few games I play that don't support Linux. From what I was reading, it sounds like disabling secure boot puts my computer at risk when I'm using Windows? If this is a longer conversation, I'll do more research and start a new thread in a more appropriate section. I just thought I'd ask. Being still new, I don't know what's an easy answer (see above, Praseodym fixing my issue with three lines of code) and what's a more complicated discussion.

Again, thanks to everyone who contributed, it feels wonderful to be in a community with intelligent and helpful people. Have absolutely beautiful days. I'll mark this thread SOLVED.

-- Lupus

---

