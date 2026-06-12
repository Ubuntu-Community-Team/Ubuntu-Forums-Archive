---
title: "fglrx not installing properly, cannot use ati driver"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by adobrakic on 2010-09-19
I'm on Ubuntu 10.04 64bit, lspci:

```
ado@ado-desktop ~ $ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 RAID bus controller: ATI Technologies Inc SB700/SB800 SATA Controller [Non-RAID5 mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200]
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
ado@ado-desktop ~ $ 

```

and for some reason, fglrx isn't configuring properly anymore:

```
Selecting previously deselected package fglrx.
(Reading database ... 144783 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.771-0ubuntu0sarvatt~lucid_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.771-0ubuntu0sarvatt~lucid_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up fglrx (2:8.771-0ubuntu0sarvatt~lucid) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.771 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-24-generic
Building for architecture amd64
Building initial module for 2.6.32-24-generic

Error! Bad return status for module build on kernel: 2.6.32-24-generic (amd64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.771/build/ for more information.
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
Processing triggers for python-support ...
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
E: Sub-process /usr/bin/dpkg returned an error code (1)
ado@ado-desktop ~ $
```

which is also disallowing me from using my ATI driver in system > admin > hardware drivers. I didnt do anything before this happened, just tried running a system update and rebooted my computer, when it came back on I noticed things weren't looking right. I tried numerous solutions I found on google, but none of them helped.

---

### Post by B4NND1T on 2010-09-19
I'm having the exact same problem, just updated and now it doesn't work.

---

### Post by adobrakic on 2010-09-19
Damnit. Now I wish I hadn't tried the various fixes, I'm sure it's just some developer mistake; I hope I didn't mess it up even more.

Are any other people having this issue as well?

---

### Post by Nisitiiapi on 2010-09-19
I'm having this problem as well on a fresh install of Lucid. It installs fine with kernel 2.6.32-21, but after updating to 2.6.32-24, the driver no longer works and won't install.  Using driver directly from ATI fails as well (installation log reports "Failed to build fglrx-8.771 with DKMS").  Very frustrating.

I'm about to reinstall for a third time and see if the issue is the kernel update or if there's an fglrx update that's getting installed and failing.

---

### Post by kwabena39 on 2010-09-20
Yes, I had this EXACT same problem too....
In fact, on several updates, I had issues with my ATI drivers...
Every time a new kernal gets sent out to the update notifier, I have to uninstall the fglrx and restore the system environment, and then reinstall the driver...


But this time, the driver did not completely uninstall correctly, and the new driver did not completely install correctly


Ubuntu needs to get better with ATI Radeon.....I never had these problems with 8.04 and 9.04

---

### Post by mastablasta on 2010-09-20
ah the stability of Ubuntu systems... Still it is a bit strange that no tester noticed this . are they not using ATI/AMD?
 
is it possible to use opensource driver until this is fixed?

---

### Post by Mark Phelps on 2010-09-20
> **kwabena39 said:**
> ... Every time a new kernal gets sent out to the update notifier, I have to uninstall the fglrx and restore the system environment, and then reinstall the driver...

Been a while since I used the fglrx driver, but from what I recall, this is exactly what you have to do every time you change the kernel version.

Also, from what I've been reading recently, the latest spate of ATI (sorry, AMD) drivers have been a disaster.

---

### Post by Mark Phelps on 2010-09-20
> **mastablasta said:**
> is it possible to use opensource driver until this is fixed?

It's always possible to use the open-source drivers.  They are installed automatically.  You have to go out of your way to install the proprietary drivers.

---

### Post by alphacrucis2 on 2010-09-20
You seem to need to completely erase the old fglrx before the --buildpkg option will work. Try running the ATI uninstall script. Should be under /usr/share/ati. I'm running Catalyst 10.9 with the 2.6.32.25 kernel and it works fine for me.

```
cd /user/share/ati
sudo sh ./fglrx-uninstall.sh
```

---

### Post by adobrakic on 2010-09-20
> **mastablasta said:**
> 
is it possible to use opensource driver until this is fixed?

Yep, but they're shitty.

> **alphacrucis2 said:**
> You seem to need to completely erase the old fglrx before the --buildpkg option will work. Try running the ATI uninstall script. Should be under /usr/share/ati. I'm running Catalyst 10.9 with the 2.6.32.25 kernel and it works fine for me.

```
cd /user/share/ati
sudo sh ./fglrx-uninstall.sh
```

I'd try this, but honestly im weary of doing anything with my ATI drivers right now.

---

### Post by alphacrucis2 on 2010-09-20
> **adobrakic said:**
> Yep, but they're shitty.



