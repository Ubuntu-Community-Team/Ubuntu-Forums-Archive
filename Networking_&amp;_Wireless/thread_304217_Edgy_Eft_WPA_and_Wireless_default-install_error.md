---
title: "Edgy Eft WPA and Wireless default-install error?"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by IntuitiveNipple on 2006-11-21
**Summary**
[LIST]
[*]Wireless configuration "out-of-the-box" doesn't work, but is corrected when a second wireless card is hot-plugged?
[*]WPA is **not** supported for Lucent WaveLAN/IEEE with orinoco_cs driver?
[*]wpasuplicant isn't correctly configured?
[/LIST]
Skip to this article for the solution: [WPA-PSK with Hermes 802.11b mini-PCI PCMCIA working](http://ubuntuforums.org/showthread.php?t=304217#4)

Please bear with me - I've tried to be as descriptive as possible to help others and hopefully aid the developers.

**Background**
After many years using administering and programming for various Linux distributions for server scenarios I have decided to move all the server, desktop, notebook and tablet PCs to Linux from Windows 2003 Server and Windows XP.

I decided to go with Ubuntu and the latest Edgy Eft 6.10 release because once its chosen it will have to last a few years.

I began with what I thought would be a challenging target - a Sony Vaio PCG-SRX41P (this is a spare - I have a PCG-SRX51P/B as my primary notebook).

These notebooks differ only in the amount of RAM and speed of CPU (SRX51P: 850MHz/384MB, SRX41: 800MHz/256MB). They have integrated internal 802.11b WiFi, Bluetooth, HSP modem, 10/100 Wired Ethernet, MemoryStick, Glidepad, Firewire, PC-Card and more.

I run them on a WPA-PSK 802.11g/b Wireless network along with a mixed bag of b/g devices, all running flavours of MS Windows/Mobile PC2003. 

**Experience**
The initial install went incredibly well. The only obvious issue during boot is the splash-screen is a flashing corrupted text-mode mess (I think thats caused by only the center of the 1024x768 LCD being used by BIOS for text-mode).

**Problem**
I had expected the internal Lucent WaveLAN/IEEE 802.11b PCMCIA-connected network adapter to be detected and configured but it wasn't.

Searching the Wiki I discovered an article about installing WPA, and it included steps to install NetworkManager, the GUI-based network configuration applet.

I was surprised to find I had to manually install NetworkManager from the Internet repository because it wasn't included in the standard Ubuntu 6.10 Desktop i386 CD image, although wpasupplicant was already installed. **This seems to me a major disadvantage, especially for those systems that don't have an alternative means of network connection.**
```
# sudo apt-get install NetworkManager
```
After restarting the PC the applet icon was available in the notification area of the task-bar, but I couldn't get it to make a connection to the WiFi network whether running WPA-PSK or Open, and it was only offering WEP key encryption.

There was no /etc/wpa_supplicant.conf so I created one based on the Wiki article. I have the feeling from the article that it expected me to find the file already existed and I should be adding additional settings to it - I still haven't resolved this or got WPA to work.

**iwconfig** showed that eth1 was the Wireless network, and had a HERMES  I card. **pccardctl** showed:
```
$ pccardctl ident
Socket 0:
  no product info available
Socket 1:
  product info: "Lucent Technologies", "WaveLAN/IEEE", "Version 01.01", ""
  manfid: 0x0156, 0x0002
  function: 6 (network)
```
And although I had created a network entry in NetworkManager for the SSID nothing seemed to work.

I even tried reinstalling **wpasupplicant** using Synaptics.

I began to think that the adapter wasn't supported by the drivers. Device Manager showed the driver to be **orinoco_cs** and I did a lot of research around that without finding a resolution.

Thinking the card wasn't supported by appropriate drivers I decided to plug in the Linksys 802.11g WPC54G PC-Card that I use in my primary notebook, the SRX51P/B.

At this point the WiFi network was still in **Open** mode.

I expected the hot-plug to recognise the LinkSys card and then ask me to configure it. There was a bit of hard-disk activity then nothing, so I left-clicked the NetworkManager icon and saw the "BCM4306 802.11b/g" listed as well as the "WaveLAN/IEEE" internal adapter, both shown *before* the SSID of my network.

I clicked on the SSID of my network and NetworkManager started its 'Trying to connect...' routine with the animated icon in the notification area.
To my surprise it connected almost immediately and the icon changed to a signal-strength meter.
**iwconfig** showed that the external card was on eth2.
I then decided to test it by unplugging the wired interface. So far, so good - Firefox was still able to connect to the web.

I right-clicked the NetworkManager icon and chose "Connection Information" and was surprised to see it reporting that the connection was on eth1 and running at 11M/bps, not eth2 and 54M/bps as I expected.

I thought it had just got confused, so I unplugged the LinkSys WPC54G expecting the network to disconnect.

I was extremely surprised but relieved to discover that the internal WaveLAN/IEEE on eth1 was indeed now connected, but **why did it need another card to be hot-plugged to fix it?**

Next, I tried re-enabling the WPA encryption on the network but after doing  that NetworkManager failed to connect, and would only offer the WEP methods of encryption.

[INDENT]* I was caught out several times by the "Wireless Network Key Required" dialog silently opening in the background, hidden behind other windows.[/INDENT]

I plugged the LinkSys WPC54G back in, and, with a left-click on the NetworkManager icon, chose to "Connect to Other Wireless Network...".

In the subsequent dialog box the available WiFi connections are listed in the "Wireless adapter" combo-box, and the available encryption options in the "Wireless Security" combo-box.

When the adapter **"Lucent Technologies WaveLAN/IEEE"** is selected **only 3 WEP modes** are shown in "Wireless Security", but when **"Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller"** is selected WEP **and WPA/WPA2** are offered.

That said I've still not successfully managed to make a WPA-PSK connection from Ubuntu. :( I have tried the manual configuration tips from the Wiki as well as using NetworkManager to guide me through the WPA steps.

Now I know that (both) the adapter supports WPA in Windows XP, so after all this it looks as if the upshot is that I can't use Ubuntu on these notebooks because **the driver doesn't support WPA**. ](*,) 

Any tips gratefully received, before I give up :rolleyes:

---

### Post by IntuitiveNipple on 2006-11-22
I've managed to get WPA-PSK for the external Broadcom 4306-based LinkSys CardBus adapter using ndiswrapper and the Windows XP Broadcom driver. However, Its only there to prove its possible, the card can't stay.

I've not been able to do the same for the internal Orinoco Mini-PCI  WaveLAN/IEEE adapter, so right now its looking like Linux isn't a viable option for these two notebooks.

---

### Post by IntuitiveNipple on 2007-01-08
I discovered there's a 2.6.x kernel driver that supports WPA for the Orinco Hermes chipsets, and I've got the source code diff[erence] from a developer in Russia who has got it working on his system, and I have the source package.

I've not had chance yet to work on this here, but I'm hoping to be able to change that soon and build working binaries. I'll document the process when I do.

---

### Post by IntuitiveNipple on 2007-01-18
Tonight I **successfully built a driver for the Agere Hermes I WaveLAN 802.11b orinoco chipset that supports [color=red]WPA-PSK[/color] (aka WPA Personal)** and I have it working in a Sony Vaio PCG-SRX41 with [color=green]**Ubuntu Edgy Eft 6.10 kernel 2.6.17**[/color].

I used a fast dual-CPU workstation to do this, and it still took hours.

I'll write this up in greater detail after I've had some sleep, but here's the basics:
[list]
[*] Installed the tools needing to build a kernel
[*] Installed the kernel source for Edgy
[*] Configured and then built the kernel (this is needed to provide files for building the driver)
[*] Applied the patch file to the **wl_lkm_718_release** Agere Hermes source code
[*] Built the Hermes source against the kernel build files
[/list]

This gave me the kernel driver module: [color=green]**wlags49_h1_cs.ko**[/color]

I then disabled the current **orinoco_cs** driver by editing **/etc/modprobe.d/blacklist** and adding to the end:
```
# remove non-WPA Hermes 802.11b driver
blacklist orinoco_cs
```
I copied [color=green]**wlags49_h1_cs.ko**[/color] to [color=blue]**/lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless**[/color]

I restarted the notebook. Once in Gnome I checked the NetworkManager applet in the notification tray. It listed the SSID of my access point (AP) under the name of the Hermes internal wireless card (WaveLAN/IEEE) as well as the external Linksys WPC54G (Broadcom DCM4306) PC-Card.

I selected the SSID under "WaveLAN/IEEE" and it connected immediately. I suspect it was so easy for me because I've already entered the WPA- Pre-Shared-Key (PSK) for my AP.

You might need to use NetworkManager applet to "Create New Wireless Network..."

I've attached the kernel-driver file in a tar.gzip files to this article. I've built one for each of the kernel sources, so check which one is appropriate for you. If you have the wrong one you'll get a "Fatal Error" report when trying to do **modprobe wlags49_h1_cs**.
[list]
[*]2.6.17-10-generic - the original Edgy Eft 6.10 source
[*]2.6.17.14 - the latest repository version as of 19 January 2007
[/list]
If you extract it to the location I've detailed, and follow my instructions above to disable any existing driver that will conflict with it, you should be good to go.

From the command line you can load it manually with **modprobe wlags49_h1_cs**.

