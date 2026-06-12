---
title: "No Wifi Adapter Found | NVIDIA MCP61 Ethernet or Realtek RTL8201N Issue?"
date: 2019-11-19
forum: Networking &amp; Wireless
---

### Post by kalion150 on 2019-11-19
I recently used a LiveUSB to do a clean install of Ubuntu 18.02 LTS on a lightly used Windows 7 desktop from 2010, and although the install went smoothly, the desktop appears unable to connect to Wifi, displaying the message "No Wifi Adapter Found." The desktop had no issues with Wifi while it had Windows 7. "lshw -class network" gives nothing, while "lspci" does show "NVIDIA Corporation MCP61 Ethernet (rev a2)," albeit as a Bridge. I have searched several websites on how to get Ubuntu to use this chip, but there seems to be no definitive answer.
[URL="https://askubuntu.com/questions/383426/trying-to-install-nvidia-corporation-mcp61-ethernet-ubuntu-13-04"]
https://askubuntu.com/questions/383426/trying-to-install-nvidia-corporation-mcp61-ethernet-ubuntu-13-04[/URL] - Answer suggests buying a new chip.

[https://www.nvidia.com/object/linux_nforce_amd64_1.0-0292.html](https://www.nvidia.com/object/linux_nforce_amd64_1.0-0292.html) - Tried downloading the driver, but repeatedly failed, with the results exactly the same as on the following link:
[URL="https://translate.google.com/translate?sl=auto&tl=en&u=https%3A%2F%2Fwww.laneros.com%2Ftemas%2Fubuntu-bajar-y-compilar-kernel-drivers-nvidia.61452%2F%3FfullSite%3D1"]
https://translate.google.com/translate?sl=auto&tl=en&u=https%3A%2F%2Fwww.laneros.com%2Ftemas%2Fubuntu-bajar-y-compilar-kernel-drivers-nvidia.61452%2F%3FfullSite%3D1[/URL] - Translation of a Spanish linux help site; is almost identical to my situation, but the translation is unclear and the solution provided seems lengthy. If there are any Spanish speakers, I'd appreciate if you could validate this solution!

[https://askubuntu.com/questions/131844/lshw-not-showing-network](https://askubuntu.com/questions/131844/lshw-not-showing-network) - Helpful solution matching my situation, but I lack/don't know where the MAC Media Interface BIOS option is on my BIOS. I've thoroughly searched through my BIOS, and doing some internet searches suggests that perhaps my option is hidden?

I've also pulled up my desktop's specifications online, which say that it uses a "Realtek RTL8201N" chip for networking. I have scoured the net for this chip's driver, but it appears that this model doesn't have a driver explicitly provided for it online. I'm under the impression that there's a driver that covers a group of Realtek networking chips, including mine, but I can't seem to find it either.

Any thoughts on what to do next?

---

### Post by chili555 on 2019-11-19
Please run and post:```
lspci -nnk
lsusb
dmesg | grep -i sdio
```Downloading and installing an ethernet driver won't help the wireless. Please stop.

---

### Post by kalion150 on 2019-11-19
For the first command:
```
00:00.0 RAM memory[0500]: NVIDIA Corporation MCP61 Memory Controller [10de:03ea] (reva1)
    Subsystem:Hewlett-Packard Company MCP61 Memory Controller [103c:2a99]
00:01.0 ISA bridge[0601]: NVIDIA Corporation MCP61 LPC Bridge [10de:03e0] (rev a2)
    Subsystem:Hewlett-Packard Company MCP61 LPC Bridge [103c:2a99]
00:01.1 SMBus[0c05]: NVIDIA Corporation MCP61 SMBus [10de:03eb] (rev a2)
    Subsystem:Hewlett-Packard Company MCP61 SMBus [103c:2a99]
    Kernel driver inuse: nForce2_smbus
    Kernel modules:i2c_nforce2
00:01.2 RAM memory[0500]: NVIDIA Corporation MCP61 Memory Controller [10de:03f5] (reva2)
    Subsystem:Hewlett-Packard Company MCP61 Memory Controller [103c:2a99]
00:02.0 USBcontroller [0c03]: NVIDIA Corporation MCP61 USB 1.1 Controller[10de:03f1] (rev a3)
    Subsystem:Hewlett-Packard Company MCP61 USB 1.1 Controller [103c:2a99]
    Kernel driver inuse: ohci-pci
00:02.1 USBcontroller [0c03]: NVIDIA Corporation MCP61 USB 2.0 Controller[10de:03f2] (rev a3)
    Subsystem:Hewlett-Packard Company MCP61 USB 2.0 Controller [103c:2a99]
    Kernel driver inuse: ehci-pci
00:04.0 PCI bridge[0604]: NVIDIA Corporation MCP61 PCI bridge [10de:03f3] (rev a1)
00:05.0 Audio device[0403]: NVIDIA Corporation MCP61 High Definition Audio [10de:03f0](rev a2)
    Subsystem:Hewlett-Packard Company MCP61 High Definition Audio [103c:2a99]
    Kernel driver inuse: snd_hda_intel
    Kernel modules:snd_hda_intel
00:07.0 Bridge[0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem:Hewlett-Packard Company MCP61 Ethernet [103c:2a99]
    Kernel driver inuse: forcedeth
    Kernel modules:forcedeth
00:08.0 IDEinterface [0101]: NVIDIA Corporation MCP61 SATA Controller[10de:03f6] (rev a2)
    Subsystem:Hewlett-Packard Company MCP61 SATA Controller [103c:2a99]
    Kernel driver inuse: sata_nv
    Kernel modules:sata_nv, pata_acpi
00:08.1 IDEinterface [0101]: NVIDIA Corporation MCP61 SATA Controller[10de:03f6] (rev a2)
    Subsystem:Hewlett-Packard Company MCP61 SATA Controller [103c:2a99]
    Kernel driver inuse: sata_nv
    Kernel modules:sata_nv, pata_acpi
00:09.0 PCI bridge[0604]: NVIDIA Corporation MCP61 PCI Express bridge [10de:03e8] (reva2)
    Kernel driver inuse: pcieport
00:0b.0 PCI bridge[0604]: NVIDIA Corporation MCP61 PCI Express bridge [10de:03e9] (reva2)
    Kernel driver inuse: pcieport
00:0c.0 PCI bridge[0604]: NVIDIA Corporation MCP61 PCI Express bridge [10de:03e9] (reva2)
    Kernel driver inuse: pcieport
00:0d.0 VGAcompatible controller [0300]: NVIDIA Corporation C61 [GeForce 6150SEnForce 430] [10de:03d0] (rev a2)
    Subsystem:Hewlett-Packard Company C61 [GeForce 6150SE nForce 430] [103c:2a99]
    Kernel driver inuse: nouveau
    Kernel modules:nvidiafb, nouveau
00:18.0 Host bridge[0600]: Advanced Micro Devices, Inc. [AMD] Family 10h ProcessorHyperTransport Configuration [1022:1200]
00:18.1 Host bridge[0600]: Advanced Micro Devices, Inc. [AMD] Family 10h ProcessorAddress Map [1022:1201]
00:18.2 Host bridge[0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAMController [1022:1202]
00:18.3 Host bridge[0600]: Advanced Micro Devices, Inc. [AMD] Family 10h ProcessorMiscellaneous Control [1022:1203]
    Kernel driver inuse: k10temp
    Kernel modules:k10temp
00:18.4 Host bridge[0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor LinkControl [1022:1204]


[1]+  Stopped                sudo nm-applet
```

Second command:
```
Bus 001 Device 004:ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 001:ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003:ID 0461:0010 Primax Electronics, Ltd HP PR1101U / Primax PMX-KPR1101UKeyboard
Bus 002 Device 002:ID 045e:076c Microsoft Corp. Comfort Mouse 4500
Bus 002 Device 001:ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Nothing for the third.

---

### Post by chili555 on 2019-11-19
I see nothing at all that is a wireless device. Is there a setting in the BIOS to enable/disable wireless? Are there antennas sticking out the back?

:confused: :confused:

---

### Post by kalion150 on 2019-11-19
No antennae, and LAN is enabled in BIOS.

---

### Post by kalion150 on 2019-11-19
On another note, when I turned off LAN in BIOS, the NVIDIA Corporation MCP61 Ethernet chip is missing, so the LAN in BIOS likely refers to that specific chip. The Realtek RTL8201N chip is still nowhere in sight.

---

### Post by kalion150 on 2019-11-20
I've been self-troubleshooting for the past few hours, and I've made some progress.

It appears that Ubuntu simply doesn't recognize the Realtek RTL8201N chip, because it is a PHYceiver (a driverless hardware device). Therefore, it's integrated into the chipset of my motherboard. ([https://www.linuxquestions.org/questions/linux-networking-3/realtek-rtl8211b-not-detected-514880/#post2968477](https://www.linuxquestions.org/questions/linux-networking-3/realtek-rtl8211b-not-detected-514880/#post2968477)) I subsequently looked up the chipset in my desktop, which was a NVIDIA GeForce 6150SE nForce 430. H&#822;o&#822;w&#822;e&#822;v&#822;e&#822;r&#822;,&#822; &#822;s&#822;i&#822;n&#822;c&#822;e&#822; &#822;t&#822;h&#822;e&#822; &#822;c&#822;h&#822;i&#822;p&#822;s&#822;e&#822;t&#822; &#822;w&#822;a&#822;s&#822; &#822;f&#822;r&#822;o&#822;m&#822; &#822;a&#822;r&#822;o&#822;u&#822;n&#822;d&#822; &#822;2&#822;0&#822;1&#822;0&#822;,&#822; &#822;t&#822;h&#822;e&#822;r&#822;e&#822; &#822;w&#822;e&#822;r&#822;e&#822; &#822;n&#822;o&#822; &#822;d&#822;r&#822;i&#822;v&#822;e&#822;r&#822;s&#822; &#822;s&#822;p&#822;e&#822;c&#822;i&#822;a&#822;l&#822;l&#822;y&#822; &#822;m&#822;a&#822;d&#822;e&#822; &#822;f&#822;o&#822;r&#822; &#822;U&#822;b&#822;u&#822;n&#822;t&#822;u&#822; &#822;b&#822;y&#822; &#822;N&#822;V&#822;I&#822;D&#822;I&#822;A&#822;.&#822; I then referenced "What's the correct driver to use with a GeForce 6150SE nforce 430 on Ubuntu and Ubuntu flavors?" ([https://askubuntu.com/questions/588538/whats-the-correct-driver-to-use-with-a-geforce-6150se-nforce-430-on-ubuntu-and](https://askubuntu.com/questions/588538/whats-the-correct-driver-to-use-with-a-geforce-6150se-nforce-430-on-ubuntu-and)), whose top answer was to use the package nvidia-304. Since my desktop had no wifi, I tediously downloaded almost 30 packages onto a USB drive on my laptop with wifi, and transferred them to the desktop to download - not knowing what packages were on the desktop and which weren't, I used trial-and-error to find all missing dependencies for the main dependencies that were needed to install nvidia-304. After installing all the dependencies, I attempted to install nvidia-304, but Ubuntu said I was still missing a large group of dependencies, a problem that was exactly the same as the one another poster on ubuntu forums found ([https://ubuntuforums.org/showthread.php?t=2396263](https://ubuntuforums.org/showthread.php?t=2396263)). I followed enigma9o7's solution (the first reply), and spent another few hours downloading 30ish packages onto a USB drive and transferring, before I finally completed all of the steps. Instead, I didn't. I'm currently in the same position as ivanjunior20 in the same thread ([https://ubuntuforums.org/showthread.php?t=2396263&p=13855116#post13855116](https://ubuntuforums.org/showthread.php?t=2396263&p=13855116#post13855116)), but instead of getting stuck at "Starting Tool to automatically collect and submit kernel crash signatures...", Ubuntu simply boots up into tty1. The main way his experience differed from enigma9o7's solution was exactly the same as mine: "From all instructions above, only 'sudo service lightdm stop' failed with error 'lightdm.service not loaded'. I thought it was OK to ignore this."

What should I do next?

EDIT: Actually, looking back to the Linux Questions forum, the driver linked was still available on archive.org. I'm currently seeing if it works on the desktop.
EDIT 2: Not sure how to run a folder in tty.

---

### Post by CatKiller on 2019-11-20
First: wow that machine is old.

The nvidia 304 driver is for your graphics. It won't help with your networking issue.

The nforce chipsets were really ropey in general. Realtek have often been really shabby about providing drivers on Windows, let alone on Linux.

There is a tool called NDISwrapper that will let you use a Windows network driver, should you be able to still find one, on Linux. I've never used it. 

A Raspberry Pi will be much simpler, much faster, use less power, and be much less of a headache than trying to beat that old machine into service. Let it die and recycle it.

---

### Post by kalion150 on 2019-11-20
So, if the nvidia 304 driver is for my graphics, should I do another clean install if I wanted to attempt using NDISwrapper? Or can you figure out a way to reverse how the following instructions are making me boot into tty1?
> **enigma9o7 said:**
> download 64-bit nvidia driver from: [URL="http://www.nvidia.com/download/driverResults.aspx/123709/en-us"]http://www.nvidia.com/download/drive...x/123709/en-us
[/URL]or 32bit: [https://www.nvidia.com/Download/driverResults.aspx/123708/en-us]("http://www.nvidia.com/download/driverResults.aspx/123709/en-us")
save patch from: [https://adufray.com/nvidia-304.137-bionic-18.04.patch](https://adufray.com/nvidia-304.137-bionic-18.04.patch)

sudo nano /etc/modprobe.d/disable-nouveau.conf 

COPY/PASTE:
blacklist nouveau
blacklist vga16fb
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
blacklist amd76_edac
options nouveau modeset=0
SAVE/EXIT (CTRL-X)

sudo apt install gcc make build-essential gcc-multilib dkms mesa-utils
cd /home/bodhi/Downloads 
./NVIDIA-Linux-x86_64-304.137.run -x
cd ./NVIDIA-Linux-x86_64-304.137
patch -p1 < ~/Downloads/nvidia-304.137-bionic-18.04.patch
sudo update-initramfs -u
reboot

After reboot you'll be in some lower resolution video driver, goto terminal and run:

sudo service lightdm stop

Press CTRL+ALT+F2 

login: bodhi
cd /home/bodhi/Downloads/NVIDIA-Linux-x86_64-304.137
sudo ./nvidia-installer
reboot

edit: 
added link for 32-bit version
Note: The nvidia installer overwrites libvdpau with a version that doesnt work with mplayer/etc, so just reinstall the normal one:
sudo apt install --reinstall libvdpau1
Also, NVIDIA does have drivers available for the GeForce 6150SE nForce 430 that used to work on Windows 7 64-bit, although NDISwrapper doesn't have this chipset in its device lists. Would using NDISwrapper to use the Windows network driver on Linux still be feasible?

---

### Post by praseodym on 2019-11-20
Does
```

pccardctl info
```

give any output?

Please also show
```

lsmod
```

---

### Post by chili555 on 2019-11-20
Please see my ndiswrapper comments here: [https://askubuntu.com/questions/1012409/what-will-happen-if-i-install-a-wlan-driver-package-using-wine/1012431#1012431](https://askubuntu.com/questions/1012409/what-will-happen-if-i-install-a-wlan-driver-package-using-wine/1012431#1012431)

ndiswrapper isn't going to work. Ever.

---

### Post by kalion150 on 2019-11-20
> **praseodym said:**
> Does
```

pccardctl info
```

give any output?

Please also show
```

lsmod
```
The first gives nothing, the latter gives the following (can't copy terminal output to a USB since it's on tty, sections do overlap):
Upper left:
[IMG]https://i.ibb.co/TDQ8Zjt/Upper-Left.jpg[/IMG]
Upper right:
[IMG]https://i.ibb.co/SNdzXb7/Upper-Right.jpg[/IMG]
Middle left:
[IMG]https://i.ibb.co/k6H3Js9/Middle-Left.jpg[/IMG]
Middle right:
[IMG]https://i.ibb.co/8dVW6Fm/Middle-Right.jpg[/IMG]
Bottom (left & right):
[IMG]https://i.ibb.co/Yp8Z2FC/Bottom-Left-Right.jpg[/IMG]

> **chili555 said:**
> Please see my ndiswrapper comments here: [https://askubuntu.com/questions/1012409/what-will-happen-if-i-install-a-wlan-driver-package-using-wine/1012431#1012431](https://askubuntu.com/questions/1012409/what-will-happen-if-i-install-a-wlan-driver-package-using-wine/1012431#1012431)

ndiswrapper isn't going to work. Ever.
Are there any other options you'd suggest? It looks like apart from trying to install a (alleged) Linux driver for GeForce 6150SE nForce 430 or using ndiswrapper with a Windows driver for said chipset, there aren't other options that wouldn't require buying a new chipset/computer.

Additionally, should I continue troubleshooting with the desktop's Ubuntu booting to tty1, and return to the normal GUI, so that I can keep all of the packages I installed via USB, or is it impossible to return to the normal GUI now and I have to do a clean install to continue troubleshooting & have a chance of a solution?

---

### Post by CatKiller on 2019-11-20
> **kalion150 said:**
> (can't copy terminal output to a USB since it's on tty, sections do overlap):

You can redirect output to a file with > like so:
```
lsmod > lsmod.txt
```

A Raspberry Pi is $35 and will be faster than that machine. I personally wouldn't spend any more time on it. If you're having fun, though, carry on.

---

### Post by kalion150 on 2019-11-20
> **CatKiller said:**
> You can redirect output to a file with > like so:
```
lsmod > lsmod.txt
```

A Raspberry Pi is $35 and will be faster than that machine. I personally wouldn't spend any more time on it. If you're having fun, though, carry on.
How would I direct that output to USB x, though, in CLI? 

As for the desktop, if you assumed a Raspberry Pi was slower than the desktop, would you have any suggestions?

---

### Post by CatKiller on 2019-11-20
> **kalion150 said:**
> How would I direct that output to USB x, though, in CLI?  

Copy it to wherever the usb drive is mounted; or grab it over SSH; or leave it there and copy it from a live environment. 

> As for the desktop, if you assumed a Raspberry Pi was slower than the desktop, would you have any suggestions?

Nope. For an ancient unsupported POS network device where you might maybe be able to find some old Windows drivers, NDISwrapper is the only option. If that *isn't* an option then there's no option.

---

### Post by cook150 on 2019-11-22
Since I have an older account, I've switched to it from kalion150. See [this link]("https://ubuntuforums.org/showthread.php?t=2431670") for details.

For the time being, since I've been able to establish a strong Ethernet connection with the desktop, I've put finding the Wi-Fi driver and using its capabilities via ndiswrapper on hold. However, I will continue troubleshooting in December and post my final results before Christmas, for others who may still be using GeForce 6150SE nForce 430 with an integrated Realtek RTL8201N PHYceiver. Thanks for all the help so far.

---

