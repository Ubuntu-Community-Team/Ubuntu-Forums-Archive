---
title: "Broadcom card not working on Ubuntu 9.10 (testing version)"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by Masterion on 2009-10-24
Okay, so I'm running the test version of Ubuntu 9.10, trying to get my Broadcom Wireless Card working. 
Going into the Help feature, it tells me to enter the code "sudo lshw -C network" to indicate if the card's working. Typing in the code gives me this:

*-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:18 memory:d0000000-d0001fff
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:03:25:14:4c:00
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=64 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
       resources: irq:23 ioport:1800(size=256) memory:d0002c00-d0002cff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:8f:30:c5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

The problem is that when I start up Ubuntu, the wireless light is on, 
but the network says that the card is disabled. What gives?

---

### Post by dvlchd3 on 2009-10-24
Try this:

```

sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

```

Now see if you can see any wireless networks show up:

```

iwlist wlan0 scanning

```

---

### Post by Masterion on 2009-10-24
> **dvlchd3 said:**
> Try this:

```

sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

```]

Inputing that gives me this:

```
 sudo: /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh: command not found 
```

---

### Post by anewguy on 2009-10-24
Please try this and post back the results - maybe there's just a small typo in the name (I did that last night myself!):

ls -al /usr/share/b43-fwcutter


I don't know if you have any experience with it, but if worse comes to worse we can always use ndiswrapper and the Windows driver for your wireless.

Dave :)

---

### Post by aesis05401 on 2009-10-24
At the end of [this doc]("http://gwos.org/udsf/doku.php/hardware:broadcom:wireless") it says that some broadcom cards can be disabled by one OS installation and therefore appear disabled to other OS's booted on the same machine.  Is there any chance that this happened on your machine?

---

### Post by Masterion on 2009-10-24
> **aesis05401 said:**
> At the end of [this doc]("http://gwos.org/udsf/doku.php/hardware:broadcom:wireless") it says that some broadcom cards can be disabled by one OS installation and therefore appear disabled to other OS's booted on the same machine.  Is there any chance that this happened on your machine?

The card works on Windows, and I guess it's possible that it happened to Ubuntu; to be sure, I'm going to run the directions in that document.

---

### Post by sandyd on 2009-10-24
try running this.
```

sudo apt-get upgrade
sudo apt-get install linux-headers-generic build-essential
mkdir ~/dev
cd ~/dev
mkdir boardcom_sta
cd broadcom_sta

```

for 32 bit
```

wget http://www.broadcom.com/docs/linux_sta/hybrid-portsrc-x86_32-v5.10.91.9.3.tar.gz

```

for 64 bit
```

http://www.broadcom.com/docs/linux_sta/hybrid-portsrc-x86_64-v5.10.91.9.3.tar.gz

```

then
```

tar xvfz *
make[FONT=monospace]
[/FONT]sudo modprobe lib80211[FONT=monospace]
[/FONT]insmod wl.ko
sudo echo "wl" >> /etc/modules


```

---

### Post by Masterion on 2009-10-25
Entering the code:

```
sudo echo "wl" >> /etc/modules
```gives me this:

```
bash: /etc/modules: Permission denied
```How do I give permission?

---

### Post by sandyd on 2009-10-25
> **Masterion said:**
> Entering the code:

```
sudo echo "wl" >> /etc/modules
```gives me this:

```
bash: /etc/modules: Permission denied
```How do I give permission?
```

sudo modprobe wl
gksudo gedit /etc/modules

```enter "wl" (without quotes) on a blank new line at the bottom of the file.

note that you could have done
```

sudo apt-get install bcm43xx-fwcutter

```then run the command that that guy gave you (cant see the actual post cause im in the reply box)

except those drivers are a bit outdated.

---

### Post by anewguy on 2009-10-25
As an alternate, if you have no luck with what's been presented here so far, it should also be possible to install the driver manually using the command line and a utility called ndiswrapper (and it's GUI'd front end, ndisgtk). There are some out there who would balk at this, since they think the new b43 drivers are the way to go, but sometimes it just works best to use ndiswrapper and be done with it. So.....

Check with the package manager and see if it shows ndiswrapper installed or not. If so, skip this step:

- put in the LiveCD you installed from
- using the file browser, navigate the CD to the main/pool/n/ndiswrapper folder
- click each of the files there (1 for utils and 1 for common) to install them
- navigate the CD to the main/pool/n/ndisgtk folder
- click on the file there to install ndisgtk

Next you need the Windows drivers for your device. Since you have the CD for it, I would suggest the following first:

