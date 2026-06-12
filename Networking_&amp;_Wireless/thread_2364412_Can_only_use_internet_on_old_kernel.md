---
title: "Can only use internet on old kernel"
date: 2017-06-23
forum: Networking &amp; Wireless
---

### Post by manatee.madness on 2017-06-23
I posted a LONG time ago about restarting my computer and suddenly having no internet. But now when I go to the GRUB menu every time I have to restart for whatever reason, I go to the same option because it's the only kernel that can find ANY wifi networks. Now this kernel is 20 things behind (I don't know the technical terms, it's something like ubuntu.general.57 or something and the most recent one is .79 or .8-something). I am having a lot of issues with other parts of my daily usage, such as some software not opening or not being able to be downloaded, and I think it's either because of the old kernel or maybe I had a faulty OS when I downloaded Ubuntu somehow. Although I'd like some insight on that too the main issue is internet.

I followed firections from someone a while back about deleting some key to turn off secure boot, which worked. But every time I go into that menu where there are all these boot settings (forget what it's called) it says that the key is still deleted and secure boot is off, but unlike with the old kernel, this my computer just doesn't pick up any networks. Sorry if this is hard to understand, I'm not good with computers and I don't know a lot of technical names and such. But I hope that someone can decipher this and help me.

---

### Post by vocx on 2017-06-24
> **manatee.madness said:**
> I posted a LONG time ago about restarting my computer and suddenly having no internet. But now when I go to the GRUB menu every time I have to restart for whatever reason, I go to the same option because it's the only kernel that can find ANY wifi networks. Now this kernel is 20 things behind (I don't know the technical terms, it's something like ubuntu.general.57 or something and the most recent one is .79 or .8-something). I am having a lot of issues with other parts of my daily usage, such as some software not opening or not being able to be downloaded, and I think it's either because of the old kernel or maybe I had a faulty OS when I downloaded Ubuntu somehow. Although I'd like some insight on that too the main issue is internet.

It sounds like you installed this Ubuntu computer a long time ago, maybe some years and perhaps never bothered to learn a bit more about the system. Maybe your computer is even running an old, unsupported version of Ubuntu, so maybe it would be wise to upgrade it or reinstall it.

Open a terminal window and run
```
uname -a
```

It should give you something like
```
Linux laptop 4.4.0-81-generic #104-Ubuntu SMP Wed Jun 14 08:17:06 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

Just for your knowledge, the current kernel is in the 4.x series. You give the first two numbers, like 4.4 kernel, to specify the major and minor version of the kernel. That makes it possible for people to more or less get an idea of the age of your system. If you say, the 3.16 kernel, people would know you are using a significantly old kernel. And if you say, 4.12, people would know you are using a cutting edge kernel. The last portion of the kernel number, .0-81, etc., is minor, and doesn't give much information, unless it's a particular release that addresses a particular issue. So the best is to provide the entire information, "4.4.0-81-generic # 104-Ubuntu SMP", etc.

You should be running at least Ubuntu 16.04, or newer. Any version older than that, 15.10, 15.04, 14.10, 14.04, etc., is probably not a good idea.

Open a terminal window and run
```
lsb_release -a
```

```

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

```

> 
I followed firections from someone a while back about deleting some key to turn off secure boot, which worked. But every time I go into that menu where there are all these boot settings (forget what it's called) it says that the key is still deleted and secure boot is off, but unlike with the old kernel, this my computer just doesn't pick up any networks. Sorry if this is hard to understand, I'm not good with computers and I don't know a lot of technical names and such. But I hope that someone can decipher this and help me.
I have no experience with this, but sounds like maybe you are going into the BIOS screen to disable the Secure boot option. Or maybe you are using UEFI boot instead of the legacy BIOS. I'm not sure, but giving more information will be helpful for people trying to help you.

---

### Post by manatee.madness on 2017-06-24
I built this desktop and installed Ubuntu 16.04 LTS in January, which felt like forever ago but I guess really isn't.

Yes, I went into the BIOS and disabled Secure Boot because someone told me to when this issue first arose. I have an ASUS motherboard so the BIOS menu is a bit different looking than normal ones.

As for commands:

First: Linux william-System-Product-Name 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Second: No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

And yes, I believe the Kernel is 4.4-something. But internet for me ONLY works if the ending is .57. Anything after that and my system won't pick up anything in the menu, even though there are several that it normally picks up.

---

### Post by vocx on 2017-06-24
> **manatee.madness said:**
> I built this desktop and installed Ubuntu 16.04 LTS in January, which felt like forever ago but I guess really isn't.

Yes, I went into the BIOS and disabled Secure Boot because someone told me to when this issue first arose. I have an ASUS motherboard so the BIOS menu is a bit different looking than normal ones.

As for commands:

First: Linux william-System-Product-Name 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Second: No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

And yes, I believe the Kernel is 4.4-something. But internet for me ONLY works if the ending is .57. Anything after that and my system won't pick up anything in the menu, even though there are several that it normally picks up.

Okay, so your system is not really old.

So, I guess you have other kernels installed ending in 4.4.0-57, 4.4.0-59, 4.4.0-62, 4.4.0-63, etc., but you say only the one ending in -57 works? That's weird.

When you install a kernel you usually pull an "extra" package which contains additional modules, that is, drivers for different hardware. It sounds like maybe only the -57 kernel has these additional modules, and the rest don't, hence why your internet only works with that particular kernel.

I suggest you check that all these extra packages are installed for each kernel that you have installed, and then try if you have internet that way.
```
aptitude search ^linux-image-4.4.0
```

You should see a long list, something like this
```

c   linux-image-4.4.0-57-generic                    - Linux kernel image for version 4.4.0 on 64 bit x86 SMP    
p   linux-image-4.4.0-57-lowlatency                 - Linux kernel image for version 4.4.0 on 64 bit x86 SMP    
c   linux-image-4.4.0-59-generic                    - Linux kernel image for version 4.4.0 on 64 bit x86 SMP    
p   linux-image-4.4.0-59-lowlatency                 - Linux kernel image for version 4.4.0 on 64 bit x86 SMP    
i A linux-image-4.4.0-78-generic                    - Linux kernel image for version 4.4.0 on 64 bit x86 SMP    
p   linux-image-4.4.0-78-lowlatency                 - Linux kernel image for version 4.4.0 on 64 bit x86 SMP    
i A linux-image-4.4.0-79-generic                    - Linux kernel image for version 4.4.0 on 64 bit x86 SMP    
p   linux-image-4.4.0-79-lowlatency                 - Linux kernel image for version 4.4.0 on 64 bit x86 SMP    
i A linux-image-4.4.0-81-generic                    - Linux kernel image for version 4.4.0 on 64 bit x86 SMP    
p   linux-image-4.4.0-81-lowlatency                 - Linux kernel image for version 4.4.0 on 64 bit x86 SMP    

```
I removed many lines, but you should see the pattern. The first column tells you if the kernel is installed. The letters "i A" indicates it is installed. The other letters, "p" and "c", means the kernel is not installed so you don't need to worry about it.

Make sure you have the corresponding extra package.
```
aptitude search ^linux-image-extra-4.4.0
```

```

c   linux-image-extra-4.4.0-57-generic              - Linux kernel extra modules for version 4.4.0 on 64 bit x86
c   linux-image-extra-4.4.0-59-generic              - Linux kernel extra modules for version 4.4.0 on 64 bit x86
i A linux-image-extra-4.4.0-78-generic              - Linux kernel extra modules for version 4.4.0 on 64 bit x86
i A linux-image-extra-4.4.0-79-generic              - Linux kernel extra modules for version 4.4.0 on 64 bit x86
i A linux-image-extra-4.4.0-81-generic              - Linux kernel extra modules for version 4.4.0 on 64 bit x86

```

If the extra package is not installed, just install it
```
sudo apt install linux-image-extra-4.4.0-78-generic
```

Do this for all the kernels that you have installed.

Now, in general, you don't need many kernels, you just need one, the one that works. Some people keep two or three kernels because if a hardware component stops working you can boot with the last working kernel. So, instead of installing many kernels, and their extra packages, I would remove all of them except the one you are currently using -57, and the newest one, for example, -81.
```

sudo apt remove linux-image-extra-4.4.0-59-generic
sudo apt remove linux-image-extra-4.4.0-62-generic
sudo apt remove linux-image-extra-4.4.0-63-generic
sudo apt remove linux-image-extra-4.4.0-64-generic
... etc.
```

Okay, now I suggest you run the script in the sticky thread of this subforum [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

This script will collect a lot of information of your system, mainly that related to your wireless card, your kernel modules, the configuration of network-manager, etc. That will help us troubleshoot further. It's essential to know which model your network card is. Just saying "it's an ASUS motherboard" is not helpful. It's a specific chip which does the connectivity, for example

```
lshw -c network
```

```

  *-network               
       description: Ethernet interface
       product: Ethernet Connection (3) I218-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: enp0s25
       version: 03
       serial: XX:XX:XX:XX:XX:XX
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.2-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:50 memory:f2200000-f221ffff memory:f223e000-f223efff ioport:4080(size=32)
  *-network
       description: Wireless interface
       product: Wireless 7265
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 59
       serial: XX:XX:XX:XX:XX:XX
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-81-generic firmware=19.324151.0 ip=192.168.1.10 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:48 memory:f2000000-f2001fff

```
This tells me I have two network cards, one for wired Ethernet and another wireless. It indicates the driver as "e1000e" in the first case, and "iwlwifi" the second.

Whenever you post terminal output in this forum please use "```
" tags, which means surrounding the text with the word CODE inside brackets. You have an opening tag and a closing tag. For example
[php]
[CODE]
apt search ^linux-image-

```
[/php]

---

### Post by manatee.madness on 2017-06-25
So it tells me that the packages are installed for ONLY kernels ending in -57 and -81. I guess I'm so used to things not working that I just default to -57 whe I restart. Let me see if I can pick up networks on -81, and I'll update when I know.

EDIT: No networks are found when I go to the GRUB menu and start from -87. I took some pictures with my phone of things I saw that you may want to see to get an idea

[http://imgur.com/a/B5BC3](http://imgur.com/a/B5BC3) <- Shows what I see when I click the network icon and something else that seems odd

---

### Post by vocx on 2017-06-26
> **manatee.madness said:**
> So it tells me that the packages are installed for ONLY kernels ending in -57 and -81. I guess I'm so used to things not working that I just default to -57 whe I restart. Let me see if I can pick up networks on -81, and I'll update when I know.

EDIT: No networks are found when I go to the GRUB menu and start from -87. I took some pictures with my phone of things I saw that you may want to see to get an idea

[http://imgur.com/a/B5BC3](http://imgur.com/a/B5BC3) <- Shows what I see when I click the network icon and something else that seems odd
The messages
```

/dev/sda2: recovering journal
/dev/sda2: Clearing orphaned inode 37880764 (uid=1001, gid=1001, mode=0100664, size=22195)
...
```

Are not exactly related to the wireless problem, but may indicate a further issue. These errors typically indicate that the computer was not shut down properly, for example, there was a power outage, or you unplugged the power cord without selecting "shut down" from the menu. When this happens the operating system doesn't finish writing properly to the hard disk, so it may leave pieces in an inconsistent state. Then, next time you boot the computer, the hard drive detects that there are some missing pieces, and tries to repair them, or deletes them. Recovering "journal" means that it's trying to recover the missing pieces from the "journal" that exists in your hard disk partition. Also "clearing orphaned inode" shows which pieces it is repairing. An "inode", in cryptic operating system speak, is a piece of a file.

So, I am not sure why you are getting these messages. If you shut down your system correctly, through the menu, and these messages don't appear any more, then that's all you need. But if you shut down your system correctly, and you still get the errors after every boot, this may indicate that your hard disk is damaged. I think you can run some utilities to thoroughly check and repair sectors on your disk, if possible. But this is a separate topic, and it would be best if you opened a new thread about it.

This error could mean some of the files needed for a specific kernel, for wireless to work correctly, are missing. It could also mean some of your personal data files are missing. Hard disk errors are essentially random. If it fails, you don't know if it damages the operating system or your personal files. It's best if you back up your personal files in case you have to reinstall the operating system.

Besides that, your picture doesn't show much. You still need to provide the information regarding your hardware.
```
lshw -c network
```

And also run the troubleshooting script [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by manatee.madness on 2017-06-26
I ran the troubleshooting script before when this first started, got the wireless.txt file, etc.

After running your code you gave me at the bottom, the terminal showed me this:

```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: Ethernet Connection (2) I219-V
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 31
       serial: 38:d5:47:b4:2c:9a
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.8-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:123 memory:f7100000-f711ffff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:1
       logical name: wlxa0046026ae11
       serial: a0:04:60:26:ae:11
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8812au ip=192.168.1.111 multicast=yes wireless=IEEE 802.11an
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```



I don't know what any of this means. Also when i shut down my computer through the menu and restarted, those messages went away. All the "inode" stuff.

---

### Post by vocx on 2017-06-27
> **manatee.madness said:**
> I ran the troubleshooting script before when this first started, got the wireless.txt file, etc.

After running your code you gave me at the bottom, the terminal showed me this:

```

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       **product: Ethernet Connection (2) I219-V**
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 31
       serial: 38:d5:47:b4:2c:9a
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=e1000e** driverversion=3.2.6-k firmware=0.8-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:123 memory:f7100000-f711ffff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:1
       logical name: wlxa0046026ae11
       serial: a0:04:60:26:ae:11
       capabilities: ethernet physical wireless
       configuration: broadcast=yes **driver=rtl8812au** ip=192.168.1.111 multicast=yes wireless=IEEE 802.11an
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```


I don't know what any of this means. Also when i shut down my computer through the menu and restarted, those messages went away. All the "inode" stuff.


**Whenever you post terminal output in this forum please use "```
" tags, which means surrounding the text with the word CODE inside brackets.** You have an opening tag and a closing tag. For example
[PHP]
[CODE]
lshw -c network

```
[/PHP]

The output from the "lshw" command tells us you have two network devices.

One is an Ethernet interface, an Intel I219-V, and it uses the driver "e1000e". The second device is a wireless interface using the "rtl8812au" driver. You can read this in your output. Just give it a look. Go line by line, and you'll notice it.

First things first. The device you are using seems to have issues in Linux. There are various reports online about this device not being well supported. Is it a sort of USB dongle that you plug into the computer? It is not integrated in the motherboard, or is it?

The solution from 2014 to the present day seems to compile the source code of the driver module, and install it that way. Maybe you did this before and don't remember at this point.
Check this [https://blog.danielscrivano.com/installing-rtl8812au-on-linux-for-wireless-dual-band-usb-adapters/](https://blog.danielscrivano.com/installing-rtl8812au-on-linux-for-wireless-dual-band-usb-adapters/)
Check this as well [https://marcnu.github.io/2016-09-10/How-to-install-Netgear-A6100-USB-Wifi-adapter-on-Ubuntu-16.04/](https://marcnu.github.io/2016-09-10/How-to-install-Netgear-A6100-USB-Wifi-adapter-on-Ubuntu-16.04/)

Compilation of drivers is done against a specific kernel. This means, if you compile the module for -54, it will not work with -81. You have to recompile it with -81 as well. Essentially, every time there is a kernel update you have to recompile the driver "rtl8812au" so it works with the new kernel. Otherwise you will have to use the previous kernel. This seems to be your case.

Instead of manually compiling, Linux provides a framework to automatically compile the drivers whenever there is a kernel update. Apparently, for your device, you have to install
```
sudo apt install rtl8812au-dkms
```
Maybe your problems will be fixed with this. Maybe not.

Here is a thread in this forum explaining some issues with the "rtl8812au" device, even after using the "-dkms" package. Eventually, it seems the user made it work.
[https://ubuntuforums.org/showthread.php?t=2335738]("https://ubuntuforums.org/showthread.php?t=2335738&page=1")

Here is a thread in this forum of a user who gave up on trying to make it work. He didn't run the wireless script, he didn't follow directions, and instead decided to not use the USB wireless device any more.
[https://ubuntuforums.org/showthread.php?t=2345309](https://ubuntuforums.org/showthread.php?t=2345309)

My suggestion is, if you don't want to bother any more, get a new wireless device, one that is well supported in Linux. Otherwise, try to make it work with the "rtl8812au-dkms" package. Try to not get frustrated if it does not work, and please follow advice.

You already ran the wireless script. Well, you have to attach the output to this forum. Copy the entire contents and paste them inside "[CODE]" tags, as described above.

---

### Post by manatee.madness on 2017-06-27
Oh wow how did I forget about this. This is a USB Network...thing... that I got when I finished building this computer. There was a disk that came with it, but I soon learned that this was optimized for Windows, and there was a long process of manual code things that I had to do for my computer to even recognize that it was plugged in. I will try to run your command at the bottom, as that looks VERY familiar. We'll see how things go.

The wireless script 

```

########## wireless info START ##########

Report from: 24 Jun 2017 21:06 PDT -0700

Booted last: 24 Jun 2017 00:00 PDT -0700

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splashradeonmodeset=1

##### desktop ###########################

Ubuntu

##### lspci #############################

00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8] (rev 31)
    Subsystem: ASUSTeK Computer Inc. Ethernet Connection (2) I219-V [1043:8672]
    Kernel driver in use: e1000e

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0781:5567 SanDisk Corp. Cruzer Blade
Bus 001 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 413c:2106 Dell Computer Corp. Dell QuietKey Keyboard
Bus 001 Device 002: ID 0846:9052 NetGear, Inc. A6100 AC600 DB Wireless Adapter [Realtek RTL8811AU]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8812au            1351680  0
eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
cfg80211              565248  1 rtl8812au
mxm_wmi                16384  0
wmi                    20480  2 mxm_wmi,asus_wmi

