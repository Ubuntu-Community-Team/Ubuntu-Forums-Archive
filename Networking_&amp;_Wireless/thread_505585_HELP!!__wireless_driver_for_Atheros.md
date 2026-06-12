---
title: "HELP!!  wireless driver for Atheros"
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by jdunn on 2007-07-20
Okay.  I've followed two separate methods to install drivers for my Aspire 5100.  I tried the NDISWrapper drivers and the aceracpi drivers and in both cases my Atheros controller remains unclaimed.  I get no error messages when doing a make but I'm not sure I'm doing it all correctly.  I'm using Kubuntu with kernel 2.6.20-16-generic.  Header files are installed.  Once I installed the build-essentials package, I was able to run the Makefiles without errors.  Did I do this correctly?  Why can't I pair a driver with the controller?

---

### Post by stchman on 2007-07-20
> **jdunn said:**
> Okay.  I've followed two separate methods to install drivers for my Aspire 5100.  I tried the NDISWrapper drivers and the aceracpi drivers and in both cases my Atheros controller remains unclaimed.  I get no error messages when doing a make but I'm not sure I'm doing it all correctly.  I'm using Kubuntu with kernel 2.6.20-16-generic.  Header files are installed.  Once I installed the build-essentials package, I was able to run the Makefiles without errors.  Did I do this correctly?  Why can't I pair a driver with the controller?

For the Atheros line you should just have to enable the restricted driver and it will work.  That is all I did to mine.  If not then use the madwifi drivers.

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

Hope this helps.

---

### Post by jdunn on 2007-07-20
Restricted driver?  I think you mean the restricted modules.  I'm using Kubuntu 7.04.  Therefore, I'm not using Synaptic package manager...rather, I'm using Adept.

---

### Post by kevdog on 2007-07-20
Ok try this, it not adept

First determine your kernel version:

uname -r

This is the key to the whole process.

Then search for the madwifi drivers from repository:

sudo apt-cache search madwifi

There will be about 10 files listed with the search.  The key is to install the package beginning with:
linux-restricted-xxxxxxxx
and ending with your kernel version.

Unfortunately you will have to type(OK its a drag) one of the packages listed in the list, so to install its:
sudo aptitude install linux-restricted-.....................

I think you get the idea.  This will install the madwifi driver for your atheros card.  Reboot and then see how it goes!

---

### Post by jdunn on 2007-07-20
No.
The restricted module for my kernel is already installed.  I'm using 2.6.20-16-generic.
'sudo apt-cache search madwifi' indicates restricted modules for my kernel that support madwifi exist.
A look in adept indicates that the restricted modules for my kernel are already installed.
 
There is no driver associated with my Atheros controller.

---

### Post by kevdog on 2007-07-20
Can you list the following

lspci -nn
lshw -C network

Something seems funny!

sudo apt-cache is a search for all possible packages -- it lists installed and uninstalled packages
I believe sudo aptitude search -- searches only installed packages

Once finding the package with apt-cache, just try installing it with aptitude install.

---

### Post by jdunn on 2007-07-20
I just re-installed Kubuntu 7.04.  The install is fresh so I can start from scratch on this driver issue.
Please tell me what I need to do.

---

### Post by jdunn on 2007-07-20
jdunn@jdunn-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:05.0 PCI bridge [0604]: ATI Technologies Inc Unknown device [1002:5a37]
00:12.0 IDE interface [0101]: ATI Technologies Inc ATI 4379 Serial ATA Controller [1002:4379] (rev 80)
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 83)
00:14.1 IDE interface [0101]: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI [1002:4376] (rev 80)
00:14.2 Audio device [0403]: ATI Technologies Inc SB450 HDA Audio [1002:437b] (rev 01)
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
02:00.0 Ethernet controller [0200]: Atheros Communications, Inc. Unknown device [168c:001c] (rev 01)
06:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
06:04.0 CardBus bridge [0607]: ENE Technology Inc CB-712/4 Cardbus Controller [1524:1412] (rev 10)
06:04.1 FLASH memory [0501]: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller [1524:0530] (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller [1524:0550] (rev 01)
06:04.3 FLASH memory [0501]: ENE Technology Inc FLASH memory: ENE Technology Inc: [1524:0520] (rev 01)
06:04.4 FLASH memory [0501]: ENE Technology Inc Unknown device [1524:0551] (rev 01)



jdunn@jdunn-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED
       description: Ethernet controller
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: iomemory:54000000-5400ffff irq:19
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@06:01.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:ce:d7:e1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.15.150 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:a000-a0ff iomemory:b0300000-b03000ff irq:21

---

### Post by damir_1105 on 2007-07-20
try:

$ lsmod | grep ath_pci

and you will see if the modul is loaded, if not try

$ sudo modprobe ath_pci    

if is error, give us output. Sorry for bad English. :)

