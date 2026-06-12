---
title: "Intel Wireless Wifi Link 5100 on Hardy"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by Revage on 2008-08-03
Hi dear community, 

i´m currently trying to Ubuntu Hardy on an Acer Aspire 5930 Laptop. 
So far, everything worked out of the box, besides the wireless adapter that seems to be a Intel Wireless Wifi Link 5100.

Though it is not listed in the supported wireless devices, i´d like to know, if there is any way to get it working. 


I already tried using the Xp driver with Ndiswrapper. It seemed to find the hardware and associated the driver with it, but though the only network interfaces showing up are eth0 and the loopback. 

No sign of a wlan0 or wireless extensions showing up in iwconfig. 

output of iwconfig 
```

lo        no wireless extensions.
eth0      no wireless extensions.
```

output of lspci
```
03:00.0 Network controller: Intel Corporation Unknown device 4232
```

output of ndiswrapper -l
```
netw5x32 : driver installed
 device (8086:4232) present
```


Anybody got an advice for me?
I´m kind of clueless by now.

Thanks in advance

Rev.

---

### Post by davedave on 2008-08-05
Hi Rev.

I'm having exactly the same problem and have posted also on the [NDISwrapper forums]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_fireboard/Itemid,34/func,view/catid,3/id,1524/#1524").

Hopefully someone will find a solution soon!

Cheers,
Dave


Edit: My laptop model# to help searchers, ASUS M51VA-AS045G

---

### Post by PMDirac on 2008-08-05
I have the exact same output as the OP, and the same wireless card, but on an Asus f8va-c1.

I'm loading the 'netw5x64' windows driver, and ndiswrapper says it's installed, and with the same 'device ... present' message as the OP.

But I don't know how to make 'wlan0' a real interface. Right now 'ifup wlan0' says 'ignoring unknown interface wlan0'.

Any help would be greatly appreciated.

---

### Post by Revage on 2008-08-06
Well, i acatually gave up on this topic or now. 

According to [Heise.de]("http://www.heise.de/open/Kernel-Log-Sicherheitskorrekturen-ohne-Neustart-2-6-26-Entwicklung-schreitet-voran--/news/meldung/107005"), the new 2.6.26 Kernel will include drivers that support the Intel Wifi Link 5000 series. 

I guess, we just have to be patient, as i wont compile a new kernel just for this.

---

### Post by superstas on 2008-08-06
I managed to install the drivers via ndiswrapper and it installs the drivers and found the hardware, but when i want to configure the network i get an error:
(network-admin:6228): Gtk-WARNING **: Unknown property: GtkComboBox.items


** (network-admin:6228): CRITICAL **: Unable to lookup session information for process '6228'

and ps aux gives me
root      6228  0.0  0.4 163376 18816 pts/0    S+   13:59   0:00 network-admin

i used these drivers
Wireless_Intel shirely peak_v12.0.0.73
they were for 64bit vista

---

### Post by PMDirac on 2008-08-09
> **superstas said:**
> 
i used these drivers
Wireless_Intel shirely peak_v12.0.0.73
they were for 64bit vista

Thanks for the info. Where did you find these drivers? I found them at this link, but couldn't download them. Maybe because of traffic. 200+MB for drivers seems a bit excessive, doesn't it?

[http://www.versiontracker.com/dyn/moreinfo/win/160272](http://www.versiontracker.com/dyn/moreinfo/win/160272)

Any other help, including any info on the drivers included in the 2.6.26 kernel would be appreciated.

---

### Post by superstas on 2008-08-10
i got them from Acer site
[ftp://ftp.work.acer-euro.com/notebook/aspire_5930/vista/Drivers/Wireless_Intel%20shirely%20peak_v12.0.0.73.zip](ftp://ftp.work.acer-euro.com/notebook/aspire_5930/vista/Drivers/Wireless_Intel%20shirely%20peak_v12.0.0.73.zip)

but still due to the network-admin bug i can`t get it to work :(

---

### Post by davedave on 2008-08-10
> **Revage said:**
> Well, i acatually gave up on this topic or now. 

According to [Heise.de]("http://www.heise.de/open/Kernel-Log-Sicherheitskorrekturen-ohne-Neustart-2-6-26-Entwicklung-schreitet-voran--/news/meldung/107005"), the new 2.6.26 Kernel will include drivers that support the Intel Wifi Link 5000 series. 

I guess, we just have to be patient, as i wont compile a new kernel just for this.

I rolled my own 2.6.26 kernel and I can confirm that using the ndiswrapper and windows driver still do not work.

In hindsight, I should have looked through the kernel configuration for a native linux driver (which is probably what you are talking about). So I might give it another go in the near future.

Cheers,
Dave

---

### Post by KimOlsen on 2008-08-13
Hey

I just got the iwl5100 working on kernel 2.6.27-rc2. But you have to enable it in the config of the kernel before you build. And also remeber to select the intel hd sound (think you have to select ALSA in order to have it show up).

You also need to have the firmware in the /lib/firmware/ directory. You can get the firmware from [http://intellinuxwireless.org/?n=Downloads]("http://intellinuxwireless.org/?n=Downloads"), and it is the iwlwifi-5000-ucode that is for the 5000 series.

After my first reboot after the kernel compile, I entered my wifi settings and it didn't work (could access the router, but not any webpages). But after rebooting once more after that it worked (why, I have no idea).

Only problem now is that I can't seem to get the nvidia 9600m gt to work with nvidia drivers.

---

### Post by Revage on 2008-08-13
Yea, I also encountered the Nvidia driver issues with the new kernel. 

By now I´m just waiting till the new kernel will be available with the updates. So long i´ll have to live without wifi. ^^

---

### Post by superstas on 2008-08-14
9600gt works fine with envy ng -> install drivers manualy and select the newest driver

---

### Post by KimOlsen on 2008-08-14
Even on the 2.6.27-rc2? Tried it without luck, but maybe I did somehting wrong.

*edit: The 9600m gt or the 9600 gt?*

---

### Post by KimOlsen on 2008-08-14
Got it working with a patched 177.13 driver described in this thread. Patch is in post #23, but please read the entire thread.
[http://www.nvnews.net/vbulletin/showthread.php?t=117209]("http://www.nvnews.net/vbulletin/showthread.php?t=117209")

So now I have an Intel Wifi Link 5100 and Nvidia 9600m gt working.

---

### Post by Joshua66 on 2008-08-23
KimOlsen, thanks for blazing a trail for Ubuntu users looking to use
the Intel 5100!  Pardon the newbie question, but what steps were involved in using the 2.6.27-RC2 kernel with Ubuntu hardy?  I ask because I'm about to get a new laptop with the Intel 5100 wireless and would like to put Ubuntu on it.  I'm willing to compile a kernel, but haven't done it before.  Many thanks for any pointers!

---

### Post by eric3_14159 on 2008-08-23
> **KimOlsen said:**
> Got it working with a patched 177.13 driver described in this thread. Patch is in post #23, but please read the entire thread.
[http://www.nvnews.net/vbulletin/showthread.php?t=117209]("http://www.nvnews.net/vbulletin/showthread.php?t=117209")

So now I have an Intel Wifi Link 5100 and Nvidia 9600m gt working.

I have an Asus g50v with those two. I haven't been able to get the wifi to work, in a 2.6.27-rc4 kernel. Could you send me your .config file for the kernel you compiled? Thanks.

---

### Post by wolframarnold on 2008-08-24
I've just bought a new Compal JHL90 (resold as PowerPro P 12:15 by powernotebooks.com), which comes with an Intel WiFi Link 5100AGN wireless adapter and an nvidia GeForce 9600M GT.

The video adapter worked with using the proprietary "nvidia" driver, which I had to set in the /etc/X11/xorg.conf.  This was quick.

The WiFi Link 51000 is giving me more headaches.  Anecdotal forum reports say that the 2.6.26 has out of the box support, but I would really like to use the Ubuntu Hardy 8.04 64 bit stock kernel.

I came across [this post by Intel]("http://lwn.net/Articles/293886/") in which they announce native support for the 5100 adapter. Kernels >= 2.6.24 can use the new support via the [compat-wireless project]("http://linuxwireless.org/en/users/Download").

I've gotten a bit further, but I seem to be stuck at the rfkill problem that's been described elsewhere.

Here are the steps I took, to get from a totally unrecognized device to a recognized device under stock Ubuntu 8.04 without a new kernel compilation:

[LIST=1]
[*]Download compat-wireless from [http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2]("http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2")
[*]Untar somewhere (I'm choosing /usr/src/) and I'm doing everything as root from here on:```
sudo su
cd /usr/src
tar xjf compat-wireless-2.6.tar.bz2
cd compat-wireless-2008-08-06
```
[*]Note, as of this writing (8/24/08), the most recent compat wireless package available was dated 8/6/08, but it does contain support for the 5100 card.
[*]Edit the config.mk file and add the following lines at the end to turn on support for the 5100 card and also for the rfkill switch:
```
CONFIG_IWL5000=y
CONFIG_IWLWIFI_RFKILL=y
```
[*]Download the firmware [iwlwifi-5000-ucode-5.4.A.11.tar.gz]("http://www.intellinuxwireless.org/?p=iwlwifi&n=downloads")
[*]```
tar xzf iwlwifi-5000-ucode-5.4.A.11.tar.gz
sudo cp iwlwifi-5000-1.ucode /lib/firmware/2.6.24-19-generic/
```
[*]```
make
make install
make load
```
This will add support for the 5100 card to the iwl4965 kernel module.  This is probably temporary and from what I read the 2.6.26 kernels already have an iwl5000 module...
[*]```
lshw -C network
  *-network DISABLED
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:73:64:e0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:55:88:02
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.8 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
```
[*]And this is where I get stuck.  The wlan0 device is not enabled.  I think this is related somehow to the hardware RF Kill switch (airplane switch) that disables wireless.  This machine has a hardware switch and a software Fn+F2 option.  Neither combination has worked for me.  Toggling the hardware switch generates errors in the syslog:
```
Aug 24 16:29:38 wta-mobile kernel: [ 1576.686265] atkbd.c: Unknown key pressed (translated set 2, code 0xf1 on isa0060/serio0).
Aug 24 16:29:38 wta-mobile kernel: [ 1576.686275] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.
```
[*]This [thread]("http://ubuntuforums.org/showthread.php?t=877789") talks about the rfkill switch, but none of the suggestions have worked for me.
[/LIST]

Any help with this is appreciated.  I haven't tried compiling a 2.6.26 kernel yet, and I'd rather not if there are other options.

---

### Post by Slipie on 2008-08-25
Thank you so much wolframarnold!
Thanks to you ive got my wireless 5100 working with hardy!

Oke so I followed your steps.
Indeed after that the device was finally reconized.
But it was still disabled.
This was because it could not load the driver

```
Aug 25 21:43:06 slipie-vaio kernel: [  342.149093] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
Aug 25 21:43:06 slipie-vaio kernel: [  342.149170] PM: Writing back config space on device 0000:05:00.0 at offset 1 (was 100002, writing 100006)
Aug 25 21:43:06 slipie-vaio firmware_helper[6847]: main: error loading '/lib/firmware/iwlwifi-5000-1.ucode' for device '/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/firmware/0000:05:00.0' with driver '(unknown)'

```

So by simply copying iwlwifi-5000-1.ucode from /lib/firmware/2.6.24-19-generic/iwlwifi-5000-ucode-5.4.A.11/ to /lib/firmware and reloading the driver it finally worked!

Thnx a lot!

---

### Post by wolframarnold on 2008-08-25
Glad this worked for you, Slipie.  I don't see the firmware load error in my syslog.

What I get is:

```
Aug 25 14:25:22 wta-mobile kernel: [  569.035589] iwl4965: START_ALIVE timeout after 4000ms.

Aug 25 14:25:24 wta-mobile NetworkManager: <info>  wlan0: Device is fully-supported using driver 'iwl4965'.
Aug 25 14:25:24 wta-mobile NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01).
Aug 25 14:25:24 wta-mobile NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start
Aug 25 14:25:24 wta-mobile NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing.
Aug 25 14:25:24 wta-mobile NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'.
Aug 25 14:25:24 wta-mobile NetworkManager: <info>  **Deactivating device wlan0.**
Aug 25 14:25:24 wta-mobile NetworkManager: <debug> [1219699524.444013] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_16_ea_73_64_e0_0').
Aug 25 14:25:25 wta-mobile kernel: [  571.649370] ACPI: PCI Interrupt 0000:0e:00.0[A] -> GSI 18 (level, low) -> IRQ 18

```

Why is the Network Manager deactivating the device???

---

### Post by Thalanix on 2008-08-25
wolframarnold: did you try without your cat5e plugged in?

I still can't get mine to work. Asus G50V. lshw -C network shows it as disabled every time I boot up, cat5e or not. What's interesting, though, is that it works just fine in single user mode.

```
iwconfig wlan0 essid my-essid
dhclient wlan0
```

```
[   46.535286] wlan0: authenticate with AP 00:1d:7e:39:##:##                                                                                  
[   46.537649] wlan0: authenticated                                                                                                           
[   46.537649] wlan0: associate with AP 00:1d:7e:39:##:##                                                                                     
[   46.539833] wlan0: RX AssocResp from 00:1d:7e:39:##:## (capab=0x401 status=0 aid=4)                                                        
[   46.539833] wlan0: associated
```

After that, I tried init 2. No go. Doesn't show disabled, so I guess that's a step in the right direction.

```
[  306.372128] iwl4965: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -5
[  306.372108] iwl4965: Radio Frequency Kill Switch is On:
[  306.372108] Kill switch must be turned off for wireless networking to work.
```

Another thing I've noticed is that the LED turns on ~13 seconds (at which you would be in single), and turns off at 29 (some time during the last few messages before, or maybe even while KDM loads up). Any suggestions would be welcome.

Edit: when lshw does show disabled, then dmesg has a different message:

```
[   28.985671] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   28.985748] PM: Writing back config space on device 0000:03:00.0 at offset 1 (was 100002, writing 100006)
[   28.985891] firmware: requesting iwlwifi-5000-1.ucode
[   30.871205] iwl4965: Radio disabled by HW RF Kill switch
[   30.871484] ACPI: PCI interrupt for device 0000:03:00.0 disabled