```

```

sudo apt install rtl8812au-dkms

```

And it told to to try and run it with --fix-missing at the end. This told me it could not fetch a couple things and there was an issue with "media switch." I tried to copy it but after I restarted I wasn't able to paste the code. If needed, I can run the whole process again, take a picture, and add an IMGUR link if it's important. It was a bunch of files from archives.ubuntu.somethingtechnicalthatIcan'tremember

---

### Post by vocx on 2017-06-27
> **manatee.madness said:**
> Oh wow how did I forget about this. This is a USB Network...thing... that I got when I finished building this computer. There was a disk that came with it, but I soon learned that this was optimized for Windows, and there was a long process of manual code things that I had to do for my computer to even recognize that it was plugged in. I will try to run your command at the bottom, as that looks VERY familiar. We'll see how things go.

The wireless script 

```

########## wireless info START ##########

```

```

sudo apt install rtl8812au-dkms

```

And it told to to try and run it with --fix-missing at the end. This told me it could not fetch a couple things and there was an issue with "media switch." I tried to copy it but after I restarted I wasn't able to paste the code. If needed, I can run the whole process again, take a picture, and add an IMGUR link if it's important. It was a bunch of files from archives.ubuntu.somethingtechnicalthatIcan'tremember

Please don't "accidentally forget" to mention things. The more information you provide the better it is to troubleshoot and fix problems. Engineers all around the world get frustrated when their clients, colleagues, bosses, family members, etc., casually "forget" to mention things. It's the same way medical doctors work. You don't hide things from your physician if you want to diagnose an issue.

You are not pasting the entire output of the wireless script. Please attach the complete output. It is important to see the hardware, as well as the configuration of the different network files used in your system.

Don't tell me what it told you, post the output. Run it again, copy the output, and paste it. Avoid taking pictures. Taking pictures is not helpful except in the extreme case when you cannot really copy and paste text, such as on startup or when the computer locks up. Linux thrives on text files. Why? Because it's easy to see, open, copy, and edit, even in a very basic computer.

First boot into the -57 kernel. Make sure your system is up to date, and with the latest packages.
```

