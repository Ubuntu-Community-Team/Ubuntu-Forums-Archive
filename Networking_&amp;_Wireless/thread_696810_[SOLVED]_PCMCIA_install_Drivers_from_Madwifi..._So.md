---
title: "[SOLVED] PCMCIA install Drivers from Madwifi... So frustrating for new user"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by fourstringin on 2008-02-14
So new to ubuntu and all i need is my PCMCIA wifi card (supported) to work. I got as far as finding that Madwifi driver wil work my card but there is no straight up new guy print telling me how to load the driver. 

I did read alot but there is so much terminal talk and jumping around and no explaination that I get lost reading throught the steps and forget what the point of the few steps or processes before it was.

I have the file extracted from mad wifi and in a folder by itself. now i need to get it in the system somehow. i plug in the card and i dont even get an unknow hardware indicator to even try to push a driver on it.

Man ububtu is hard even after reading all the sticky's (which can be so much i forget what the thread is even about when im through with it.)

Just want to install the driver. :(

---

### Post by dca on 2008-02-14
Depending on what the card type (manf & chipset) is, if it's recognized in Ubuntu 7.10, after installation and reboot, it should give a pop-up message from the tray indicating that 'Restricted Drivers' are in use.  When you click and open it should reference 'Atheros Hardware Abstraction Layer' and have a checkbox and indication if it's in use or not.  The location of 'Restricted Drivers' is in the 'System -> Administration' menu...

---

### Post by fourstringin on 2008-02-14
I dont get a thing from Ububtu. No recognition indication at all.

---

### Post by dca on 2008-02-14
Can you post the output from the command 'lspcmcia' into a reply?

---

### Post by fourstringin on 2008-02-14
wow im going to need the whole line. I just found the terminal today. (be great if people called it that, might not have taken digging to figure that out)

So I need to know what to type into the terminal. Then ill post the output.

---

### Post by dca on 2008-02-14
lspcmcia
 
it's a lowercase L

---

### Post by fourstringin on 2008-02-14
Ok when i type it i gert this

Socket 0 Bridge:              [yenta_cardbus]          (bus ID: 0000:00:0a.0)
    CardBus card - - see "lspci" for more information
Socket 1 Bridge:              [yenta_cardbus]          (bus ID: 0000:00:0a.1)

So does any of this mean it sees the card?

---

### Post by dca on 2008-02-14
...now type in lspci and post.... make sure the device in question is connected...

---

### Post by fourstringin on 2008-02-14
ok it gave me tons of information too much to type out.  I think it sees it though. 

I see some 802.11 stuff in there so im guessing it knows it there. 

So since it sees it how can i get it to work?
I have the madwifi files

---

### Post by dca on 2008-02-14
The problem is everyone viewing these posts don't know what it is.  Being PCMCIA makes it a little difficult for me but by looking at the card we get the manufacture name, looking at the results of lspci tell us the chipset used inside to see if the version actually is compatible using MadWifi (for Atheros chipsets) or not...

---

### Post by dca on 2008-02-14
...not to mention that if you go into the 'Restricted Drivers' portion it doesn't reference MadWifi drivers in use or enabled isn't good either.

---

### Post by fourstringin on 2008-02-14
ok well here is what i got back when i typed lspci

the relevant part i think because doing the same lspci without the card in does not bring up this line says:

Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)


Now my card is D-Link AirPlus G
Model DWL-G630
H/W Ver :A1 F/W Ver. :2.2.0.11

Looking it up it says its compatable just needs the driver from Madwifi
So i downloaded it. Just need to install it if im correct in sayign this works with Linix

---

### Post by fourstringin on 2008-02-14
> **dca said:**
> ...not to mention that if you go into the 'Restricted Drivers' portion it doesn't reference MadWifi drivers in use or enabled isn't good either.

Im not to sure what you mean here
it doesn't reference MadWifi drivers in use or enabled isn't good either?

---

### Post by dca on 2008-02-14
This is the easiest way I know to install Ubuntu MadWifi.  Open terminal, type uname -r and write down what it says.  Go into Synaptic Package Manager, click search and type in window 'madwifi'.  It should bring up somewhere in the list linux-restricted-modules-2.6.22-14-generic (or whatever the last part is matching uname -r command:  generic, 386, server, etc).  You'll notice in the description along w/ nvidia stuff, it includes MadWifi.
 
We may want to get add'l help on this because I never bothered installing latest vers of MadWifi release direct from their site because I've always used the ones provided w/ the distro assuming they were tested and known to work.

---

### Post by dca on 2008-02-14
> **fourstringin said:**
> Im not to sure what you mean here
it doesn't reference MadWifi drivers in use or enabled isn't good either?