```

Edit 2: renaming everything 1 by 1 in /etc/rc2.d came up with the problem (for myself): S99acpi-support (renamed to K01acpi-support). There probably is a better way, but it works. For now.

---

### Post by KimOlsen on 2008-08-27
> **Joshua66 said:**
> KimOlsen, thanks for blazing a trail for Ubuntu users looking to use
the Intel 5100!  Pardon the newbie question, but what steps were involved in using the 2.6.27-RC2 kernel with Ubuntu hardy?  I ask because I'm about to get a new laptop with the Intel 5100 wireless and would like to put Ubuntu on it.  I'm willing to compile a kernel, but haven't done it before.  Many thanks for any pointers!

The easy way to build a new kernel would be to use something like [KernelCheck]("http://kcheck.sourceforge.net/") that automates most of the process. Remember to select Development under the "New Kernel Patch Options" to get the 2.6.27-rc4 (at the moment).

When the config gui starts. Remember to select the iwl options (think it is under device drivers -> wireless). Think it is at least iwlcore and iwl5000, will need to check when I get to my laptop later. And also, for sound it seems like most laptops need to check the alsa option and intel hd (even if not intel, because you get more choices when you select that).

---

### Post by KimOlsen on 2008-08-27
> **eric3_14159 said:**
> I have an Asus g50v with those two. I haven't been able to get the wifi to work, in a 2.6.27-rc4 kernel. Could you send me your .config file for the kernel you compiled? Thanks.

I'll check if I still have it later when I have my laptop available. If I still have it, it is fairly "vanilla" but a few things to get it working.

---

### Post by fayaz on 2008-08-27
That's not necessarily true. The kernel has been updated since Hardy was released. Those updates could have added support for Puma and Montevina. A quick google didn't confirm or disprove that, but I'm guessing that processor support will at least be available as of 2.6.27. Of course, Hardy is still using 2.6.24, so support may not be available in it.
----------------
Ancil

[Louisiana Alcohol Addiction Treatment](http://www.alcoholaddiction.org/louisiana)

---

### Post by KimOlsen on 2008-08-27
> **wolframarnold said:**
> 
Edit the config.mk file and add the following lines at the end to turn on support for the 5100 card and also for the rfkill switch:
```
CONFIG_IWL5000=y
CONFIG_IWLWIFI_RFKILL=y
```


Do you know if there are more config options for the compat-wireless? Is it the same as in the kernel compile config?

Hopeing to go back to the official kernel, or try out Fedora 10 or OpenSUSE 11.1 when they hit beta. (Since they  use the 2.6.27 kernel). Hope they settle for 2.6.27 in the Intrepid release.

> **wolframarnold said:**
> 
This will add support for the 5100 card to the iwl4965 kernel module. This is probably temporary and from what I read the 2.6.26 kernels already have an iwl5000 module...


Not so sure it made it to the 2.6.26 kernel, could not see any option for the iwl5000 when I tried to do a compile of the 2.6.26 kernel.

---

### Post by Persida on 2008-08-27
I have recently installed Ubuntu Hardy on a new HP DV5-1056tx laptop and am also having problems with the Intel wireless wifi link 5100 card install (although I appear to be having no problems with the nVidia 9600gt video card). 

Unfortunately, the majority of what was said in this thread, and at, [http://intellinuxwireless.org/?n=Info](http://intellinuxwireless.org/?n=Info), went straight over my head, this being my first foray into linux usage. Looks like it will be back to using Vista for me until I can figure it all out :s

---

### Post by KimOlsen on 2008-08-27
Here is my .config file for my 2.6.27-rc2

---

### Post by Persida on 2008-08-28
Well I decided to give Wolframarnolds suggestions ago. It's been a massively steep learning curve (which resulted in me having to reinstall Ubuntu because I changed the permissions on the /usr directory), but I think I've gotten something now. However, I'm stuck somewhere around these steps here;

> **wolframarnold said:**
> 
[*]Download the firmware [iwlwifi-5000-ucode-5.4.A.11.tar.gz]("http://www.intellinuxwireless.org/?p=iwlwifi&n=downloads")
[*]```
tar xzf iwlwifi-5000-ucode-5.4.A.11.tar.gz
sudo cp iwlwifi-5000-1.ucode /lib/firmware/2.6.24-19-generic/
```
[*]```
make
make install
make load
```

I've downloaded the above file fine but then I got a little confused, at first I just downloaded it to the desktop and then tried moving it into the /usr/src directory, I have no idea if it matters where it is. I managed to copy the ucode file into the stated directory, although I just extracted the file on the desktop and copied it from there, not sure if that's ok or not. 

When I try to use the "make" command I get the error message "*** No targets specified and no makefile found.  Stop." I'm not sure if I'm supposed to be in a directory or something, I've tried a few different targets doesn't seem to be working. 

So I suppose my question is where should the iwlwifi-5000-ucode-5.4.A.11.tar.gz file be saved (or does it not matter)? and what directory (or anything else) should I be in to execute the make command?

Thanks for any help, this is all very new and different to me, (but I'm trying :P)

Persida.

---

### Post by Giblet5 on 2008-08-29
> **KimOlsen said:**
> Here is my .config file for my 2.6.27-rc2


Yes, but does 2.6.27 actually work with the 5100?
What happens when you toggle the RF kill switch?
(this even breaks the Vista x64 driver...and only a power-cycle fixes it)


On 2.6.24-21 (with the compat iwl4965 module and the 5100 microcode) I can't get past that network disabled business.

That worked perfectly for one session only. As soon as I rebooted, it was dead and no tweaking or nudging will wake the thing up.

I'm considering getting a wireless express card with a proven stability record.

---

### Post by wolframarnold on 2008-08-29
> **Giblet5 said:**
> Yes, but does 2.6.27 actually work with the 5100?
What happens when you toggle the RF kill switch?

I compiled a 2.6.27-rc4 kernel from stock sources.  And I have still no wireless on my Compal JHL90 :(  The problem is still the same, the device is somehow magically deactivated; I've tried it with and without the wired connection plugged in.  I still think it's something to do with the hardware or software RF Kill Switch, but I've run out of things to try.  I'm strongly considering returning the laptop; it seems to be a bit too cutting edge for its own good.

---

### Post by wolframarnold on 2008-08-29
> **Persida said:**
> Well I decided to give Wolframarnolds suggestions ago. It's been a massively steep learning curve (which resulted in me having to reinstall Ubuntu because I changed the permissions on the /usr directory), but I think I've gotten something now. However, I'm stuck somewhere around these steps here;
Sorry, man, I didn't spell out the background that I was assuming.  Once you do "sudo su" you're super user and all files created become owned by root.  You can change file owner ship with "chown" and file permissions with "chmod".  Ask some Unix guru you know about the details for what you're trying to do.

> I've downloaded the above file fine but then I got a little confused, at first I just downloaded it to the desktop and then tried moving it into the /usr/src directory, I have no idea if it matters where it is. I managed to copy the ucode file into the stated directory, although I just extracted the file on the desktop and copied it from there, not sure if that's ok or not.
The extraction location doesn't matter; only where you copy it to.

> When I try to use the "make" command I get the error message "*** No targets specified and no makefile found.  Stop." I'm not sure if I'm supposed to be in a directory or something, I've tried a few different targets doesn't seem to be working.
Yes, you need to "cd" to the compat... source directory.  Get someone with a bit of Unix background to help you.

> 
So I suppose my question is where should the iwlwifi-5000-ucode-5.4.A.11.tar.gz file be saved (or does it not matter)? and what directory (or anything else) should I be in to execute the make command?
Doesn't really matter, all that matters is where you copy to extracted file to, see instructions.

Good luck!

---

### Post by wolframarnold on 2008-08-29
> **KimOlsen said:**
> Do you know if there are more config options for the compat-wireless? Is it the same as in the kernel compile config?

I'm not sure they are the same as in kernel config, but it's probably a safe guess.  I discovered these options by browsing some of the obvious header files (the ones named with 5000 or rfkill).  Software engineering is all about making educated guesses, most of the time...

---

### Post by KimOlsen on 2008-08-29
> **Giblet5 said:**
> Yes, but does 2.6.27 actually work with the 5100?


Answer:
> **KimOlsen said:**
> 
So now I have an Intel Wifi Link 5100 and Nvidia 9600m gt working.

And the kill switch does at least seem to work. It cuts wifi, and turns off the wifi led, and on again when I press it again.

---

### Post by KimOlsen on 2008-08-29
> **wolframarnold said:**
> I compiled a 2.6.27-rc4 kernel from stock sources.  And I have still no wireless

Did you remember to select the iwl5000 in the config? Here are the iwl part of my config.

```

CONFIG_IWLWIFI=m
CONFIG_IWLCORE=m
CONFIG_IWLWIFI_LEDS=y
CONFIG_IWLWIFI_RFKILL=y
CONFIG_IWLAGN=m
CONFIG_IWLAGN_SPECTRUM_MEASUREMENT=y
CONFIG_IWLAGN_LEDS=y
CONFIG_IWL5000=y

```

I couldn't get the compat-wireless project files to compile with
CONFIG_IWL5000=y
CONFIG_IWLWIFI_RFKILL=y
set in the config.mk file. Or any other of the options. So seems I'll be going 2.6.27 at least a bit longer.

---

### Post by wolframarnold on 2008-08-29
> **KimOlsen said:**
> Did you remember to select the iwl5000 in the config? Here are the iwl part of my config.
...

Yes, I did.  The device is being recognized but gets mysteriously disabled (see my syslog record from an earlier post in this thread).  What's your hardware, Kim?

---

### Post by KimOlsen on 2008-08-29
> **wolframarnold said:**
> ..., but I would really like to use the Ubuntu Hardy 8.04 64 bit stock kernel.


Have you tried the 32 bit version? Maybe it's only a 64 bit problem. Not easy to tell since almost everyone in this thread have not said anything about that. I'm running 32 bit.

Also one small note from an old post. Didn't check my logs at that point, so no idea if it is even related to your problems in any way.
> **KimOlsen said:**
> 
After my first reboot after the kernel compile, I entered my wifi settings and it didn't work (could access the router, but not any webpages). But after rebooting once more after that it worked (why, I have no idea).


When you ask about hardware, do you want to know the laptop model or chip-set and such?

[I]Add: Just remebered that there is also WMI for different laptops that you might have to enable in your config.
[/I]
```