sudo apt update && sudo apt upgrade

```

Make sure the package is installed
```

sudo apt install rtl8812au-dkms

```

Document any strange output or error messages that you get.

Run the wireless script, paste the output here.

Repeat the same steps with the newest kernel you have, for example, -81. That is, try installing the "rtl8812au-dkms" package, and running the wireless script, and paste it here as well.

---

### Post by manatee.madness on 2017-06-27
The Wireless Script in its entirety (didn't realize there was more):

```


########## wireless info START ##########

Report from: 24 Jun 2017 21:06 PDT -0700

Booted last: 24 Jun 2017 00:00 PDT -0700

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splashradeonmodeset=1

##### desktop ###########################

Ubuntu

##### lspci #############################

00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8] (rev 31)
    Subsystem: ASUSTeK Computer Inc. Ethernet Connection (2) I219-V [1043:8672]
    Kernel driver in use: e1000e

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0781:5567 SanDisk Corp. Cruzer Blade
Bus 001 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 413c:2106 Dell Computer Corp. Dell QuietKey Keyboard
Bus 001 Device 002: ID 0846:9052 NetGear, Inc. A6100 AC600 DB Wireless Adapter [Realtek RTL8811AU]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8812au            1351680  0
eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
cfg80211              565248  1 rtl8812au
mxm_wmi                16384  0
wmi                    20480  2 mxm_wmi,asus_wmi
video                  40960  2 i915_bpo,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s31f6 Link encap:Ethernet  HWaddr <MAC 'enp0s31f6' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:f7100000-f7120000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:818 errors:0 dropped:0 overruns:0 frame:0
          TX packets:818 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:75133 (75.1 KB)  TX bytes:75133 (75.1 KB)