- put in the driver CD
- using the file browser, navigate the CD searching for a "driver" or "drivers" or some such thing sub folder. In this folder, see if there are individual .inf and .sys files.
- if there are individual .inf and .sys files, copy them to your desktop
- if there is only an executable, try opening it - it may come up in the archive handler so you can extract just the .inf and .sys files. If not, post back and we'll get them for you.

At this point, you should have the Windows driver .sys and .inf files on your desktop. Start ndisgtk (you may have to go to a terminal window and type ndisgtk and press enter). You want to install a new device and point it to your desktop for the driver files.

Once done with that, it might be wise to add to the blacklist so that the other modules don't conflict with your new driver:

- sudo gedit /etc/modprobe.d/blacklist.conf

- scroll to the end of the last line in the file and press enter a couple of times

- add these 2 lines:

b43
ssb

Save the file, close the editor and reboot. Then see if your wireless is working.

Just an alternative way of trying to get this working as well.

Dave :)

---

### Post by sandyd on 2009-10-25
> **anewguy said:**
> As an alternate, if you have no luck with what's been presented here so far, it should also be possible to install the driver manually using the command line and a utility called ndiswrapper (and it's GUI'd front end, ndisgtk). There are some out there who would balk at this, since they think the new b43 drivers are the way to go, but sometimes it just works best to use ndiswrapper and be done with it. So.....

Check with the package manager and see if it shows ndiswrapper installed or not. If so, skip this step:

- put in the LiveCD you installed from
- using the file browser, navigate the CD to the main/pool/n/ndiswrapper folder
- click each of the files there (1 for utils and 1 for common) to install them
- navigate the CD to the main/pool/n/ndisgtk folder
- click on the file there to install ndisgtk

Next you need the Windows drivers for your device. Since you have the CD for it, I would suggest the following first:

- put in the driver CD
- using the file browser, navigate the CD searching for a "driver" or "drivers" or some such thing sub folder. In this folder, see if there are individual .inf and .sys files.
- if there are individual .inf and .sys files, copy them to your desktop
- if there is only an executable, try opening it - it may come up in the archive handler so you can extract just the .inf and .sys files. If not, post back and we'll get them for you.

At this point, you should have the Windows driver .sys and .inf files on your desktop. Start ndisgtk (you may have to go to a terminal window and type ndisgtk and press enter). You want to install a new device and point it to your desktop for the driver files.

Once done with that, it might be wise to add to the blacklist so that the other modules don't conflict with your new driver:

- sudo gedit /etc/modprobe.d/blacklist.conf

- scroll to the end of the last line in the file and press enter a couple of times

- add these 2 lines:

b43
ssb
**wl**

Save the file, close the editor and reboot. Then see if your wireless is working.

Just an alternative way of trying to get this working as well.

Dave :)
added wl since its included by default on ubuntu (or at least it was on mine)

---

### Post by anewguy on 2009-10-26
Thanks Carlee!  I haven't used it since back about version 8 or so, and at that time all we blacklisted was the old bcm43xx module, so I was trying to remember them from what I've read, but I guess I sure missed that one!

Thanks again!

Dave :)

---

### Post by cxwhite on 2009-11-22
Thanks for this thread, folks.

Carlee, I followed your instructions for using the latest broadcom driver and everything eventually went as you described, but the OS (9.10) is not talking to the wifi.

One error that came up is a message about licensing, but I don't know.

[I][B][FONT=Tahoma]make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
[/FONT][/B][FONT=Tahoma][B]  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /hybrid_wl/wl.o
see include/linux/module.h for more information
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'[/B]
[/FONT]
[/I]I also ran into the permission denied message when I attempted to make the "wl" entry to etc/modules.

I'll have a go at the ndiswrapper that newguy suggested after a good night's sleep.  
Is there a logfile I can check to see what is going wrong?

Thanks again.
-Chris

---

### Post by cxwhite on 2009-11-22
I'm still not exactly certain why it worked or what I actually did, but my broadcom wifi is finally working on my Dell D410, thanks to the commands posted earlier in this thread.

Thanks all.

After several attempts at loading the broadcom linux drivers according to carlee's explicit directions, things just didn't work out.

So I issued this command:
[B]
sudo apt-get install b43-fwcutter[/B]

This pulled down the necessary files and immediately prompted me for a firmware installation.  I said "yes" and off it went on its merry way. The app reinstalled things I had deleted, and in the end, when I rebooted, I saw the nearby wireless networks in the neighborhood and was able to connect to mine using wpa2 encryption.

Hooray!
-Chris

---