---

### Post by jdunn on 2007-07-20
lsmod | grep ath_pci
ath_pci                97312  0
wlan                  204484  1 ath_pci
ath_hal               192592  1 ath_pci

no error with 'sudo modprobe ath_pci'

lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED
       description: Ethernet controller
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: iomemory:54000000-5400ffff irq:19
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@06:01.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:ce:d7:e1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.15.150 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:a000-a0ff iomemory:b0300000-b03000ff irq:21

---

### Post by damir_1105 on 2007-07-20
try: 

$ iwconfig

give us output

if you don't have this tool:

$ sudo apt-get install wireless-tools

---

### Post by jdunn on 2007-07-20
wireless-tools package is installed.

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by kevdog on 2007-07-20
Did you install the restricted drivers again??

If you did, try
sudo modinfo ath_pci

sudo modprobe -v ath_pci

I see the card is currently unclaimed.

---

### Post by jdunn on 2007-07-21
filename:       /lib/modules/2.6.20-16-generic/madwifi/ath_pci.ko
license:        Dual BSD/GPL
version:        0.9.3.1
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     D33427613CC54A874D9A746
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.20-16-generic SMP mod_unload 586
parm:           countrycode:Override default country code (int)
parm:           outdoor:Enable/disable outdoor use (int)
parm:           xchanmode:Enable/disable extended channel mode (int)
parm:           rfkill:Enable/disable RFKILL capability (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|onoe|sample], defaults to 'sample' (charp)
parm:           ath_debug:Load-time debug output enable (int)


no errors with sudo modprobe -v ath_pci

the controller is still unclaimed.

---

### Post by kevdog on 2007-07-21
Thanks for hanging in there.  I can see your having a problem.  Well I thought the restricted drivers would work but obviously thats not going to happen from what you are giving me.

One problem is that I looked directly both on the ndiswrapper and madwifi websites directly, and on either site, nothing is mentioned about your support for your type of card.

We could try either method, because either method is going to be "experimental".  Do you know anything else about your wireless card???  Do you have Windows XP drivers??? Do you have any other type of internet connection -- such as a wired ethernet connection for the computer or a different computer with a connection that you can transfer some file via USB stick??

---

### Post by jdunn on 2007-07-21
Thanks Kevdog and others who've replied and have attempted to solve this problem.  I haven't given up yet but, I am starting to consider rpurchasing a separate wireless lan card for the laptop.

I do have WinXP drivers that are supposedly for this Atheros controller.  I downloaded it from the Acer website.  It was in a list of WinXP drivers for my particular notebook...However, the list shows that the driver is supported for a different model notebook.  Acer seems to have much better support for its Vista drivers...but, this notebook came with Vista pre-installed and I HATED IT.

I do have a wired ethernet connection on the notebook that I'm using now and it works fine.  I also have a USB stick that I use to transfer files (also works fine on the notebook).  Why do you ask?  I still need wireless ethernet.  I use the notebook at home on my wired connection but I also use it in class at a local university where only wireless is available.

My specific notebook is the Aspire 5100-3357.  I have yet to find information showing specifically what Atheros controller is used on my notebook.  Someone else in the forums made a short guide explaining how he got wireless to work on his Aspire 5100 using the NDISWrapper.  I tried his guide but It didn't work for me.  :(