I'd try this, but honestly im weary of doing anything with my ATI drivers right now.

I go through this process every month as I download and install the latest Catalyst every release, so I never really install it through the Ubuntu repos. I'm not really too bothered if the manual install breaks as I have learned how to get out of trouble. If Ubuntu release a new Catalyst through the normal repos then yes, the install should rightfully be painless. Can you open a bug report in Launchpad?

---

### Post by Giraffro on 2010-09-21
> **alphacrucis2 said:**
> I go through this process every month as I download and install the latest Catalyst every release, so I never really install it through the Ubuntu repos. I'm not really too bothered if the manual install breaks as I have learned how to get out of trouble. If Ubuntu release a new Catalyst through the normal repos then yes, the install should rightfully be painless. Can you open a bug report in Launchpad?

Here's the bug report in Launchpad: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/642518]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/642518")

---

### Post by adobrakic on 2010-09-21
> **Giraffro said:**
> Here's the bug report in Launchpad: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/642518]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/642518")

Props for this. Hopefully this will speed the process of fixing this issue up.
Can those of you who this issue pertains to make sure that you click the link that says "Does this affect you" at the top left? Thanks!

---

### Post by Giraffro on 2010-09-22
A fix has been released for Lucid; the version number is 2:8.723.1-0ubuntu5. If you use either of the Ubuntu-X PPA's, their packages have not been fixed and neither has the official installer from ATI, though it [will be fixed for the next release]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/642518/comments/53").

The update might not show up straight away depending on which update server you use. I use the UK server and it took a few hours to show up in lucid-proposed. If you can't wait, try changing the download server in Software sources to the main server.

---

### Post by adobrakic on 2010-09-22
wait, how exactly do you get the update? October is kinda far away.

---

### Post by Giraffro on 2010-09-23
> **adobrakic said:**
> wait, how exactly do you get the update? October is kinda far away.

If you haven't uninstalled your ATI drivers, it should appear in update manager. It's only the official ATI release from their website that won't get updated till October.

---

### Post by adobrakic on 2010-09-24
what's the name of the ati drivers? i have fglrx installed, but im not sure if that's what you're talking about.

---

### Post by Mark Phelps on 2010-09-24
> **adobrakic said:**
> what's the name of the ati drivers? i have fglrx installed, but im not sure if that's what you're talking about.

fglrx IS the ATI proprietary driver.

---

### Post by sandyd on 2010-09-24
see fix in signature.

---

### Post by adobrakic on 2010-09-24
> This is due to a slight renaming which caused the fglrx drivers not to find the correct function while compiling the kernel module.

You can easily fix this error by doing the following steps.

I can't believe that's what messed this entire thing up. Unfortunately, I have 2.6.35-x installed.

---

### Post by sandyd on 2010-09-24
> **adobrakic said:**
> I can't believe that's what messed this entire thing up. Unfortunately, I have 2.6.35-x installed.
you can use it on those kernels too.

---

### Post by adobrakic on 2010-09-25
no dice man. i followed the isntructions exactly, but just changed the version numbers to what I have:

```
ado@ado-desktop ~ $ sudo apt-get install fglrx
[sudo] password for ado: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  fglrx
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 31.7MB of archives.
After this operation, 108MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  fglrx
Authentication warning overridden.
Get:1 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ lucid/main fglrx 2:8.780-0ubuntu1 [31.7MB]
Fetched 31.7MB in 1min 25s (371kB/s)                             s
(Reading database ... 168853 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.780-0ubuntu1_amd64.deb) ...

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.780-0ubuntu1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a8.780-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ado@ado-desktop ~ $ 

```

---

### Post by adobrakic on 2010-09-27
smfh, after updating the 2.6.25-x or w.e kernal, i logged into that, and fglrx seemed to install fine. i went into hardware drivers, and it showed my ATI driver as "installed but not in use." I thought it just needed a reboot to finish installing. Every kernal would freeze during boot, and I would have to force my PC to turn off by holding the power button. I then went into recovery for one of the kernals, used failsafe video driver or whatever it is and removed the fglrx, but when I logged back in, neither my ethernet port nor my wifi were detected. smfh^2. im back to windows for a few months again. thanks for all the help guys.

---

### Post by dfa on 2010-10-27
Same problem here.  I'm using 2.6.32-25 and thinking of trying to downgrade the kernel back to the useful one where I could actually use the driver.  
Moral of story--- Don't let your friends mess with your updating.

---

### Post by dfa on 2010-10-27
SANDYD!!! You rock! worked perfectly.  I've been stuck on this thing for days now.  Thanks alot!

---

