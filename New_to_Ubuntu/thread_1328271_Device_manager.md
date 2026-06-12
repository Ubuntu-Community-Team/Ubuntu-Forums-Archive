---
title: "Device manager?"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by Nikkiru on 2009-11-16
I'm trying to find where they hid the device manager. I'd have thought it would be under  the admin tab, but no luck. 

Also, how do you install device drivers? I have a device which needs a driver, and I have the driver, but nothing in "help" seems to address how you put the two together.

---

### Post by Paqman on 2009-11-16
There isn't really a device manager, and drivers are usually built into the system. Some devices such as graphics and wifi cards will need a driver, if so they're available from System > Admin > Hardware Drivers.

What device do you have that you're trying to use?

---

### Post by Nikkiru on 2009-11-16
> **Paqman said:**
> There isn't really a device manager, and drivers are usually built into the system. Some devices such as graphics and wifi cards will need a driver, if so they're available from System > Admin > Hardware Drivers.

What device do you have that you're trying to use?

I looked there, but it was blank, and only purported to address what they called "proprietary drivers". The "help" link led to a loop of articles, one of  which did say that I might need to download and install drivers, but gives no clue as to how one accomplishes this. 

I'm trying to determine whether or not my onboard wifi card is actually installed, and I'm also trying to install an external wifi card. I know the external isn't installed, because if it were it would be picking up a network, as it does in windows. 



So when you say there is no functional equivalent of a device manager, are you telling me that  there actually is  no way to determine what hardware is installed and what its status is?

---

### Post by halitech on 2009-11-16
couple of ways to find out what hardware is installed. The command
```
lshw
``` will tell you in a terminal. If you want a GUI, install hardinfo```
sudo apt-get install hardinfo
``` and then run hardinfo

to figure out about the wireless, run ```
iwconfig
```

---

### Post by philinux on 2009-11-16
Wireless cards and other hardware have drivers already in the kernel. Not usually necessary to install drivers.

To check whats there open a terminal Apps>access>terminal and type this in.

Post back with the result.

```
lspci
```

You can install from synaptic a nice gui for this info. There are in fact two. sysinfo and hardinfo. Once installed they appear under Apps>system tools.

---

### Post by Nikkiru on 2009-11-16
> **halitech said:**
> couple of ways to find out what hardware is installed. The command
```
lshw
``` will tell you in a terminal. If you want a GUI, install hardinfo```
sudo apt-get install hardinfo
``` and then run hardinfo

to figure out about the wireless, run ```
iwconfig
```

How and where do you post this command?

---

### Post by halitech on 2009-11-16
open a terminal and type them in

---

### Post by Paqman on 2009-11-16
Into a terminal window. Applications > Accessories > Terminal.

---

### Post by Nikkiru on 2009-11-16
> **halitech said:**
> open a terminal and type them in

How do you do this?

---

### Post by philinux on 2009-11-16
[apt:sysinfo]("apt:sysinfo")

[apt:hardinfo]("apt:hardinfo")

Just click the links in turn to install the two apps.

---

### Post by Nikkiru on 2009-11-16
> **philinux said:**
> Wireless cards and other hardware have drivers already in the kernel. Not usually necessary to install drivers.

For whatever reason, my external wifi card works in windows, but not in ubuntu 9.1. I have a driver which purports to be for a debian kernal. I want to be able to install it.  So far, I haven't seen any way to do this. Do you know how?

I'm sorry to be so insistent. But in order to deal with  this I have to log off windows, and if it doesn't work I'll need to log back on. So I'd like to be able to copy this thread, and have it cover every contingency I might have to deal with.

---

### Post by Nikkiru on 2009-11-16
> **philinux said:**
> [apt:sysinfo]("apt:sysinfo")

[apt:hardinfo]("apt:hardinfo")

Just click the links in turn to install the two apps.

When I click on the links, I get an error message. I guess that's because I can only get online in windows. But when I try to download the link targets to save as files for when I log onto ubuntu, I also get an error message saying that they aren't downloadable.

Is there any way to install these apps if you can't get online with ubuntu?

---

### Post by halitech on 2009-11-16
Can you plug the machine in to a wired connection until we get the wireless working? It will be a lot easier if you can.

---

### Post by Paqman on 2009-11-16
> **Nikkiru said:**
> 
Is there any way to install these apps if you can't get online with ubuntu?

Nope. Both those packages are in the Universe repository, so unless you've got a copy of the Ubuntu DVD (as opposed to the CD) then you haven't got a copy of them locally.

Can you just plug into the router to get online?

Either way, you don't need them to interrogate your wifi hardware and drivers. The commands halitech gave you will do the job.

---

### Post by Nikkiru on 2009-11-16
I can't plug directly into the router, nor otherwise get a hard-wired connection.

So does anybody know how to install a driver from disk in case I need to?

---

### Post by Paqman on 2009-11-16
> **Nikkiru said:**
> 
So does anybody know how to install a driver from disk in case I need to?

What format is this driver in, and where did you get it from? You might find if it's a tarball that it's got installation instructions in a text file inside it.

---

### Post by Nikkiru on 2009-11-16
> **Paqman said:**
> What format is this driver in, and where did you get it from? You might find if it's a tarball that it's got installation instructions in a text file inside it.
I can quote from the "readme" file, and maybe somebody else can translate it into English? 