wlx<IF from MAC [IF2]> Link encap:Ethernet  HWaddr <MAC 'wlx<IF from MAC [IF2]>' [IF2]>  
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fd32:f4d4:4f6:0:fd5f:e9c8:945d:f3b5/64 Scope:Global
          inet6 addr: fe80::ecc6:bd8d:bd34:5439/64 Scope:Link
          inet6 addr: fd32:f4d4:4f6:0:f501:4f02:5ae9:a0c0/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:812689 errors:0 dropped:2508 overruns:0 frame:0
          TX packets:330846 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1206491407 (1.2 GB)  TX bytes:33170565 (33.1 MB)

##### iwconfig ##########################

lo        no wireless extensions.

enp0s31f6  no wireless extensions.

wlx<IF from MAC [IF2]>  IEEE 802.11an  ESSID:"Schoeps41"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:5.18 GHz  Access Point: <MAC 'Schoeps41' [AC1]>   
          Bit Rate:150 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=88/100  Signal level=86/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlx<IF from MAC [IF2]>
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlx<IF from MAC [IF2]>

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       916     1  0 19:14 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek 
GENERAL.PRODUCT:                        802.11ac WLAN Adapter 
GENERAL.DRIVER:                         rtl8812au
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/net/wlx<IF from MAC [IF2]>
GENERAL.IP-IFACE:                       wlx<IF from MAC [IF2]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Schoeps41
GENERAL.CON-UUID:                       455966f9-84a0-4ed2-83b4-ed536d4adbb2
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     150 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   455966f9-84a0-4ed2-83b4-ed536d4adbb2 | Schoeps41
IP4.ADDRESS[1]:                         192.168.1.111/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             71.10.216.1
IP4.DNS[2]:                             71.10.216.2
IP4.DNS[3]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1498443267
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.111
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.1.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 71.10.216.1 71.10.216.2 192.168.1.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.1.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fd32:f4d4:4f6:0:fd5f:e9c8:945d:f3b5/64
IP6.ADDRESS[2]:                         fd32:f4d4:4f6:0:f501:4f02:5ae9:a0c0/64
IP6.ADDRESS[3]:                         fe80::ecc6:bd8d:bd34:5439/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp0s31f6
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (2) I219-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.8-4
GENERAL.HWADDR:                         <MAC 'enp0s31f6' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/enp0s31f6
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Schoeps41        <MAC 'Schoeps41' [AC2]>  Infra  11    2462 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Schoeps41-guest  <MAC 'Schoeps41-guest' [AC3]>  Infra  11    2462 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  --         no        
Schoeps41        <MAC 'Schoeps41' [AC1]>  Infra  36    5180 MHz  54 Mbit/s  68      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Schoeps41]] (600 root)
[connection] id=Schoeps41 | type=wifi | permissions=user:nathan:;
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=Schoeps41
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp0s31f6  no frequency information.