CONFIG_ACER_WMI=m
CONFIG_ASUS_LAPTOP=m
CONFIG_FUJITSU_LAPTOP=m
# CONFIG_FUJITSU_LAPTOP_DEBUG is not set
# CONFIG_TC1100_WMI is not set
# CONFIG_HP_WMI is not set
CONFIG_MSI_LAPTOP=m
# CONFIG_COMPAL_LAPTOP is not set
CONFIG_SONY_LAPTOP=m
CONFIG_SONYPI_COMPAT=y
CONFIG_THINKPAD_ACPI=m
```
*So you might just need to enable the right one (probably CONFIG_COMPAL_LAPTOP in your case)*

---

### Post by wolframarnold on 2008-08-29
> **KimOlsen said:**
> Have you tried the 32 bit version?
No I haven't tried.  I'm running 64 bit.  Worth a thought, but would require a complete re-install...
> **KimOlsen said:**
> Add: Just remebered that there is also WMI for different laptops that you might have to enable in your config.
Possible.  I did download the sources for [compal-laptop]("http://eko.one.pl/index.php?page=compal-laptop") but reading the sources, this thing only provides getters and setters for the radio states that are accessed by a GUI tool.

---

### Post by KimOlsen on 2008-08-30
> **wolframarnold said:**
> 
Possible.  I did download the sources for [compal-laptop]("http://eko.one.pl/index.php?page=compal-laptop") but reading the sources, this thing only provides getters and setters for the radio states that are accessed by a GUI tool.

But if you are having trouble with the rf killswitch, give it a go. Just a recompile with one more config option enabled.

Getters and setters for radio states is kinda what you want. Since it is C it is not OO and then the getters and setters might work on the wifi hw (not variables in an object). So you can set the rfkill on the wifi card. (Or it might work in a completely different fashion, not gone into detail of how it works)

Think this might your last chance of getting it to work on 64 bit (or maybe at all). At least for now.

---

### Post by davbren on 2008-08-30
Ok as far as compilation is concerned I'm not particularly experienced, I'm having the same issues as you and have had no luck. I'm using the Samsung Q310. Unfortunately neither my ethernet or my wifi is working. I'm looking to upgrade the kernel but I have no net connection, i am dual booting vista and ubuntu so I can still use the laptop and download stuff on to the shared disk...

I have the intel link 5100 card. I have installed the firmware, I have also tried to use ndiswrapper, this says the hardware is detected but still doesn't use it. 

I really dont know how to compile or configure the kernel. Just about everything that has been said so far has gone over my head...

If someone has a way to get the Marvell Yukon ethernet that would just be a start, at least I could get some sort of internet connection...

Thank you in advance.
Dave.

---

### Post by hoc on 2008-08-30
@wolframarnold:

I also have a Compal JHL90 (not rebranded) with Intel WiFi Link 5100AGN and running Kubuntu 64bit (with KDE4). Everything installed just fine out of the box, except the gfx, wireless and hotkeys. I got gfx working by following standard procedure (restricted modules and such). Even installing compiz and emerald was a breeze. 

And following your steps I got the wireless working except for the killswitch. The hotkeys are also on my todo list, but not that important to me.

So ... thanks for the info!

[edit]Too good to be true. One reboot later and it seems I have the same problem as you. My card did work though before the reboot and before I touched the killswitch. I will look into this and post back if I fixed it.[/edit]

---

### Post by davbren on 2008-08-30
```
*-network
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
```

I thought I'd try this but mine came up differently, I've loaded the driver and everything. After the *-network it says UNCLAIMED/UNCLASSIFIED, I can't remember for the moment, I'm on my vista partition,  so its difficult to be sure :). Has anyone else seen this?

---

### Post by sumwonyuno on 2008-08-30
Hello everyone,

I guess you can add me to the list of Compal JHL90 (Sager) owners w/ disabled Intel WiFi 5100's.

I've tried Intrepid alpha 5, doesn't detect the 5100.  Due to other problems (i.e. shutdown), I've downgraded back to 64-bit Hardy.

I have a zd1211rw-based USB adapter, as a backup.  compat-wireless solved the bugginess of the default zd1211 driver (no detection), but wouldn't detect the 5100 on kernel 2.6.24-19 or -21.

I tried KernelCheck to update to 2.6.26.3, and still no progress.  Then I selected the development patch, to 2.6.27-rc5.  Now, both the 5100 and zd1211 are disabled.  I'm pretty sure I entered correct info into the kernel config.

I'm in Vista atm; I remember in the system log and dmesg about repeating messages for the PCI address of the 5100 adapter and iwlagn/iwl4965.

EDIT:
dmesg (syslog is similar)
> 

[   14.323248] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27kds
[   14.323250] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   14.328242] iwlagn 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.328270] iwlagn 0000:0e:00.0: setting latency timer to 64
[   14.328318] iwlagn: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   14.357047] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[   14.357570] iwlagn 0000:0e:00.0: PCI INT A disabled
[   14.357824] phy0: Selected rate control algorithm 'iwl-agn-rs'
...
[   14.437238] udev: renamed network interface wlan0 to wlan1
...
[   50.843616] iwlagn 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   50.843715] iwlagn 0000:0e:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   50.843892] firmware: requesting iwlwifi-5000-1.ucode
...
[   55.232102] iwlagn: START_ALIVE timeout after 4000ms.
[   55.232247] iwlagn 0000:0e:00.0: PCI INT A disabled
[   57.281763] r8169: eth0: link down
[   57.283817] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   57.880164] iwlagn 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   57.880251] iwlagn 0000:0e:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[B][   61.884113] iwlagn: START_ALIVE timeout after 4000ms.
[   61.884177] iwlagn 0000:0e:00.0: PCI INT A disabled
[   78.945126] iwlagn 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   78.945202] iwlagn 0000:0e:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)[/B]


---

### Post by wolframarnold on 2008-08-31
I've launched a new thread specifically for owners of the Compal JHL90: [http://ubuntuforums.org/showthread.php?t=906909]("http://ubuntuforums.org/showthread.php?t=906909")

---

### Post by Giblet5 on 2008-09-01
> Too good to be true. One reboot later and it seems I have the same problem as you. My card did work though before the reboot and before I touched the killswitch. I will look into this and post back if I fixed it.


That's exactly what I saw; worked for one session only and never again.

There's a problem in the __init stage. It doesn't initialize the controller at all, other than poking some settings in, that I can see.

I admit that I jumped on that, rebooted into Vista, got a wifi connection (to init the controller) and rebooted into linux. Still no joy.

Weirdness and weirdocity. I'll try and get some time to look at the __init code later.

---

### Post by Giblet5 on 2008-09-01
> **davbren said:**
> Ok as far as compilation is concerned I'm not particularly experienced, I'm having the same issues as you and have had no luck. I'm using the Samsung Q310. Unfortunately neither my ethernet or my wifi is working. I'm looking to upgrade the kernel but I have no net connection, i am dual booting vista and ubuntu so I can still use the laptop and download stuff on to the shared disk...

I have the intel link 5100 card. I have installed the firmware, I have also tried to use ndiswrapper, this says the hardware is detected but still doesn't use it. 

I really dont know how to compile or configure the kernel. Just about everything that has been said so far has gone over my head...

If someone has a way to get the Marvell Yukon ethernet that would just be a start, at least I could get some sort of internet connection...

Thank you in advance.
Dave.


I posted brief instructions for the Marvell controller in this thread:
[http://ubuntuforums.org/showthread.php?t=902337](http://ubuntuforums.org/showthread.php?t=902337)

At least you get the gigabit ethernet comms...

---

### Post by Zeroangel on 2008-09-03
I have an HP Pavilion DV5-1035CA laptop

Well after unsuccessfully playing around with various Linux distros (including arch, which didnt support my laptop's ethernet adapter), trying to load the iwl5000 drivers, endlessly messing with the CLI, and even compiling my own kernel from the .27 sources using the kernel-check utility, I was unsuccessful.

Today I installed the Intrepid Ibex alpha, upgraded all my packages to the latest through the update manager, and everything JUST WORKED!

So for those who are without support currently, it will be supported in Intrepid Ibex which is to be released at the end of October

---

### Post by alfito on 2008-09-03
Hello.

I have given a try to kernel 2.6.27-2 (avilable on intrepid repos) and the result is great. Wireless works "out of the box".

I am running an Acer 5930g model.

---

### Post by davbren on 2008-09-03
Hi, I can't even get the live cd to boot for intrepid. This is really frustrating! I just want wifi!!

---

### Post by Giblet5 on 2008-09-03
> **davbren said:**
> Hi, I can't even get the live cd to boot for intrepid. This is really frustrating! I just want wifi!!

Samsung Q310?

Do you know - with any certainty - what network chips your laptop uses?

This thread is focusing on the Intel Pro 5100AGN wireless chip. As of this post, there is no resolution for Hardy (8.04) yet, other than some one-shot successes followed by epic failures.

Maybe the 5100AGN is bipolar.

If your laptop uses a newer Marvell Technology ethernet (wired) chip, you can get instructions on getting it working from the Marvell website as I indicated above.

If you aren't comfortable with command-line Linux, and find it difficult to adapt to nested and threaded frustrations, then perhaps the combination of leading-edge hardware and leading-edge software is not where you want to be ..... cuz this is what The Leading Edge looks and feels like. It can be as frustrating as it can be rewarding. So, suck it up, go read the specs on your laptop, then write me a 5100AGN driver that works!

---

### Post by alfito on 2008-09-03
Just move temporaly sources.list to intrepid repos. Download linux-image-2.6.27-2-generic, idem headers and restrictred modules and restricted common. (There is no risk on that yo can always boot with 2.6.24 hardy kernel, do not upgrade other packages or you will mess up).
Move again to hardy repos. Reboot and take a look to wireless extensions.
At least in this Acer 5930g it is working fine, no problem after shutdown or reboot.

And the Marvell ethernet keeps working also, although loos like there is some kind of problem with that sky2 driver, repoted here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/227204]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/227204")

Regards

---

### Post by alfito on 2008-09-03
Which kernel version are you using, 32 or 64?
Looks like it could be related with the 64bit version. Look here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/256629]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/256629")

---

### Post by wolframarnold on 2008-09-03
I GOT WIRELESS on my Compal JHL90 hardward, with 64 bit Kubuntu Hardy.

What it took what a kernel compile of 2.6.27-rc5 with the latest snapshot patches, currently "-git4", from the [kernel archive]("http://kernel.org/").

I saw some commits to the wireless driver that discussed interrupt workarounds for hardware bugs, and I suspected something like this, because of these syslog entries, which _**I don't see any more**_:
```
Sep  3 18:13:12 wta-mobile NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): (wlan0): could not trigger wireles
s scan: Network is down
[...]
Sep  3 18:13:17 wta-mobile kernel: [ 8953.685236] iwlagn 0000:0e:00.0: PCI INT A disabled

```My initial guesses that the issue was related to the RF Kill switch are thus incorrect.  I think there is still a problem with the RF Kill switch being recognized properly by the OS, but it doesn't keep the wireless adapter from working...

In due time, these changes will probably make it into the Intrepid release, due out next month.  So, full out-of-the box support is probably just a month away.

---

### Post by Giblet5 on 2008-09-04
Sometimes I enjoy beating a problem to death, sometimes not.

Since all the iwlagn driver work is taking place on the 2.6.27 kernel, I decided to bite the bullet and install Intrepid (8.10).

Intrepid correctly identifies the ethernet and wireless network chips, right out of the gate.

Sounds great, huh? I mean dmesg shows it recognized and configured an Intel 5100AGN Wireless adapter! Eureka.

Except, the wireless STILL doesn't work presumably because the wmaster0 interface (layer to mac80211) is disabled. There is no clear indication as to why...it just IS and you will not question it.

"iwlist wlan0 scan" reports that the interface is down.
"ifconfig wlan0 up" reports that wlan0 is already configured.
"lshw -C network" only shows the ether and wmaster0 interfaces, and wmaster0 is DISABLED.

This is the same WiFi chip that works fine on Vista x64. I guess Intel was more diligent about providing a working driver for Windows...

(There are no XP drivers for this chip that I know of, so don't recommend the ndiswrapper solution. Vista drivers won't work.)

So, rather than wait weeks and try another 200,000 tweaks to nudge this chip into working as well as any 14-cent-per-dozen 802.11a chip would do, I ordered a 4965AGN PCIe Mini Card to replace the 5100AGN in my laptop.

The 4965AGN card provides three antenna connection points, so I guess I need to find room for a Pringle's can inside the case. ;) The 5100AGN is a cheap imitation of the 4965AGN, even if it uses a little less power.

How's that for a hardcore, pure brute-force, fix to a driver problem?

---

### Post by Giblet5 on 2008-09-04
> **wolframarnold said:**
> I GOT WIRELESS on my Compal JHL90 hardward, with 64 bit Kubuntu Hardy.
...
I saw some commits to the wireless driver that discussed interrupt workarounds for hardware bugs, and I suspected something like this, because of these syslog entries, which _**I don't see any more**_:

Heck yeah. I saw that too, but using the "irqpoll" kernel option eliminated the missed interrupt hiccup, although wmaster0 remained dead.

I suspect they did something more than some interrupt work...

That's great news though!

---

### Post by interskh on 2008-09-04
> **Slipie said:**
> Thank you so much wolframarnold!
Thanks to you ive got my wireless 5100 working with hardy!

Oke so I followed your steps.
Indeed after that the device was finally reconized.
But it was still disabled.
This was because it could not load the driver

```
Aug 25 21:43:06 slipie-vaio kernel: [  342.149093] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
Aug 25 21:43:06 slipie-vaio kernel: [  342.149170] PM: Writing back config space on device 0000:05:00.0 at offset 1 (was 100002, writing 100006)
Aug 25 21:43:06 slipie-vaio firmware_helper[6847]: main: error loading '/lib/firmware/iwlwifi-5000-1.ucode' for device '/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/firmware/0000:05:00.0' with driver '(unknown)'