If you have the driver in place and modprobe reports "not found", go to the **/lib/modules/<kernel version>/** directory and do **depmod**. Then try loading the driver once more with modprobe.

Please let me know your experiences - I'll have to find an appropriate way to distribute this and instructions, because its a big and long job having to compile the entire kernel in order to compile just this driver.

Edit: 2007-01-23 Updated binary archives to Contain Agere copyright message

---

### Post by IntuitiveNipple on 2007-01-21
I've added another binary build of the driver, for kernel 2.6.17.14, to the post above.

---

### Post by setag on 2007-01-23
Could you attach the patch file for the wl_lkm_718_release? Or is there any internet resource for the 2.6.x kernel driver/patch?

---

### Post by IntuitiveNipple on 2007-01-23
At the moment, no I can't, until I confirm the licensing terms of the patch author and the original source.

---

### Post by busrider on 2007-02-01
I'm trying to get my Orinoco gold to work with Dapper.  I've searched the forum and can't
find anything on a solution to use it with WPA on Dapper.  I assume the procedure outlined
here won't work, or will it?

---

### Post by Megabuntu on 2007-02-07
What's the status of the patch file and licensing issues? I think it may fix my problem...:confused:

---

### Post by IntuitiveNipple on 2007-02-08
I've had confirmation from Agere's legal representive that the licence for the existing Agere source-code packages is BSD-style and can be freely used.
> I would like to confirm that the two drivers; Linux LKM Wireless Driver Source Code, Version 7.18 and Linux LKM Wireless Driver Source Code, Version 7.22 comply with Open Source BSD License. Therefore the source code can be distributed in unmodified or modified form consistent with the terms of the license.
That source contains a 'binary' firmware image that has to be loaded into the chipset at run-time...
> The Linux driver architecture was based on two modules, the MSF (Module specific functions) and the HCF (Hardware Control Functions).  Included in the HCF is run-time firmware (binary format) which is downloaded into the RAM of the Hermes 1/2/2.5 WMAC.
This hex coded firmware is not based on any open source software and hence it is not subject to any Open Source License.  The firmware was developed by Agere and runs on the DISC processor embedded within the Hermes 1/2/2.5 Wireless MAC devices
Nothing wrong with that, its an approach often taken where the firmware code is loaded at run-time rather than embedded in EEPROM or similar on the device.

I'm now waiting for a response from the developer of the 2.6.x source patch.

Apart from the legal issues his concerns are that his hack might be kernel-build-version specific and not portable across builds and he's not wanting to be providing support for users who may have problems with it and can't hack the source to fix their issues themselves.

---

### Post by dtech on 2007-02-08
Any chance this could be modified to work with the latest xubuntu powerpc? It's usefull because the Airport card, the old native internal WLAN card of apples laptop: the iBook, uses a Lucent Wavelan Hermes I chipset. It has kernel 2.6.17-10-powerpc.

---

### Post by IntuitiveNipple on 2007-02-09
In ***theory*** it should but you never know until you try it. 

You could try downloading the Agere source code packages and seeing how well they compile - if you get errors related to architecture-specific issues that would indicate some architecture hacking is necessary.

---

### Post by dtech on 2007-02-09
But wasn't the whole problem that that driver didn't support WPA? I am not a linux expert so I don't exactly know how it works, but my problem is that I cannot select WPA in the ubuntu network configuration screen, and hoped with this driver it would be possible. And I figured that since the kernel is not 2.6.14-10-generic nor 2.6.14-14 but 2.16.14-10-powerpc I could not use this binary driver, or is this not true?

---

### Post by IntuitiveNipple on 2007-02-09
This isn't a binary driver. I think you're getting confused with the fact it *contains* a *binary image* to be loaded into the card's memory and executed by the card's DISC chip.

They do it that way to reduce costs and make it easier to upgrade/fix bugs/add functionality later - the other way would be to put it in firmware which makes it harder to change. 

The host operating system driver is responsible for loading that *binary image* into the card's memory and starting the card's micro-processor executing it.

The driver's Linux source code, when compiled, knows how to load that binary image and  'talk' to the card on behalf of Linux.

So, if you find you can compile the Linux 2.4.x source code on your PowerPC architecture then you've a good chance that the 2.6.x driver source code will also compile, and will give you a working WPA driver.

---

### Post by George M. Harkin on 2007-02-09
IntuitiveNipple,
  Thanks for  your work on this, I saw that this was the direction to go, but never had the time and the effort to get 'er done. Great work!.

Do you see this getting merged back into the Hermes driver any time soon? Recompiling is fun and all, but being "good to go" is always better.

---

### Post by IntuitiveNipple on 2007-02-10
Once I've got the OK from the Russian programmer that hacked the Agere drivers to work with kernel 2.6.x, it is my intention to post the source somewhere permanent.

He has flagged it as GPL but I'd like to get his approval seeing as he sent me the patch privately and has expressed concerns over it being suitable for all 2.6.x kernel versions.
I know he's recently altered it to work with 2.6.20, for instance.

I've got three notebooks that make use of it with WPA2 802.11g, so I suspect I'll be wanting to ensure it stays current for a while as the kernel develops.

I do a bit of kernel hacking myself but I don't want to have to dive into this as well as other stuff - all I want is an "it just works" solution.

---

### Post by George M. Harkin on 2007-02-13
I was so happy that this was working that when I realized that the driver did not support the power save mechanisms of Ubuntu I became totally bummed out. No Suspend, No Hibernate

But fear not! As soon as you post the source, I'll make it my mission to learn the code and make it powersave like no other.

I'll be reading the source for the orinoco_cs driver tonight, as that powersaves just fine. Working from that, I will (read should) be able to get 'er done.


**EDIT**
Looks as if it was the NetworkManager process still clinging onto the wlags49_h1_cs module. I'll look for a way to get the ACPI scripts to stop/start the process on suspend/resume

**EDIT**
Meh... it was not the NetworkManager. Without the module loaded, it suspends fine.

---

### Post by IntuitiveNipple on 2007-02-14
[SIZE="4"][color=blue]**WPA2 kernel 2.6 patch for Agere Hermes 1 Orinoco 802.11b Wireless driver**[/color][/SIZE]

As an interim measure for those wanting to make a start with this driver, I'm attaching the patch file generated by **diff** against the **wl_lkm_718_release** source package available from Agere web site.

This patch works with kernel version 2.6.17-10 and 2.6.17.14  on i686 (i386) but it might need tweaking for others.
If you have to hack it please post a patch file back here.

I'm also attaching the Agere source code here for convenience.

Here's the steps to follow:
[LIST=1]
[*]Create a new folder
[*]Extract source code to a sub-folder
[*]Uncompress the patch file
[*]Apply the patch
[*]Compile the driver (must have a compiled kernel for it to link to)
[*]Update the kernel module list
[*]Install the new driver
[/LIST]
I'd recommend building the kernel and driver on a fast PC if the target notebook/laptop is a relatively slow PC, especially if you're building the Ubuntu generic kernel (which builds everything regardless of whether your PC uses it).

---

### Post by IntuitiveNipple on 2007-02-14
Here's the steps I took to build the driver. I used a powerful multiprocessor workstation to cut down on time. It means I didn't perform all the steps on the same PC.

This assumes the compressed archives are in your home directory at the start.

From your home directory, prepare the source and patch files
```
$ mkdir AgereHermes
$ cp wl_lkm_718_release.tar.gz AgereHermes/
$ cp wlags49.diff.bz2 AgereHermes/
$ cd AgereHermes
$ bunzip2 wlags49.diff.bz2
$ mkdir wl_lkm_718_release
$ tar -xz -C wl_lkm_718_release -f wl_lkm_718_release.tar.gz
$ ls
wlags49.diff  wl_lkm_718_release  wl_lkm_718_release.tar.gz

```
Apply the patch (answer no ("**n**") to the questions about **wlags49_26/.built-in.o.cmd**)
```
$ patch -p0 <wlags49.diff
patching file wl_lkm_718_release/ap_h1.c
patching file wl_lkm_718_release/Build
The next patch would delete the file wlags49_26/.built-in.o.cmd,
which does not exist!  Assume -R? [n] n
Apply anyway? [n] n
Skipping patch.
1 out of 1 hunk ignored
patching file wl_lkm_718_release/dhf.c
patching file wl_lkm_718_release/dhf.h
patching file wl_lkm_718_release/dkms.conf

...

patching file wl_lkm_718_release/wl_priv.c
patching file wl_lkm_718_release/wl_profile.c
patching file wl_lkm_718_release/wl_sysfs.c
patching file wl_lkm_718_release/wl_util.c
patching file wl_lkm_718_release/wl_wext.c
$
```
At this point I generally switch to super-user to avoid having to repeatedly use the *sudo* prefix, by doing
```
$ sudo su
```
Build the kernel, ensuring you have enabled PCMCIA and PCCARD support (the driver needs to link against them).
```
$ cd /usr/src/linux
$ make menuconfig
$ make-kpkg clean
$ fakeroot make-kpkg --initrd --append-to-version=-hermes-wpa kernel_image kernel_headers
```

Build the driver using the format: 
make -C /path/to/kernel/src/ [O=/path/to/kernel/build] M=$PWD
```
$ cd ~/AgereHermes/wl_lkm_718_release
$ make -C /usr/src/linux  M=$PWD
$ ls *.ko
wlags49_h1_cs.ko
```
**wlags49_h1_cs.ko** is the new driver.

If you're installing on the same PC
```
$ make -C /usr/src/linux M=$PWD module_install
```
Otherwise copy it into place on the target PC (ensure you install to the correct kernel version)
```
$ cp wlags49_h1_cs.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless

```
Blacklist the orinoco_cs driver
```
$ echo "# remove non-WPA Hermes 802.11b driver" >> /etc/modprobe.d/blacklist 
$ echo "blacklist orinoco_cs" >> /etc/modprobe.d/blacklist
```
Update the module dependencies
```
$ depmod
```
Unload the current module, and load the new one (or restart the PC to ensure it loads at boot)
```
$ rmmod orinoco_cs
$ modprobe wlags49_h1_cs
```
**Caveat:** I've checked a few of these steps just now to ensure I've got the syntax correct, but its a while since I built the kernel and installed the driver so small mistakes may have crept into these instructions.

---

### Post by dtech on 2007-02-14
Is there any change this can be done for the 2.6.17-10-powerpc kernel of the PPC version of ubuntu? I would do it, but if you had to use a multi-processor workstation in order to cut down on time, how long will it take on my old G3 700mhz? :(

---

### Post by IntuitiveNipple on 2007-02-14
If you customise your kernel-build configuration to remove all the bits that you aren't using, you can considerably reduce the build time.

On the dual-CPU workstation, an Ubuntu generic build of Edgy took about 3 hours. Once I'd eliminated the unnecessary items it reduced to about 20 minutes.

You can let it build the kernel overnight. You only need to build the kernel once, its only needed by the WiFi network driver to link against.

Building the network driver takes about a minute.

Using **make menuconfig** I removed:

ISDN, All network drivers for hardware I don't have, network drivers for unused protocols (ATM, IPX, etc.), chipset drivers for IDE and SCSI drivers,  support for ISA, MCA, EISA, sound drivers, graphics drivers, telephony, special serial drivers, parallel-port IDE drivers, some video-device drivers, a few USB devices, many input devices, non-standard keyboards, etc.

I left in support for SCSI (needed for USB flash memory devices), PCMCIA and PCCard.

There's a whole lot you can find to disable, but don't try to be too aggresive - if you're not sure better to build as a module, just in case.

---

### Post by setag on 2007-02-16
Thank you for posting the patch file and the steps to build the driver. I successfully compiled it on Arch Linux using kernel 2.6.19 (which I didn't have to compile - the kernel header files are provided by the Arch kernel package).

---

### Post by IntuitiveNipple on 2007-02-16
Thanks for the report - it looks like building on PPC arch may work, too.  Have you also managed to get the driver to work on a WPA2-secured wireless network?

Your remarks about only requiring the kernel-headers package for your architecture reminded me of something: The only reason I built the kernel originally is that I was hacking a bug in the kernel's partition-scanning logic that affected a RAID-1 array, and I've had to rebuild the kernel-headers to match each custom-kernel I've built, and for the notebook built a custom-kernel that includes the framebuffer driver for the graphics device.

For people using the stock kernel its likely that you don't need to build the kernel to link against, but to simply install (using Synaptic or apt-get) the kernel-headers matching your kernel version.

---

### Post by Hoby on 2007-02-21
Can this be included in the next Ubuntu release? It'd be really nice to have WPA supported in the driver for my Airport card and it's not practical for me (or most everyone else) to compile new kernels.

I applaud the efforts that went into making 6.10 support the airport card on a basic level.. it's wonderful and good, it was the deciding factor to put Xubuntu on my iBook. But I'd expected that WPA support was part of that effort.

---

### Post by dtech on 2007-02-21
Well, I don't know if things like this normally are included in ubuntu, but I think it's just a few days too late. Ubuntu 7.04 alpha 4 has just been released and marked as "feature complete" :(

---

### Post by xorwen on 2007-02-21
Hi,
if I understand correctly, it's not necessary to compile the kernel. All I need to compile is the driver. It would be very useful to desribe the modification of the howto in the variant without the kernel compilation. I'm not an advanced user to think out which commands are unnecessary in this case.
It is not clear for me at the step:
[I]Build the driver using the format: 
make -C /path/to/kernel/src/ [O=/path/to/kernel/build] M=$PWD[/I]
:confused: 
I have no kernel source code and I don't know they are essencial to build the driver.

Thanx.

---

### Post by jeromew on 2007-03-21
Thanks a lot nipple for your work. Without it I would be in serious trouble.

I doubt this can be an official part of Ubuntu but my suggestion would be to make it part of wiki with a link to this page. 

I have another wireless adapter (BCM43XX) and unfortunately it doesn't have a fully functional kernel driver either. What they did is have an unofficial apt repository (obviously requires more dedication) and a link in the wiki. It was a decent solution.

Of course, I'll be happy if someone keeps posting new binaries in this thread. Does anyone know if the driver will work with the most recent kernel update?

---

### Post by mibeuten on 2007-03-25
Hi,
I also had a lot of problems trying to get my Hermes-I based "Toshiba wireless mini-PCI" card (built in a Toshiba Tecra 9100 notebook) connected with a WPA-encyrpted network.
After days of google-ing I came across your post... after installing the binaries you've posted, it was a matter of minutes to get it running. THANK'S A LOT !!!

@jeromew: I'm running the latest kernel update (2.6.17-11) for the Edgy distribution -> the wlags49 module binary seems to work fine!

---

### Post by smesterheide on 2007-03-26
Thank you very much. Great work! It works fine for me.

---

### Post by DagdaMor on 2007-04-13
Although I haven't setup WPA yet, the patch seems to work fine on 2.6.18.3, WEP enabled. This thread appeared on Google just as I thought I'd have to take a crash course in kernel programming. Phew!

---

### Post by dtech on 2007-04-13
A little bit offtopic, but you should really try to use WPA. Recently it was discovered WEP can be cracked in about a minute. (It was already possible to do it in 10-40 minutes)
[source](http://www.cdc.informatik.tu-darmstadt.de/aircrack-ptw/)
> 
We were able to extend Klein's attack and optimize it for usage against WEP. Using our version, it is possible to recover a 104 bit WEP key with probability **50%** using just **40,000 captured packets**. For 60,000 available data packets, the success probability is about 80% and for **85,000 data packets about 95%**. Using active techniques like deauth and ARP re-injection, **40,000 packets can be captured in less than one minute** under good condition. **The actual computation takes about 3 seconds and 3 MB main memory on a Pentium-M 1.7 GHz** and can additionally be optimized for devices with slower CPUs. **The same attack can be used for 40 bit keys too with an even higher success probability**.


---

### Post by pptp on 2007-04-19
Hi there,

I spent  a week or so  trying to get my Speedtouch 110 wireless PCMCIA card to  work
on Linux (Debian Etch). It does not work with stock Linux hermes/wavelan drivers. The
same for ndiswrapper with XP drivers. Problem with ndiswrapper is that the ST110 XP
drivers do not have a .INF file. So here I am, a little stuck.

I found the Agere wl_lkm archive, and the 2.6 patch from Andrey. You can download
them at [http://www.xs4all.nl/~pptp/agere/](http://www.xs4all.nl/~pptp/agere/) . Can someone verify that the
Speedtouch110 pcmcia wireless card works with this driver?

Jan Pieter.

---

### Post by jeromew on 2007-04-20
binary module does not load under feisty's default kernel...

---

### Post by pptp on 2007-04-20
> I found the Agere wl_lkm archive, and the 2.6 patch from Andrey. You can download
> them at [http://www.xs4all.nl/~pptp/agere/](http://www.xs4all.nl/~pptp/agere/) . Can someone verify that the
> Speedtouch110 pcmcia wireless card works with this driver?

OK, it does not work. The ST110 is HermesII. Anybody out there who can bring
back the HermesII support in Andrey's patch? I'm now using the original Agere
code on kernel 2.4.18.

Jan Pieter.

---

### Post by ringonian on 2007-04-21
> **jeromew said:**
> binary module does not load under feisty's default kernel...

Neither does the compiled kernel version:

$ uname -r
2.6.20-15-generic

$ lsmod | grep wlags
wlags49_h1_cs         182452  1 
pcmcia                 39212  1 wlags49_h1_cs
pcmcia_core            40852  4 wlags49_h1_cs,pcmcia,yenta_socket,rsrc_nonstatic

$ pccardctl ident
Socket 0:
  no product info available
Socket 1:
  product info: "Dell", "TrueMobile 1150 Series PC Card", "Version 01.01", ""
  manfid: 0x0156, 0x0002
  function: 6 (network)

Network Manager no longer connects to any secure or unsecure network.  I have to rerun dhclient to connect.

---

### Post by pptp on 2007-04-27
> > I found the Agere wl_lkm archive, and the 2.6 patch from Andrey. You can download
> them at [http://www.xs4all.nl/~pptp/agere/](http://www.xs4all.nl/~pptp/agere/) . Can someone verify that the
> Speedtouch110 pcmcia wireless card works with this driver?

OK, it does not work. The ST110 is HermesII. Anybody out there who can bring
back the HermesII support in Andrey's patch? I'm now using the original Agere
code on kernel 2.4.18.


I got my Speedtouch 110 wireless PCMCIA card working with kernel 2.6! All I had to
do with Andrey's source was use the hermes2 firmwares, define HERMES2 in the top
Makefile, and fix 1 bug in wl_wext.c. It now works with Debian/Etch 2.6.18 default
kernel. The archive is at [http://www.xs4all.nl/~pptp/agere/wlags49.tar.bz2](http://www.xs4all.nl/~pptp/agere/wlags49.tar.bz2) .Unpack
the archive. In /usr/src/ , make  a symlink 'linux' to your kernel-source or -headers, cd to
the wlags49 dir and type ./Build . When the module compiled, copy wlags49_h2_cs.ko
to /lib/modules/`uname -r`/kernel/drivers/net/wireless/ , and do depmod -a .


Jan Pieter.

---

### Post by pptp on 2007-04-29
> I got my Speedtouch 110 wireless PCMCIA card working with kernel 2.6! All I had to
do with Andrey's source was use the hermes2 firmwares, define HERMES2 in the top
Makefile, and fix 1 bug in wl_wext.c. It now works with Debian/Etch 2.6.18 default
kernel. The archive is at [http://www.xs4all.nl/~pptp/agere/wlags49.tar.bz2](http://www.xs4all.nl/~pptp/agere/wlags49.tar.bz2) .Unpack
the archive. In /usr/src/ , make a symlink 'linux' to your kernel-source or -headers, cd to
the wlags49 dir and type ./Build . When the module compiled, copy wlags49_h2_cs.ko
to /lib/modules/`uname -r`/kernel/drivers/net/wireless/ , and do depmod -a .


It now compiles with kernel 2.6.21.1. I'm posting this with my laptop
running the latest kernel.org  kernel . I'll add HermesI support tonight.
Please let me know if that works or not.

When I eject the card, the PC hangs. Is this the same with the original
patch for 2.6 from Andrey? The source does not look very clean. It
needs major cleanup. It looks like someone removed every line that
didn't compile OK. BTW, I did the same to make it work for 2.6.21.1.


Jan Pieter.

---

### Post by neilballantyne on 2007-05-03
Hi,

I'm following IntuitiveNipple's instructions for patching and building against a Debian Etch 2.6.18 system. The module compiles, and I can see available networks and select WPA Personal for encryption, but when I try and connect I just get the following:

May  3 15:34:03 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth2 for sub-path eth2.dbus.get.reason
May  3 15:34:03 localhost kernel: eth2: PRI 31 variant 2 version 9.48
May  3 15:34:03 localhost kernel: eth2: NIC 5 variant 4 version 5.00
May  3 15:34:03 localhost kernel: ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
May  3 15:34:03 localhost kernel: eth2: PRI 31 variant 2 version 9.48
May  3 15:34:03 localhost kernel: eth2: NIC 5 variant 4 version 5.00

---

### Post by DagdaMor on 2007-05-05
Although it seems to work rather well using WEP, any attempts to use WPA with the patched driver have resulted in various nastiness. Often the machine goes out to lunch long enough that the hardware watchdog reboots it. This is with kernel 2.6.18.3 on an up to date Debian testing machine.

*edited to add: I'll post the relevant debug output from wpa_supplicant soon

---

### Post by Wilb on 2007-05-08
Thanks to everyone for their work on this, just got WPA working on a Dell Truemobile chip under Feisty :-)

---

### Post by glennric on 2007-05-10
I have had trouble getting this to work on a Toshiba Satellite Pro 6000 laptop with a Hermes (I) wireless card.  I can get the module to compile and load on boot, but network manager is not able to connect to any of the detected networks.  I like that this driver shows signal strength in the network manager applet, unlike the default orinoco driver.  I just need to connect to networks (secure and unsecure).  Has anyone had success with a Hermes (I) chipset and these drivers with WPA in Feisty?  (Actually I am running the 2.6.21 kernel)

Edit:  I was able to compile the wlags drivers for HermesI under the 2.6.21.1 kernel using the file [http://www.xs4all.nl/~pptp/agere/wlags49-4.tar.bz2](http://www.xs4all.nl/~pptp/agere/wlags49-4.tar.bz2), and it can connect to wpa networks using dhclient.  However, network manager will not connect.  Any ideas how to fix this?

---

### Post by Tikitoe on 2007-05-10
Wiib, could you provide some detail on the exact steps you followed?  I am trying to get WPA running under Feisty on a Dell laptop with a TM 1150 card in its mini-PCI slot.  I followed the directions provided by pptp and everything seemed to go fine, but now the wireless connection doesn't even show up in the GNOME network manager.  Thanks!

---

### Post by muimui on 2007-06-12
Hi i just wanted to contribute my compiled driver so you dont need to fiddle with it... this ones for ubuntu feisty fawn 7.04 kernel 2.6.20-16-generic 
Its a Sony Vaio PCG-SRX51P (/B) and "pccardctl ident" outputs:

Socket 1:
  product info: "Lucent Technologies", "WaveLAN/IEEE", "Version 01.01", ""
  manfid: 0x0156, 0x0002
  function: 6 (network)

 to use it extract the driver to any folder and from there copy it with

**sudo  cp wlags49_h1_cs.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless**

then do


**sudo echo "# remove non-WPA Hermes 802.11b driver" >> /etc/modprobe.d/blacklist**

**sudo echo "blacklist orinoco_cs" >> /etc/modprobe.d/blacklist**

then restart, if you do 

**lsmod |  grep wlags49**

after that you should see that the driver has loaded  (one of the lines should contain "wlags49_h1_cs " in front of it, if this is the case you can now use your wlan as normally with gnome networkmanager, but now wpa should work once you have configured it and entered the key...

good luck

muimui

ps. many thanks to intuitivenipple for providing the sourcecode, it took me half a year of fiddling around before i found this, great job... :D

---

### Post by IntuitiveNipple on 2007-06-13
Hey muimui, thanks for the compiled Feisty 2.6.20-16 version. I am about to install Feisty on 2 Vaios, the SRX51P/B and SRX41P so you've saved me having to mess about :)

I've 'upgraded' to a Vaio  VGN-FE41Z now to replace the notebooks and workstation and will be selling off the old notebooks with Feisty installed and configured.

---

### Post by muimui on 2007-06-14
hmm you rather be careful, i just wanted to write you because i have got problems with the driver... i have compiled them from the posted source code  plus the diff patch you posted, and they load ok and i can connect to a WPA tkip network and surf for a while but the behaviour is strange: the signal strength goes up to 100% sometimes and then drops to normal level, this would not be the problem but after some time (sooner when there is more traffic) it drops to zero and although gnome.networkmanager says its connected (with 0 %) the connection is broken.... when i try to reenable it by clicking on the network again, or disabling the network the laptop FREEZES. scroll lock and caps lock blink and there it stands and i have to power it off.... any idea what causes this or at which logs i could look at? i have tried ( im not really an expert) pccardctl reset and turning wlan on and off with the hardware switch, none of them helped. remarkably is that the laptop only freezes when i disable the network (more precisely gnome.networkmanager  says "now disconnected" and then it freezes) or click on it in gnome network manager, it doesnt freezes when the connection breaks....

---

### Post by IntuitiveNipple on 2007-06-15
When I get around to installing it on the notebooks here I'll see if they are affected the same way too. It is possible the problem is isolated to the one PC rather than being a widespread problem.  

If others have problems with Feisty I'm sure they'll eventually post a response here.

---

### Post by muimui on 2007-06-19
I have tried a bit here and cant find the cause for the problem, it seems to be completly random. Size of packets transmitted so far, number of packets transmitted, screensaver, power  management, nothing seems to cause this, i cant reproduce the error at will. The problem is that there ist no message in syslog, kernellog or messagelog, the system  just silently crashes, so im pretty much stuck tracking down the problem, and by the way hardware driver debugging doesnt happen to be one of my hobbys ;). The next thing i wanted to try is to build a version of the driver with debugging enabled, to maybe get a hint from additional message output, but maybe there is an alternative: There is a tool called ndiswrapper which makes normal windows driver (NDIS) usable in Linux. I have found a driver for many windows (plural) and it works with wpa on my win xp partition. The problem is that ndiswrapper installs the driver but doesnt say  'hardware present'. I assume that this happens because of the windows .inf file which comes with the driver (and which ndiswrapper uses to install the driver on linux) is somewhat universal and includes all drivers in the package, so maybe ndiswrapper picks the wrong one. For example the first entry it finds in the inf... My question to anyone reading this is now: Have you...

a)... got a working driver for windows which supports wpa? If yes: can you please post a link or zip (i need the .inf and all .sys/.dl or just the original packagel) here so i can try it with ndiswrapper

b)...know enough about the structure of .inf files to remove all unecessary drivers from the inf, so it maybe works with ndiswrapper. If yes: would you please edit the inf or tell me how to edit it and post here. (The inf is in the attached zip file, and windows calls the card once installed "ORiNOCO Mini PCI Card"  Matching Device ID is "pcmcia\lucent_technologies-wavelan/ieee-911f" )

c) ...know how to correctly configure ndiswrapper with the driver in the attached package (for driver identification see b)  ) If yes: Please post a response..

The way to go seems to be b) since i already got a working driver i only need somone with basic knowledge of .inf files / ndiswrapper...

Greetings and thanks in advance

                                             muimui

The driver is to big to attach but can be found at 

**[http://members.driverguide.com/driver/detail.php?driverid=343365]("http://members.driverguide.com/driver/detail.php?driverid=343365")**
(it without registration and such just look close and you will find the right buttons...)

---

### Post by IntuitiveNipple on 2007-06-19
I originally tried to use the NDISwrapper method but there was an issue that prevents it working, which I can't remember how, but is why I worked to get the Linux source code made available.

---

### Post by muimui on 2007-06-19
Ok, i think i am on the edge of giving up... ndiswrapper cannot find the hardware for some reason, and you say that it probably cat work and best of all: the module wont compile with debug enabled. Just when i thought Ubuntu was finally a Linux working out of the box. :( (But to be just i have to say that the WinXP WPA driver shows a somewhat similar bitchy 

muimui

---

### Post by karmik on 2007-06-19
OK, a big THANK YOU is in order.
I used to be a ubuntu user for a very short while (i like to mess with my systems too much for it so i switched back to gentoo although i must say i install ubuntu on every relatives/friends/neighbors computer i can put my hands on.) NONETHELESS i still lurk this FINE forum for solutions like this one. Dudes you solved a problem for whom i googled restlessly for almost a year now. THANKS Intuitive Nipple.
BTW: You should really really advertise this solution more because LOADS and i mean *LOADS* of people have their HermesI wifi card not working in WPA mode, try to google for hermes wpa_supplicant and you'll get plentiful results.
It really really needs to be advertised MOAR.
Thanks Again dude.
(Btw, i'm on Gentoo 2007.0 x86 with Gentoo-sources 2.6.20-r8, the module compiled and loaded like a breeze and querying the card with wpa_supplicant with -Dwext doesn't return any error like before).

Kudos to you and to Ubuntuforums which is TEH problem-solving community.

---

### Post by angelmartinezn on 2007-06-28
Thanks, now I can use my old lucent/orinoco card with wpa...

Thanks to everybody!!!

---

### Post by fisch.auge on 2007-07-03
Thanks so much! Works fine with kernel 2.6.20-gentoo-r8!!!

---

### Post by soyut on 2007-07-13
Tikitoe,
Did you find a solution to getting WPA working on your Dell laptop with TM 1150? I have read most of the related  postings and tried most out. But, I am still without a WPA solution.
Thank you.

---

### Post by anomalyconcept on 2007-07-13
Which TM 1150 card do you have?  IIRC, there was both a mini-PCI and a PC card version.

I've gotten the PC card version to work (using the given code), although it happens that I came back to this thread to see if there was any new information regarding kernel version 2.6.22, which uses a new wireless stack.  I've already tried- it doesn't compile cleanly.  I haven't looked yet, but I figure I'd respond to the last post.

---

### Post by IntuitiveNipple on 2007-07-16
Good news! Andrey emailed me today with updated source code.

**I'd be grateful for some testing** by those of you using Feisty or Gutsy (kernels 2.6.20, 2.6.21, 2.6.22) to ensure it builds cleanly and works. If you get any compiler warnings or errors please let me know so I can fix them. (I've checked it works with the Feisty 32-bit Desktop LiveCD and WPA Personal (TKIP) but it doesn't work with WPA2 Personal).

Here are Andrey's primary comments:
> comparing with version you had user visible changes are

- suspend should work without need to reload driver. I cannot test suspend to 
RAM (it locks up my notebook) but suspend to disk works; I'm using it daily

- it now compiles only station code by default; it avoids including large 
binary blob with AP firmware that probably nobody uses

- it compiles without UIL support by default (private Agere IOCTLs, allowing 
direct settings of specific driver properties). It requires work to make it 
lock-clean and I do not have it for something I do not use

Otherwise it just cleans up some locking issues. It definitely works for 
2.6.22 and 2.6.21 and probably earlier versions; but as stated several times 
I do not attempt to maintain compatibility with previous kernels.
I did some investigation and found that the changes to sysfs between kernel 2.6.20 (Feisty) and 2.6.21/22 broke the driver so it wouldn't compile on 2.6.20. I've spent a few hours tracking them down and adding conditional preprocessor macros that alter the source-code based on the kernel-version being built so the one source should build on all versions.

To make it easier to build just the module I've also modified the Makefile so you can build and install it using:
```
$ make
$ sudo make install
$ sudo modprobe wlags49_h1_cs
```
from whatever directory you've put the source-code.

I'm attaching two packages: the source-code (for those of you wanting to experiment) and the pre-built kernel module for Feisty 2.6.20-16-generic.

---

### Post by IntuitiveNipple on 2007-07-16
If you want to use this latest driver with the Feisty LiveCD there are a few hoops to jump through that aren't trivial so I thought I'd save you the hassle of working it out and document what I had to do.

Booting from the LiveCD causes the orinoco_cs driver to be loaded, so it needs to be unloaded before you can use the wlags_h1_cs WPA driver.

Once at the desktop, start an Xterm (Applications -> Accessories -> Terminal)

Check the current network configuration. You need to know which interface is WiFi:
```
$ ifconfig
$ iwconfig
```
I had to software 'eject' the PCCard to allow orinoco_cs to be unloaded. If it isn't, the refcnt on orinoco_cs remains at 1 and the module won't unload.
```
$ lsmod | grep orinoco
```
List the PC-cards then eject the socket number that orinoco_cs is attached to:
```
$ pccardctl ls
$ sudo pccardctl eject 1
```
Unload orinoco_cs:
```
$ sudo modprobe -r orinoco_cs
$lsmod | grep orinoco
```
The output of the lsmod command shouldn't list any modules.

Copy the kernel driver into place and update the modules dependencies (this assumes you've already extracted and copied wlags49_h1_cs.ko):
```
$ sudo cp wlags49_h1_cs.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/
$ sudo depmod -a
```
Re-enable the PC-Card socket:
```
$ sudo pccardctl insert 1
```
(The number is the socket used in the eject command previously)

Load the driver, enable networking with your device-name in place of **eth1** and set your WiFi ESSID where I've put **<wlan_name>**, then check:
```
$ sudo modprobe wlags49_h1_cs
$ sudo iwconfig eth1 essid <wlan_name>
$ sudo ifconfig eth1 up
$ iwconfig
$ ifconfig

```
Use the NetworkManager applet in the panel notification area to choose your wireless network. Assuming it is a WPA network you will be prompted for the key.

If all goes well the first 'light' in the NetworkManager applet icon will go green when the WPA is authorised and the second light when the network interface receives a DHCP lease and IP address.

---

### Post by burns1111 on 2007-08-01
I have had some luck with the install.  Everything went fine, the wlags is in, orinico is out.

However, it does not seem to want to get a network address from any WPA network.  I have tried a few, and it always stalls on the network key.

It is much further than I was...it has the option for WPA now, which it did not have before!  There has been a lot of great work involved here.

As far as my testing of it went, that's about all.  I'll report anything else if it changes!  Thanks for everything!

---

### Post by EdTheUniqueGeek on 2007-08-06
> Tikitoe,
Did you find a solution to getting WPA working on your Dell laptop with TM 1150? I have read most of the related postings and tried most out. But, I am still without a WPA solution.
Thank you

Soyut and Tikitoe, I'm looking for a solution for my TM 1150 mini-PCI also.

---

### Post by yossarian1936 on 2007-08-19
Hi there, 

My device manager in Feisty says the following about my wireless card, which is an internal card in a Samsung V30:

Agere Systems
Hermes2 Mini-PCI WaveLAN a/b/g
pci_product_id: 43824 (0xab30)

Can anyone tell me if this driver supposed to work for this card?  I've been trying to get it working for years...I tried installing both the binary kernel module and building from source, but so far nothing has happened even though lsmod says the module is loaded.  

Here's hoping!

---

### Post by DtJee on 2007-08-27
I am running this driver in Gutsy.. and it works.. except the network manager... it wont let me connect to any network. I can see them in the listing .. but that it stayes for ages in the waiting status and then drops back to not connected.

---

### Post by burns1111 on 2007-08-27
I had the same issue with the driver stalling at the "requesting a network address" stage.  It would continually ask me for my WPA passkey.  I thought that maybe something was buggy with my router, so just a quick refresh of the settings (changing the number of DHCP addresses available was enough) on my router seemed to do the trick.

---

### Post by DtJee on 2007-08-30
And now it works ???

---

### Post by DtJee on 2007-09-14
Any updates here ?? I am still using this driver with Gutsy and it still works...

---

### Post by stmiller on 2007-09-19
Hi Intuitive, thank you for your work! I have a few questions.

The driver on page 6 makes and installs fine under PowerPC 2.6.19.7, and I can load the module ok. I'm using the airport original orinoco Hermes I 802.11b card. Should the same driver work for Hermes I and Hermes II cards?

I have blacklisted and removed orinoco and associated modules, but a wireless card is still not detected by networkmanager, or at all. I can confirm in dmesg that the driver loads ok. iwconfig and ifconfig both do not list a wireless device. Any clues? Any other PowerPC users out there? Thanks.

EDIT: I'm going to try a more recent kernel and see if that is the problem here.
EDIT 2: Current Feisty 2.6.20-16: same problem. No wireless card found. Module compiles and loads okay.

---

### Post by Audesse on 2007-09-23
Same as STMiller...if anyone has successfully gotten this to work on a G3 iBook or similar, please let us know how!

---

### Post by burns1111 on 2007-09-30
Just reporting that an upgrade to Gutsy beta (as of September 29th, 2007) made the driver not work initially.  After a rebuild/reinstall of the wlags49 source posted in this forum, it is all working great again.

---

### Post by moxie12 on 2007-09-30
Still no luck with Feisty (2.6.20-16). 

Went through the instructions on page 6 and the module loaded just fine, could see my network with plenty of green bars, got options for WPA-Personal, but the process always hangs on getting an IP address. Filled in the constant requests for passkey and tried setting up keys in Keyring manager, no joy. Commented out everything but lo entries in /etc/interfaces, still nothing worked.

I ended up getting rid of Network Manager and trying wicd Manager, but still out of luck. Works fine with no encryption or WEP, but WPA just doesn't happen.

I finally tried cutting out the middleman and running wpa_supplicant from command line:
sudo wpa_supplicant  -c/etc/wpa_supplicant.conf -ieth1 -Dwext
with results:

[INDENT]Trying to associate with nn:nn:nn:nn:nn:nn (SSID='my_ssid' freq=0 MHz)
ioctl[SIOCSIWAUTH]: Invalid argument
WEXT auth param 6 value 0x1 - ioctl[SIOCSIWAUTH]: Invalid argument
WEXT auth param 1 value 0x4 - ioctl[SIOCSIWAUTH]: Invalid argument
WEXT auth param 2 value 0x4 - ioctl[SIOCSIWAUTH]: Invalid argument
WEXT auth param 3 value 0x2 - ioctl[SIOCSIWAUTH]: Invalid argument
WEXT auth param 10 value 0x1 - ioctl[SIOCSIWAUTH]: Invalid argument
WEXT auth param 8 value 0x0 - ioctl[SIOCSIWAP]: Operation not supported
Association request to the driver failed
Associated with nn:nn:nn:nn:nn:nn
WPA: Key negotiation completed with nn:nn:nn:nn:nn:nn [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection nn:nn:nn:nn:nn:nn completed (auth) [id=0 id_str=]
[/INDENT]

I also tried running the same line with the Hermes driver with result:
[INDENT] Unsupported driver 'hermes'.[/INDENT]


My wpa_supplicant.conf looks like this:

network={
        ssid="my_ssid"
        scan_ssid=1
        key_mgmt=WPA-PSK
        proto=WPA
        pairwise=TKIP
        group=TKIP
        psk=[a long hex key not in quotes]
}

Thanks for any ideas on what is going wrong!

---

### Post by moxie12 on 2007-09-30
BTW, I am using an Orinoco Gold Classic  in a Dell Latitude C610.

---

### Post by moxie12 on 2007-10-05
Finally, problem solved-- combination of the following:
1. my router, an SMC2804wbrp-g print server,  translates  WPA passphrases to PSK in a strange way. I finally had to take a hex password and put it in the ASCII passphrase box. It also would not accept a passphrase longer than 62 characters though it had space for 63 characters.  Bizarre.

 Then, Wicd would accept this hex password in quotes (though Win XP accepts the password as a straight hex!)  I figured this out after trying every possible combination of hex/ASCII, in quotes/not in quotes, longer than 32 chars/shorter than 62 chars  passwords.

2. Wicd is a fantastic solution to the constantly-popping up keyring manager problem.   Wicd tray-edgy.py works, but Wicd-tray.py couldn't ever find the IP address for me. 

Anyway, these were not faults of the driver! WPA is now working beautifully for me. Thanks so much to OP for working this out for us!

---

### Post by carac on 2007-10-23
Can somebody (IntuitiveNipple?) please post a binary for gutsy (2.6.22) ? Pretty, pretty, pretty please :)

---

### Post by aspora.isernia on 2007-11-01
> **carac said:**
> Can somebody (IntuitiveNipple?) please post a binary for gutsy (2.6.22) ? Pretty, pretty, pretty please :)

Yeah... Me too, I'm waiting that someone posts the bin of this module... [-o<
Many thanks!!!

a.i :-D

---

### Post by carac on 2007-11-01
I managed to compile one of the above sources on a very light X200 and the build process was OK (and surprisingly short - it seems that you do not need the full source for the kernel, only the headers - which I had after a rather standard clean 7.10 setup).

I have attached two files - the source again and the resulting module - I believe:

1. wlags49_h1_cs.ko should be placed into /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless

2. orinoco_cs should be blacklisted in /etc/modprobe.d/blacklist

3. depmod -a

4. restart system.

HOWEVER ON MY SYSTEM (Dell X200 with Dell 1150 wireless module) IT DOES NOT WORK - the network seems to be detected but it never connects (not even on open networks) - I am probably missing something - most likely the internal firmware of THIS card is different from the internal firmware for the card on people where it works - any hint on that ??? (as far as I understand with this adapter there is an internal firmware but also certain drivers just load a separate firmware in the RAM of the card - and since I have not seen any loadable firmware with wlags49_h1_cs.ko I suppose it can only work with the internal-flash firmware ... which probably in my case is too old :( )



Below are the two attachments - source (same as from a post before) and module for 2.6.22!

---

### Post by aspora.isernia on 2007-11-01
> **carac said:**
> I managed to compile one of the above sources on a very light X200 and the build process was OK (and surprisingly short - it seems that you do not need the full source for the kernel, only the headers - which I had after a rather standard clean 7.10 setup).
...
Below are the two attachments - source (same as from a post before) and module for 2.6.22!

Carac!! :KS
WELL DONE!!
Many many thanks!! I have the same Dell X200 and your work worked so fine!!
Trust me: your module performs incredibly well, the only difficulty I found was during the creation of the /etc/network/interfaces file. If you follow the steps of the WPA tutorial, all will work!!

Wow: this community is great!!
THANKS!! :lolflag:

---

### Post by carac on 2007-11-04
> **aspora.isernia said:**
> Carac!! :KS
WELL DONE!!
Many many thanks!! I have the same Dell X200 and your work worked so fine!!
Trust me: your module performs incredibly well, the only difficulty I found was during the creation of the /etc/network/interfaces file. If you follow the steps of the WPA tutorial, all will work!!

Wow: this community is great!!
THANKS!! :lolflag:


Actually encouraged that the module was working for you I have decided to give it another try - and IT WORKS !!! :guitar:

However with wlags49_h1_cs the system does not seem to suspend any more - any ideas ??? I even tried to add wlags49_h1_cs in /etc/default/acpi-support under modules= but it still hangs :frown:

---

### Post by teilaxu on 2007-11-10
carac, thank you. WELL DONE. driver is working in my toshiba portege 3500.:popcorn:

---

### Post by carac on 2007-11-11
> **teilaxu said:**
> carac, thank you. WELL DONE. driver is working in my toshiba portege 3500.:popcorn:

Can you still suspend/resume ?

---

### Post by teilaxu on 2007-11-11
Hi Carac,

still now I don't check SUSPEND/RESUME, sorry, it isn't working. And another trouble is that with generic kernel work (except suspend) but in 'rt' kernel doesn't, any idea?.

But,I'm happy and I want to be graceful with all the community because without your help now I sall have only ethernet cable connection.

If I can help in something...

---

### Post by burpsmirk on 2007-12-07
Wooooo... bloody fantastic!! 

5 days I've wasted trying to get this %"&£ing Dell TrueMobile 1150 card working with gutsy. 

Thank you very much to all who contributed (notably IntuativeN & carac). I was just starting to loose faith in Linux before I'd even got round to trying it! 

(In case you're wondering, suspend/resume does not work (on a Dell Latitude C840), but I'm not too fussed cause it didn't work before either!)

BTW: how would I go about configuring this? Is there a .config file somewhere or is it all done via NM?

---

### Post by moussaba on 2007-12-19
Worked perfectly on my DELL C840.  I had to change my router to use WPA as WPA2 is not supported by the TrueMobile 1150.  Thanx for the help.




QUOTE=carac;3683345]I managed to compile one of the above sources on a very light X200 and the build process was OK (and surprisingly short - it seems that you do not need the full source for the kernel, only the headers - which I had after a rather standard clean 7.10 setup).

I have attached two files - the source again and the resulting module - I believe:

1. wlags49_h1_cs.ko should be placed into /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless

2. orinoco_cs should be blacklisted in /etc/modprobe.d/blacklist

3. depmod -a

4. restart system.

HOWEVER ON MY SYSTEM (Dell X200 with Dell 1150 wireless module) IT DOES NOT WORK - the network seems to be detected but it never connects (not even on open networks) - I am probably missing something - most likely the internal firmware of THIS card is different from the internal firmware for the card on people where it works - any hint on that ??? (as far as I understand with this adapter there is an internal firmware but also certain drivers just load a separate firmware in the RAM of the card - and since I have not seen any loadable firmware with wlags49_h1_cs.ko I suppose it can only work with the internal-flash firmware ... which probably in my case is too old :( )



Below are the two attachments - source (same as from a post before) and module for 2.6.22![/QUOTE]

---

### Post by anomalyconcept on 2007-12-24
> **carac said:**
> However with wlags49_h1_cs the system does not seem to suspend any more - any ideas ??? I even tried to add wlags49_h1_cs in /etc/default/acpi-support under modules= but it still hangs :frown:

I have to forcibly remove the module in order to suspend/hibernate.  I use hibernate/suspend2/whatever it's called now (something with ice?), but I presume suspending (to RAM) encounters the same error.

I actually have a little script that I use to hibernate, and the relevant line is:
rmmod -f wlags49_h1_cs

This forcibly removes the module (modprobe -r or rmmod alone don't seem to want to unload the module), and doesn't seem to cause any problems for me when resuming.  The module just needs to be loaded once you resume (modprobe wlags49_h1_cs) and your wireless should be up and running again.

I'm trying to get monitor mode to work with this driver; I want to use Kismet and WPA. =)

---

### Post by glennric on 2007-12-29
I have created and attached a deb of the kernel module for the latest gutsy kernel if anyone wants it.  This will only install the kernel module.  It is up to you to get it working.  I haven't had success getting it to work with network manager, and only partial success with wicd.  I can only get it to work properly from the command line.  If anyone knows how to get it to work with network manager please let me know.

I also attached the diff file which shows what I did to debianize the source.  If you download the file wlags49-h1-cs.tar.bz2 from previous posts, extract it, and change to the directory created by extracting, then you can apply the diff by typing
```
zcat /path/to/wlags49-h1-cs.diff.gz | patch -p1
```
After that type 
```
fakeroot debian/rules binary
```
and you will have created the deb I attached.

---

### Post by KenEkis on 2008-01-13
YEAH thx dude..

Got WPA working on my DELL C400 with Truemobile 1150

All tho the only selection is WPA personal i cant connect to WEP anymore, but then again i can reverse and enable orinoto_cs by editing the blacklist.

For those totally linux noobs as me i did following:

downloadet wlags49_h1_cs.ko.bz2 (536.8 KB) on my windows machine, unpack'd it with winrar, renamed it from wlags49_h1_cs.ko[1] to wlags49_h1_cs.ko, then put it on a USB key. Plugged it into my Unbuntu machine and copied it to my home directory, e.g /home/"loginname", in my case /home/default.

opened ternimal and write -->     sudo mv wlags49_h1_cs.ko /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless

in terminal again write -->   sudo gedit /etc/modprobe.d/blacklist then put: blacklist orinoco_cs in the end of the file and save.

step 3 and 4 are pretty forward :)

/Kenny

---

### Post by torstenkarusseit on 2008-01-20
Hi,
is there anyone who successfully use this driver with Debian 2.8.18-5-686 ?
May you post the binary ?
How it's possible to compile the driver without kernel sources ?

---

### Post by DenzilS on 2008-01-25
Woohoo! Praise be to Carac and IntuitiveNipple!

I have just tried this on my Dell C400 with 7.10 and it works just fine. Don't know about Suspend/Resume - don't use it anyway.

Thankyou, thankyou, thankyou,

Denzil

---

### Post by anomalyconcept on 2008-02-09
In the interest of keeping this thread up to date, below are some changes I made in order to get the driver to compile on the 2.6.24 branch.

I think I used the 2.6.22 patched code, since I just copied the source directory previously used to compile a module for a 2.6.22 kernel.

Anyway, here are the changes:
in the Makefile, change CFLAGS to EXTRA_CFLAGS.  
It may not be a clean/ideal solution, but it worked for me.  I'm not too certain on what CFLAGS actually does, but judging by the error it throws, the 2.6.24 specified ones are different than the wlags49 ones.

wl_cs.c, line 312: comment out 'SET_MODULE_OWNER(dev);'
I tried this after finding a [patch for another driver]("http://progfr.com.free.fr/rtl8187_2.6.22_to_2.6.24.patch") that basically #if'd it out.  I'm not sure if the conditional syntax can be used directly, but I basically did what the preprocessor would do and removed it.

Maybe someone could figure out how to make those changes degrade gracefully with < 2.6.24 branches and post a patch file.  I refrained from doing so because I'm not certain my solutions are the ideal way of doing things.

Hope this helps.

---

### Post by happy_wlags_user on 2008-02-23
Hello

in order to use suspend with the wlags driver:
I got it to work today! Still bathing in happiness I want to share it with you! 
Here is the Howto:

thanks to this post I was able to do it: [link]("http://www.joshgerdes.com/blog/2007/11/20/fix-ubuntu-710-suspend-issue-on-dell-m140-laptop/")

In Order to get it working you have to automatically unload the module. This is done by the scripts in /etc/acpi/suspend.d in the (by the first numbers determined) alphabetical order of  their names.

So first create [I]/etc/acpi/suspend.d/07-wlags_unload.sh
[/I]
```

#!/bind/sh

# stopping network - manager
/etc/dbus-1/event.d/25NetworkManager stop

# eject wlan - card
pccardctl eject 2

# unload wlags49_hs_cs module
rmmod wlags_49_h1_cs


```

and change it to an executable

EDIT: I forgot to say, that the last number of the pccardctl command can be specific in each pc, its the slotnumber where the wlancard is connected. But, having read the howto of IntuitiveNipple for installing wlags at the beginning of this thread, you may already know how to determine it.

```

sudo chmod +x /etc/acpi/suspend.d/07-wlags_unload.sh

```

Now suspend should work properly.
In order to automatically reload the module on restart, create */ect/acpi/resume.d/99-wlags_reload.sh*