wlx<IF from MAC [IF2]>  32 channels in total; available frequencies :
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
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:5.18 GHz (Channel 36)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp0s31f6  Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.18 GHz (Channel 36)

wlx<IF from MAC [IF2]>  Scan completed :
          Cell 01 - Address: <MAC 'Schoeps41' [AC1]>
                    ESSID:"Schoeps41"
                    Protocol:IEEE 802.11an
                    Mode:Master
                    Frequency:5.18 GHz (Channel 36)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=88/100  Signal level=86/100  
                    Extra:fm=0003
          Cell 02 - Address: <MAC 'Schoeps41' [AC2]>
                    ESSID:"Schoeps41"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=31/100  Signal level=73/100  
                    Extra:fm=0003
          Cell 03 - Address: <MAC 'Schoeps41-guest' [AC3]>
                    ESSID:"Schoeps41-guest"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:144 Mb/s
                    Quality=15/100  Signal level=73/100  
                    Extra:fm=0003

##### module infos ######################

[rtl8812au]
filename:       /lib/modules/4.4.0-57-generic/kernel/drivers/net/wireless/rtl8812au.ko
version:        v4.3.14_13455.20150212_BTCOEX20150128-51
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     8E7CA44A11A3D9B9A05D5E5
depends:        cfg80211
vermagic:       4.4.0-57-generic SMP mod_unload modversions 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           rtw_usb_rxagg_mode:int
parm:           rtw_qos_opt_enable:int
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_special_rf_path:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_bw_mode:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_vht_enable:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           rtw_led_enable:Enable status LED (int)
parm:           rtw_hiq_filter:0:allow all, 1:allow special, 2:deny all (uint)
parm:           rtw_adaptivity_en:0:disable, 1:enable (uint)
parm:           rtw_adaptivity_mode:0:normal, 1:carrier sense (uint)
parm:           rtw_adaptivity_dml:0:disable, 1:enable (uint)
parm:           rtw_amplifier_type_2g:BIT3:2G ext-PA, BIT4:2G ext-LNA (uint)
parm:           rtw_amplifier_type_5g:BIT6:5G ext-PA, BIT7:5G ext-LNA (uint)
parm:           rtw_RFE_type:default init value:64 (uint)
parm:           rtw_TxBBSwing_2G:default init value:0xFF (uint)
parm:           rtw_TxBBSwing_5G:default init value:0xFF (uint)
parm:           rtw_OffEfuseMask:default open Efuse Mask vaule:0 (uint)
parm:           rtw_FileMaskEfuse:default drv Mask Efuse vaule:0 (uint)
parm:           rtw_tx_pwr_lmt_enable:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_tx_pwr_by_rate:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_phy_file_path:The path of phy parameter (charp)
parm:           rtw_load_phy_file:PHY File Bit Map (int)
parm:           rtw_decrypt_phy_file:Enable Decrypt PHY File (int)

