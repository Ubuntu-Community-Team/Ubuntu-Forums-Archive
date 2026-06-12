---
title: "No Wireless Connection in network-admin"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by antisho on 2007-08-23
My wireless connection was working fine up until a few days ago. I have no idea what happened, but now no "Wireless Connection" appears in network-admin at all. My /etc/network/interfaces is
```
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

iface eth1 inet static
wireless-essid linksys
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
```
but anything I try tells me, essentially, eth1 doesn't exist and eth0 and lo aren't wireless connections. Changing the static IPs to DHCP has no effect either. I'm running Feisty... can anyone help?

---

### Post by bmartin on 2007-08-23
How did you originally get your wireless to work? Did you follow some instructions to install the drivers, or did it work out-of-the-box?

---

### Post by antisho on 2007-08-23
I don't remember if it worked out of the box. It usually worked, sometimes some tweaking was required, but eth1 at least always *existed*.

---

### Post by bmartin on 2007-08-23
What's the output of **lspci**? If you can find the relevant lines, that's all that's needed.

Then we'll either have to find a kernel module that's appropriate for your wireless card or use ndiswrapper, I guess. Were you using ndiswrapper before? The solution might be as simple as **sudo modprobe ndiswrapper**. If you're not sure, run the command **ndiswrapper -l**. If there are any drivers installed, you were using it.

---

### Post by antisho on 2007-08-23
Yes, I'm using ndiswrapper - my wireless card is Broadcom; lspci gives
```
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```
But sudo modprobe ndiswrapper:
```
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.20-16-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
```
That file doesn't exist, apparently.

---

### Post by bmartin on 2007-08-23
OK, let's redo the Broadcom installation. I promise this'll be quick and relatively painless.

Go to [this thread]("http://ubuntuforums.org/showthread.php?t=405990") and download/run the 0.3.1 installer. Make sure you use the ndiswrapper installation.

EDIT: Don't use the offline installer. It doesn't support the 386 kernel (it only supports the generic kernel).

EDIT: If the installer spits out a message saying **ndiswrapper is already the newest version**, delete the old ndiswrapper file using **sudo rm /usr/sbin/ndiswrapper**.

---

### Post by antisho on 2007-08-23
I believe I've tried this before... but anyway, it gives me
```
./bcm43xx-ndiswrapper.sh: line 120: ndiswrapper: command not found
* inserting ndiswrapper module
./bcm43xx-ndiswrapper.sh: line 122: ndiswrapper: command not found
./bcm43xx-ndiswrapper.sh: line 124: ndiswrapper: command not found
FATAL: Could not open '/lib/modules/2.6.20-16-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko': No such file or directory
*** Installation is complete. You may need to restart your computer for the changes to take effect.
```
Strangely, when I try to run ndiswrapper...
```
$ ndiswrapper
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
$ sudo apt-get install ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-common is already the newest version.
ndiswrapper-common set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by bmartin on 2007-08-23
Okay, here's how that happened:
1. ndiswrapper-common is still marked as an installed package in Apt.
2. The ndiswrapper source code's installation removed the old ndiswrapper programs.
3. ndiswrapper failed to compile.

I'd try compiling ndiswrapper manually. It'll take a long time to download the Broadcom drivers, unfortunately. I recommend [this guide]("http://ubuntuforums.org/showthread.php?t=297092").

I have no idea why ndiswrapper would fail to compile. The installer downloads the necessary packages. You used the installer on a computer w/ an internet connection, right?

If all else fails, I'll happily compile a DEB of ndiswrapper for you. Just let me know.

---

### Post by bmartin on 2007-08-23
Here's a DEB to save you the trouble. I simply downloaded your kernel headers and recompiled for that kernel.

To install it, use **dpkg -i**.

---

### Post by antisho on 2007-08-23
All right... I'll try those.

---

### Post by antisho on 2007-08-23
It works! Thanks.

---

### Post by bmartin on 2007-08-23
Sweet! Out of curiosity, did you use my DEB or did you compile it yourself?

---

### Post by antisho on 2007-08-23
Compiled. Not that the deb was broken or anything - I just did the other way first, and it works.

---

### Post by antisho on 2007-09-25
Well, I'm having the same problem again, and I have no idea why. When I try that same guide, I get

```
$ sudo ndiswrapper -m
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
```

Maybe I just need to reboot. If not, why is this happening?

---

