---
title: "networkmanager ndiswrapper ar5212"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by ozooha on 2007-05-01
I am running Feisty Fawn 7.04 and my wifi card ar5212 (NETGEAR WPN511) works flawlessly with the networkmanager.
However the signal strength is always between 50-62% which wasn't the case with Edgy (always 100%) in which I configured to work with ndiswrapper and my windows driver.
My question is can I use ndiswrapper to change my default driver which come with Feisty with the windows driver and still use the networkmanager?
If so can you tell me how? I mean either a few guidelines with command lines or a post in the forum or a website.
I truely appreciate your patience with my rant.
OZooHA

---

### Post by gruadp on 2007-05-01
you can try easily:

[LIST=1]
[*]install the ndiswrapper-packages ndiswrapper-common, ndiswrapper-utils and optionally ndisgtk
[*]get the win-drivers to your harddisk - something like ar512.inf and the related sys-file
[*]install the win-driver with the ndisgtk-tool (windows-wireless-drivers in system-adminstration) or  even easier with (as root) ndiswrapper -i youdriver.inf
[*] check ifconfig if you've got your new  network-device
[/LIST]

I'm sure it helps if you deactive the native module for your card before :)

But in general I've to say that to me wireless worked much better in edgy than in feisty also. Whyever.

p

---

### Post by spd106 on 2007-05-01
If you are going to pursue this course of action then I have a few comments that you should consider.

You will need to blacklist the ath_pci and ath_hal drivers in the /etc/modprobe.d/blacklist file or they will conflict with ndiswrapper on boot.

Network Manager only understands the wireless extensions interface and ndiswrapper probably supports this better than madwifi at the moment, so using N M shouldn't be a problem.

The newest release of ndiswrapper (v1.43) has some changes that affect Atheros cards, so that one might work out better, but it will involve building from source.

---

### Post by UrbenLegend on 2007-05-01
The only reason why your edgy setup gave you 100% signal strength is because ndiswrapper does not tell you the signal strength, so it always reports 100%. You will almost never get 100% in the real world. I'd say stick with the native drivers.

---

### Post by ozooha on 2007-05-01
> **UrbenLegend said:**
> The only reason why your edgy setup gave you 100% signal strength is because ndiswrapper does not tell you the signal strength, so it always reports 100%. You will almost never get 100% in the real world. I'd say stick with the native drivers.
I know that 100% is ideal but when all bars are lit up in winxp why could I not get the same in ubuntu. Besides the router is like a meter or 3 around me with no interference.
OZooHA

---

### Post by ozooha on 2007-05-01
> **spd106 said:**
> If you are going to pursue this course of action then I have a few comments that you should consider.

You will need to blacklist the ath_pci and ath_hal drivers in the /etc/modprobe.d/blacklist file or they will conflict with ndiswrapper on boot.

Network Manager only understands the wireless extensions interface and ndiswrapper probably supports this better than madwifi at the moment, so using N M shouldn't be a problem.

The newest release of ndiswrapper (v1.43) has some changes that affect Atheros cards, so that one might work out better, but it will involve building from source.

Thanks for the input. How would I know for sure what to blacklist..you pointed out - ath_pci & ath_hal need to be blacklisted. How did you know that..through "lsmod" or what?
I presume if my ndiswrapper doesn't work and I want to restore back to the native feisty driver I can just delete those entries from the black list or simply delete the blacklist list file if it contains only those entires related to the native driver.
If I have to build the latest ndiswrapper..do I just do the usual "make install" for building it?
Thanks you again. I look forward to your response.
OZooHA

---

### Post by ozooha on 2007-05-01
> **gruadp said:**
> you can try easily:

[LIST=1]
[*]install the ndiswrapper-packages ndiswrapper-common, ndiswrapper-utils and optionally ndisgtk
[*]get the win-drivers to your harddisk - something like ar512.inf and the related sys-file
[*]install the win-driver with the ndisgtk-tool (windows-wireless-drivers in system-adminstration) or  even easier with (as root) ndiswrapper -i youdriver.inf
[*] check ifconfig if you've got your new  network-device
[/LIST]

I'm sure it helps if you deactive the native module for your card before :)

But in general I've to say that to me wireless worked much better in edgy than in feisty also. Whyever.

p

How do I do the blacklist the components of the native feisty driver?
What command do I need to execute to get a list of components that need to be blacklisted?
"lsmod" or what?
OZooHA

---

### Post by spd106 on 2007-05-02
If you look through the output of these commands you will see which driver is being loaded.
```
dmesg
```
```
sudo lshw -class network
```

The /etc/modprobe.d/blacklist file contains a line blacklist "driver name", if you decide to go back to using it then either delete the line you have added or just put a hash in front of it (comment out).
E.g. 

This is mine, note that I added the bcm43xx driver because I use ndiswrapper instead for my Broadcom card.
```
$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# added manually on 20070109
blacklist bcm43xx

```
While useful, lsmod only shows you the drivers currently loaded. You can add/remove drivers on the fly with the modprobe tool, but bear in mind that the changes will not survive a reboot.

UrbenLegend is probably right about the signal strength, but you don't have anything to lose except and it's worth trying out if only for the experience.

---

### Post by spd106 on 2007-05-02
The other way to disable madwifi is to follow the procedure given on the developers website.
[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

---

### Post by ozooha on 2007-05-02
> **spd106 said:**
> The other way to disable madwifi is to follow the procedure given on the developers website.
[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

Appreciate your inputs and comments. Will do it for the experience.
Thanks.
OZooHA

---

### Post by tcoffee on 2008-05-06
This approach recently worked for me, so I wanted to give more details for those who may be trying it:

I recently installed 8.04 Hardy Heron on a Lenovo Thinkpad R60 with an Atheros AR5212 802.11abg NIC (rev 01) wireless chipset. As with previous Ubuntu versions, my attempts to achieve wireless connectivity with NetworkManager failed even though the OS had automatically installed the Atheros restricted drivers on installation. With previous installations, I had tried several other solutions (including madwifi) without success.

My machine came with Windows XP pre-installed, which I left on a dual-boot partition when I installed Hardy. I currently have no wired internet connection, so I followed the procedure below:

In Windows:

1. downloaded ndiswrapper-common, ndiswrapper-utils-1.9, and ndisgtk as *.deb files from [http://packages.ubuntu.com](http://packages.ubuntu.com)

2. copied C:\WINDOWS\system32\net5211.inf and C:\WINDOWS\system32\drivers\ar5211.sys

3. exported these files and rebooted into Linux

In Linux:

4. installed ndiswrapper via

sudo dpkg -i ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk

5. blacklisted the existing Linux Atheros drivers by adding the following lines to /etc/modprobe.d/blacklist:

blacklist ath_pci
blacklist ath_hal

6. rebooted the machine

7. went to System >> Administration >> Windows Wireless Drivers and used the GUI to install net5211.inf

8. rebooted again (possibly not necessary)

9. used NetworkManager to connect to wireless as advertised

---