[cfg80211]
filename:       /lib/modules/4.4.0-57-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     FD4B9DA2F385F0531B5CB0B
depends:        
intree:         Y
vermagic:       4.4.0-57-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8812au]
if2name: wlan%d
ifname: wlan%d
rtw_80211d: 0
rtw_adaptivity_dml: 0
rtw_adaptivity_en: 0
rtw_adaptivity_mode: 0
rtw_ampdu_amsdu: 0
rtw_ampdu_enable: 1
rtw_amplifier_type_2g: 0
rtw_amplifier_type_5g: 0
rtw_antdiv_cfg: 2
rtw_antdiv_type: 0
rtw_busy_thresh: 40
rtw_bw_mode: 33
rtw_channel: 1
rtw_channel_plan: 89
rtw_chip_version: 0
rtw_decrypt_phy_file: 0
rtw_enusbss: 0
rtw_FileMaskEfuse: 0
rtw_hiq_filter: 1
rtw_ht_enable: 1
rtw_hwpdn_mode: 2
rtw_hwpwrp_detect: 0
rtw_hw_wps_pbc: 1
rtw_initmac: (null)
rtw_ips_mode: 1
rtw_lbkmode: 0
rtw_led_enable: 1
rtw_load_phy_file: 68
rtw_low_power: 0
rtw_lowrate_two_xmit: 1
rtw_max_roaming_times: 2
rtw_mc2u_disable: 0
rtw_mp_mode: 0
rtw_network_mode: 0
rtw_notch_filter: 0
rtw_OffEfuseMask: 0
rtw_power_mgnt: 1
rtw_qos_opt_enable: 0
rtw_rf_config: 5
rtw_RFE_type: 64
rtw_rfintfs: 2
rtw_rx_stbc: 1
rtw_smart_ps: 2
rtw_special_rf_path: 0
rtw_TxBBSwing_2G: 255
rtw_TxBBSwing_5G: 255
rtw_tx_pwr_by_rate: 0
rtw_tx_pwr_lmt_enable: 0
rtw_usb_rxagg_mode: 2
rtw_vcs_type: 1
rtw_vht_enable: 1
rtw_vrtl_carrier_sense: 2
rtw_wifi_spec: 0
rtw_wmm_enable: 1

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

