---
title: "unable to install ATI/AMD drivers"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by nookatee on 2010-10-12
Hello,
   I'm getting the infamous "black-screen of death" whereby the system begins to boot up, but then the monitor simply turns off. I've been trying to attack this from a number of ways (including uninstalling wine - which I haven't figured out how to do yet. see: [http://ubuntuforums.org/showthread.php?t=1593621](http://ubuntuforums.org/showthread.php?t=1593621))


I tried to update the drivers (mind you, everything I'm doing has been via the 10.04 live cd), but I get this message:

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer/fglrx-amdcccle_8.723.1-0ubuntu4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer/fglrx-amdcccle_8.723.1-0ubuntu4_i386.deb) 404  Not Found [IP: 91.189.88.40 80]

Some additional information:

ubuntu@ubuntu:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650

---

### Post by nookatee on 2010-10-12
here is my lspci output:

ubuntu@ubuntu:/home$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:03.2 IDE interface: Intel Corporation Mobile 4 Series Chipset PT IDER Controller (rev 07)
00:03.3 Serial controller: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
03:00.0 Network controller: Intel Corporation PRO/Wireless 5350 AGN [Echo Peak] Network Connection
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)

---

### Post by seventhsamurai on 2010-10-12
ATI is notorious for poor Linux support, especially for older cards. I tried everything under the sun to get my Radeon x1250 to full functionality on my Acer Extensa Laptop. Tried suggested fixes from every forum. Always ended up with an issue similar to your's, and none of the fixes to get out of this issue worked. I had to reformat everytime. Now I have just made my peace and did a fresh install, accepting it the way Ubuntu configures it automatically.

---

### Post by sandyd on 2010-10-12
> **seventhsamurai said:**
> ATI is notorious for poor Linux support, especially for older cards. I tried everything under the sun to get my Radeon x1250 to full functionality on my Acer Extensa Laptop. Tried suggested fixes from every forum. Always ended up with an issue similar to your's, and none of the fixes to get out of this issue worked. I had to reformat everytime. Now I have just made my peace and did a fresh install, accepting it the way Ubuntu configures it automatically.
Thats just because ATI doesn't support your card anymore.
Well, there ARE drivers, but they just don't work with your version of ubuntu.
see? [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)

---

### Post by sandyd on 2010-10-12
> **nookatee said:**
> here is my lspci output:

ubuntu@ubuntu:/home$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:03.2 IDE interface: Intel Corporation Mobile 4 Series Chipset PT IDER Controller (rev 07)
00:03.3 Serial controller: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
03:00.0 Network controller: Intel Corporation PRO/Wireless 5350 AGN [Echo Peak] Network Connection
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)
```

sudo apt-get update
```
then try again.

---

### Post by alphacrucis2 on 2010-10-12
The OP's card being a Mobility Radeon HD 3650 is fully supported by the current ATI Catalyst drivers. You should normally install the Catalyst driver via the system hardware drivers menu. Or alternatively download the latest from ATI Catlayst 10.9 hotfix version (don't use this with Maverick Meercat as you need at least Catalyst 10.10 which is only available via the Ubuntu Maverick repos at this time). To install the hotfix version, download and then extract the installer and then follow the ubuntu ATI binary driver howto. 

[http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx]("http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx")

[Binary driver Howto]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI")

---

### Post by nookatee on 2010-10-12
> **sandyd said:**
> ```

sudo apt-get update
```
then try again.


this is what happens when I run sudo apt-get update (keep in mind i'm running from a live cd):
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by alphacrucis2 on 2010-10-12
> **nookatee said:**
> this is what happens when I run sudo apt-get update (keep in mind i'm running from a live cd):
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


You can only have one copy of synaptic, update manager etc running at a time. 

However you can't test the Catalyst driver from a live CD as you have to reboot to activate the driver. Rebooting on the live CD will lose the install of the driver so what you are attempting to do is a non starter.

---

### Post by phredbull on 2010-10-12
I'm using an ATI Radeon 7500 w/kernel 2.6.35, and OSS has worked pretty well for me in Lucid and Karmic.
(Direct rendering & 3d works, Compiz works, though it slows things down a bit, and I can play OpenArena & Quake Live, but framerates aren't too hot.)
Here's the master thread on ATI & Linux;
[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)
Good luck!

---

### Post by nookatee on 2010-10-12
> **alphacrucis2 said:**
> You can only have one copy of synaptic, update manager etc running at a time. 

However you can't test the Catalyst driver from a live CD as you have to reboot to activate the driver. Rebooting on the live CD will lose the install of the driver so what you are attempting to do is a non starter.

so....
what do i do now? I mean, i need to update the driver in order to (presumably) get my monitor to operate properly when I start up my machine. But I can't start up my machine without using the live CD.
...does this mean i need to reformat?:confused:

---

### Post by sandyd on 2010-10-13
> **nookatee said:**
> so....
what do i do now? I mean, i need to update the driver in order to (presumably) get my monitor to operate properly when I start up my machine. But I can't start up my machine without using the live CD.
...does this mean i need to reformat?:confused:
oops.
I missed that part.

Press esc when you get to the first purple screen.
select more options (whatever key it is, I don't remember)
select nomodeset.

you should be good to go.

---

### Post by nookatee on 2010-10-13
> **sandyd said:**
> oops.
I missed that part.

Press esc when you get to the first purple screen.
select more options (whatever key it is, I don't remember)
select nomodeset.

you should be good to go.


I appreciate the help but I've tried that already and was unsuccessful. :-(
That's why i thought to try and remove Wine. But no word on that thread yet.

---

### Post by alphacrucis2 on 2010-10-13
> **nookatee said:**
> I appreciate the help but I've tried that already and was unsuccessful. :-(
That's why i thought to try and remove Wine. But no word on that thread yet.


So you have an install on your hard disk that isn't working and you are running the live CD to try and fix it? I wouldn't bother about the live CD. This is what I would do:

1. Reboot and get grub2 to display the boot menu by holding down the SHIFT key during boot up. Select recovery mode (down arrow) from the grub menu and hit enter.

2. On the recovery mode menu that should then come up, arrow down to "root      Drop to root shell prompt" hit enter
 
3. Enter the following at the root prompt:

```
apt-get --purge remove fglrx
```

4. Reboot via ```
shutdown -r now
``` . You should be able to get into gnome in low res mode.

5. Download and install the Catalyst 10.9 hotfix driver I mentioned above.

PS. if the reboot still doesn't work then try removing wine as well as fglrx at step 3:

```
apt-get remove wine
```

---

### Post by nookatee on 2010-10-13
I gave up.

I backed up the most important files (some python scripts) with box.net.

I then reformatted and installed fedora 13.

so long Ubuntu.

---