```

#!/bin/sh

# WlAN modul wlags49_h1_cs wieder laden

modprobe wlags49_h1_cs

# restart Network Manager 

/etc/dbus-1/event.d/25NetworkManager start


```

Again, change the script to an executable:

```

sudo chmod +x /ect/acpi/resume.d/99-wlags_reload.sh

```

With me it worked fine, so I hope it does with you as well!
:guitar:

Regards,

Alex

---

### Post by MartijnV on 2008-02-28
I've got a Dell C610 with the agere/orinoco minipci card. I'm running Ubuntu 7.10. The 2.6.22 driver seems to work, but then I get the following message:

Feb 28 22:29:57 dellPIII kernel: [   22.120000] wlags49_h1_cs v7.18 for PCMCIA, 03/31/2004 14:31:00 by Agere Systems, [http://www.agere.com](http://www.agere.com)
Feb 28 22:29:57 dellPIII kernel: [   22.120000] *** Modified for kernel 2.6 by Andrey Borzenkov <arvidjaar@mail.ru> $Revision: 39 $
Feb 28 22:29:57 dellPIII kernel: [   22.120000] *** Station Mode (STA) Support: YES
Feb 28 22:29:57 dellPIII kernel: [   22.120000] *** Access Point Mode (AP) Support: YES
Feb 28 22:29:57 dellPIII kernel: [   23.420000] eth1: Wireless, HCF failure: "Expected adapter event did not occur in expected time"
Feb 28 22:29:57 dellPIII kernel: [   23.420000] wlags49_h1_cs: register_netdev() failed
 

Am I missing something?

---

### Post by MartijnV on 2008-03-01
Never mind,

sudo apt-get install pcmcia-cs was the solution to my problems!

I wanted some extra information, tried cartctl info and got the message to install pcmcia-cs first.

I also started cardmgr, which seemed to do the trick. I havenot seen if it still works after a reboot.

---

### Post by jugglefish on 2008-03-01
Hello guys,

My friend just yesterday got an old Toshiba Tecra 9100. Installing Ubuntu was straight forward as expected but then it took me a whole day to figure out this wirelesse thingy. After I almost left the house to buy an extra external adapter I discovered the end of this thread.

BIG THX to whoever made this possible. Dont' know about suspend/resume yet but getting a WPA-based connect is now finally possible. :->

I just copied the binary wlags49_h1_cs.ko (see some posts above) into the appropriate place (/usr/lib/modules/), depmod, blacklisted orinoco_cs and IT WORKS. :->

Just want to let you know there's someone out there who appreciates your work very much.

warm regards

---

### Post by Cows on 2008-03-17
I haven't tested it yet but I will soon. I would like to thank IntuitiveNipple for making this possible and everyone else who tested and worked on this. This is a huge step for Wireless Networking.

---

### Post by Cows on 2008-03-21
I am compiling it on Ubuntu 8.04 Alpha 6 atm. I will be posting up the .ko for 2.6.24 later tonight. I don't know if the .ko file is platform specific but it is being compiled on a iBook G3 PPC.

---

### Post by IntuitiveNipple on 2008-03-27
Well, it's time to get it working on Hardy (2.6.24)!

I think it's time we created a universal source package and then build the .deb packages for all the kernels from Edgy to Hardy. If the Launchpad PPA will build kernel module packages I'll put them on there (if not I'll set up a repository for them). For those with an Apple Mac you'll need to build them separately.

I've grabbed all the source packages from this thread, including **glennric**'s Debian packaging diff, and hopefully I can create a single package that will work for all Ubuntu versions.

---

### Post by propwashz on 2008-04-07
Any luck with the deb files? Waiting patiently ...... and thanks for all your work in solving this!!:):KS:KS

---

### Post by Neal Mann on 2008-04-16
First off, thanks for all of the work that has been done so far on these drivers.

We have a number of Dell Latitude C600 and C610 laptops here at my university, and many of them have Dell TrueMobile 1150 cards onboard.  Unfortunately, a lot of these laptops have wireless only.  We are going to be selling some soon, and I wanted to demo Ubuntu on them so we didn't have to put Windows 2000 back on them (yuck!).  It's really important for these computers to have a stable wireless connection.

Okay, enough backstory.  Here are some system details:
[B]Dell Latitude C600, 700 MHz PIII, 256 MB RAM
Dell TrueMobile 1150 WLAN card (mini-PCI, not CardBus)
Ubuntu 7.10 with all latest patches (as of 2008-04-11)[/B]

Our campus wireless network uses 802.1x authentication via PEAP/MSCHAPv2 with dynamic WEP keys, so I wanted to get this working with that network first.  The included orinoco_cs drivers don't appear to have WPA support for this card (as is apparent from this and other threads), so I didn't even have the option of 802.1x authentication in network-manager.  Running wpa_supplicant manually with a wpa_supplicant.conf file, correctly configured, also didn't work.

Next, I tried switching from the orinoco drivers to an ndiswrapper solution, but none of the XP drivers I tried would load correctly (granted, I was using the Ubuntu repository version of ndiswrapper; I didn't bother trying to compile the latest release yet).  That's when I found this thread and the kernel module source code posted by IntuitiveNipple.

I first tried loading the pre-compiled module for Gutsy that carac posted on page 8 of this thread.  This worked insofar as I could see all available wireless networks, and WPA support was enabled.  However, when trying to connect to our 802.1x-authenticated network, it would appear to connect but would never actually do so.  So, thinking the 802.1x stuff was throwing a wrench in the works, I tried to connect to an unencrypted wireless network, but it stalled in the same manner.

At this point, I compiled the kernel module myself with IntuitiveNipple's makefile on page 6, but I had the same results as with carac's precompiled module.

The only clues I can find that might point to the problem are found when I run wpa_supplicant from the terminal.  Here's what I see:

```

WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
ioctl[SIOCSIWAUTH]: Invalid argument
WEXT auth param 6 value 0x1 - WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
ioctl[SIOCSIWAUTH]: Invalid argument
WEXT auth param 0 value 0x1 - ioctl[SIOCSIWAUTH]: Invalid argument
WEXT auth param 1 value 0x10 - ioctl[SIOCSIWAUTH]: Invalid argument
WEXT auth param 2 value 0x10 - ioctl[SIOCSIWAUTH]: Invalid argument
WEXT auth param 3 value 0x0 - ioctl[SIOCSIWAUTH]: Invalid argument
WEXT auth param 10 value 0x1 - ioctl[SIOCSIWAUTH]: Invalid argument
WEXT auth param 8 value 0x1 - ioctl[SIOCSIWAP]: Operation not supported
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b1a len=14
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b1a len=14

```

This section will repeat every 5 seconds or so, presumably trying to reconnect to a network.  On a Linksys WPC11 card that I did get working with our wireless networks (both unencrypted and 802.1x-authenticated), I don't see any ioctl errors.

When carac first posted the kernel module on page 8, s/he said that it didn't work, but later said that it did.  There were no details of what changed except that it was tried again.  Are there any more details that you can give?

---

### Post by carac on 2008-04-20
> **Neal Mann said:**
> 
...
When carac first posted the kernel module on page 8, s/he said that it didn't work, but later said that it did.  There were no details of what changed except that it was tried again.  Are there any more details that you can give?

I believe in my case was a misconfiguration in Networkmanager or something like that (and if I remember correctly it was fixed by a restart and connecting 'from scratch').

However I believe that all of the people using WPA including myself were actually using WPA-PSK, not the real WPA+radius or similar configuration ... never tested something like that :(

---

### Post by glennric on 2008-04-24
I have created a deb for Hardy Heron.  I attached the source, diff, and deb.  The source is the same as before, but I attached it for convenience.

---

### Post by xt28 on 2008-05-09
Cows, have you had any luck getting this to work on the iBook?

Has anyone else?

Here's another pointer I found that might be helpful:
[http://sourceforge.net/mailarchive/forum.php?thread_name=47BA07F2.7050105%40gmail.com&forum_name=orinoco-users](http://sourceforge.net/mailarchive/forum.php?thread_name=47BA07F2.7050105%40gmail.com&forum_name=orinoco-users)

---

### Post by gliverman on 2008-05-16
> **glennric said:**
> I have created a deb for Hardy Heron.  I attached the source, diff, and deb.  The source is the same as before, but I attached it for convenience.

Okay... I may just be missing something simple but I need some help.  I have a new install of 8.04 and I ran 
```

sudo dpkg -i wlags49-h1-cs-2.6.24-16-generic_2.6.24-16-generic-0ubuntu1_i386.deb  
```

and then edited /etc/modprobe.d/blacklist, adding 
```

# remove non-WPA Hermes 802.11b driver
blacklist orinoco_cs

```
to the end of the file.  After a reboot the new driver is loaded and I have the option to connect via WPA Personal in Network Manager but it spins and says "Waiting for Network Key for the wireless network 'GENE-2'..." and then the connection fails.  

This is the full extent of what has been done... ideas?

---

### Post by jugglefish on 2008-05-18
> **glennric said:**
> I have created a deb for Hardy Heron.  I attached the source, diff, and deb.  The source is the same as before, but I attached it for convenience.

Many THX again. works nicely on a Toshiba Laptop

---

### Post by Wubuntish on 2008-05-25
I get the following with the .deb on a Ubuntu Hardy Server on a Toshiba Tecra 8200 with wpa_supplicant using Wext:

```
Trying to associate with 00:0f:66:51:6d:0f (SSID='<essid>' freq=2447 MHz)
Association request to the driver failed
Associated with 00:0f:66:51:6d:0f
WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
WPA: Could not verify EAPOL-Key MIC - dropping packet
WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
WPA: Could not verify EAPOL-Key MIC - dropping packet
```

Any ideas?

EDIT:
Never mind, seems to work now for some reason. =X

---

### Post by some1l8 on 2008-05-27
new driver 
7.22 for linux (wl_lkm_722abg)
[http://www.lsi.com/support/downloads/legacy/wl_lkm_722_abg.tar.gz]("http://www.lsi.com/support/downloads/legacy/wl_lkm_722_abg.tar.gz")
anyone konw how to make the drive on hardy 8.04? i tried to complie the driver with no luck just returned with lots of errors.

---

### Post by some1l8 on 2008-05-27
sorry, forgot to metion card interface is (mini) pci, not pcmcia. for toshiba tecra 8200

---

### Post by jopadan on 2008-05-29
I've managed to compile the wlags49-h1-cs module today for linux-2.6.26-rc4 on amd64 I just had to change the manfid and stuff like that and fix some errors for the build with debugging enabled.
When I insert the card the module loads and segfaults with the following trace:

pccard: PCMCIA card inserted into slot 0
cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xfffff
cs: memory probe 0x50000000-0x500fffff: excluding 0x50000000-0x500fffff
cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa0ffffff
cs: memory probe 0xfa000000-0xfbffffff: excluding 0xfb000000-0xfb1fffff
pcmcia: registering new device pcmcia0.0
wlags49_h1_cs.o:>:init_module
wlags49_h1_cs v7.18 for PCMCIA, 03/31/2004 14:31:00 by Agere Systems, [http://www](http://www)
.agere.com
*** Modified for kernel 2.6 by Andrey Borzenkov <arvidjaar@mail.ru> $Revision: 3
9 $
*** Station Mode (STA) Support: YES
*** Access Point Mode (AP) Support: YES
wlags49_h1_cs.o:>>:wl_adapter_init_module
wlags49_h1_cs.o:wl_adapter_init_module wl_adapter_init_module() -- PCMCIA
wlags49_h1_cs.o:>>>:wl_adapter_attach
wlags49_h1_cs.o:>>>>:wl_device_alloc
wlags49_h1_cs.o:<<<<:wl_device_alloc
wlags49_h1_cs.o:>>>>:wl_adapter_insert
wlags49_h1_cs.o:>>>>>:wl_insert
wlags49_h1_cs.o:wl_insert Calling hcf_connect()...
wlags49_h1_cs.o:wl_insert Calling wvlan_go() to perform a card reset...
wlags49_h1_cs.o:>>>>>>:wl_go
wlags49_h1_cs.o:>>>>>>>:wl_disable
wlags49_h1_cs.o:<<<<<<<:wl_disable
wlags49_h1_cs.o:>>>>>>>:wl_disable_wds_ports
wlags49_h1_cs.o:<<<<<<<:wl_disable_wds_ports
wlags49_h1_cs.o:wl_go Downloading STA firmware...
wlags49_h1_cs.o:>>>>>>>:wvlanGetPriRecords
eth0: PRI 31 variant 2 version 9.48
eth0: NIC 1 variant 1 version 4.00
wlags49_h1_cs.o:<<<<<<<:wvlanGetPriRecords
wlags49_h1_cs.o:wl_go Card MAC Address: BE:31:01:00:02:00
wlags49_h1_cs.o:>>>>>>>:wl_put_ltv
general protection fault: 0000 [1] PREEMPT 
CPU 0 
Modules linked in: wlags49_h1_cs(+) snd_seq_midi snd_emu10k1_synth snd_emux_synt
h snd_seq_virmidi snd_seq_midi_emul snd_pcm_oss snd_mixer_oss snd_seq_dummy snd_
seq_oss snd_seq_midi_event snd_seq nvidia(P) snd_emu10k1 snd_rawmidi snd_ac97_co
dec ac97_bus snd_pcsp snd_pcm snd_seq_device snd_util_mem snd_timer snd_hwdep sn
d ath5k mac80211 soundcore emu10k1_gp k8temp hwmon cfg80211 snd_page_alloc gamep
ort i2c_nforce2
Pid: 16130, comm: modprobe Tainted: P          2.6.26-rc4 #1
RIP: 0010:[<ffffffffa06b500a>]  [<ffffffffa06b500a>] :wlags49_h1_cs:hcf_put_info
+0x33a/0x4d0
RSP: 0018:ffff810020473ac8  EFLAGS: 00010046
RAX: ffff020009731362 RBX: ffff810009730a28 RCX: 0000000000000830
RDX: 0000000000000001 RSI: ffff810009730a28 RDI: ffff8100097307b8
RBP: ffff8100097307b8 R08: 00000000ffffffff R09: 0000000000000000
R10: 0000000000000000 R11: 0000000000000010 R12: 0000000000000000
R13: ffff810009730a28 R14: ffff8100097307b8 R15: ffff810009730a28
FS:  00007fae558c16f0(0000) GS:ffffffff80a5f000(0000) knlGS:00000000f6967b90
CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
CR2: 00007fff501ff04c CR3: 000000002047d000 CR4: 00000000000006e0
DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Process modprobe (pid: 16130, threadinfo ffff810020472000, task ffff810017154d30
)
Stack:  ffffffffa06b377e ffff810009731362 ffff810009730600 0000000000000000
 ffff810009730a28 ffffffffa06ab22f 000000000000fc01 ffff810009730600
 ffff810009731260 0000000000000000 ffff810009730a28 ffff8100097312a9
Call Trace:
 [<ffffffffa06b377e>] ? :wlags49_h1_cs:cmd_exe+0x8e/0xb0
 [<ffffffffa06ab22f>] ? :wlags49_h1_cs:wl_put_ltv+0x7f/0x18d0
 [<ffffffffa06aced4>] ? :wlags49_h1_cs:wl_go+0x304/0x3b0
 [<ffffffffa06af607>] ? :wlags49_h1_cs:wl_insert+0x24c7/0x2600
 [<ffffffff805bef43>] ? register_netdevice+0x53/0x320
 [<ffffffff805bf251>] ? register_netdev+0x41/0x60
 [<ffffffffa06b2efc>] ? :wlags49_h1_cs:wl_adapter_insert+0x20c/0x230
 [<ffffffffa06b309e>] ? :wlags49_h1_cs:wl_adapter_attach+0x8e/0x150
 [<ffffffff80504052>] ? pcmcia_device_probe+0xe2/0x190
 [<ffffffff80488f85>] ? driver_probe_device+0x95/0x1a0
 [<ffffffff80489119>] ? __driver_attach+0x89/0x90
 [<ffffffff80489090>] ? __driver_attach+0x0/0x90
 [<ffffffff804885bd>] ? bus_for_each_dev+0x4d/0x80
 [<ffffffff8028bcb8>] ? kmem_cache_alloc+0x88/0x90
 [<ffffffff80488ad8>] ? bus_add_driver+0xc8/0x250
 [<ffffffff804893f5>] ? driver_register+0x55/0x140
 [<ffffffff80504b00>] ? pcmcia_register_driver+0xe0/0x140
 [<ffffffffa06b2b6a>] ? :wlags49_h1_cs:wl_adapter_init_module+0x1a/0xd0
 [<ffffffffa06750ba>] ? :wlags49_h1_cs:wl_module_init+0xba/0x153
 [<ffffffff8025561b>] ? sys_init_module+0x17b/0x1a80
 [<ffffffff80503df0>] ? pcmcia_dev_present+0x0/0x50
 [<ffffffff8020b6bb>] ? system_call_after_swapgs+0x7b/0x80


Code: c3 48 8b 43 08 31 d2 48 85 c0 48 89 45 18 74 04 0f b7 53 10 48 8b 45 18 66
 89 55 20 45 31 e4 66 c7 45 24 00 00 66 c7 45 22 00 00 <66> c7 00 00 00 66 c7 45
 26 00 00 48 83 c4 08 5b 5d 44 89 e0 41 
RIP  [<ffffffffa06b500a>] :wlags49_h1_cs:hcf_put_info+0x33a/0x4d0
 RSP <ffff810020473ac8>
---[ end trace 918c4f637d65443f ]---
note: modprobe[16130] exited with preempt_count 1
BUG: scheduling while atomic: modprobe/16130/0x10000002
Pid: 16130, comm: modprobe Tainted: P      D   2.6.26-rc4 #1

Call Trace:
 [<ffffffff80736d89>] thread_return+0x148/0x22f
 [<ffffffff8022a49c>] __cond_resched+0x1c/0x50
 [<ffffffff807373a1>] _cond_resched+0x31/0x40
 [<ffffffff80275243>] unmap_vmas+0x733/0x770
 [<ffffffff8027968d>] exit_mmap+0x6d/0x110
 [<ffffffff8022d5bd>] mmput+0x1d/0xd0
 [<ffffffff80233531>] do_exit+0x191/0x830
 [<ffffffff8020c4a4>] oops_end+0x74/0x80
 [<ffffffff80738e79>] error_exit+0x0/0x51
 [<ffffffffa06b500a>] :wlags49_h1_cs:hcf_put_info+0x33a/0x4d0
 [<ffffffffa06b4ea8>] :wlags49_h1_cs:hcf_put_info+0x1d8/0x4d0
 [<ffffffffa06b377e>] :wlags49_h1_cs:cmd_exe+0x8e/0xb0
 [<ffffffffa06ab22f>] :wlags49_h1_cs:wl_put_ltv+0x7f/0x18d0
 [<ffffffffa06aced4>] :wlags49_h1_cs:wl_go+0x304/0x3b0
 [<ffffffffa06af607>] :wlags49_h1_cs:wl_insert+0x24c7/0x2600
 [<ffffffff805bef43>] register_netdevice+0x53/0x320
 [<ffffffff805bf251>] register_netdev+0x41/0x60
 [<ffffffffa06b2efc>] :wlags49_h1_cs:wl_adapter_insert+0x20c/0x230
 [<ffffffffa06b309e>] :wlags49_h1_cs:wl_adapter_attach+0x8e/0x150
 [<ffffffff80504052>] pcmcia_device_probe+0xe2/0x190
 [<ffffffff80488f85>] driver_probe_device+0x95/0x1a0
 [<ffffffff80489119>] __driver_attach+0x89/0x90
 [<ffffffff80489090>] __driver_attach+0x0/0x90
 [<ffffffff804885bd>] bus_for_each_dev+0x4d/0x80
 [<ffffffff8028bcb8>] kmem_cache_alloc+0x88/0x90
 [<ffffffff80488ad8>] bus_add_driver+0xc8/0x250
 [<ffffffff804893f5>] driver_register+0x55/0x140
 [<ffffffff80504b00>] pcmcia_register_driver+0xe0/0x140
 [<ffffffffa06b2b6a>] :wlags49_h1_cs:wl_adapter_init_module+0x1a/0xd0
 [<ffffffffa06750ba>] :wlags49_h1_cs:wl_module_init+0xba/0x153
 [<ffffffff8025561b>] sys_init_module+0x17b/0x1a80
 [<ffffffff80503df0>] pcmcia_dev_present+0x0/0x50
 [<ffffffff8020b6bb>] system_call_after_swapgs+0x7b/0x80

pccard: card ejected from slot 0

I changed the mailbox address transfer in wl_put_ltv to use-the correct size with the following diff:

--- wlags49_26/wl_main.c        2008-05-29 19:27:20.000000000 +0200
+++ wlags49-h1-cs/wl_main.c     2008-05-29 19:20:32.000000000 +0200
@@ -1965,14 +1957,13 @@
     /* Send our configuration to the card. Perform any endian translation
        necessary */
 
-
     /* Register the Mailbox; VxWorks does this elsewhere; why? */
-    lp->ltvRecord.len       = 4;
-    lp->ltvRecord.typ       = CFG_REG_MB;
-    lp->ltvRecord.u.u32[0]  = (u_long)&( lp->mailbox );
-    lp->ltvRecord.u.u16[2]  = ( MB_SIZE / sizeof( hcf_16 ));
+      lp->ltvRecord.len       = sizeof(hcf_16*) + sizeof(hcf_16);
+      lp->ltvRecord.typ       = CFG_REG_MB;
+      ((CFG_REG_MB_STRCT FAR *)(LTVP)&(lp->ltvRecord))->mb_addr = (hcf_16*)lp->mailbox;
+      ((CFG_REG_MB_STRCT FAR *)(LTVP)&(lp->ltvRecord))->mb_size = MB_SIZE / sizeof( hcf_16 );
 
-    hcfStatus = hcf_put_info( &( lp->hcfCtx ), (LTVP)&( lp->ltvRecord ));
+      hcfStatus = hcf_put_info( &( lp->hcfCtx ), (LTVP)&( lp->ltvRecord ));
I am using the source code of glenerics last post with the attached diff to make it compile with debugging.

Now I get the following trace and no segfault also the return value seems to be correct but it still has lots of errors and doesn't seem to work:

wlags49_h1_cs.o:>:init_module
wlags49_h1_cs v7.18 for PCMCIA, 03/31/2004 14:31:00 by Agere Systems, [http://www.agere.com](http://www.agere.com)
*** Modified for kernel 2.6 by Andrey Borzenkov <arvidjaar@mail.ru> $Revision: 39 $
*** Station Mode (STA) Support: YES
*** Access Point Mode (AP) Support: YES
wlags49_h1_cs.o:>>:wl_adapter_init_module
wlags49_h1_cs.o:wl_adapter_init_module wl_adapter_init_module() -- PCMCIA
wlags49_h1_cs.o:<<:wl_adapter_init_module
wlags49_h1_cs.o:<:init_module
wlags49_h1_cs.o:>:wl_adapter_attach
wlags49_h1_cs.o:>>:wl_device_alloc
wlags49_h1_cs.o:<<:wl_device_alloc
wlags49_h1_cs.o:>>:wl_adapter_insert
wlags49_h1_cs.o:>>>:wl_insert
wlags49_h1_cs.o:wl_insert Calling hcf_connect()...
wlags49_h1_cs.o:wl_insert Calling wvlan_go() to perform a card reset...
wlags49_h1_cs.o:>>>>:wl_go
wlags49_h1_cs.o:>>>>>:wl_disable
wlags49_h1_cs.o:<<<<<:wl_disable
wlags49_h1_cs.o:>>>>>:wl_disable_wds_ports
wlags49_h1_cs.o:<<<<<:wl_disable_wds_ports
wlags49_h1_cs.o:wl_go Downloading STA firmware...
wlags49_h1_cs.o:>>>>>:wvlanGetPriRecords
eth0: PRI 31 variant 2 version 9.48
eth0: NIC 1 variant 1 version 4.00
wlags49_h1_cs.o:<<<<<:wvlanGetPriRecords
wlags49_h1_cs.o:wl_go Card MAC Address: BE:31:01:00:02:00
wlags49_h1_cs.o:>>>>>:wl_put_ltv
wlags49_h1_cs.o:wl_put_ltv CFG_REG_MB                        : 0xffff810027411362
wlags49_h1_cs.o:wl_put_ltv CFG_REG_MB result                 : 0x0000
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_MAX_DATA_LEN              : 0x05e4
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_MAX_DATA_LEN result       : 0x0000
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_SYSTEM_SCALE              : 0x0001
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_SYSTEM_SCALE result       : 0x0000
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_OWN_CHANNEL               : 0x000a
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_OWN_CHANNEL result        : 0x0000
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_MICRO_WAVE                : 0x0000
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_MICRO_WAVE result         : 0x0000
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_MCAST_RATE                : 0x0002
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_MCAST_RATE result         : 0x0000
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_OWN_NAME                  : Linux
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_OWN_NAME result           : 0x0000
wlags49_h1_cs.o:wl_put_ltv CFG_RTS_THRH                      : 0x092b
wlags49_h1_cs.o:wl_put_ltv CFG_RTS_THRH result               : 0x0000
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_PORT_TYPE                 : 0x0001
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_PORT_TYPE result          : 0x0000
wlags49_h1_cs.o:wl_put_ltv CFG_TX_RATE_CNTL                  : 0x0003
wlags49_h1_cs.o:wl_put_ltv CFG_TX_RATE_CNTL result           : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_PM_ENABLED                : 0x0000
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_PM_ENABLED result         : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_MCAST_RX                  : 0x0001
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_MCAST_RX result           : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_MAX_SLEEP_DURATION        : 0x0064
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_MAX_SLEEP_DURATION result : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_CREATE_IBSS                   : 0x0000
wlags49_h1_cs.o:wl_put_ltv CFG_CREATE_IBSS result            : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_DESIRED_SSID                  : LinuxAP
wlags49_h1_cs.o:wl_put_ltv CFG_DESIRED_SSID result           : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_OWN_ATIM_WINDOW           : 0x0000
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_OWN_ATIM_WINDOW result    : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_HOLDOVER_DURATION         : 0x0064
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_HOLDOVER_DURATION result  : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_PROMISCUOUS_MODE              : 0x0000
wlags49_h1_cs.o:wl_put_ltv CFG_PROMISCUOUS_MODE result       : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_AUTHENTICATION            : 0x0001
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_AUTHENTICATION result     : 0x0004
wlags49_h1_cs.o:wl_put_ltv MAC Address                       : BE:31:01:00:02:00
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_OWN_MAC_ADDR
wlags49_h1_cs.o:wl_put_ltv CFG_XXX_MAC_ADDR result           : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_OWN_SSID                  : LinuxAP
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_OWN_SSID result           : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_ENCRYPTION                : 0x0000
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_ENCRYPTION result         : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_SET_WPA_AUTH_KEY_MGMT_SUITE   : 0x0000
wlags49_h1_cs.o:wl_put_ltv CFG_SET_WPA_AUTH_KEY_MGMT_SUITE result: 0x0004
wlags49_h1_cs.o:>>>>>>:wl_set_wep_keys
wlags49_h1_cs.o:<<<<<<:wl_set_wep_keys
wlags49_h1_cs.o:<<<<<:wl_put_ltv
wlags49_h1_cs.o:<<<<:wl_go
Clocksource tsc unstable (delta = 14060952536 ns)
wlags49_h1_cs.o:<<<:wl_insert
wlags49_h1_cs.o:>>>:wl_stats
wlags49_h1_cs.o:<<<:wl_stats
eth0: Wireless, io_addr 0x9040, irq 16, mac_address BE:31:01:00:02:00
wlags49_h1_cs.o:<<:wl_adapter_insert
wlags49_h1_cs.o:<:wl_adapter_attach
wlags49_h1_cs.o:>:wl_stats
wlags49_h1_cs.o:<:wl_stats
wlags49_h1_cs.o:>:wl_adapter_open
wlags49_h1_cs.o:>>:wl_open
wlags49_h1_cs.o:>>>:wl_apply
wlags49_h1_cs.o:>>>>:wl_disable
wlags49_h1_cs.o:<<<<:wl_disable
wlags49_h1_cs.o:>>>>:wl_disable_wds_ports
wlags49_h1_cs.o:<<<<:wl_disable_wds_ports
wlags49_h1_cs.o:>>>>:wl_put_ltv
wlags49_h1_cs.o:wl_put_ltv CFG_REG_MB                        : 0xffff810027411362
wlags49_h1_cs.o:wl_put_ltv CFG_REG_MB result                 : 0x0000
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_MAX_DATA_LEN              : 0x05e4
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_MAX_DATA_LEN result       : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_SYSTEM_SCALE              : 0x0001
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_SYSTEM_SCALE result       : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_OWN_CHANNEL               : 0x000a
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_OWN_CHANNEL result        : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_MICRO_WAVE                : 0x0000
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_MICRO_WAVE result         : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_MCAST_RATE                : 0x0002
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_MCAST_RATE result         : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_OWN_NAME                  : Linux
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_OWN_NAME result           : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_RTS_THRH                      : 0x092b
wlags49_h1_cs.o:wl_put_ltv CFG_RTS_THRH result               : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_PORT_TYPE                 : 0x0001
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_PORT_TYPE result          : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_TX_RATE_CNTL                  : 0x0003
wlags49_h1_cs.o:wl_put_ltv CFG_TX_RATE_CNTL result           : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_PM_ENABLED                : 0x0000
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_PM_ENABLED result         : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_MCAST_RX                  : 0x0001
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_MCAST_RX result           : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_MAX_SLEEP_DURATION        : 0x0064
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_MAX_SLEEP_DURATION result : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_CREATE_IBSS                   : 0x0000
wlags49_h1_cs.o:wl_put_ltv CFG_CREATE_IBSS result            : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_DESIRED_SSID                  : LinuxAP
wlags49_h1_cs.o:wl_put_ltv CFG_DESIRED_SSID result           : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_OWN_ATIM_WINDOW           : 0x0000
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_OWN_ATIM_WINDOW result    : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_HOLDOVER_DURATION         : 0x0064
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_HOLDOVER_DURATION result  : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_PROMISCUOUS_MODE              : 0x0000
wlags49_h1_cs.o:wl_put_ltv CFG_PROMISCUOUS_MODE result       : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_AUTHENTICATION            : 0x0001
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_AUTHENTICATION result     : 0x0004
wlags49_h1_cs.o:wl_put_ltv MAC Address                       : BE:31:01:00:02:00
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_OWN_MAC_ADDR
wlags49_h1_cs.o:wl_put_ltv CFG_XXX_MAC_ADDR result           : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_OWN_SSID                  : LinuxAP
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_OWN_SSID result           : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_ENCRYPTION                : 0x0000
wlags49_h1_cs.o:wl_put_ltv CFG_CNF_ENCRYPTION result         : 0x0004
wlags49_h1_cs.o:wl_put_ltv CFG_SET_WPA_AUTH_KEY_MGMT_SUITE   : 0x0000
wlags49_h1_cs.o:wl_put_ltv CFG_SET_WPA_AUTH_KEY_MGMT_SUITE result: 0x0004
wlags49_h1_cs.o:>>>>>:wl_set_wep_keys
wlags49_h1_cs.o:<<<<<:wl_set_wep_keys
wlags49_h1_cs.o:<<<<:wl_put_ltv
wlags49_h1_cs.o:>>>>:wl_enable
wlags49_h1_cs.o:<<<<:wl_enable
wlags49_h1_cs.o:wl_apply Enable port 0 failed: 0x4
wlags49_h1_cs.o:>>>>:wl_enable_wds_ports
wlags49_h1_cs.o:<<<<:wl_enable_wds_ports
wlags49_h1_cs.o:<<<:wl_apply
eth0: Wireless, HCF failure: "Expected adapter event did not occur in expected time"
wlags49_h1_cs.o:<<:wl_open
wlags49_h1_cs.o:<:wl_adapter_open
wlags49_h1_cs.o:>:wl_stats
wlags49_h1_cs.o:<:wl_stats

---

### Post by some1l8 on 2008-05-29
> **glennric said:**
> I have created a deb for Hardy Heron.  I attached the source, diff, and deb.  The source is the same as before, but I attached it for convenience.

installed and blacklisted orinoco_cs on hardy. reboot and can see wpa option, but just cant connect to the network? my laptop is toshbia tecra 8200. agere/hermes1 wireless mini pci. anyone know how to get it work? thanks

---

### Post by glennric on 2008-06-04
I should have mentioned that there is some difficulty getting the wlags driver to work with network manager.  Sometimes it will and sometimes it won't.  Most of the time I have to connect from the command line.  The following commands work for me:
```

sudo iwconfig eth1 essid ROUTERNAME
sudo ifconfig eth1 up
sudo dhclient eth1
```
Replace ROUTERNAME with the essid of the router you are trying to connect to.  You may have to wait until network manager quits trying to connect for this to work (or kill nm-applet).

Edit:  By the way you may have to do a little more to use WPA.

---

### Post by davemiles871 on 2008-06-07
Has anyone had any success with this driver on the latest 2.6.24.18 kernel ? After my most recent system update I dont seem able to build the driver anymore and get dependency errors relating back to the 24.16 kernel that was installed by default when the system was first built. I even took the step of making my own kernel but the driver wont build on this for other reasons. I'm currently going back to a clean install and starting again.

I will keep trying and post any results but in case I'm reinventing the wheel thought it best to ask.

Dave

---

### Post by davemiles871 on 2008-06-09
Ok so I’ve now fixed the problems with the build I mentioned in the last post.

Here’s a summary of the steps needed to build this driver for Hardy Heron with all the latest updates. The process is documented in parts in this thread but you need to read quite a lot to get to the complete process for making a working driver. I felt it worthwhile collating all this into a single article.

Note that I’m assuming that you have got your system set up so the ‘su’ command works and you are running as root. This make the amount of typing required a little less.

First I did a clean install of the entire system using a PXE network install, which gets the very latest versions of everything at the first attempt. If you are not able to do this then at least update the system to the latest versions by running the update manager or by using 

```
apt-get upgrade
```

This should get your system to somewhere near to the same kernel version as mine, which was 2.6.24-18 on the day I made the driver that worked. Check this with 

```
uname -a
```

Next you should get together all the bits needed to build a kernel.

I used

```
apt-get install linux-kernel-devel fakeroot build-essential libncurses5 libncurses5-dev
```

which gets all the bits needed to do a traditional Debian Style build. You don’t need to download the kernel source at this point unless you actually want to make a kernel, which is in itself a rewarding experience but not really necessary for this driver to work.

Heres how to get the source if you do feel adventurous:

```
apt-get install linux-source
mkdir ~/src
cd ~/src
tar xjvf /usr/src/linux-source-<version-number-here>.tar.bz2
cd linux-source-<version-number-here>
```

Download the latest versions of the driver source and patch, posted by glennric in post #96 of this thread. Best to put these files into a working directory such as a subdirectory under you home directory.

Decompress and Unpack these 

```
gunzip wlags49-h1-cs.diff.gz

tar -xjvf wlags49-h1-cs.tar.bz2
```

This last step will create a subdirectory wlags49-h1-cs.

Patch the source using the patch file unpacked earlier.

```
patch –p0 <wlags49-h1-cs.diff
```

This will run without error in the environment you have just created. Earlier posts suggest that some errors would be found, in the current setup there should be none.

You need to make a couple of edits to avoid compilation errors. You will need to master a Linux editor to do this, but gedit is pretty simple if you don’t want to get into the mysteries of ‘vi’.

Move into the subdirectory where the driver source lives, then firstly edit the Makefile and secondly one of the source files.

```
cd wlags49-h1-cs
gedit Makefile
gedit wl_cs.c
```
In Makefile, on line 2 change CFLAGS to EXTRA_CFLAGS. 

In wl_cs.c on (or near) line 312 comment out the SET_MODULE_OWER(dev) statement. It should read

```
/* SET_MODULE_OWER(dev) */
```

Not far to go now.

Now in the same directory, you should issue the command

```
make 
```
Note again that other postings add a number of command line arguments, these are not required provided you are building on the target machine, it works it out for itself. This should now complete without error.

Next install the driver.

```
make install
```

Disable the existing Orinoco driver so that the new driver gets installed next time round.

```
echo “# Disable the non-WPA Orinoco driver” >>/etc/modprobe.d/blacklist
echo “blacklist orinoco_cs” >>/etc/modprobe.d/blacklist
```

In theory at least you should now be able to load and run the driver. You should be able to issue the sequence of commands:

```
depmod
rmmod orinoco_cs
modprobe wlags49-h1-cs
```
However this usually fails for me as the Orinoco driver is already loaded, so a quick reboot will sort that out.

After this, you should be able to click on the network configuration icon, and lo and behold under the wireless networks should appear any WPA networks in your locale, and it is then self evident how to configure it.

I still have a couple of minor niggles with this driver, which are:

1) It periodically disconnects, but this seems to be very much a feature of a very long session. In normal use it seems to stay connected for longer than my attention span.

2) It doesn’t always start up automatically, it seems to load the driver but not connect to any network. You need to go back into the network configuration tool and reconnect, or refer to the earlier posting by glennric for a command line invocation which will allow the connection to be established.

In both cases I haven’t had long enough yet to fully diagnose the problem.

I hope this is a useful summary.

---

### Post by casualprogrammer on 2008-06-10
Hi Folks,

thanks for providing the patched orinoco driver, it seems to work with ifup, yet not with NetworkManager under openSUSE 11.0 RC1.

What is your experience with NM ? Am I missing something ?

Casual

---

### Post by casualprogrammer on 2008-06-10
> **IntuitiveNipple said:**
> Well, it's time to get it working on Hardy (2.6.24)!

I think it's time we created a universal source package and then build the .deb packages for all the kernels from Edgy to Hardy. 

Hello IN,

this is really a good job, alas little known outside Ubuntu, I therefore have filed an enhancement request at kernel.org to make your solution part of the kernel, so _all_ distros can join in the fun..

[http://bugzilla.kernel.org/show_bug.cgi?id=10891](http://bugzilla.kernel.org/show_bug.cgi?id=10891)

It would probably help your cause a lot if Sergey, you and the others here supported it.

Have a lot of fun...

Casual

---

### Post by davemiles871 on 2008-06-12
Hi Casual

I've found that using netmanager it seems to be a lottery. First time I set it up it did work ok, after a reboot. Next time I visited the machine it had dropped off the network, and nothing I did could make it work again. After another reboot, it still did nothing, but revisiting the GUI and re-setting up it started up again. Since then it seems to have started every time the machine is booted and works without issue. If I had to put a number to it at the moment I'd say its about 80% ok.

Dave

---

### Post by davemiles871 on 2008-06-25
Just upgraded to the latest 24-19 kernel through automatic updates, and the driver did not (of course) get loaded.

Its as simple as recompiling the driver for the new kernel, as all the bits you need to do the job will have been updated automatically as part of the update process.

Simply while running as root

```
make && make install
```

If this succeeds (it should) then

```
reboot
```

Enjoy.

Dave

---

### Post by jbruder on 2008-06-26
After struggling with some vid issues to get a new kernel going, I was finally able to follow the instructions, make & install the driver on my g3 dual usb ibook. I still feel like I'm missing something. While my WPA-PSK network shows up in NM, WPA does not appear on the authentication dropdown. The strange thing is that it DOES show up in manual configuration, but when i configure it it won't connect. 

I really want to thank you guys for bringing this together, but any additional help would be appreciated.

Edit: I'm running 8.04 w/ 2.6.24-19-powerpc kernel installed from alternate cd / install. Most recent packages from synaptic.

---

### Post by jbruder on 2008-06-28
> **glennric said:**
>  Edit:  By the way you may have to do a little more to use WPA.

Have you been successful in getting WPA up? What does the "little more"
entail?

Thanks!

---

### Post by mikesbo on 2008-07-01
I've read the first couple of pages in this thread and saw someone post the driver for Dapper or Edgy, or one of those older distributions, so:

I'm not a hard-core linux guy, just a user, so could I beg one of you guys who've gone through the trouble of recompiling the kernel to build the driver for the truemobile 1150 NIC so as to support WPA, to post the resulting driver here (with whatever Agere, I think it was, copyright information is needed) with instructions for installation?

Linux/Unix commands, etc. are fine for me, it's the setup to recompile the kernel I'm not up for.

I'm hoping one of you has done this and has it lying around, and it won't be any more effort than just posting it.

Thanks

---

### Post by jbruder on 2008-07-01
> **mikesbo said:**
> I've read the first couple of pages in this thread and saw someone post the driver for Dapper or Edgy, or one of those older distributions, so:

I'm not a hard-core linux guy, just a user, so could I beg one of you guys who've gone through the trouble of recompiling the kernel to build the driver for the truemobile 1150 NIC so as to support WPA, to post the resulting driver here (with whatever Agere, I think it was, copyright information is needed) with instructions for installation?

Linux/Unix commands, etc. are fine for me, it's the setup to recompile the kernel I'm not up for.

I'm hoping one of you has done this and has it lying around, and it won't be any more effort than just posting it.

Thanks

Mike, go back to page 11 - it has a comprehensive walk-through with step-by-step commands for hardy. I don't have much compilation experience, and it was pretty straightforward. Of course, it doesn't work for me, but as far as I can tell it's only because I'm working with PowerPC and an airport card. Most x86 users seem to have had success.

---

### Post by mikesbo on 2008-07-01
Wow, it worked for me.  Thanks to davemiles871 for summarizing all of it (I've tagged the post), and to jbruder for reading all 12 pages...

It was the multi-hour kernel compile I was worried about, and it wasn't needed after all.  My C840 is now up and running with WPA.

Next is the nvidia graphics driver...

---

### Post by doofusdog on 2008-07-12
great! it goes!

first tried the deb file, but of course my kernel was slightly different

but the building the module as on page 11 did the trick, very fast to do even on this slightly slow laptop

this with mini-pci module in a toshiba a100

save me from taking the easy boring option and loading XP

thanks guys!

---