grep: /etc/pm/config.d/.config.swp: Permission denied

##### udev rules ########################

##### dmesg #############################

[   16.910051] rtl8812au: module verification failed: signature and/or required key missing - tainting kernel
[   16.911322] RTL871X: rtl8812au v4.3.14_13455.20150212_BTCOEX20150128-51
[   16.911323] RTL871X: rtl8812au BT-Coex version = BTCOEX20150128-51
[   16.959018] RTL871X: rtw_ndev_init(wlan0)
[   16.986511] rtl8812au 1-1:1.0 wlx<IF from MAC [IF2]>: renamed from wlan0
[   28.186674] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready (repeated 2 times)
[   28.421859] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready (repeated 2 times)
[   29.165810] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready
[   37.039448] RTL871X: rtw_set_802_11_connect(wlx<IF from MAC [IF2]>)  fw_state=0x00000008
[   37.184336] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF2]>: link becomes ready

########## wireless info END ############

```

I tried to copy in -81 and paste here, but it WILL NOT SAVE the thing I copied after I restart. So I am sorry, but pictures are all I can do. So this is what I saw when I ran

```

sudo apt install rtl8812au-dkms

```

[URL="http://xitulis.imgur.com/all/"]http://xitulis.imgur.com/all/ 

[/URL]
(The one on the far left)

It says that the packages or whatever are already installed, yet nothing shows. When I go to EDIT CONNECTIONS, I can see my wifi network in there, but I can't see it when I try to actually connect to a network. If that makes sense. If you can't tell already, I am not good with computers, nor am I good at explaining things. I'm sorry that I'm making this difficult for you, but trust me, I am probably just as frustrated as you are.

---

### Post by vocx on 2017-06-28
> **manatee.madness said:**
> The Wireless Script in its entirety (didn't realize there was more):

```


########## wireless info START ##########
...
########## wireless info END ############

```

I tried to copy in -81 and paste here, but it WILL NOT SAVE the thing I copied after I restart. So I am sorry, but pictures are all I can do. So this is what I saw when I ran

```

sudo apt install rtl8812au-dkms