> Release Date: 2007-08-22, ver 1.24
RTL8187B Linux driver version 1.24

   --This driver supports RealTek RTL8187/RTL8187B Wireless LAN NIC
     for
     2.6 kernel:
     Fedora Core 2/3/4/5/6/7, Debian 3.1, Mandrake 10.2/Mandriva 2006, 
     SUSE 9.3/10.1/10.2, Gentoo 3.1, etc.
     2.4 kernel:
     Redhat 9.2, etc
   - Support Client mode for either infrastructure or adhoc mode
   - Support WEP, WPAPSK and WPA2PSK connection

< Component >
The driver is composed of several parts:
	1. Module source code
	  stack.tar.gz
	  drv.tar.gz
	
	2. Script ot build the modules
	  makedrv

	3. Script to load/unload modules
	  wlan0up 
	  wlan0down 

	4. Script and configuration for DHCP
 	  wlan0dhcp
	  ifcfg-wlan0
	4. Supplicant source code:
	  wpa_supplicant-0.5.3.tar.gz

	5. Example of supplicant configuration file:
	  wpa1.conf

< Installation >
Runing the scripts can finish all operations of building up modules 
from the source code and start the nic.
	1. Build up the drivers from the source code
	  ./makedrv

	2. load the driver module to kernel and start up nic
	  ./wlan0up
          Note: when "insmod: error inserting 'xxxx.ko': -1 File exists" comes out
                after run ./wlan0up, please run ./wlan0down first, then it should 
                be ok.


All I know is that I left click and  right click every file in the folder that looks like it might be something analogous to an executable file, and nothing ever happens.

---

### Post by hal10000 on 2009-11-16
I guess your main problem is to gwt your wireless working. Don't care for the graphical system tools by now. You can get all the information you need by typing a command into a terminal window, and it's even better do do this if you want to post the output of the commands here, so people can help you to get your network running.

In the very most cases you don't need to compile a driver by yourself. The very most drivers are already installed or can be installed easily though your package manager, so there's usually no need to download any zipped package from somewhere in the internet.

The first thing you should do is to give us as many information about your wireless cards as possible:
-manufacturer
-model
-chipset (if you know it)
-usb or pci device

You should also tell something about the way it is to be connected:
-accesspoint or router
-encryption method (WEP or WPA/WPA2)
-static or dynamic ip-address

Then plug in all your wireleess cards, open  a terminal window and post the outputs of the following commands:

```

lspci
lsusb
sudo lshw -C network
iwconfig
ifconfig
route

```
You can easily mark the outputs and paste them with your middle mouse button to post it here or to save it in a textfile for later use in windows.

With these informations we should be able to get your wireless card running.

[EDIT] The RealTek RTL8187/RTL8187B Wireless LAN NIC needs no installation, the driver is already installed

---

### Post by Paqman on 2009-11-16
You might want to check this thread:

[HOWTO: Get RTL8187B (ID: 8197) Working. Step by Step]("http://ubuntuforums.org/showthread.php?t=792092&highlight=RTL8187b+%26amp%3B+HOWTO%3A")

...for some step-by-step instructions on getting your particular wireless card set up.

Personally i'd just pull the nasty Realtek card out and replace it with a nice cheap Intel card that will just work without all the stress of hacking an incompatible card. You could pick one up off eBay for pocket change.

---

### Post by Nikkiru on 2009-11-16
> **Paqman said:**
> Nope. Both those packages are in the Universe repository, so unless you've got a copy of the Ubuntu DVD (as opposed to the CD) then you haven't got a copy of them locally.

Can you just plug into the router to get online?

Either way, you don't need them to interrogate your wifi hardware and drivers. The commands halitech gave you will do the job.

> **Paqman said:**
> What format is this driver in, and where did you get it from? You might find if it's a tarball that it's got installation instructions in a text file inside it.

> **Paqman said:**
> You might want to check this thread:

[HOWTO: Get RTL8187B (ID: 8197) Working. Step by Step]("http://ubuntuforums.org/showthread.php?t=792092&highlight=RTL8187b+%26amp%3B+HOWTO%3A")

...for some step-by-step instructions on getting your particular wireless card set up.

Personally i'd just pull the nasty Realtek card out and replace it with a nice cheap Intel card that will just work without all the stress of hacking an incompatible card. You could pick one up off eBay for pocket change.

This card has the range I need, unlike most other external cards I've tried. It certainly has more range than the internal wifi card on my laptop (a latitude D600), which also doesn't appear to be working in Ubuntu.

I'm also finding out from other threads that 9.1 has some serious issues around connectivity, especially with wifi cards. Could it be that what I really need to do is install an earlier version?

---

### Post by Paqman on 2009-11-16
> **Nikkiru said:**
> 
I'm also finding out from other threads that 9.1 has some serious issues around connectivity, especially with wifi cards. Could it be that what I really need to do is install an earlier version?

I really couldn't say for certain, since i've had no trouble with my laptop. I'd say it's really unlikely though. If there was support for that card in the older kernels, it would also be in Karmic's kernel. I don't think your problem is a bug, the problem is that your wifi chipset isn't supported.

---

### Post by Nikkiru on 2009-11-16
OK, so it's not supported in that the driver isn't embedded in the kernel. It's not embedded in the windows kernel either, but I managed to install it with no problems. 

I have the driver. I just need somebody to tell me how to install it.

---

### Post by Paqman on 2009-11-17
That's because Windows has a very limited selection of drivers in the kernel compared to Linux, so it's normal to have to add them yourself. Adding them manually on Linux is unusual, which is why it's a lot more messy than it should be. Ubuntu has tried to solve this by installing most troublesome drivers through the Hardware Drivers utility, but that's not much use for you if your particular card sin't supported by that tool.

Did you try the instructions in the thread I linked to?

---