```

So by simply copying iwlwifi-5000-1.ucode from /lib/firmware/2.6.24-19-generic/iwlwifi-5000-ucode-5.4.A.11/ to /lib/firmware and reloading the driver it finally worked!

Thnx a lot!


Hi,

i followed wolframarnold and ur steps and finally makes my 5100 work!

thank you very much

my laptop is Thinkpad T400 with Intel wifi 5100

Best wishes!

@Kyle

---

### Post by epilogue on 2008-09-04
well, got a problem here.

i followed wolframarnold steps and i cant make compat-wireless.

here:

```
root@ayberk-laptop:/usr/src/compat-wireless-2.6-old-2008-09-04# make
make -C /lib/modules/2.6.24-19-generic/build M=/usr/src/compat-wireless-2.6-old-2008-09-04 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
/usr/src/compat-wireless-2.6-old-2008-09-04/config.mk:54: "WARNING: You are running a kernel >= 2.6.23, you should enable in it CONFIG_NETDEVICES_MULTIQUEUE for 802.11[ne] support"
  CC [M]  /usr/src/compat-wireless-2.6-old-2008-09-04/drivers/misc/eeprom_93cx6.o
In file included from /usr/src/compat-wireless-2.6-old-2008-09-04/include/net/compat.h:37,
                 from <command-line>:0:
/usr/src/compat-wireless-2.6-old-2008-09-04/include/linux/compat_autoconf.h:1: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;need&#8217;
make[3]: *** [/usr/src/compat-wireless-2.6-old-2008-09-04/drivers/misc/eeprom_93cx6.o] Error 1
make[2]: *** [/usr/src/compat-wireless-2.6-old-2008-09-04/drivers/misc] Error 2
make[1]: *** [_module_/usr/src/compat-wireless-2.6-old-2008-09-04] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2
```

i looked inside the compat-autoconf.h and result: "You need git to generate compat-release file"

and i want to add lshw -c results: 

```
root@ayberk-laptop:/usr/src/compat-wireless-2.6-old-2008-09-04# lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

```

---

### Post by davbren on 2008-09-04
> **Giblet5 said:**
> Samsung Q310?

Do you know - with any certainty - what network chips your laptop uses?

This thread is focusing on the Intel Pro 5100AGN wireless chip. As of this post, there is no resolution for Hardy (8.04) yet, other than some one-shot successes followed by epic failures.

Maybe the 5100AGN is bipolar.

If your laptop uses a newer Marvell Technology ethernet (wired) chip, you can get instructions on getting it working from the Marvell website as I indicated above.

If you aren't comfortable with command-line Linux, and find it difficult to adapt to nested and threaded frustrations, then perhaps the combination of leading-edge hardware and leading-edge software is not where you want to be ..... cuz this is what The Leading Edge looks and feels like. It can be as frustrating as it can be rewarding. So, suck it up, go read the specs on your laptop, then write me a 5100AGN driver that works!

Okie Doke, lemme just get my genius cap on! lol I have no problem with upgrading to the new intrepid stuff, its just one more frustration that all I get from the live cd is a black screen. I'm sure I can work this one out. I'm in contact with Marvell about their driver, coz it sux. It doesn't work properly. I've followed your instructions and theirs and it still doesn't want to work...

As for wifi, I need to ethernet working before I can try pointing my repos anywhere. I really don't want to swap this laptop coz this keyboard is soooo cool! such a satisfying clack! :D

Cheers for all your help guys. I'll carrying on crusading for 5100agn support! :guitar:

---

### Post by theburningor on 2008-09-04
I've been following this thread for a couple days now but just wanted to chime in to see sort of where thinga are at.

It appears that using the 2.6.27-rc2 Kernel (32-bit) was sufficient, correct? Most of the other problems have had to do with 64-bit systems?  

FYI: Running Dell Latitude e6500 with Intel Wifi 5100, NVIDIA 160M gfx and Hardy Heron

---

### Post by wolframarnold on 2008-09-04
> **epilogue said:**
> well, got a problem here.

i followed wolframarnold steps and i cant make compat-wireless.

Yes, I had the same issue.  The compat-wireless stuff has changed.  The following information supersedes my [previous post]("http://ubuntuforums.org/showthread.php?p=5657450#post5657450").

The really good news is that _I GOT WIRELESS WORKING for the COMPAL JHL90 under the 64-bit Kubuntu Hardy 2.4.24 stock kernel with the latest compat-wireless download_, which I hadn't been able to do previously (my previous success required custom-compiling the latest 2.6.27 kernel.  Read on:

They now consider the 2.6.24 kernels "old" and you need the [compat-wireless-2.6-old.tar.bz2]("http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6-old.tar.bz2") download.  The [compat-wireless page]("http://wireless.kernel.org/en/users/Download") has been updated accordingly.

Once you got that file, untar it as follows, and it'll create a source tree dated with today's date, as of this writing 9/4/08:
```
sudo su
cd /usr/src
compat-wireless-2.6-old.tar.bz2
cd compat-wireless-2.6-old-2008-09-04
```

As in the [previous post]("http://ubuntuforums.org/showthread.php?p=5657450#post5657450"), you still need to hand edit config.mk and add:
```
CONFIG_IWL5000=y
CONFIG_IWLWIFI_RFKILL=y
```

Now follow the instructions in [previous post]("http://ubuntuforums.org/showthread.php?p=5657450#post5657450") to download the firmware.

Now you can run:
```
make
sudo make install
sudo make load
```

And hopefully your device is now recognized by the system and by Ubuntu/Kubuntu's wireless desktop tools.
```

sudo lshw -C network
  *-network
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:73:64:e0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 ip=192.168.1.7 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11abgn

```

---

### Post by epilogue on 2008-09-04
i follow exactly same steps and i still get same error. i am sure that i have no mistake and i followed your steps one by one. and i still get same errors when i try to "make" it.

---

### Post by KimOlsen on 2008-09-04
If you are feeling adventurous, you can now also get intrepid alpha 4, it will contain the 2.6.27 kernel after an update (It will probably be in the alpha 5 that is scheduled for release just about now).

---

### Post by wolframarnold on 2008-09-04
> **epilogue said:**
> i follow exactly same steps and i still get same error. i am sure that i have no mistake and i followed your steps one by one. and i still get same errors when i try to "make" it.

You know, I got it working once, but then after reboot, same dilemma.  I got it back to work with running "make unload" and "make load" again, but the changes don't stick.

My advice is wait for the next Intrepid Alpha release.  The kernel support for the 5100 driver on the Compal JHL90 platform just came in on 9/3/08 to the kernel repository.

Or compile the latest kernel with latest snapshot patches (works for me for now).

---

### Post by epilogue on 2008-09-04
thanks for advices. i am a bit newbie so i think i should wait for intrepid :)

---

### Post by Giblet5 on 2008-09-06
Just some notes for those considering a switch to Intrepid to correct this:

I am now running Intrepid with a custom kernel 2.6.27-rc5, 64-bit, compiled for low-latency desktop use.

It's a Gateway P-7811FX laptop, has a 5100agn wifi chip and the new Marvell ethernet chip. Intrepid has native support for the ethernet, so there's that.

However, the Intel 5100AGN is recognized, but wmaster0 is disabled and the 5100 does not work as a result.

I could install the 32-bit Intrepid - I too expect this is a 64-bit issue - but I PAID for all this RAM and I will darn-well use it.

This problem is wide-spread, most commonly reported with the "PCI INT A disabled" error message from dmesg.

There are reports of people getting it to work -- heck, even I got it to work for one session - but there is no explanation available as to why it happens and there is no real "FIX".

Disgusted and irate, I chickened-out and ordered a 4965AGN PCIe Mini Card to replace the 5100 chip with something that works and is a higher-end chip. Maybe I'll get an extra 20 cm of range out of it...

---

### Post by theburningor on 2008-09-09
I was following another similar thread to this one relating to the Intel WiFi Link 5300 and found a solution that worked for me with my 5100 WiFi:

This is adapted from a post by pythaes22.  I have included some updated steps:


Code:

```
sudo apt-get install build-essential
wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-5.4.A.11.tar.gz
tar -xzvf iwlwifi*
sudo cp iwlwifi-5000-ucode-5.4.A.11/iwlwifi-5000-1.ucode /lib/firmware

```

Now go to [http://linuxwireless.org/en/users/Download#Wheretodownload](http://linuxwireless.org/en/users/Download#Wheretodownload) and download the compat-wireless package for your system. The default kernel for 32-bit Hardy is 2.6.24 which is compat-wireless-old.tar.bz2

```
bunzip2 compat-wireless-old.tar.bz2
tar xf compat-wireless-old.tar
cd compat-wireless-2.6-old/

```

Now type:
Code:

```
gedit config.mk
```

A file will open. Search for the string CONFIG_IWL4965_HT=y. Directly after that string, on a new line, add this string:
Code:

```
CONFIG_IWL5000=y
```

Then save and close the file, and finish the installation with:
Code:

```
make
sudo make install
sudo make unload
sudo make load
```

Now reboot.

This worked without a hitch for me.

---

### Post by morgwon on 2008-09-09
followed instructions from theburningor and my latitude e6400 now has working wireless. Thanks.

---

### Post by Jerzabek39 on 2008-09-09
Made the same on my Fujitsu Siemens Amilo Pi 3525 and... nothing.. :(

---

### Post by phoenix116 on 2008-09-09
did the same on a COMPAL JHL90 --> no success, even with kernel update to 2.6.27rc5... 

my system log shows a kind of timeout when trying to activate wlan0

already tried to activate via sudo ifconfig wlan0 up
get this error: SIOCSIFFLAGS : connection timed out

I am quite sure this is an 64-bit-only problem, has anyone found a solution?

thanks for your help

---

### Post by Lokiii on 2008-09-09
> **phoenix116 said:**
> did the same on a COMPAL JHL90 --> no success, even with kernel update to 2.6.27rc5... 

my system log shows a kind of timeout when trying to activate wlan0

already tried to activate via sudo ifconfig wlan0 up
get this error: SIOCSIFFLAGS : connection timed out

I am quite sure this is an 64-bit-only problem, has anyone found a solution?

thanks for your help


Thanks to theburningor, I finally have WiFi on my Acer 5930G. However, I also got the SIOCSIFFLAGS : connection timed out when trying to activate wlan0. However, after numerous reboots and repeating the steps in theburningor's guide, it finally worked.

I'm still not sure exactly what I did that solved the problem, but what I did was:

Follow the steps explained in post from theburningor.
Reboot
Start the terminal, navigate to the compat-wireless-2.6-old dir, then type:

```
sudo make unload
sudo make load
sudo ifconfig wlan0 up
```

Then it worked perfectly for me! After doing this, I re-installed Ubuntu (as ive been doing so much crap to get the wifi card working), and went through that process again and it worked!

So, good luck all! This one worked for me at least! If the above steps dont work the first time, reboot and try again a few times :)

Cheers, and thanks loads!

---

### Post by acheong87 on 2008-09-10
I confirm that theburningor's instructions (post #62) work perfectly on a clean installation of Slackware 12.1 (Linux 2.6.24.5).  Thank you [pythaes22] for translating the German solution, and [theburningor] for further refinements!

My machine is an IBM/Lenovo ThinkPad T500 with the Intel Wireless Wifi Link 5300, but I'm sure it works for the 5100 as well.

Also, although not much shorter, here are some alternate methods to extraction:

```
tar zxvf iwlwifi-5000-ucode-5.4.A.11.tar.gz
```

and...

```
tar jxvf compat-wireless-old.tar.bz2
```

---

### Post by superstas on 2008-09-10
well 64 bit ubuntu 8.04 and i get SIOCSIFFLAGS: Connection timed out
:/

---

### Post by tofuconfetti on 2008-09-10
theburningor,

Your instructions were flawless.  I'm running hardy with a 2.6.24-19 generic kernel (standard updates are current), with nvidia drivers, on a brand new HP dv5-1017nr laptop.  Wifi is working flawlessly.

Nice work on the instructions.  I was going to wait until 8.10 came out, but now all is cool.  

Thanks.

---

### Post by jasex on 2008-09-10
Hey all... struggling with the 5100 too, on a  HP Pavilion DV4-1020US, will confirm if theburningor's fix works or not.

:D

:( EDIT: did not work... not as far as I can tell... about two minutes after performing sudo make load... the computer locked up... nothing would respond, and my capslock light started flashing. restarted... computer locked up on GDM login. restarted again... back in ubuntu... still seem to be at square one... orange wi-fi light... though a new development is... when I turn on the computer, it becomes blue temporarily, then... SIZZLE back to orange... pressing it does nothing. there's not even an option in network manager for enabling wireles... is there perhaps a step I missed... Ubuntu 7.10 64bit... upgraded to 8.04 64 bit... not straight 8.04 install

---

### Post by dfacto on 2008-09-11
worked for sony vaio vgn-sz540; thanks!

---

### Post by Lokiii on 2008-09-11
> **superstas said:**
> well 64 bit ubuntu 8.04 and i get SIOCSIFFLAGS: Connection timed out
:/

Look at my previous post! I am also running a clean install of 64bit Ubuntu, and after doing what I described, it now works!

I have to do:
sudo make unload
sudo make load

each time I boot up, but it works :D

---

### Post by lopata on 2008-09-12
ae   it works :)
tnx

---

### Post by sumwonyuno on 2008-09-13
Yes!

The Intel Wifi 5100 AGN works after the last update in 64-bit Intrepid Ibex Alpha 5 (to kernel 2.6.27.3).

---

### Post by Mastodront on 2008-09-13
Trying to get the wireless working on the girlfriends laptop; an ASUS X72V with an 5100. Seems like I can't get kill switch problem solved.

I began with Hardy and the method posted by wolframarnold on page to (compat-wireless and manual download of the firmware). Seems like the modules are loaded and all seems fine; if I run "sudo lshw -C network" I get; 
```
 *-network               
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:65:ba:74
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 00:22:15:5d:c4:7d
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=85.224.206.179 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