```

[URL="http://xitulis.imgur.com/all/"]http://xitulis.imgur.com/all/ 

[/URL]
(The one on the far left)

It says that the packages or whatever are already installed, yet nothing shows. When I go to EDIT CONNECTIONS, I can see my wifi network in there, but I can't see it when I try to actually connect to a network. If that makes sense. If you can't tell already, I am not good with computers, nor am I good at explaining things. I'm sorry that I'm making this difficult for you, but trust me, I am probably just as frustrated as you are.
The output of the wireless script looks fairly okay. The only big problem I see is that your wireless network card is not being found correctly. It is definitely an issue with the "rtl8812au" module, so it seems you need to upgrade it somehow, and maybe change some parameters here and there.

I don't understand why you cannot copy the information from the terminal. What do you mean it won't save? By the way, I clicked your link to the picture, and it does not show a picture. Maybe you posted the wrong link?

Yes, you mentioned that you are not good at computers before, thus why I take my time to explain each step as much as I think it's useful. Yeah, I don't think you are the best at explaining things, but it's alright, try to explain as much as you can, use as many words as you think are necessary. Words in a computer screen don't cost a thing, it's just time and patience. And that's the problem with some people, they don't feel like reading and writing enough to troubleshoot. I'm not really frustrated. It is what it is. I try to be helpful.

---

### Post by jeremy31 on 2017-06-28
In the -81 kernel, please check ```
modinfo rtl8812au | egrep -i 'file|vermagic'
```
Your results show a match in the old kernel
```
[rtl8812au]
filename:       /lib/modules/4.4.0-57-generic/kernel/drivers/net/wireless/rtl8812au.ko
version:        v4.3.14_13455.20150212_BTCOEX20150128-51
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     8E7CA44A11A3D9B9A05D5E5
depends:        cfg80211 
vermagic:       4.4.0-57-generic SMP mod_unload modversions 
```
As the filename and vermagic show the same kernel version, does the same happen when booted into the -81 kernel?

Also post results for ```
dkms status
```
You could have more than one version of the dkms module installed

---

### Post by manatee.madness on 2017-06-29
IMGUR LINK (I hope): [http://imgur.com/ptiVTbx](http://imgur.com/ptiVTbx)

I mean that I highlight the output in the terminal in kernel -81, and copy it. When I restart the computer, go to the GRUB menu and select kernel -57, I go to the terminal, press CTRL+SHIFT+V, like I normally do, and nothing pastes. So it doesn't save after I switch kernels. At this point I'm thinking I may just try to find a new USB network thing, as I have had SEVERAL issues with this particular one in the past. And it always takes days of replying, trying new codes and commands and such before the issue is finally fixed, and then a new one pops up a month or two later. I just don't think it's worth the trouble, and I would save a lot more time if I just got a more reliable wifi thing.

---

### Post by vocx on 2017-06-29
> **manatee.madness said:**
> IMGUR LINK (I hope): [http://imgur.com/ptiVTbx](http://imgur.com/ptiVTbx)

I mean that I highlight the output in the terminal in kernel -81, and copy it. When I restart the computer, go to the GRUB menu and select kernel -57, I go to the terminal, press CTRL+SHIFT+V, like I normally do, and nothing pastes. So it doesn't save after I switch kernels. At this point I'm thinking I may just try to find a new USB network thing, as I have had SEVERAL issues with this particular one in the past. And it always takes days of replying, trying new codes and commands and such before the issue is finally fixed, and then a new one pops up a month or two later. I just don't think it's worth the trouble, and I would save a lot more time if I just got a more reliable wifi thing.
Well, no, it doesn't save when you reboot the computer. If you create a new file, write things on it, then reboot, the new file doesn't appear again after a reboot, does it? That's fairly obvious, no? What can you do? Open a new text file using "gedit", copy the text from the terminal, paste the text in the file, **save the file**. Reboot the computer, choose the other kernel. The file that you saved is still there, with the text that you copied.

About the network card, see the bottom of my post #8
> **vocx said:**
> 
...

Here is a thread in this forum of a user who **gave up on trying to make it work**. He didn't run the wireless script, he didn't follow directions, and instead decided to not use the USB wireless device any more.
[https://ubuntuforums.org/showthread.php?t=2345309](https://ubuntuforums.org/showthread.php?t=2345309)

My suggestion is, **if you don't want to bother any more, get a new wireless device**, one that is well supported in Linux. Otherwise, try to make it work with the "rtl8812au-dkms" package. Try to not get frustrated if it does not work, and please follow advice.

...

I do think this device is a bit troublesome, and that is a shame. However, if it works with kernel -57, it seems it can be made to work, the only problem is that the "rtl8812au" is not compiled correctly against the new kernel. If it is, it may work, but some things need to be changed in the configuration files. It is up to you if you want to continue.

If you do, boot into the -81 kernel and run the commands in post #13.
```
modinfo rtl8812au | egrep -i 'file|vermagic'
dkms status
```
After this, there is maybe one or two more steps to try.

Remember that you can copy and paste the output into a text file, and if you save it, it will be there after you reboot.

---

