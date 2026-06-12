---
title: "wireless-info.txt gives no output on live USB ubuntu gnome 16.04"
date: 2017-08-03
forum: Networking &amp; Wireless
---

### Post by mattiadale on 2017-08-03
I'd like to install ubuntu gnome 16.04 on a HP Stream 13 notebook, but before doing that I wanted to try it from the live usb without installing it.
It boots fine, but the wifi does not work. I tried to run the "wireless-info.txt" code, but it only prints the first line of the code ([COLOR=#000000]########## wireless info START ##########): If I try to run the other commands separately in the terminal (being in the same directory) it works fine. Any clue why this might be happening?

Also, does it make sense to check whether it works or not from the live usb? Cause I want to be sure that once I install it I can at least connect to the internet.[/COLOR]

---

### Post by Bucky Ball on 2017-08-03
Welcome. While booted to a live session, open a terminal and run this command:

```
sudo lshw -C network
```

Post the output back here between [code] tags, please (see link in my signature for how to use code tags). Finding out what card you are using will let us know whether it is going to work or not. Whether it works in a live session or not is sometimes misleading. It might work but not work in the install. It might not work, but will work in the install with the correct drivers (which might be installed on your first update). 

Post the output of the command and we'll see what you have.

---

### Post by mattiadale on 2017-08-03
Thanks! Here is the output:

```

  *-network UNCLAIMED     
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:91000000-91007fff

```

---

### Post by chili555 on 2017-08-03
Running the live USB, you should be able to go to Software and Updates > Additional Drivers and install the wireless driver for your Broadcom and be all set.

---

### Post by mattiadale on 2017-08-03
When I select my device driver and click on "Apply Changes" it says "applying changes..." and after some seconds it just toggles back to "Do not use the device" option :/

---

### Post by chili555 on 2017-08-03
Any clues in the log? From the terminal:```
cat /var/log/syslog | grep -i bcmwl
```

---

### Post by mattiadale on 2017-08-03
I get this:

```

ubuntu-gnome@ubuntu-gnome:~$ cat /var/log/syslog | grep -i bcmwl
Aug  3 22:10:48 ubuntu-gnome org.debian.apt[1228]: 22:10:48 AptDaemon [INFO]: CommitPackages() was called: dbus.Array([dbus.String('linux-generic'), dbus.String('bcmwl-kernel-source')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s'))
Aug  3 22:10:48 ubuntu-gnome AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String('linux-generic'), dbus.String('bcmwl-kernel-source')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s'))
Aug  3 22:10:52 ubuntu-gnome AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String('linux-generic'), dbus.String('bcmwl-kernel-source')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Aug  3 22:10:52 ubuntu-gnome org.debian.apt[1228]: 22:10:52 AptDaemon.Worker [INFO]: Committing packages: dbus.Array([dbus.String('linux-generic'), dbus.String('bcmwl-kernel-source')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Aug  3 22:11:38 ubuntu-gnome AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String('linux-generic'), dbus.String('bcmwl-kernel-source')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s'))
Aug  3 22:11:38 ubuntu-gnome org.debian.apt[1228]: 22:11:38 AptDaemon [INFO]: CommitPackages() was called: dbus.Array([dbus.String('linux-generic'), dbus.String('bcmwl-kernel-source')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s'))
Aug  3 22:11:39 ubuntu-gnome AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String('linux-generic'), dbus.String('bcmwl-kernel-source')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Aug  3 22:11:39 ubuntu-gnome org.debian.apt[1228]: 22:11:39 AptDaemon.Worker [INFO]: Committing packages: dbus.Array([dbus.String('linux-generic'), dbus.String('bcmwl-kernel-source')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))

```

---

### Post by chili555 on 2017-08-03
Weird. That means nothing useful. How about:```
sudo dpkg -s bcmwl-kernel-source
sudo modprobe wl
```

---

### Post by mattiadale on 2017-08-04
I ran the first command and it says ```
 dpkg-query: package 'bcmwl-kernel-source' is not installed and no information is available 
```
So I installed it (with sudo apt-get install bcmwl-kernel-source, hope it is correct) and it gives the followinf output:
```

Package: bcmwl-kernel-source
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 7870
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: bcmwl
Version: 6.30.223.271+bdcom-0ubuntu1~1.1
Replaces: bcmwl-modaliases
Depends: dkms, linux-libc-dev, libc6-dev
Conflicts: bcmwl-modaliases
Description: Broadcom 802.11 Linux STA wireless driver source
 This package contains Broadcom 802.11 Linux STA wireless driver
 for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,
 BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based
 hardware.
Modaliases: wl(pci:v000014E4d00004311sv*sd*bc02sc80i*, pci:v000014E4d00004312sv*sd*bc02sc80i*, pci:v000014E4d00004313sv*sd*bc02sc80i*, pci:v000014E4d00004315sv*sd*bc02sc80i*, pci:v000014E4d00004727sv*sd*bc02sc80i*, pci:v000014E4d00004328sv*sd*bc02sc80i*, pci:v000014E4d00004328sv*sd*bc02sc80i*, pci:v000014E4d00004329sv*sd*bc02sc80i*, pci:v000014E4d0000432asv*sd*bc02sc80i*, pci:v000014E4d0000432bsv*sd*bc02sc80i*, pci:v000014E4d0000432csv*sd*bc02sc80i*, pci:v000014E4d0000432dsv*sd*bc02sc80i*, pci:v000014E4d00004365sv*sd*bc02sc80i*, pci:v000014E4d00004353sv*sd*bc02sc80i*, pci:v000014E4d00004357sv*sd*bc02sc80i*, pci:v000014E4d00004358sv*sd*bc02sc80i*, pci:v000014E4d00004359sv*sd*bc02sc80i*, pci:v000014E4d00004331sv*sd*bc02sc80i*, pci:v000014E4d000043a0sv*sd*bc02sc80i*, pci:v000014E4d000043B1sv*sd*bc02sc80i*)
Original-Maintainer: Alberto Milone <alberto.milone@canonical.com>

```

The second command gives:
```

modprobe: ERROR: could not insert 'wl': Required key not available

```

---

### Post by chili555 on 2017-08-04
> modprobe: ERROR: could not insert 'wl': Required key not availableAh, haaaa! Well there's the problem then. Please see: [https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules)

---

### Post by mattiadale on 2017-08-04
Thank you very much!

---

### Post by chili555 on 2017-08-04
So, that means that the wireless is working now? If so, please use thread tools at the top to mark Solved.

---