If the hardware was there during installation and Ubuntu detects it, when you restart the computer the balloon pops up warning you that restricted drivers (such as MadWifi) are in use.

---

### Post by fourstringin on 2008-02-14
This version run ok on my system but i think i may switch to Xubuntu. Would I go through the same process? To get the drivers working or does Xubuntu not have fully whats normal Ububtu has?

---

### Post by fourstringin on 2008-02-15
ok i reinstalled the madwifi from the disk like it asked. Then i Restarted but still not seeing that i have a wireless PCMCIA card attached. Something else I needed to do? Please dont take anything for granted if this was windows i would just need a couple coach words adn the rest would fall in place but in this i need to be told step by little step untill i catch on.

Thanks guys this is helping im learning, slowly but im seeing the light.

---

### Post by fourstringin on 2008-02-15
Ok i found this file in the Madwifi... Needless to say its all egyptian to me. I really read and and tried to understand it but try to see this from my point of view. I know Windows period. This kinda hinders me because I;m not sure what all this is saying. 

Check out what the read me says and if you can maybe add to it and reverse a couple steps to tell me what i need to do that would help alot.


THIS IS WHAT THE INSTALL FILE FROM MADWIFI SAYS:


MADWIFI: Multimode Atheros Driver for WiFi on Linux (VAP branch)
================================================================

* Copyright (c) 2002-2005 Sam Leffler.  All rights reserved.

Read the file COPYRIGHT for the complete copyright.


Requirements
------------

- Configured kernel sources of the target kernel.  Some Linux
  distributions provide headers, makefiles and configuration data - it
  should suffice.

- Wireless Extensions support (14 or later, 17 preferred) - option
  CONFIG_NET_RADIO in kernel .config file.

- Sysctl support - option CONFIG_SYSCTL in kernel .config file.

- Crypto API support - option CONFIG_CRYPTO in kernel .config file (AES
  support is used if present, otherwise the AES-CCMP cipher module falls
  back to a private implementation).

- gcc of same version that was used to compile the kernel.  At least
  make sure that the first two version numbers or the compiler are the
  same (e.g. it's OK to use gcc 3.4.6 to compile MadWifi if the kernel
  was compiled by gcc 3.4.2).  Ignoring this rule will cause "Invalid
  module format" errors during module load.

Linux 2.4.x kernels starting with 2.4.22 and 2.6 kernels should work
without problems.  Due to quick pace of Linux development, there is no
way compatibility with the future 2.6 kernels can be ensured.  However,
the latest 2.6 kernel at the time of the release should be expected to
work.

Automatic module loading support (CONFIG_KMOD) is recommended; otherwise, 
care will have to be taken to manually load needed modules.

Building the driver
-------------------

The driver is built using the Linux kernel build mechanism.  This means
you must have some part of the kernel source distribution installed on
the machine where you want to build the driver.  In particular, the
kernel include files, makefiles, build scripts and configuration must be
available.

This will be present if you built your kernel from source.  Otherwise
you may need to install an additional kernel development package from
your distribution that would match your kernel.  For example, the
development package for the default kernel is called linux-headers on
Debian and kernel-devel on Fedora Core.  Installing a package with full
kernel sources should not be generally necessary.

Note: in the following examples "$" stands for your system prompt;
you're not expected to type that as part of the actual command.  "#"
stands for the command prompt when the commands must be executed by
root.

Most people can just type:

  $ make

in the top-level MadWifi source directory to build all the modules for
the currently running system.

You MUST do a "make clean" before compiling for a different version of
Linux, e.g. building for 2.6 after building for 2.4.

If you want to compile MadWifi for a different kernel, you need to
specify the location of the kernel build tree, e.g.:

  $ make KERNELPATH=/usr/src/linux-2.6.3

Note that you can also specify this path by setting an environment
variable; e.g.

  $ export KERNELPATH=/usr/src/linux-2.6.3
  $ make

If the kernel was built outside the source directory, KERNELPATH should
point to the output directory where .config is located, not to the
sources.

MadWifi currently provides four different rate control algorithms,
ONOE, AMRR, SAMPLE and MINSTREL.  SAMPLE and MINSTREL are both very
advanced, but MINSTREL is quite new.  Consequently, SAMPLE is used by
default.  In order to make MadWifi use e.g. AMRR instead, you have to
specify that as the module parameter e.g.

  # modprobe ath_pci ratectl=amrr

NOTE: Changing the rate control is only required (and recommended) for
      users who want to setup an access point using MadWifi in difficult
      (e.g. lossy) environments and who know what they are doing.