```

...which I suppose is correct. Though when I look in nm-applet (or knetworkmanager) it doesn't list any wireless networks at all. dmesg gives me;

```
 35.990368] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   35.990453] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[   35.990653] firmware: requesting iwlwifi-5000-1.ucode
[   36.069701] iwlagn: Radio disabled by HW RF Kill switch
[   38.735302] NET: Registered protocol family 17
[   63.836222] NET: Registered protocol family 10
[   63.838874] lo: Disabled Privacy Extensions
[   63.842890] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

I tried to uninstall the modules and upgrade to Intrepid 5, first 2.6.27-2-generic and then 2.6.27-3-generic. The problem is exactly the same there :(

Any suggestions?

---

### Post by braineatingalien on 2008-09-13
I followed the instructions on the previous page and now it shows wireless networks but it doesn't list any in range.  I have a HP DV5t with 5100.  I tried 8.10 alpha 5 and it does work nearly perfect but I cant use that because the bluetooth doesn't work properly.  so how do I display wireless networks in range?

---

### Post by expect0 on 2008-09-14
Having exactly the same problem as Mastodront. Have been trying to get my Intel Wireless 5300 to work (in my Asus S37S) for several weeks now and the dmesg output seems to suggest it actually works for a couple of seconds - until the RF kill switch disables it again.

This can be comprehended by the fact that the WLAN LED gets turned on when booting up but gets disabled after about 10 seconds later (still booting). The networkmanager seems to have been able to get the wireless network list in this time but as such is unable to actually connect when the laptop is finished booting.

Unfortunately there's no such switch on my laptop and the BIOS doesn't provide any settings either. So we just have yet to figure out how to invoke that hidden switch :rolleyes:

---

### Post by lopata on 2008-09-14
btw my card is working very well and wifi conection too,  but there is still "sudo lshw -C network"  Intel Unknown  :D

its writen 'unknown' but the wifi is working,  LOL

---

### Post by JSorrell on 2008-09-14
> **Lokiii said:**
> Thanks to theburningor, I finally have WiFi on my Acer 5930G. However, I also got the SIOCSIFFLAGS : connection timed out when trying to activate wlan0. However, after numerous reboots and repeating the steps in theburningor's guide, it finally worked.

I'm still not sure exactly what I did that solved the problem, but what I did was:

Follow the steps explained in post from theburningor.
Reboot
Start the terminal, navigate to the compat-wireless-2.6-old dir, then type:

```
sudo make unload
sudo make load
sudo ifconfig wlan0 up
```

Then it worked perfectly for me! After doing this, I re-installed Ubuntu (as ive been doing so much crap to get the wifi card working), and went through that process again and it worked!

So, good luck all! This one worked for me at least! If the above steps dont work the first time, reboot and try again a few times :)

Cheers, and thanks loads!

I had the same exact problems.

To everyone who has the SIOCSIFFLAGS problem, *keep trying!*. It took me two reinstalls and tons of times repeating the steps but it finally worked on my copy of Ubuntu 8.04 with the default kernel. Thanks, Lokiii.

[EDIT] It's not perfect, however. After a restart, it no longer works. It's a little touchy.

---

### Post by basix9 on 2008-09-15
hello all,

i'm not a Ubuntu user but a Debian user. So I'm not as lucky as you guys to have Intrepid Ibex's 2.6.27 kernel with the wifi 5100 driver already in it.

I'm currently using 2.6.26-1-686 kernel. With the drivers found here: [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