[http://ubuntuforums.org/showthread.php?t=490800](http://ubuntuforums.org/showthread.php?t=490800)

---

### Post by kevdog on 2007-07-21
I saw your other post, but before running out and getting another card, lets just try a few things first.  Nothing to lose at this point.

I know that you installed ndiswrapper -- but how do you install it??? I want you to compile and install it from source.  That means if you used synaptic or someother  method (apt, aptitude), I need you to uninstall it via the very same method.

First there are a few things you need to do to compile from source -- install the build-essential package along with the linux header files.  Here is how to do this in case you dont have an internet conneciton:

```
If you already have an internet connection (ie a working wired ethernet connection), 
please skip to step #4. Without any internet connection, please begin at step #1.

All commands typed at command prompt:

   1. After booting into Ubuntu, put the Ubuntu installation CD in drive and wait for it to "spin up"
   2. sudo apt-cdrom add
   3. sudo aptitude update
   4. sudo aptitude install build-essential linux-headers-`uname -r`
```


Ok, next grab the ndiswrapper source files from: _[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)_
You want ndiswrapper-1.47

Working at command line
```
cd ~
mkdir ndiswrapper
cd ndiswrapper 
Place the ndiswrapper-1.47.tar.gz inside this ~/ndiswrapper

```
To proceed
```
tar -zxvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
make distclean
make
sudo make install
```

Verify installation with
```
ndiswrapper -v
```
I cant remember the exact output but make sure you dont get any errors.

Next create and place your Windows XP wireless driver into ~/driver:
```
cd ~
mkdir driver
cd driver
```

Ensuring the ***.sys and ***.inf file for the WinXP driver are in the~/driver directory:
```
sudo ndiswrapper -i *****.inf
```

Verify installation with:
```
ndiswrapper -l
```
Make sure no errors are reported and you get something like:
> 
bcmwl5: driver installed
device (14E4:4320) present 


Ok, to insert the ndiswrapper module into the linux kernel:
```
sudo depmod -a
```

Ensure you dont get any errors when running this command.  Then:
```
sudo modprobe ndiswrapper
```

To verify there wasnt any errors:
```
dmesg
```
and look for something like:
> ndiswrapper version *version* loaded

Next lets make an alias for wlan0 associated with ndiswrapper
```
sudo ndiswrapper -m
```

And ensure that the ndiswrapper module is loaded at boot:
```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

I recommend rebooting at this time.
```
sudo shutdown -r now
```

Additional modifications may be needed to your /etc/network/interfaces and /etc/iftab files, since the wireless interface we are know using is going to be known as wlan0, and not eth0, eth1, ath0, etc.  Im not sure how your previous setup was configured, hence possibly the need to further alter these files.  I also recommend that you turn off any router encryption (WEP,WPA), and any MAC filtering at the router for the time being until we can verify basic connectivity.  We can build these complexities into the setup once everything is up and running.

---

### Post by damir_1105 on 2007-07-21
I take this from [www.madwifi.org:](www.madwifi.org:)

Possible workaround for problems with mini-PCI cards ¶

Many laptops which have mini-pci wireless cards provide a means to switch the radio of the card on and off. Many mini-pci cards respond to a signal on “Pin 13” which controls this function.

If your radio is stuck ‘off’, you will be able to load the madwifi driver correctly, but it won’t find any access points or peers when making scans.

Firstly check the laptop bios settings to ensure that there isn’t a “Disable Radio” or “Disable mini-pci” option selected.

Unfortunatly for us linux users, some laptops operate this mechanism purely in software drivers, requiring either an equivalant linux driver (see [http://rfswitch.sourceforge.net/](http://rfswitch.sourceforge.net/)), or to use the NDIS-Wrapper drivers. In some cases, simply getting “ACPI” working may be enough to make appropriate hot-keys turn the radio on / off.

For laptops which don’t have an appropriate driver, you can also control the RF kill feature (on Atheros cards) with a module option:

**modprobe ath_pci rfkill=0**

This way your wireless card should ignore the state of pin 13.

---

### Post by kevdog on 2007-07-21
Good find -- did it work???

---

### Post by jdunn on 2007-07-21
My laptop has a button and indicator on the front that enables/disables the wireless radio for the integrated wireless controller.  I make sure the indicator is always on.  I haven't checked for a wireless setting in the BIOS but I had Vista on this laptop previously with wireless working.

---

### Post by jdunn on 2007-07-21
Kevdog,
These are way too many steps considering I'm also getting instructions from other threads for installing different drivers (madwifi and aceracpi).  Also,  this is all experimental.  I need a solution by the end of the weekend.

---

### Post by jdunn on 2007-07-21
I'm giving up.  Chances are only slight I will have a working driver from trying any of these solutions.  Chances are likely I'll trash the kernel/applications and have to make a complete reinstall of Kubuntu from scratch.  Someone in another thread suggested I install Synaptic...I tried it and stopped right there because I've heard of too many people trashing their Kubuntu installs running Synaptic.  Furthermore, my time is limited.  a wireless card that works out of the box is the way to go.  Now, I just need advice on choosing one.  If there is none that works out of the box, then I'm SOL with a useless laptop that I can't return.

---

### Post by damir_1105 on 2007-07-21
Users' Laptops confirmed as needing workarounds 
Fujitsu S2020 

    * Sellotape over pin 13 causes radio to work. - Switch on back had no effect.
    * Another user from Malaysia - Yup, follow the steps above covering dat Pin 7(if u see it from only one side). My Askey branded mini pci that uses Atheros AR5005 chipset works after doing that. However, take note that the mini pci wifi card sucks up battery power as it has been permanently enabled.
    * (Note from another user: Strange. My Fujitsu S2020 works fine without any tricks like this. Just make sure that the hardware radio on/off switch on the back of the notebook is set to the “on” position… This is with a “Garlic” model S2020, I guess others might be different but I thought that the others had Broadcomm wireless cards.) 

Toshiba Satellite 1905-S303 

    * with an Askey/Toshiba AR5212 mini-pci card. The radio on/off switch has no effect. 

Toshiba Satellite 2430-S101 

    * with an Intel Pro/Wireless 2200 b/g mini-pci card. The radio on/off switch has no effect. 

Toshiba Satellite 1905-S301 

    * with an Askey/Toshiba AR5001X and Intel PRO/Wireless 2100 mini-pci card. 

Toshiba Tecra 9100 

    * with an Agere Systems MPC13A-20/R; the radio on/off switch has no effect. 

Routerboard18 PCI-2-8xMiniPCI 

    * The rfkill option works for the routerboard18 - without it only the cards will be detected but no wave will come out. Steffen D. 

Fujitsu Siemens Amilo L1310G with Atheros AR5005G 802.11abg NIC (rev 01) 

    * The rfkill option worked just fine. The enable/disable button works only in windows with the appropriate software. 

Toshiba Satellite P25-507 with AR5211 802.11ab NIC (rev 01) 

    * Needs kernel parameter 'pci=assign-busses' at boot time in order to see miniPCI behind a 'transparent PCI bridge'
    * Put a line 'options ath-pci rfkill=0' in /etc/modprobe.d/madwifi
    * Actual Atheros chipset seems to be AR5001X+, which has AR5211 as one of three chips.
    * Tested on Debian Sarge with custom kernel 2.6.19.1 

Toshiba Satellite 1130 with Broadcom 802.11b NIC 

    * Pin 13 trick did the job. Now I can finally throw away the POS usb wireless I was using. 

ACER TravelMate 8006LMi 

rfkill just did the job. Tested on Ubuntu 6.10. by Herakles
Toshiba Satellite Pro A30 

The sellotape over pin 13 trick worked for my Intel Pro/Wireless 2100bg card but unfortunately the range is greatly reduced for some reason. This card works fine with full range capabibities in my newer laptop! - gktechnology

---

### Post by kevdog on 2007-07-22
Sorry I couldnt help you, but if you try the ndiswrapper thing it would only take at most 20 minutes to see if it would work or not.  There really wasnt that many steps, and I basically gave you a cookie-cutter method how to do everything.  And yes Synaptic works with Kubuntu.  If you are worried about something try Adept which is the Kubuntu equivalent.  Anyway I didnt tell you to do anything with Synaptic or Adept. 

If ndiswrapper doesnt work the game plan would be to compile the madwifi drivers from scratch.  I helped someone about 1 week ago, and after trying somethings, she used ndiswrapper to get everything up and running!

---

### Post by rojanu on 2007-07-22
I have posted [here]("http://ubuntuforums.org/showthread.php?t=498923&highlight=ar5005g&page=2")but I realised that it was marked solved without any proper solution

I have installed everything and was working OK but one day I can't remember what I did wifi stopped working now ath_pci module is loaded but there is no wireless device created for some reason
```
modinfo ath_pci
filename:       /lib/modules/2.6.22-8-generic/madwifi/ath_pci.ko
license:        Dual BSD/GPL
version:        0.9.3.1
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     D33427613CC54A874D9A746
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.22-8-generic SMP mod_unload 586 
parm:           countrycode:Override default country code (int)
parm:           outdoor:Enable/disable outdoor use (int)
parm:           xchanmode:Enable/disable extended channel mode (int)
parm:           rfkill:Enable/disable RFKILL capability (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|onoe|sample], defaults to 'sample' (charp)
parm:           ath_debug:Load-time debug output enable (int)
```
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```
```
 lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
08:01.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
08:01.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)
08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
08:04.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
```
```
 dmesg | grep -i ath
[   38.929995] ath_hal: module license 'Proprietary' taints kernel.
[   38.932465] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   39.068091] ath_pci: 0.9.4.5 (0.9.3.1)
```
```
sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:08:02.0
       logical name: eth0
       version: 10
       serial: 00:16:36:a1:43:c5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.100 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: AR5005G 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 4
       bus info: pci@0000:08:04.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
```any ideas?

---

### Post by jdunn on 2007-07-22
Is someone trying to hijack this thread?  Rojanu, I'd appreciate it if you'd post your problems in a seperate thread.

Kevdog,
I decided to try and give it another go.  I followed your directions up to dmesg and here are my results:

[ 4489.944000] sdb: Mode Sense: 03 00 00 00
[ 4489.944000] sdb: assuming drive cache: write through
[ 4489.968000] SCSI device sdb: 498432 512-byte hdwr sectors (255 MB)
[ 4489.976000] sdb: Write Protect is off
[ 4489.976000] sdb: Mode Sense: 03 00 00 00
[ 4489.976000] sdb: assuming drive cache: write through
[ 4489.976000]  sdb: sdb1
[ 4489.984000] sd 2:0:0:0: Attached scsi removable disk sdb
[ 4489.984000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[ 4552.016000] usb 1-3: USB disconnect, address 4
[ 7110.408000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[ 7110.436000] ndiswrapper: driver net5211 (,01/20/2006,4.2.2.7) loaded
[ 7110.440000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[ 7110.440000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 19
[ 7110.440000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[ 7110.440000] ndiswrapper (NdisWriteErrorLogEntry:231): log: C0001389, count: 4, return_address: f0e125d4
[ 7110.440000] ndiswrapper (NdisWriteErrorLogEntry:234): code: 0xd3f247c8
[ 7110.440000] ndiswrapper (NdisWriteErrorLogEntry:234): code: 0x28
[ 7110.440000] ndiswrapper (NdisWriteErrorLogEntry:234): code: 0xf0d3d000
[ 7110.440000] ndiswrapper (NdisWriteErrorLogEntry:234): code: 0xf0d3d000
[ 7110.444000] ndiswrapper (miniport_init:275): couldn't initialize device: C000009A
[ 7110.444000] ndiswrapper (pnp_start_device:426): Windows driver couldn't initialize the device (C0000001)
[ 7110.444000] unregister_netdevice: device eth%d/d3f24000 never was registered
[ 7110.444000] ndiswrapper (miniport_halt:339): device d3f24400 is not initialized - not halting
[ 7110.444000] ndiswrapper: device eth%d removed
[ 7110.444000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[ 7110.444000] ndiswrapper: probe of 0000:02:00.0 failed with error -22
[ 7110.460000] usbcore: registered new interface driver ndiswrapper

---

### Post by jdunn on 2007-07-22
Okay, Kevdog.  I followed all your instructions.  Still no luck.

lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED
       description: Ethernet controller
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: iomemory:54000000-5400ffff irq:18
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@06:01.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:ce:d7:e1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.15.150 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:a000-a0ff iomemory:b0300000-b03000ff irq:19

---

### Post by rojanu on 2007-07-22
No one is trying to hijack anything and if you had spent some time and enough attention you would have noticed that our problems are the same thing and a step further what I am adding is, that the card was working now is not suggesting that somewhere in the update procedure either kernel and/or madwifi has changed thats why the wifi card remains unclaimed eventhough ath_pci module is loaded, which probably means it is not the correct module for the card,

And I must add that no one owns the posts as long as posted material is relevant anyone can post to any thread,  besides your method of posting two posts one after other should not be used as you can actually edit your preious post.

---

### Post by jdunn on 2007-07-22
Kevdog, 
btw, when I tried ndiswrapper previously, I used 'make' rather than downloading from the package installer.
I had followed these directions:

[http://ubuntuforums.org/showthread.php?t=490800&highlight=aspire+5100](http://ubuntuforums.org/showthread.php?t=490800&highlight=aspire+5100)

---

### Post by jdunn on 2007-07-22
here is where I got the WinXP driver.  My notbook PC is an Acer Aspire 5100-3357

[http://www.acerpanam.com/synapse/forms/portal20.cfm?recordid=3436&formid=3394&website=AcerPanAm.com&siteid=7117&words=all&keywords=&areaid=2](http://www.acerpanam.com/synapse/forms/portal20.cfm?recordid=3436&formid=3394&website=AcerPanAm.com&siteid=7117&words=all&keywords=&areaid=2)

---

### Post by rojanu on 2007-07-22
OK, here is what I did to solve my problem hopefully it will help you too.

First I read some where on the web that
```
wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
```sometimes happens because the wireless switch is not on and driver tries to turn the wifi card on.

then installed the acerhk from [http://kanotix.com/files/debian/pool/main/a/acerhk/]("http://kanotix.com/files/debian/pool/main/a/acerhk/")
then did ```
sudo modprobe acerhk
sudo echo "on" > /proc/driver/acerhk/wirelessled
sudo rmmod ath_pci
sudo modprobe ath_pci

```and then iwconfig shows the card now you can
```
iwlist ath0 scan
``` and it will scan wireless nets

---

### Post by jdunn on 2007-07-22
rojanu,
which did you install from kanotix?...the deb file or the tar.z which i assume has the makefiles?

---

### Post by jdunn on 2007-07-22
rojanu,
I downloaded and unpacked the tar.gzip file.  I have the appropriate kernel header files and the build-essential package installed but a 'make' on the acerhk driver terminated in errors.

sudo make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/jdunn/Downloads/acerhk-0.5.34 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/jdunn/Downloads/acerhk-0.5.34/acerhk.o
/home/jdunn/Downloads/acerhk-0.5.34/acerhk.c:38:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/jdunn/Downloads/acerhk-0.5.34/acerhk.o] Error 1
make[1]: *** [_module_/home/jdunn/Downloads/acerhk-0.5.34] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [acerhk.ko] Error 2

---

### Post by rojanu on 2007-07-22
.dep file should just install fine unless you have a 64bit system

download it and 
```
sudo dpkg -i *.dep
``` should do the trick in case if there is a problem, probably it can't find the dependencies```
sudo apt-get -f install
```should do it.

---

### Post by jdunn on 2007-07-22
*sigh*

I got the deb package installed and followed your instructions.  However...

iwlist ath0 scan
ath0      Interface doesn't support scanning.

---

### Post by jdunn on 2007-07-22
powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology MK-38 processors (version 2.00.00)
[   29.708000] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0xb
[   29.708000] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xd
[   29.708000] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xf
[   29.708000] powernow-k8:    3 : fid 0x8 (1600 MHz), vid 0x11
[   29.708000] powernow-k8:    4 : fid 0x0 (800 MHz), vid 0x18
[   33.324000] ppdev: user-space parallel port driver
[   34.084000] apm: BIOS not found.
[   34.640000] Bluetooth: Core ver 2.11
[   34.640000] NET: Registered protocol family 31
[   34.640000] Bluetooth: HCI device and connection manager initialized
[   34.640000] Bluetooth: HCI socket layer initialized
[   34.680000] Bluetooth: L2CAP ver 2.8
[   34.680000] Bluetooth: L2CAP socket layer initialized
[   34.768000] Bluetooth: RFCOMM socket layer initialized
[   34.768000] Bluetooth: RFCOMM TTY layer initialized
[   34.768000] Bluetooth: RFCOMM ver 1.8
[   66.588000] hda_codec: num_steps = 0 for NID=0x19
[   66.884000] hda-intel: Invalid position buffer, using LPIB read method instead.
[   67.440000] hda_codec: num_steps = 0 for NID=0x19
[34364.684000] input: Acer hotkey driver as /class/input/input9
[34364.688000] Acer Travelmate hotkey driver v0.5.34
[34393.856000] ath_pci: driver unloaded
[34406.352000] ath_pci: 0.9.4.5 (0.9.3.1)
[34406.352000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 18
[34406.352000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[34406.356000] wifi%d: unable to attach hardware: 'Hardware didn't respond as expected' (HAL status 3)
[34406.356000] ACPI: PCI interrupt for device 0000:02:00.0 disabled

---

### Post by jdunn on 2007-07-22
bump

---

### Post by stchman on 2007-07-23
> **jdunn said:**
> Restricted driver?  I think you mean the restricted modules.  I'm using Kubuntu 7.04.  Therefore, I'm not using Synaptic package manager...rather, I'm using Adept.

No, restricted drivers are different that restricted modules.  Restricted modules are kernel updates.  Restricted drivers are drivers that can be used with properly equipped kernels.  Restricted drivers are also closed source drivers.

---

### Post by rojanu on 2007-07-24
[QUOTE=jdunn] wifi%d: unable to attach hardware: 'Hardware didn't respond as expected' (HAL status 3)[/QUOTE]
read [http://madwifi.org/wiki/UserDocs/Troubleshooting]("http://madwifi.org/wiki/UserDocs/Troubleshooting")
 about this

---