This distribution includes support for a variety of target platforms.
Because of the binary nature of the HAL not all platforms are supported
(the list grows as time permits).  The supported target platforms can be
found with:

  $ ls hal/public/*.inc

A target specifies the CPU architecture, byte order (unless implied by
the CPU), and the ABI/file format.  For most popular platforms, the
build system will find the appropriate files.  When cross-compiling or
compiling for less common platforms, the target platform may need to be
specified using the TARGET variable, e.g:

  $ make TARGET=armv4-le-elf

Consult the contents of the .inc file to find out what the target
platform is and what toolchain was used to build the HAL object module. 
Beware of mixing toolchains; some target platforms require that the HAL
and driver be built with the same toolchain (i.e. compiler, assembler,
and linker) and the same compiler flags.  If you get warnings about
incompatible compiler flags, chances are that you are compiling for a
wrong target or using an incompatible compiler.


Cross-compiling
---------------

The build system is designed to support cross-compiling without any
modification to the distribution files.  It should be sufficient to
specify any parameters on the make command line.

In most cases, only KERNELPATH and CROSS_COMPILE need to be defined. 
CROSS_COMPILE is the prefix for cross-compiling tools.  For instance, if
the cross compiler is called arm-linux-gcc, set CROSS_COMPILE to
"arm-linux-":

  $ make KERNELPATH=/usr/src/linux-arm CROSS_COMPILE=arm-linux-

The build system determines ARCH and TARGET based on the .config file in
the Linux build tree.  TARGET still may need to be provided on the
command line some uncommon systems.  If ARCH is determined incorrectly,
please report it.


Loading the modules
-------------------

Building the software will generate numerous loadable modules:

  ath_pci		Atheros driver for PCI/Cardbus devices
  ath_hal		Atheros HAL
  wlan			802.11 support layer
  wlan_wep		WEP cipher support
  wlan_tkip		TKIP cipher support
  wlan_ccmp		AES-CCMP cipher support
  wlan_xauth		external authenticator
  wlan_acl		MAC ACL support for AP operation
  wlan_scan_ap		AP scanning support
  wlan_scan_sta		station scanning support
  ath_rate_onoe		ONOE rate control
  ath_rate_amrr		AMRR rate control
  ath_rate_sample	SAMPLE rate control

The ath_pci module must be loaded either manually or by the system, e.g.
through the hotplug or card manager support.  The remaining modules are
loaded automatically as needed, so after doing a "make install" you only
need to run following:

  # modprobe ath_pci

For automatic module loading you may need to modify your system's
configuration files so the necessary modules are loaded when an Atheros
device is recognized.  The exact procedure varies from system to system.

There are module parameters available to fit your needs, e.g. you can
set the countrycode manually if your card's EEPROM does not contain the
correct one for your location.  See
[http://www.unicode.org/onlinedat/countries.html](http://www.unicode.org/onlinedat/countries.html) to find your code.

To activate German frequencies you would specify:

  # modprobe ath_pci countrycode=276

To see all available module parameters type:

  $ modinfo ath_pci


Integrating into the kernel sources
-----------------------------------

It is also possible to patch Linux kernel sources to integrate MadWifi
directly into the kernel tree.  This allows building MadWifi as part of
the kernel.  This could be useful for embedded systems that don't
support loadable modules.  Please refer to patches/README for details.


Further information
-------------------

Further information on how to work with the driver can be found in the
file README.  In addition, the project's wiki has a lot of valuable
information:

[http://madwifi.org/](http://madwifi.org/)

---

### Post by Junglizer on 2008-02-15
I don't know anything about the Atheros Restricted drivers, but...

Here's the rundown on how I would get the madwifi drivers working, I believe they are in the package tree but I've never done it that way, and the following method should work regardless of the OS. This is compiling from source and installation/configuration is all done from the command line.

Download the current release of the madwifi drivers [http://downloads.sourceforge.net/madwifi/madwifi-0.9.3.3.tar.gz]("http://downloads.sourceforge.net/madwifi/madwifi-0.9.3.3.tar.gz"), thats the source.

Extract them and enter the newly created directory.
```

tar xvf madwifi-0.9.3.3.tar.gz
cd madwifi-0.9.3.3/

```
There should be a README or an INSTALL file, file which you can read using the less command.
```

less README

```
Pressing "q" quits from the less text viewer.
However, you can just do the following inside of the madwifi directory:
```

make clean
make
make install

```
The make process, the compile, takes about 5-10 minutes based on your system specs.
Once you've completed the 3 previous steps you can remove the directory, as all the contents have been installed in the proper locations on your system.
```

cd ..
rm -rf madwifi-0.9.3.3/

```
Using the drivers/utils:
You should now run
```

iwconfig

```
You will probably see a wifi0 device and an ath0 device. It may work right at this point, but I would recommend you start from scratch so you can see how to do this in the future.
```

wlanconfig ath0 destroy

```
This destroys the device association. We can recreate it using the following command, keep in mind that you may have to change this a bit for your system, but 9/10 times it will work just fine for most people:
```

wlanconfig ath0 create wlandev wifi0 wlanmode sta

```
We're creating an 'ath0' device to interface with the 'wifi0' kind of "front-end" if you will and we are putting it in 'sta' mode, which is the most common type. Specifically "client-server" or rather you connecting to an AP.

Now you'll want to find which AP's to connect to, so we scan for availble ones:
```

iwlist ath0 scan | more

```
Chances are pretty good taht you'll find your home AP in the list, we'll call it "homeAP" for the sake of this. So we associate with that AP.
```

iwconfig ath0 essid "homeAP"

```
Now we get a network address using DHCP.
```

dhclient ath0

```
Run ifconfig or iwconfig again to see that you correctly retrived an IP address.

You may have to edit /etc/resolv.conf based on your settings.
But that's the gist of it.

---

### Post by fourstringin on 2008-02-15
ok i got to the first step of entering the code. Well the code is shown on two lines so i tried two lines and between hit enter. I got an error so i tried to just do it all on the same line. Still got an error. 

Is there something i missing?

---

### Post by fourstringin on 2008-02-15
ok I think that your code will not work with normal Ubuntu

I tried just doing this 

(I dont know how to make the code box)

cd
rm -rf madwifi0.9.3.3/
iwconfig (then got this responce)
 lo       no wireless extrnsions
 eth0  no wireless extensons


Anythoughts on my process?

---

### Post by fourstringin on 2008-02-16
Ok completed the process and I have a walk through of getting wireless driver installed.

how to install wireless PCMCIA Driver

After looking and talking to alot of people here is the process that worked for me.

ok Step 1
go to terminal and type lspci

with the PCMCIA card in the laptop you will get an output telling you all the PCI cards in the system the wireless one will look like this

 *network UNCLAIMED
description: Ethernet controller
product: Marvell W8300 802.11 Adapter
vendor: Marvell Technology Group Ltd.
physical id:1
bus info: pci@0000:02.00.0
version: 7
width: 32 bits
clock:66 MHz
capabilities: pm cap_list
configuration: latency=0

Now that you can see the type of card you can use that to look up the WINDOWS DRIVER to use later on. 

Step 2

Download ndiswrapper This program will convert the windows driver to work on Ubuntu Linux.
Download here: [http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)

This program is kinda hard to use so also download an interface called ndisgtk that will use ndiswrapper with ease.
Download here: [http://linuxappfinder.com/package/ndisgtk](http://linuxappfinder.com/package/ndisgtk)

First install ndiswrapper. To do this just put the extracted file on your desktop.
then go to Terminal. You want to change the Directory to target the Desktop. 

Type:
 cd Desktop (note that the D is capital, case matters)

 once you see that your in Desktop then 
Type:
cd  ndiswrapper-1.52 (so you know you can hit n then tab and it will fill the rest out for you, as long as nothing else on your desktop starts with n)

now your in the folder
Type
make clean (then hit enter and wait for it to complete)
make (then wait for that to complete)
make install (after that finished it done)

Now ndiswrapper-1.52 is installed. you can delete the file from your Desktop

Step 3

Install the interface that uses ndiswrapper-1.52
Download and extract it to your desktop
inside the folder will be an easy install icon. Click it and install it.

Once it is installed you can go to System > Administration > Windows Wireless Drivers
To access the program.

Step 4 the hard part.
Now we need to find a windows driver that will work when written into Linux. Best bet is to look up the drivers from the manufactures website and get the drivers from win 98 and up. The file we will be looking for in each is the .INF file. Once you have the folder on your desktop you will need to look through it and try each driver out for your exact card (remember there are different versions for many cards so you need to make sure that even if the model number is the same the Version is also the same.) 

With the driver folder on the Desktop use the interface and add new driver. Click it and search the folders and try out each driver. 
Add one then go up to the top bar and click on the network connection. Enable wireless and then it should start working. If not try another driver untill it works. Try both right and left clicking it to see the different options. 

Note... After I removed the driver file my wireless stopped working. you will need to add the driver to a folder adn not delete it. Im not sure of the best place but just make sure once you find the right .INF file you store it in a safe place. And make sure the Windoes Wireless Drivers program knows where it is located. Once you get it workign you may need to move the file and then repeat the process of installing the driver from its new location.

Anyother questions feel free to ask me ill help you all i can. Im still new so I can understant the frustration

---