and the instructions here: [http://ubuntuforums.org/showthread.php?p=5727196](http://ubuntuforums.org/showthread.php?p=5727196)

anyway, i have a peculiar problem. Sometimes the wifi card gets configured. But a sure shot way of making it work is by running these commands in succession:

iwconfig wlan0 essid <my_essid> **mode managed** rate auto key <key_goes_here> 
iwconfig wlan0 essid <my_essid> **mode auto** rate auto key <key_goes_here> 

Obviously the second command shouldn't work and it doesnt BUT for some stupid reason this forces the card to work correctly. But I am having problems with the driver dropping my wifi connection at times. Its quite rare but it does happens once a day.

When are we likely to see ndiswrapper support or decent working drivers for these cards?

---

### Post by superstas on 2008-09-16
thank you Lokiii for the first time it didn`t work but after the reboot it worked -> woop

edit.

oh wait it stopped working :/
still the same statement ..... timeout

---

### Post by Diegovr on 2008-09-16
The same happens to me but in an HP Pavilion DV5-1010US, it has also bluetooth integrated


> **jasex said:**
> Hey all... struggling with the 5100 too, on a  HP Pavilion DV4-1020US, will confirm if theburningor's fix works or not.

:D

:( EDIT: did not work... not as far as I can tell... about two minutes after performing sudo make load... the computer locked up... nothing would respond, and my capslock light started flashing. restarted... computer locked up on GDM login. restarted again... back in ubuntu... still seem to be at square one... orange wi-fi light... though a new development is... when I turn on the computer, it becomes blue temporarily, then... SIZZLE back to orange... pressing it does nothing. there's not even an option in network manager for enabling wireles... is there perhaps a step I missed... Ubuntu 7.10 64bit... upgraded to 8.04 64 bit... not straight 8.04 install

---

### Post by braineatingalien on 2008-09-16
Well I got my dv5t working.  I tried it again and it worked. I must have missed a step.

---

### Post by Diegovr on 2008-09-16
> **braineatingalien said:**
> Well I got my dv5t working.  I tried it again and it worked. I must have missed a step.

I have followed the steps posted here, but when I try to conect again to an ap, my laptop got freeze and I have to restart it again.

I have a HP Pavilion DV5 too

Could you please post here the exact steps did you follow to, I'll appreciate a lot.

Thanks and regards,

---

### Post by VOVEEE on 2008-09-17
It works on HP Compaq 6830s so owners of this laptop can use this to make wireless card work. :)

---

### Post by basix9 on 2008-09-17
did you guys try updating to the latest Ubuntu Intrepid Ibex release? That kernel has got to work. I've downloaded a vanilla kernel.org kernel and compiled it myself and wireless works very nicely ( should say flawlessly actually :) )!

Edit: Incase you are on an older version of Ubuntu and want to upgrade to the latest and greatest kernel then you have two options. 1. Download Ibex's latest kernel source, copy over your .config and compile it yourself. 2. Download the vanilla kernel.org kernel and compile that.

I'm not sure if the 2nd option would be good for you guys since it will probably muck up some of the nice features that the Ubuntu team puts in your kernel.

In either case follow this tutorial and you ought to be good to go: [http://www.howtoforge.com/kernel_compilation_ubuntu_p2](http://www.howtoforge.com/kernel_compilation_ubuntu_p2)

---

### Post by jakey21 on 2008-09-18
Hello, i followed all the steps. I got it to work but for some reason the light on my DV4-1028US centrino 2 works then the light flickers blue and red. Blue meaning working, red meaning off.  When i restart it doesnt work but restart again it does the same thing. When the light flickers and i take it off power it starts clicking, all the sounds are disabled. This is a 64 bit vista computer running on a 32 bit ubuntu. any help is appreciated thank you.  hope you can understand what i wrote. forgot to mention my kernel is 2.6.24-19

---

### Post by jakey21 on 2008-09-18
i wonder if its because its sayin iwlagn instead of iwl5000. if it is how do i change that?

 *-network               
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:7a:35:a0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

---

### Post by RaZe42 on 2008-09-18
> **basix9 said:**
> did you guys try updating to the latest Ubuntu Intrepid Ibex release? That kernel has got to work. I've downloaded a vanilla kernel.org kernel and compiled it myself and wireless works very nicely ( should say flawlessly actually :) )!

Edit: Incase you are on an older version of Ubuntu and want to upgrade to the latest and greatest kernel then you have two options. 1. Download Ibex's latest kernel source, copy over your .config and compile it yourself. 2. Download the vanilla kernel.org kernel and compile that.

I'm not sure if the 2nd option would be good for you guys since it will probably muck up some of the nice features that the Ubuntu team puts in your kernel.

In either case follow this tutorial and you ought to be good to go: [http://www.howtoforge.com/kernel_compilation_ubuntu_p2](http://www.howtoforge.com/kernel_compilation_ubuntu_p2)

Which kernel did you choose? 2.6.26 or 2.6.27.rc6
I'm going to try this with the 2.6.27 kernel, had no luck with the method on page 7

---

### Post by basix9 on 2008-09-18
> **RaZe42 said:**
> Which kernel did you choose? 2.6.26 or 2.6.27.rc6
I'm going to try this with the 2.6.27 kernel, had no luck with the method on page 7

Please reread my post. I've told exactly what kernel I've used and how to compile it.

---

### Post by basix9 on 2008-09-18
> **jakey21 said:**
> Hello, i followed all the steps. I got it to work but for some reason the light on my DV4-1028US centrino 2 works then the light flickers blue and red. Blue meaning working, red meaning off.  When i restart it doesnt work but restart again it does the same thing. When the light flickers and i take it off power it starts clicking, all the sounds are disabled. This is a 64 bit vista computer running on a 32 bit ubuntu. any help is appreciated thank you.  hope you can understand what i wrote. forgot to mention my kernel is 2.6.24-19

Upgrade your kernel. I think the stable driver works only with the .27 kernel.

---

### Post by remu on 2008-09-22
I've got 8.04 64bit, these instructions worked for me, and I did a clean install so that I could square some stuff away, however now the instructions don't fully work for me. After following theburningror's instructions and rebooting, I can see all of the wireless ap's around me, but I am unable to connect to any of them. It tries to connect, but doesn't succeed. Running dmesg tells me that the authentication timed out.

The only difference from before is that now in the config.mk file, there is no entry for "CONFIG_IWL4965_HT=y", just "CCONFIG_IWL4965=y" and right underneath that the line "CONFIG_IWL5000=y" is already present.

> **theburningor said:**
> 
Now type:
Code:

```
gedit config.mk
```

A file will open. Search for the string CONFIG_IWL4965_HT=y. Directly after that string, on a new line, add this string:
Code:

```
CONFIG_IWL5000=y
```

Then save and close the file

I don't know whats wrong, but I wish I can get this solved, don't really feel like waiting untill the end of October for Intrepid.

---

### Post by hmell on 2008-09-23
I tried to get wireless / Wifi Link 5100 working on my asus B50A using the latest Ubuntu Intrepid Ibex release (alpha 6). I cant connect to any wlan. scanning (iwlist) works but it shows not all available networks. 

then i tried mandriva 2009.1 RC 1 live cd and it works out of the box. this system is using kernel 2.6.27-server-0.rc5.2.1mnb #1 SMP

opensuse 11.1 beta 1 with 2.6.27 rc6 does also not work.

... i want my ubuntu back!

---

### Post by rasmus91 on 2008-09-24
I don't know how to make my 5100 agn working, so i'd like to ask you guys if someone would write a complete guide on how to make wireless work on ubuntu 8.04 64 bit system... i need this pretty much so please write it...

BTW please make it idiot proof, so that i don't miss something, or mess something up...

---

### Post by ModestRain on 2008-09-26
> **remu said:**
> I've got 8.04 64bit, these instructions worked for me, and I did a clean install so that I could square some stuff away, however now the instructions don't fully work for me. After following theburningror's instructions and rebooting, I can see all of the wireless ap's around me, but I am unable to connect to any of them. It tries to connect, but doesn't succeed. Running dmesg tells me that the authentication timed out.

The only difference from before is that now in the config.mk file, there is no entry for "CONFIG_IWL4965_HT=y", just "CCONFIG_IWL4965=y" and right underneath that the line "CONFIG_IWL5000=y" is already present.



I don't know whats wrong, but I wish I can get this solved, don't really feel like waiting untill the end of October for Intrepid.

It seems something broke after September 9th.

[http://git.kernel.org/?p=linux/kernel/git/mcgrof/compat-wireless-2.6-old.git;a=shortlog]("http://git.kernel.org/?p=linux/kernel/git/mcgrof/compat-wireless-2.6-old.git;a=shortlog")

The September 9th version worked for me.

[http://www.orbit-lab.org/kernel/compat-wireless-2.6/2008/09/compat-wireless-old-2008-09-09.tar.bz2]("http://www.orbit-lab.org/kernel/compat-wireless-2.6/2008/09/compat-wireless-old-2008-09-09.tar.bz2")

This probably could be regenerated from git as well.

---

### Post by nzgreen on 2008-09-26
> **ModestRain said:**
> The September 9th version worked for me.

Worked for me too.  Thanks!

---

### Post by kasaku on 2008-09-26
Hi , Revage , on your way , i make that output 

[COLOR="Red"]kasaku@kasaku-laptop:~$ sudo lshw -C network
  *-network DISABLED    [/COLOR]  
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:ba:41:18
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:86:00.0
       logical name: eth0
       version: 00
       serial: 00:1f:29:b3:8d:32
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.98 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
kasaku@kasaku-laptop:~$ 


when i user commmand ifconfig , I can't see the eth1 , that you say about wireless interface, 

can you help me , thx verymuch ,:guitar:

---

### Post by Diegovr on 2008-09-29
Hi guys,

I've followed up to all the indications posted here, I've done my wireless card work (well, almost), now when I check it using lswh -C network it's showing available, also it can look for wireless networks available, BUT, when I choose a network to connect, it just simply fail. When I try to see the dmesg output, this is what is shown me:

[  956.668982] wlan0: authenticate with AP 00:1c:10:a9:f0:98
[  956.669385] wlan0: authenticate with AP 00:1c:10:a9:f0:98
[  956.844893] wlan0: authenticate with AP 00:1c:10:a9:f0:98
[  957.033429] wlan0: authenticate with AP 00:1c:10:a9:f0:98
[  957.232563] wlan0: authentication with AP 00:1c:10:a9:f0:98 timed out

I dont know what else to do, this wireless card is drive me craizy. My laptop is an HP DV5-1010us, I'll give you also my lshw config and ifconfig:

 root@debian-pride:~/installers/iwlwifi-5000-ucode-5.4.A.11# lshw -C network
  *-network               
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:ac:29:66
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:b6:cd:3b
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.100 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
root@debian-pride:~/installers/iwlwifi-5000-ucode-5.4.A.11# 

wlan0     Link encap:Ethernet  HWaddr 00:16:ea:ac:29:66  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-EA-AC-29-66-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@debian-pride:~/installers/iwlwifi-5000-ucode-5.4.A.11# 

if you could help me, I'd appreciated that.

Thanks.

---

### Post by barlowrm on 2008-09-30
Hi,

I was having problems with my intel 5100 on my asus laptop (Hardy, kubuntu flavour), until I found this forum.

First of all THANKS to all those who contributed.

I tried several of the suggestions, and at the end I could have the 5100 correctly recognised by using the rc3 of the 2.6.27 kernel.

Now I am facing the problem already reported here: the wifi led is actually working, it is ON during all the boot sequence, but it gets switched off when the x session starts (I'm not implying this is X's fault of course).

I made one more test: boot 2.6.27 using the "recovery mode" and drop to a root shell when prompted. At that stage the 5100 is up and running. I can actually launch iwlist and see the access points around.

If instead I choose to go on with normal boot, then rfkill is somehow activated and I cannot find a way to switch it off again.

I think I can conclude that this is not a driver issue, but rather some weird interaction with some application being run in the boot sequence.

Do you have any idea of who may be switching off the radio? More important: do you know how I can undo whatever it's doing? I tried echoing 0s around sensible places in /sys/.../../rfkill, but the resulting state is always 2, so maybe I'm not looking in the right place?

Thanks for your help,

Andrea.

---

### Post by hmarkg on 2008-10-03
I faced error when typing this code 

```
make
sudo make install
sudo make unload
sudo make load
```

---

### Post by prem1er on 2008-10-03
Has anyone had any luck with getting the 5100 working on Ubuntu 8.10 and the 2.6.27 kernel?

---

### Post by kforum on 2008-10-03
it works fine,
if the ubuntu devs configured the kernel to use the driver properly, i believe all you _might_ need is the intel wifi ucode.
you can download it at [http://intellinuxwireless.org/?n=Downloads](http://intellinuxwireless.org/?n=Downloads).

i think you have to download the iwlwifi-4965-ucode-228.57.2.21.tgz
one, i believe it has the 5x00 series in it, but im not sure.

shouldn't a ubuntu dev be talking about this?

---

### Post by prem1er on 2008-10-03
> **kforum said:**
> it works fine,
if the ubuntu devs configured the kernel to use the driver properly, i believe all you _might_ need is the intel wifi ucode.
you can download it at [http://intellinuxwireless.org/?n=Downloads](http://intellinuxwireless.org/?n=Downloads).

i think you have to download the iwlwifi-4965-ucode-228.57.2.21.tgz
one, i believe it has the 5x00 series in it, but im not sure.

shouldn't a ubuntu dev be talking about this?

Agreed.  Maybe they are actually waiting for the release of 8.10, but some insight would be nice.

---

### Post by remu on 2008-10-03
> **prem1er said:**
> Has anyone had any luck with getting the 5100 working on Ubuntu 8.10 and the 2.6.27 kernel?

Mine works out of the box on Intrepid.

---

### Post by prem1er on 2008-10-03
Thank you.

---

### Post by vicG on 2008-10-03
> **prem1er said:**
> Has anyone had any luck with getting the 5100 working on Ubuntu 8.10 and the 2.6.27 kernel?

Yes.  Just grabbed the dvd today (i386) and just installed now.  Stone stock Ibex beta, worked right out of the box.

On this same machine, could not get 8.04 to work, although admittedly I didn't try every last recommendation in this thread.

Great job and kudos to the developers!

-- happily wireless with the 5100

---

### Post by lindylex on 2008-10-03
ModestRain, how did you find out that this was broken after 2009.September.09 ?  I spent three days trying to figure this out then I finally read this and it solved my problem.

Using: Debian Ethch 4.0 | Intel WiFi Link 5300 (AGN)

Thanks

---

### Post by neo007 on 2008-10-05
I've Intrepid beta installed but no wireless on my hp dv5 1040ew. I followed instructions from the page number 7 and the result is that the switch is glowing blue (enabled) but I can't connect to an access point with password although the key is correct - it keeps asking for the key after a couple of seconds trying to connect. Any ideas?

I found that it's a [regression](http://ubuntuforums.org/showpost.php?p=5857541&postcount=95) (this topic) but is it somewhere submitted in order for devs to fix it?

---

### Post by rasmus91 on 2008-10-05
HI

i have a 5100 agn, I've tried to install driver for the card, but couldn't make it work. can any of you tell me how to install itrepid, and if there any risk it could ruin my hardware? (I've heard rumors that intreped can ruin hardware)

---

### Post by prem1er on 2008-10-06
> **rasmus91 said:**
> HI

i have a 5100 agn, I've tried to install driver for the card, but couldn't make it work. can any of you tell me how to install itrepid, and if there any risk it could ruin my hardware? (I've heard rumors that intreped can ruin hardware)

Intrepid only has problems because of the 2.6.27 kernel.  It doesn't involve the wifi chip at all.  I think the bug you are referring to is this one.  [http://blogs.computerworld.com/when_linux_goes_bad_the_e1000e_ethernet_bug]("http://blogs.computerworld.com/when_linux_goes_bad_the_e1000e_ethernet_bug").  Read about it.  

On another note, I have heard of some people having success with the new kernel and the 5100 agn, however I am not one of them.  I just patched the kernel from Hardy to 2.6.27 and I'm still having no luck with my wifi.  The driver is working and networks are detected, but it won't connect to any of them.  Secured or unsecured.

---

### Post by Randseed on 2008-10-06
> **theburningor said:**
> I've been following this thread for a couple days now but just wanted to chime in to see sort of where thinga are at.

It appears that using the 2.6.27-rc2 Kernel (32-bit) was sufficient, correct? Most of the other problems have had to do with 64-bit systems?  

FYI: Running Dell Latitude e6500 with Intel Wifi 5100, NVIDIA 160M gfx and Hardy Heron

I can confirm that this driver does NOT work with 2.6.27-rc8 on an Intel Centrino 2 Duo (64-bit) with an Intel 5100 AGN. This includes trying with the latest versions of compat-wireless, both with support compiled into the kernel and with relying totally on the compat-wireless modules. This also includes using the config.mk hacks.

Basically, the 3x and 4x modules will be compiled. The 5x module apparently never is. Neither the 3x nor the 4x module will recognize the card. Yes, I have the 5000 firmware installed in /lib/firmware. Yes, I have ensured that the RF kill switch is on. And yes, I've actually cycled the RF kill switch and there's no difference.

This card is coming out in a lot of new laptops. Linux needs support for this badly.

---

### Post by Diegovr on 2008-10-07
Hi all,

Cheking the last comments and trying to install the driver, I downloaded the compat-wireless-old-2008-09-09, which is the one that really work. Well, I've installed it and it works !!! BUT, whe I restart my laptop it just left to work, giving this message:

[  137.741580] iwl4965: START_ALIVE timeout after 4000ms.
[  137.741656] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[  142.258310] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  142.258370] PM: Writing back config space on device 0000:02:00.0 at offset 1 (was 100002, writing 100006)
root@debian-pride:/home/diegovr# 


To get my wireless card to work again I have to unload the modules, uninstall, reinstall and load the modules again, that's disgusting but it's the only way that I've found to keep working my iwl5100 wireless card.

---

### Post by neo007 on 2008-10-10
After today's update I got my wifi working. I'm not sure if it's due to kernel update or something else but it's working with Intrepid.

---

### Post by kermiac on 2008-10-11
I spent more than a few hours toying around with the Intel Wireless Wifi Link 5100 on a fresh Hardy install today. After sifting through numerous forums, newsgroups & mailing lists I was about to give up & wait the 19 days 'til Intrepid is due to be released.
Then I remembered playing around with "**wicd**". 
This has SOLVED my wireless issues. 
I can now keep either a static or dynamic wireless IP after rebooting!
Installing "wicd" removes "network-manager" & "network-manager-gnome". As far as I can tell this does not have any nasty side effects, but please note I'm still a bit of a noob (damn my "windows mentality"!).
I followed the very simple instructions from the [wicd website]("http://wicd.sourceforge.net/download.php").
Only minor hiccup I had was connecting to encrypted networks. If you have a message similar to "encryption must be enabled for this network", you have to click the "Advanced Settings" button and enter your encryption info in the window that pops up.  There are templates already setup, you should be able to use WPA 1/2 with no problem.
Hope this helps someone avoid the headaches I went through today :)

---

### Post by hmarkg on 2008-10-13
Hi all before this i have problems with the wireless card, and i tried the solution in page 2 of this post. It didnt solve my problem. I cannot enable my wireless card, everytime i do so the whole computer will hang there. 

[CENTER][IMG]http://i66.photobucket.com/albums/h267/hmarkg/Screenshot-2.png[/IMG]

[IMG]http://i66.photobucket.com/albums/h267/hmarkg/Screenshot-1-1.png[/IMG][/CENTER]

Now i'm using Wicd, the wired connection worked fine but the wireless is still useless

---

### Post by eyefragment on 2008-10-13
I'm quite a linux newbie, so this post is largely blind leading the blind.  Still, I've got my card working, and would like to do what I can to help in this thread.

I decided to go ahead and install Intrepid to try to get my card working.  After some extensive googling, I've managed to get it running, so this might be of some use to someone else.  These steps might be useful under hardy too.

First, run sudo lshw -C network to see if your card is being detected, if your card is disabled (indicated by *-network DISABLED), and if your card has drivers (configuration: driver=????).  If you're running Intrepid, it should already have the drivers.  In my case, the drivers were installed, the card was detected, but the network was DISABLED.  My drivers were iwlagn.

Next, run

dmesg | grep -i iwlagn

This tells you a bit more about what your card is trying to do.  In my case, it was failing to load the microcode.  I don't know how to fix other issues, but to fix this one, download the microcode from [http://intellinuxwireless.org/?n=downloads](http://intellinuxwireless.org/?n=downloads), copy your microcode file into one of /lib/firmware or /lib/firmware/[your kernel number here].  I'm not sure which one is correct (I copied it to both, and am afraid to touch anything)

After that, run ifconfig wlan0 up.  This solved the issue for me.

---

### Post by hmarkg on 2008-10-14
Thanks for trying to help me out. I shell try it tomorrow after i'm done with my studies. I'm having a test tomorrow. Still got some to go...

---

### Post by zavaro on 2008-10-14
Alright, well, I've used a slew of these fixes, trying desperately to get this to work.  I'm pretty new to messing with drivers and such in Ubuntu, my only other Linux experiences were on Fedora years ago.

I'm able to roam and discover the Wifi networks through the card, encrypted or not, but times out when trying to connect to them.

Confusing, huh?

---

### Post by RaZe42 on 2008-10-15
Those with Asus M50V* laptops with an intel wireless card, I redirect you to [this]("http://ubuntuforums.org/showthread.php?t=921556&highlight=asus+m50") thread(post #3) 
Worked on intrepid beta with kernel 2.6.27 using wicd(most probably will work with networkmanager)

---

### Post by queequag on 2008-10-16
I have a Lenovo U330 with an Intel Wifi 5100 wireless card, and I was able to get my wireless to work with WPA2 encryption using the method using Wicd mentioned in posts #114 and #116 of this thread.  I also removed the script mentioned in a previous post dealing with the RFkill switch, but this is not neccesary, and my rFkill switch still works.  

All that was needed was to instal wicd, restart and check that dmesg picked up the wireless card as an Intel 5100, run ifconfig wlan0 up, and wifi networks showed up in Wicd.  

Thanks alot!

---

### Post by hmarkg on 2008-10-16
Does this means that if i upgrade to ubuntu 8.10 will solve this problem... 14 more days faster faster...!!! what the sound problem....

---

### Post by Ævar Arnfjörð Bjarmason on 2008-10-17
I have a [working 5100 card on a Thinkpad R400](http://ubuntuforums.org/showthread.php?t=950036) under 8.10 beta.

---

### Post by bguito on 2008-10-17
Hello guys, i am using Mint, but since this is (I think) based on Ubuntu, i guess that things should not be so different.

I did exactly what **theburningor** (page 7) said to, though I had to use the 9th september version of the compat that so gently, **ModestRain** included on his post (page 10). 

My Wireless is an **Intel WIFI 5100**.

Kernel: **2.6.24-21**


Im still a newbie in what comes to linux, and what I am about to say might seem pretty obvious for most of you, but there's a chance of existing someone that doesn't know this, as i didn't before.
> **Diegovr said:**
> To get my wireless card to work again I have to unload the modules, uninstall, reinstall and load the modules again, that's disgusting but it's the only way that I've found to keep working my iwl5100 wireless card.

Basicly, I saw Diegovr and a few more guys complaining about this. I was facing myself the same situation aswell. But i didn't have to reinstall, all i was doing was unload and re-load the modules again and voilá.

So I did: 
```
lshw -C network
``` 

(might require the sudo before, but im quite sure it doesnt).

This will list your network devices (don't know if this is only about PCI cards, i think it is, but since we're talking about this specific one..).
So basicly you should see ethernet and wireless devices loaded (for those who are having the same issue i was, remember to only do this after reloading the modules). More or less at one of the last lines of your wireless device, you'll have something like "driver=blabla".
This blabla is the module that was loaded, and in our case, is working. at least for me it is so far.
In my case the module loaded was the iwl4965 so there was something like "Driver=iwl4965". Should be iwl5000? maybe, but it is working so far so I'll dig it later.
This is the module you want to be loaded after the startup, so lets make it happen:
Go to the terminal:

```
sudo gedit /etc/modules
```
After the last line, write down the name of the drivers you saw that were loaded, when you did 'lshw -C network'.
ATENTION to capital or small letters. Everything in Linux is case sensitive, so if there appeared in small letters (my case) type it down in small letters.

If you used theburningor way to install your drivers means you didnt use ndiswrapper, (dunno what it is? then nevermind this), I advice you remove that. If it's not here, even better, nevermind, but I had it on mine modules file by default.  Don't know how much is it possible to cause a conflict, but if you're not using it why loading it? (a more experienced guy confirm me this please).

Now reboot, and your drivers should be loaded automatically. Sorry for the long post, still learning how to pro write posts in small sizes.

Thanks to all of you, speccially theburningor and ModestRain

regards,
bguito

---

### Post by Lokiii on 2008-10-19
After the Ubuntu updates on, what was it, Thursday? My Intel Wifi Link 5100 doesnt work anymore with the previously used method. Anyone have any new ideas, or should I just wait for 8.10?

Cheers!

---

### Post by el_Salmon on 2008-10-20
> **Lokiii said:**
> After the Ubuntu updates on, what was it, Thursday? My Intel Wifi Link 5100 doesnt work anymore with the previously used method. Anyone have any new ideas, or should I just wait for 8.10?

Cheers!

Me the same. Hoping a solution...:(

---

### Post by bguito on 2008-10-21
To both of you, as i said, I'm not a pro but..
Did those updates include a new kernel? If so, it might be that, and so, try booting with the previous version. If not, nevermind, I can't help you.. :<

---

### Post by Turner22 on 2008-10-21
Hi,

Thanks for those drivers, really i was looking for it...

I have many more doubts please help me out guys.

---

### Post by senortighto on 2008-10-21
> **phoenix116 said:**
> did the same on a COMPAL JHL90 --> no success, even with kernel update to 2.6.27rc5... 

my system log shows a kind of timeout when trying to activate wlan0

already tried to activate via sudo ifconfig wlan0 up
get this error: SIOCSIFFLAGS : connection timed out

I am quite sure this is an 64-bit-only problem, has anyone found a solution?

thanks for your help

i too have a compal jhl90 and i just installed ibex and everything works great right out of the box!  i connected up to my WPA network right quick; i got totally fed up trying to make it work in hardy.  so that might be an option to those trying to get the 5100 wireless working.

---

### Post by seattle vic on 2008-10-23
It looks like this thread has been going on for a while.  It was useful; I downloaded the driver, u-code, followed the instructions, played with the rfkill bit entries, gave up, went to Intrepid, only partial luck, and back to Hardy.  No luck. Even with 8.10 I could only get sporadic success.  After 6 pretty much full days playing with this, reading everything I could find on the web, more re-boots than windows, I'm worn down.

I'm currently doing an upgrade back to 8.10/2.6.27-7 and will play with that when I get some energy.  I'm happy for the few that were able to get it working.  I have a new Asus m-70vm-c1.  Fantastic machine except for the new wireless hardware.  Like somebody said, cutting edge hardware and software leads to frustration, eventually joy, but not yet.  Maybe it's the pesky kill switch.

If anybody has had success with an M-70, please let me know, thanks.

I did go to wicd toward the end, as at least one person reported success.  It didn't help, but does seem to be a nicer interface.  I don't know if it will persist over nm when my upgrade finishes, but I would like to hear what people think of it in this system.

If I thought it'd do any good, I'd paste the results of dmesg, lshw, lspci, etc, but I think it's all been covered, and I've tried pretty much everything in this thread.  I'll probably just live with 8.10 and update as modules are improved; hopefully they'll get it fixed.

---

### Post by Lokiii on 2008-10-24
Not sure if there was a new kernel in there with the updates. I was in a hurry and didnt check! Can anyone confirm or deny this? Cuz Wifi isnt working at all now :(

---

### Post by bguito on 2008-10-24
Lokii, when you boot u can see the current Kernel Versions and even chose which one to be loaded... Im only insisting so much on the kernel cause when I tried to put Mint5 fully operacional, i had like 4 different problems and all them were connected to the kernel version i Was using at that moment....

---

### Post by vulto on 2008-10-24
I have been trying to get the 5100 AGN working on the 64 bit version of Ubuntu 
I now see there were others who tried in vain and the majority gave up trying. 
As Windows XP has no trouble working with this card on my lap-top, I decided to revert to windows xp . Gradually I am discovering now why Linux dialects and Ububtu are no perfect replacement . Yoy really must be a guru to get things working -especially new hardware- which almost always is available on windows. Even then it fails with some cards and for the reason why nobody with any seniority seems approachable.  And I can understand that : It's all for free...I keep using Ubuntu on my older desk-top . Perhaps in the future the linux comunities can think of a commercial development commodity , where you can buy working applications and drivers ?? If one of our aims is to break the monopoly of Gates on the  pc o.s. platform  , then providing free software that isn't at least as good will be no good. In this way there is still no competition and no drive for microsoft to make things cheaper.  Still I have much respect for all of the people who dedicate their time towards these things , but introducing some commercial thinking and removing the religious edges may provide better results for many . ( I realise this is probably what they call in Holland "cursing in the church" , but there you are ) Best wishes , Wim

---

### Post by seattle vic on 2008-10-24
> **Lokiii said:**
> Not sure if there was a new kernel in there with the updates. I was in a hurry and didnt check! Can anyone confirm or deny this? Cuz Wifi isnt working at all now :(

I just loaded 8.10 from the latest iso and it's 2.6.27-7.

After struggling with trying to load drivers and u-code in Hardy, without success, it was refreshing to have it pop up and find my wireless network, as well as others in the neighborhood.

However, even though the network manager icon says it's connected to my wireless network, it's not getting through the the applications, like firefox or snaptic, etc.  I'm doing a static connection, but know the ip, dns, etc are good, as it's what I use with my wired version.

The only other thing I wonder about is if this could be related to wpa, as I do have security set.  I've read some things about this being an issue.

My laptop is a asus m-70.  Anybody have experience with this version and wpa?

---

### Post by seattle vic on 2008-10-26
Well, a quick follow-up.  After playing with it for a while, several boot-ups, the wireless with wpa is working well, as is sound and video.  So far so good.  So, doing a complete re-install with the latest 8.10 iso seemed to do the trick.

Now to work on getting blue ray to function :)

Seattle Vic
Asus M70VM-C1

---

### Post by remu on 2008-10-26
seattle vic: What sound card do you have?

---

### Post by seattle vic on 2008-10-26
> **remu said:**
> seattle vic: What sound card do you have?

Good question.  The laptop is an ASUS M-70, and I presume the sound is part of the Intel chipset which is the pm45.  Here's what lscpi says:

vic@vic-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
**00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)**
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GS (rev a1)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
07:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

However, the newegg discription says:

Azalia compliant audio chip, with 3D effect & full duplex

---

### Post by remu on 2008-10-26
Seattle Vic: Could you do me one more favour please. Go ahead and save this script and then run it. [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh). this will then post alsa debugging information out to a website. If you could post that, it would be great! I'm trying to figure out what Audio Codec is being used in your system. I am having sound issues even though we both are using the ICH9 Chipset.
Thanks!

---

### Post by seattle vic on 2008-10-27
> **remu said:**
> Seattle Vic: Could you do me one more favour please. Go ahead and save this script and then run it. [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh). this will then post alsa debugging information out to a website. If you could post that, it would be great! I'm trying to figure out what Audio Codec is being used in your system. I am having sound issues even though we both are using the ICH9 Chipset.
Thanks!

Sure.  The laptop is currently packed up in my car and ready to head to the airport for its 1st business trip.  (The large 17" screen seemed like a good idea until I put it in it's case for travel...).  I'll (hopefully!) be able to hook up from my hotel room tonight and will send out the results.

---

### Post by kedmond on 2008-10-27
Just in case there's anyone out there looking for help with this problem:

I am on a Dell Latitude E6400 with an Intel Wifi Link 5300.

I am running Ubuntu 8.04 (Hardy Heron).  I did exactly what post #62 said, and rebooted.  The wifi light above my keyboard lit up while the kernel was loading, and left-clicking on the nm-applet in the menu bar (in Gnome) displays the accessible wireless networks quickly.

Thank you SO much to post #62!

-kedmond

---

### Post by seattle vic on 2008-10-28
> **remu said:**
> Seattle Vic: Could you do me one more favour please. Go ahead and save this script and then run it. [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh). this will then post alsa debugging information out to a website. If you could post that, it would be great! I'm trying to figure out what Audio Codec is being used in your system. I am having sound issues even though we both are using the ICH9 Chipset.
Thanks!

I tried to run the alsa script, but it got hung with the following msg:

Do you want to run this script? [y/n] : read: 263: Illegal option -e

I'll try and debug it tomorrow.

---

### Post by superstas on 2008-10-28
Acer Aspire 5930g intel 5100 works out of the box on Kubuntu 8.10 rc desktop amd64

---

### Post by R0r0 on 2008-10-29
> **remu said:**
> Seattle Vic: Could you do me one more favour please. Go ahead and save this script and then run it. [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh). this will then post alsa debugging information out to a website. If you could post that, it would be great! I'm trying to figure out what Audio Codec is being used in your system. I am having sound issues even though we both are using the ICH9 Chipset.
Thanks!

I have an Asus M51VR. I did a fresh install with Kubuntu 8.10 RC and my wifi seems to work. I recommend you to do a fresh install !

My sound card works perfectly and you can find my alsa debugging information on : [http://www.alsa-project.org/db/?f=5c7bf631956168cba3f6cdfd8945fca350f2e8f0](http://www.alsa-project.org/db/?f=5c7bf631956168cba3f6cdfd8945fca350f2e8f0)

---

### Post by remu on 2008-10-30
Okay, I know this isn't related to the Wifi. But anyone having sound issues, especially on the HP dv4, dv5, and dv7. Even if you have used to get a work around to fix the problem for you. Read this: [http://ubuntuforums.org/showpost.php?p=6068909&postcount=26](http://ubuntuforums.org/showpost.php?p=6068909&postcount=26). This actually fixes the issue without any nasty kernel option side effects. Or it did for me anyway.
Hope this helps.

---

### Post by kacike76 on 2008-11-01
Thank you remu.  I too have a clean install of Intrepid and got my sound working on my dv7 laptop.  The max volume is nowhere near what you get in vista, but it works.  Is there a way to get more volume?

---

### Post by kacike76 on 2008-11-01
I just did a clean install of Intrepid on my HP proliant dv7-1025nr laptop, and got almost everything working.  My wireless card is currently working but it is intermittent.  Sometimes on reboot, the wireless card is disabled and the only way to get the card to enable is to boot into vista, power down and then boot into ubuntu.  Is anyone having similar troubles with their wireless? Is there any command to reset the card without having to boot into windows. 


thank you.

---

### Post by remu on 2008-11-01
> **kacike76 said:**
> Thank you remu.  I too have a clean install of Intrepid and got my sound working on my dv7 laptop.  The max volume is nowhere near what you get in vista, but it works.  Is there a way to get more volume?

Open the volume control, then take the "Front", "Headphones", and "Master" to the maximum. Use PCM to control the volume in the future. To get your volume slider on your keyboard to control the audio, go to System>Pref>Sound, at the bottom, choose Alsa Mixer from the drop down box and click PCM to highlight it, then hit close. Hopefully that should fix it. Let me know if it does or doesn't.

As for the wireless, I am not having any problems on my system, so I don't know what to tell you, sorry.

---

### Post by kacike76 on 2008-11-12
Remu, does your microphone work with your dv4 laptop.  I got everything else working except for my mic.  I am unable to capture sound using the onboard HDA Intel sound card.  When setting the volume controls for capture i adjust the settings to unmute the microphone, but these setting are not retained.  I close the window and open it again and the microphone goes back to mute.  

Thank you

---

### Post by remu on 2008-11-12
kacike76, Yes, I got the microphone working. What I needed to do was go to the Volume control, and then under choose preferences. From there, I checked Digital Input Source. Once I did that, I had a new tab under the volume control window called "Options". Then, under the options tab, I chose Digital Mic 1 from the Digital Input source. After doing that my microphone now works.
Hope that helps you.

---

### Post by ma2k1 on 2008-11-29
Working here!

After I've installed Intrepid Ibex on my new work machine **Hp 6730s**
wireless Intel Corporation PRO/Wireless 5100 AGN was detected but isn't usable (wireless led --> yellow) and no wireless network was recognized.

Then I've installed firmware and downloaded compact wireless, as described in this thread by **theburningor** (pag.7), rebooted and this time all work great.
My and other wireless network was detected, wireless led are now blue and I can use my wireless connection (wpa2).

Great :)

---

### Post by lindylex on 2008-12-12
I am try to get the 5300 to work with.
Debian Lenny, Amd 64 bit
I am getting the &#8220;SIOCSIFFLAGS: Connection timed out&#8221; error after I run &#8220;ifconfig wlan0 up&#8221;

uname -a
Linux trabajar 2.6.26-1-amd64 #1 SMP Wed Nov 26 18:26:02 UTC 2008 x86_64 GNU/Linux

Has anyone with the same specs successfully installed this?

Thanks

[EDIT]
This is so easy to fix.

1. Compile a kernel >= 2.6.27
 -  If you use Debian use this tutorial on how to compile a kernel.
   [http://forums.debian.net/viewtopic.php?t=20789](http://forums.debian.net/viewtopic.php?t=20789)
 -  If you use Ubuntu use this.
   [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)
   
2.  Use this link to download the correct kernel
    [http://www.kernel.org/pub/linux/kernel/v2.6/](http://www.kernel.org/pub/linux/kernel/v2.6/)

3.  When you get to this command from the tutorials "make menuconfig", navigate to this part of the kernel configuration menu.
    Device Drivers/Network device support/Wireless LAN/
    + Scroll down and choose.
      Intel Wireless Wifi Next Gen AGN
    + Choose the following and place an star next to.
      Intel Wireless WiFi 4965AGN and Intel Wireless WiFi 5000AGN
    + Choose Exit at the bottom until you save and exit.
4.  Continue with the kernel compiling.

Work for me Debian Lenny, Linux trabajar 2.6.27.8 #1 SMP Sat Dec 13 01:18:36 EST 2008 x86_64 GNU/Linux, Intel Wireles 5300 AGN

[EDIT]

This .deb file can be used to install the kernel which supports the wifi 5X00 Intel Wifi cards.  This is for Debian Lenny 64 bit x86_64.

[http://mo-de.net/d/debian_lenny_intel_wifi_5X00_kernel_deb.tar.gz](http://mo-de.net/d/debian_lenny_intel_wifi_5X00_kernel_deb.tar.gz)

---

### Post by uniqueumang on 2008-12-14
Umm is your wireless button touch sensitive

---

### Post by lindylex on 2008-12-23
uniqueumang, are you asking me this question?  If so the answer is yes.  I touch the button to turn the wifi on and off if I want to.  I usually just leave it on.

---

### Post by rocketsquash on 2009-01-14
Hey guys!

Running Ubuntu Hardy on Acer 7730, and my wireless card wasnt working, followed this link, and in under 2 min it was working 100%, enjoy: [http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers]("http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers")

Just find out what kernel ur using by typing in: *uname -r* and then download the appropriate tar from the website.

Cheers

---

### Post by fallen04 on 2009-01-16
I am also having trouble getting wireless network working on my toshiba notebook. My notebook has the Intel 5100 driver. I can connect to a unsecured network, but I cant connect to my wpa secured wireless network. The wireless network works fine when I boot to Vista. I have pasted the results when running lshw -c network command in terminal mode. 

 *-network               
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 16
       serial: 00:1e:68:a4:6f:dc
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:47:e0:60
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=10.1.1.4 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3e:6b:f2:5c:06:45
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by hasinasi on 2009-01-17
What kind of secured network is it? 
There are several problems out there with WPA2 Enterprise networks. 
You can see more info in this bug: 
[https://bugs.launchpad.net/ubuntu/intrepid/+source/wpasupplicant/+bug/272185]("https://bugs.launchpad.net/ubuntu/intrepid/+source/wpasupplicant/+bug/272185")
My problems were fixed by using the workaround suggested by Dan Bracey on Jan 9. 
So in my case, it was not a driver issue. Let me know if you need more info. Good luck.

---

### Post by Julolidine on 2009-01-17
I followed the links on page 7, and still no luck.  It was working yesterday, and when I woke up today, it was not working anymore.  

lshw -c network shows the status of wlan0 as being DISABLED.  Any clue how to get it going again?

---

### Post by Adam Yee on 2009-02-20
Thanks again to 'theburningor' for his instructions to fix the Intel Wireless Wifi Link 5100 driver issue (see [here]("http://ubuntuforums.org/showpost.php?p=5754065&postcount=62"))!  I lost my wireless connection abilities a few days ago even though the latest driver was installed on my Intrepid.

What was key for me was going to [http://linuxwireless.org/en/users/Download#Wheretodownload]("http://linuxwireless.org/en/users/Download#Wheretodownload") and downloading the latest compat-wireless package.

---

### Post by Ubelha on 2009-03-18
What should i do?
I'm a newbie with linux i have ubuntu 8.10.
Please help me.

---

### Post by eliavv on 2009-04-18
sorry but i didn't understand no.7
what should i write in Konsol?

---

### Post by $$H3aT-MaCh1n3$$ on 2010-06-16
Hi there!!!:lolflag:

I'm using Backtrack 4 in Vmware Workstation. I'm able to do bridge connection that way i can access the web browser. I having trouble accessing and following the step "The Burningor" provide us. I already followed all the steps he gave us,but it doesn't seems to function. I actually erase and re-began everything again without being sucessful like 2 or 3 times already. I had been investigating for a while, and supposedly vmware workstation is not able to detect physical wifi cards meaning that as a consequence is not gonna be able to detect this one. I seriously would like for someone to confirm me this to be sure.

Here is some useful information:

> Uname -a
Linux bt 2.6.30.9 #1 SMO Dec1 21:51:08 EST 2009 i686 GNU/Linux

> iwconfig
lo no wireless extensions.

eth0 no wireless extensions 

This is what i get so it seems it is incompatible but for shure with this installation of some drivers and by compiling them i will be successful of course if this is what i think.

> ifconfig
eth0 Link encap:Ethernet HWaddr 00:0c:29:7f:bd:e4
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1118 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1093641 (1.0 MB) TX bytes:0 (0.0 B)
Interrupt:19 Base address:0x2000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

---

### Post by nogueira13 on 2010-08-16
Hi, I am trying to connect to a wireless network. I am able to connect, but the connection is too unstable. It keeps connected less than 2 minutes if I try to access a site or homepage. I don't know what is happening. My laptop is a Dell Inspiron 15 with Ubuntu 10.04 64 bits. I read in another Forum (Intel for windows vista) that it was an issue with the [Power Save Polling (PSP) causes connection issues with some access points. ]("http://support.intel.com/support/wireless/wlan/sb/CS-006205.htm")
 They suggest: "An optional workaround is to manually put the Wi-Fi adapter into  Continuously Aware Mode (CAM). This disables the PSP feature. The Wi-Fi  adapter can be put into CAM using the following methods:

[Intel® PROSet/Wireless WiFi Connection Utility]("http://www.intel.com/support/wireless/wlan/sb/CS-006205.htm#i")
[etwork Control Panel Applet (NCPA)]("http://www.intel.com/support/wireless/wlan/sb/CS-006205.htm#m")"

But I don't know how to disable this feature in Ubuntu Linux. May you help me shoing me in step by step? Perhaps it happens me to get a stable connection.
sorry for my poor English. My native language is Brasilian Portuguese.
Thanks in advance.
Antonio Carlos

---

