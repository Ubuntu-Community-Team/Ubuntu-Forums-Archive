---
title: "wlan0 disconnecting in intrepid"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by goodrench on 2008-10-28
I have upgraded to intrepid just a couple of days ago and my wireless card (intel 4965) I have all of the updates installed but I am having trouble staying connected with my network. I had no troubles in hardy heron.

About every minute my connection will be dropped and then reconnected in about 2-3 seconds.
I am using wicd as my network manager.
Here is the output from dmesg

```
[190875.374165] wlan0: associated
[190885.567312] wlan0: deauthenticated
[190885.602540] iwlagn: index 255 not used in uCode key table.
[190886.570158] wlan0: authenticate with AP 00:17:3f:9e:0a:3c
[190886.571862] wlan0: authenticated
[190886.571874] wlan0: associate with AP 00:17:3f:9e:0a:3c
[190886.574261] wlan0: RX ReassocResp from 00:17:3f:9e:0a:3c (capab=0x411 status=0 aid=1)
[190886.574270] wlan0: associated
[190952.582729] wlan0: No ProbeResp from current AP 00:17:3f:9e:0a:3c - assume out of range
[190952.592639] iwlagn: index 255 not used in uCode key table.
[190960.753296] wlan0: deauthenticated
[190967.548132] iwlagn 0000:04:00.0: PCI INT A disabled
[190967.552392] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[190967.787411] iwlagn 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[190967.787511] iwlagn 0000:04:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[190967.988303] Registered led device: iwl-phy0:radio
[190967.988345] Registered led device: iwl-phy0:assoc
[190967.988382] Registered led device: iwl-phy0:RX
[190967.988419] Registered led device: iwl-phy0:TX
[190968.045392] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[190970.250803] iwlagn 0000:04:00.0: PCI INT A disabled
[190970.401993] iwlagn 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[190970.402105] iwlagn 0000:04:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[190970.600952] Registered led device: iwl-phy0:radio
[190970.600999] Registered led device: iwl-phy0:assoc
[190970.601035] Registered led device: iwl-phy0:RX
[190970.601071] Registered led device: iwl-phy0:TX
[190970.663356] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[190971.749447] wlan0: authenticate with AP 00:17:3f:9e:0a:3c
[190971.749482] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[190971.768873] wlan0: authenticate with AP 00:17:3f:9e:0a:3c
[190971.768911] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[190971.962650] wlan0: authenticate with AP 00:17:3f:9e:0a:3c
[190971.962695] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[190972.160158] wlan0: authenticate with AP 00:17:3f:9e:0a:3c
[190972.160203] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[190972.362649] wlan0: authentication with AP 00:17:3f:9e:0a:3c timed out
[190972.362666] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[190974.848471] wlan0: authenticate with AP 00:17:3f:9e:0a:3c
[190974.851829] wlan0: authenticate with AP 00:17:3f:9e:0a:3c
[190974.851855] wlan0: authenticated
[190974.851861] wlan0: associate with AP 00:17:3f:9e:0a:3c
[190974.857031] wlan0: RX AssocResp from 00:17:3f:9e:0a:3c (capab=0x411 status=0 aid=1)
[190974.857042] wlan0: associated
[190974.863105] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[190985.100056] wlan0: no IPv6 routers present
[193996.692534] iwlagn: index 255 not used in uCode key table.
[197034.581628] iwlagn: index 255 not used in uCode key table.
[199114.322567] device wlan0 entered promiscuous mode
[199128.930107] device wlan0 left promiscuous mode
[200072.533317] iwlagn: index 255 not used in uCode key table.

```
I don't know if this may be a bug in the kernel driver or is something going on with my home router?
Above there is a line that says

```
[190885.567312] wlan0: deauthenticated
```

Does this mean that someone is deauthing my card?

---

### Post by pytheas22 on 2008-10-28
There's some weird stuff going on there.  It's especially curious that it says your card is going into monitor mode at one point--you weren't doing that on purpose, were you?

What is the 'lspci -nn' line for your card?  Did you google to see if others are having problems with your chipset on Intrepid?

Also, did you try rebooting your router?  It may help...

---

### Post by goodrench on 2008-10-28
"lspci -nn"

```
~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
04:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
0a:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
0a:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
0a:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
0a:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
0a:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)

```
I have tried rebooting my router.
No difference.
I am not trying to put the card into monitor mode.

---

### Post by pytheas22 on 2008-10-29
How did you get this card working in Hardy?  You must have compiled the driver from source, right, as this card should not have had support in Hardy?  You could try reinstalling using the same source that you used before and it would probably work better.  Is that possible?

---

### Post by Son of Silas on 2008-10-29
Same problem here... I have the 4965AGN chipset in a Dell 1525 Inspiron. I upgraded to Intrepid from Hardy, if/when i can actualy connect to a wireless network (I've tried 2 at work and at home) it takes ages, then disconnects. When it is connected the connection speed is terrible. In Hardy it works out of the box with the iwl4965 driver and nm-applet 0.6, I note Intrepid uses the iwlagn driver for my chipset instead and nm-applet 0.7

I wondered if it was the new nm-applet that was causing the issue so I tried Knetworkmanager instead - no joy. Can anyone tell me how I can disable the iwlagn driver and revert back to iwl4965 and see if that fixes it?

---

### Post by goodrench on 2008-10-29
> **pytheas22 said:**
> How did you get this card working in Hardy?  You must have compiled the driver from source, right, as this card should not have had support in Hardy?  

The card worked flawlessly in hardy. Monitor mode did not work before hardy but it was perfect in hardy right out of the box.
> 
You could try reinstalling using the same source that you used before and it would probably work better. Is that possible? 

If you mean go back to hardy, I really don't want to do that.

---

### Post by Son of Silas on 2008-10-29
I fired up intrepid this morning to find wireless via my 4965AGN is working perfectly. I have updates occuring without notification, so i don't know whats changed (or if this will last) but so far my issue seems fixed.

---

### Post by goodrench on 2008-10-29
just checked mine and it still seems to be disconnecting.

---

### Post by pytheas22 on 2008-10-29
goodrench: sorry, I thought that Hardy didn't have out-of-the-box support for your card, as I thought it was one of the newer Intel cards, but I guess not.

What is certain is that under Intrepid, your card is using the iwlagn driver, which did not exist on Hardy.  Hardy would have used a driver called iwl4965 for your card.  So perhaps switching back to the iwl4965 driver would help you, as Son of Silas suggests.

To test, run these commands:
```

sudo modprobe -r iwlagn iwl4965
sudo modprobe iwl4965
```

If you get error messages from those commands, please post them.  If you get no errors, wait a few seconds, and your wireless connection should be brought up.  See if you can connect under it with better stability.

Note that this would not be a permanent fix, as the changes from the commands above would be erased after you reboot.  If this solves the problem, however, we can make your system permanently use the iwl4965 driver in place of iwlagn.

---

### Post by goodrench on 2008-10-29
> **pytheas22 said:**
> goodrench: sorry, I thought that Hardy didn't have out-of-the-box support for your card, as I thought it was one of the newer Intel cards, but I guess not.

What is certain is that under Intrepid, your card is using the iwlagn driver, which did not exist on Hardy.  Hardy would have used a driver called iwl4965 for your card.  So perhaps switching back to the iwl4965 driver would help you, as Son of Silas suggests.

To test, run these commands:
```

sudo modprobe -r iwlagn iwl4965
sudo modprobe iwl4965
```

If you get error messages from those commands, please post them.  If you get no errors, wait a few seconds, and your wireless connection should be brought up.  See if you can connect under it with better stability.

Note that this would not be a permanent fix, as the changes from the commands above would be erased after you reboot.  If this solves the problem, however, we can make your system permanently use the iwl4965 driver in place of iwlagn.
excellent!
I will try it as soon as I get home tonight.

---

### Post by goodrench on 2008-10-29
Just curious.
What is the difference between the two drivers?

---

### Post by Son of Silas on 2008-10-29
hmmm..... My problem has returned. I am getting disconnected again from both the WPA n/w at home and the open n/w at work.... I'll try switching drivers.

---

### Post by Son of Silas on 2008-10-29
> **pytheas22 said:**
> goodrench: 
```

sudo modprobe -r iwlagn iwl4965
sudo modprobe iwl4965
```



That doesn't seem to unload the iwlagn driver? when I type the first line I am disconnected from my n/w, but upon issuing the second it reconnects again using iwlagn... any ideas?

---

### Post by pytheas22 on 2008-10-29
> Just curious.
What is the difference between the two drivers? 

I'm not positive what the difference is, but I think that iwlagn is a driver that supports the latest generation of Intel cards, and includes 11n support.  iwl4965 only supports 4965 chipsets and as far as I know doesn't support 11n mode.

> 
That doesn't seem to unload the iwlagn driver? when I type the first line I am disconnected from my n/w, but upon issuing the second it reconnects again using iwlagn... any ideas?

That's strange.  Does it give you any error messages when you try to unload iwlagn?  You could also try adding iwlagn to the blacklist:
```

echo 'blacklist iwlagn' | sudo tee -a /etc/modprobe.d/blacklist
```

Then reboot, and try to load iwl4965 again.  Unfortunately I'm not as familiar with Intrepid as I should be; there may have been some changes that make iwlagn not want to unload.

---

### Post by goodrench on 2008-10-30
I can't unload the iwlagn either. I have tried to blacklist the driver and that worked ok, but when I rebooted and tried to load the iwl4965 module I got an error saying that the module didn't exist.
When I run 

```
locate iwl4965 

```

This is what I get

```
/usr/src/linux-headers-2.6.27-7-generic/include/config/iwl4965.h
/usr/src/linux-headers-2.6.27-7-server/include/config/iwl4965.h

```

Does this mean that the module is installed? Or maybe available?
I can't believe that this would make it to the final release of intrepid.
Especially with all of these wireless cards out there.
Does anyone know if this has been reported as a bug?
I would really like to use the old driver again.

---

### Post by pytheas22 on 2008-10-30
Yeah, it looks like iwl4965 was not included in Intrepid...those two files that you found using 'locate' are just header files, not kernel modules.  They probably did this because iwlagn is supposed to replace iwl4965, but it's unfortunate that they didn't at least leave iwl4965 there, even if it's not used by default.

In principle, it should be possible to install the iwl4965 driver from source by compiling the compat-wireless stack, however. To do that, first download [this file]("http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2008-10-30.tar.bz2") and save it to your desktop.  Then run:
```

sudo apt-get install build-essential
cd ~/Desktop
tar xjvf compat-wireless-2008* 
cd compat-wireless-2008*
make
sudo make install
sudo make unload
sudo make load
```

Then reboot, and run these commands to unload iwlagn and load iwl4965:
```

sudo modprobe -r iwlagn
sudo modprobe iwl4965
```

In principle, this would work.  However (DISCLAIMER), I haven't had time to install Intrepid yet, and you can't compile the compat-wireless stack on the Hardy kernel (unless you use the compat-wireless-old source code), so I can't confirm that this will even build for you, let alone solve your problem.  In a worst case, it may break iwlagn.  But it *should* work, so if you don't mind a little risk, I'd give it a try.

---

### Post by goodrench on 2008-10-30
Great stuff pytheas22.
I have a busy weekend but I will definitely give it a try.
What's the worst that can happen?
Thanks again.

---

### Post by JGrubbs on 2008-10-30
My wife's Dell 1525 had no problems with 8.04, and was working okay with the beta 8.10 when I added the network-manager to the software sources, but when I removed the software sources for the final 8.10 her wireless stopped working after the upgrade.

---

### Post by pytheas22 on 2008-10-30
> What's the worst that can happen?

The worst is that you'd end with broken versions both of iwlagn and iwl4965.  But since iwlagn doesn't really work for you in the first place, the risk isn't huge.

EDIT: you could also try adding those network-manager repositories to your /etc/apt/sources.list file, as JGrubbs describes below.  If the issue is caused by NM, then that could help (in that case, using [wicd]("http://wicd.sourceforge.net") instead of NM would probably also help).

> 
 My wife's Dell 1525 had no problems with 8.04, and was working okay with the beta 8.10 when I added the network-manager to the software sources, but when I removed the software sources for the final 8.10 her wireless stopped working after the upgrade.

That's interesting.  Do you know if your wife's machine also has an Intel wireless card?  Also, what exactly do you mean by adding network-manager to the software sources--do you mean that you added a new repository to the sources list or something?

---

### Post by JGrubbs on 2008-10-30
For the network-manager to work during the beta and RC I added the following to my software sources:

deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid main

This made the network-manager work without any problems, but I removed that from the software sources to see if they fixed the network-manager in the final release.

---

### Post by Son of Silas on 2008-10-31
> **JGrubbs said:**
> My wife's Dell 1525 had no problems with 8.04, and was working okay with the beta 8.10 when I added the network-manager to the software sources, but when I removed the software sources for the final 8.10 her wireless stopped working after the upgrade.

The 4965AGN chipset is a cost option thats only available (in the UK at least) if you buy the windoze variant of the 1525. Had I stuck with the standard 11g chipset that Dell ships with the Ubuntu variant I probably wouldn't have had this grief :-)

I tried blacklisting the iwlagn driver... and as was rightly pointed out (after I had disabled it) iwl4965 isn't included in intrepid. Net result: I have been offline since, waiting to have access to a wired n/w.. hohum :-)

---

### Post by JGrubbs on 2008-10-31
My wife's 1525 has a Broadcom BCM4311 802.11b/g WLAN, it worked fine with Hardy, and even worked okay with the Intrepid beta and release candidate, but it only works now if I reboot the computer, it will find the wireless connection and connect, and stay connected untill I close the laptop, then it looses the connection and requires rebooting to connect again.

---

### Post by JGrubbs on 2008-11-01
I got this working today, but checking something I should have thought to check before. For some reason my WEP security key was changed to something totally different than what it was before the upgrade. I changed it back today, and now my wireless disconnects when the laptop goes to sleep, but I am able to reconnect by clicking on the icon and selecting the wireless connection again, without having to reboot.

---

### Post by Son of Silas on 2008-11-02
> **pytheas22 said:**
> 
```

sudo apt-get install build-essential
cd ~/Desktop
tar xjvf compat-wireless-2008* 
cd compat-wireless-2008*
make
sudo make install
sudo make unload
sudo make load
```

Then reboot, and run these commands to unload iwlagn and load iwl4965:
```

sudo modprobe -r iwlagn
sudo modprobe iwl4965
```


This doesn't seem to work... The link to the required file is down. :-(

I still have the same issues. I can stay connected for a while, then it justs freezes my PC if i try to copy any large amount of data over WiFi

---

### Post by goodrench on 2008-11-02
> **pytheas22 said:**
> Yeah, it looks like iwl4965 was not included in Intrepid...those two files that you found using 'locate' are just header files, not kernel modules.  They probably did this because iwlagn is supposed to replace iwl4965, but it's unfortunate that they didn't at least leave iwl4965 there, even if it's not used by default.

In principle, it should be possible to install the iwl4965 driver from source by compiling the compat-wireless stack, however. To do that, first download [this file]("http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2008-10-30.tar.bz2") and save it to your desktop.  Then run:
```

sudo apt-get install build-essential
cd ~/Desktop
tar xjvf compat-wireless-2008* 
cd compat-wireless-2008*
make
sudo make install
sudo make unload
sudo make load
```

Then reboot, and run these commands to unload iwlagn and load iwl4965:
```

sudo modprobe -r iwlagn
sudo modprobe iwl4965
```

In principle, this would work.  However (DISCLAIMER), I haven't had time to install Intrepid yet, and you can't compile the compat-wireless stack on the Hardy kernel (unless you use the compat-wireless-old source code), so I can't confirm that this will even build for you, let alone solve your problem.  In a worst case, it may break iwlagn.  But it *should* work, so if you don't mind a little risk, I'd give it a try.

Well, I tried it and it didn't go very well.
I had to reinstall the kernel but before I did I had to remove the folder /lib/modules/<kernel version>
then everything was back to normal.

It sure would be nice if they could just include an option through jockey or something where you could select what driver you want to use, or they could just put iwl4965 back into the kernel options.

Is this possible through jockey?

Should we submit this to ubuntu brainstorm or just file it as a bug?

I would think that with the intel drivers being as open that they are, there wouldn't be any situations like this.
I am no coder by any means but maybe it isn't quite as simple as it sounds to make these changes.

---

### Post by goodrench on 2008-11-02
Will I have to compile a custom kernel to get this working?
I really hope that I don't.
I have never had much luck compiling my own kernel.
I tried it back when the intel 4965 card was first supported in the kernel.
I ended up with a lot of my other hardware not working ie: sound and video.
I also like to use virtualbox which does not play nice with a customized kernel.
If I have to put up with a frequent disconnect for the next little while, then, so be it.
I would really like to see this fixed though.

---

### Post by pytheas22 on 2008-11-02
Sorry that the instructions didn't work, and that I didn't reply sooner.  The problem is that the file name changed.  Apparently it changes often.  To get the right file, go to [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/) and download the file called 'compat-wireless-2008 - [some date].tar.bz2 (this file should be the fourth one from the bottom).  Don't download the one with 'old' in its name.

After you've downloaded the correct file, try running:
```

sudo apt-get install build-essential
cd ~/Desktop
tar xjvf compat-wireless-2008* 
cd compat-wireless-2008*
make
sudo make install
sudo make unload
sudo make load
```

That should build the iwl4965 driver for you.  You should not have to compile a whole kernel just to get the iwl4965 driver.

And you all may indeed want to consider filing a bug report about this, because your cards should be working using the iwlagn driver.  That's ultimately what needs to be fixed; switching to iwl4965 is just an idea for a work around.

---

### Post by Son of Silas on 2008-11-03
When I type```

sudo make unload

```
I get:
```

Unloading mac80211...
FATAL: Module mac80211 is in use.
Unloading cfg80211...
FATAL: Module cfg80211 is in use.
make: *** [unload] Error 1
```

Any ideas?

Also, how do I file a bug report?

I really appreciate you taking time to help me with this, thank you :-)

---

### Post by goodrench on 2008-11-03
When I run sudo make load I get the following errors.

```
sudo make load

Loading ipw2100...
Loading ipw2200...
Loading libertas_cs...
FATAL: Error inserting libertas_cs (/lib/modules/2.6.27-7-generic/updates/libertas_cs.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading usb8xxx...
Loading p54pci...
WARNING: Error inserting mac80211 (/lib/modules/2.6.27-7-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting p54pci (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/p54/p54pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading p54usb...
WARNING: Error inserting mac80211 (/lib/modules/2.6.27-7-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting p54usb (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/p54/p54usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading adm8211...
WARNING: Error inserting mac80211 (/lib/modules/2.6.27-7-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting adm8211 (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/adm8211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading zd1211rw...
Loading rtl8180...
WARNING: Error inserting mac80211 (/lib/modules/2.6.27-7-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rtl8180 (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/rtl8180.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rtl8187...
WARNING: Error inserting mac80211 (/lib/modules/2.6.27-7-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rtl8187 (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/rtl8187.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading p54pci...
WARNING: Error inserting mac80211 (/lib/modules/2.6.27-7-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting p54pci (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/p54/p54pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading p54usb...
WARNING: Error inserting mac80211 (/lib/modules/2.6.27-7-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting p54usb (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/p54/p54usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading iwl3945...
WARNING: Error inserting mac80211 (/lib/modules/2.6.27-7-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting iwl3945 (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/iwlwifi/iwl3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading iwl4965...
WARNING: Error inserting mac80211 (/lib/modules/2.6.27-7-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting iwlagn (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/iwlwifi/iwlagn.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rtl8180...
WARNING: Error inserting mac80211 (/lib/modules/2.6.27-7-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rtl8180 (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/rtl8180.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rtl8187...
WARNING: Error inserting mac80211 (/lib/modules/2.6.27-7-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rtl8187 (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/rtl8187.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rtl8180...
WARNING: Error inserting mac80211 (/lib/modules/2.6.27-7-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rtl8180 (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/rtl8180.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rtl8187...
WARNING: Error inserting mac80211 (/lib/modules/2.6.27-7-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rtl8187 (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/rtl8187.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rt2400pci...
WARNING: Error inserting mac80211 (/lib/modules/2.6.27-7-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00pci (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/rt2x00/rt2x00pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rt2400pci (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/rt2x00/rt2400pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rt2500pci...
WARNING: Error inserting mac80211 (/lib/modules/2.6.27-7-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00pci (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/rt2x00/rt2x00pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rt2500pci (/lib/modules/2.6.27-7-generic/updates/rt2500pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rt61pci...
WARNING: Error inserting mac80211 (/lib/modules/2.6.27-7-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00pci (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/rt2x00/rt2x00pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rt61pci (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/rt2x00/rt61pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rt2500usb...
WARNING: Error inserting mac80211 (/lib/modules/2.6.27-7-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00usb (/lib/modules/2.6.27-7-generic/updates/rt2x00usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rt2500usb (/lib/modules/2.6.27-7-generic/updates/rt2500usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rt73usb...
WARNING: Error inserting mac80211 (/lib/modules/2.6.27-7-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00usb (/lib/modules/2.6.27-7-generic/updates/rt2x00usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rt73usb (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/rt2x00/rt73usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rndis_wlan...
Loading at76_usb...
Module ath_pci not detected -- this is fine
WARNING: Error inserting mac80211 (/lib/modules/2.6.27-7-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath5k (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/ath5k/ath5k.ko): Unknown symbol in module, or unknown parameter (see dmesg)
ath5k loaded successfully
Module bcm43xx not detected -- this is fine
WARNING: Error inserting mac80211 (/lib/modules/2.6.27-7-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting b43 (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/b43/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting mac80211 (/lib/modules/2.6.27-7-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting b43legacy (/lib/modules/2.6.27-7-generic/updates/drivers/net/wireless/b43legacy/b43legacy.ko): Unknown symbol in module, or unknown parameter (see dmesg)
b43 loaded successfully
b43legacy loaded successfully

```

---

### Post by pytheas22 on 2008-11-03
goodrench: it looks like something weird happened when you built the drivers, and mac80211.ko was not built correctly.  You could try compiling the driver again, or restart your computer.  Did you get the same error message mentioned by Son of Silas after you ran 'sudo make unload'?

Either way, for both of you, did you try restarting your computers?  Basically 'sudo make unload' and 'sudo make load' are just a way of reinserting the new drivers without restarting your computer, but restarting would have the same effect.  So after a restart, is your card still using iwlagn?  If it is, what happens if you run:

```
sudo modprobe -r iwlagn iwl4965
sudo modprobe iwl4965
```
> 
Also, how do I file a bug report?

Go to [here]("https://launchpad.net/ubuntu/+filebug/+login"), create a launchpad account, and you will then be able to file a report.   I couldn't find any reports for this issue (I didn't search exhaustively but I looked pretty hard), so one of you should definitely file a report.  Include your 'lspci -nn' output in the report.

---

### Post by goodrench on 2008-11-03
I just updated some new kernel stuff and upon reboot, checked dmesg and found this.

```
[   50.625610] iwlagn 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   50.625725] iwlagn 0000:04:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[   50.625930] firmware: requesting iwlwifi-4965-2-lbm.ucode
[   50.867424] Registered led device: iwl-phy0:radio
[   50.867467] Registered led device: iwl-phy0:assoc
[   50.867498] Registered led device: iwl-phy0:RX
[   50.867528] Registered led device: iwl-phy0:TX
[   50.909687] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   52.825354] r8169: eth0: link down
[   52.826153] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   54.922365] iwlagn 0000:04:00.0: PCI INT A disabled
[   55.707144] iwlagn 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   55.707258] iwlagn 0000:04:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[   55.917505] Registered led device: iwl-phy0:radio
[   55.917547] Registered led device: iwl-phy0:assoc
[   55.917582] Registered led device: iwl-phy0:RX
[   55.917618] Registered led device: iwl-phy0:TX
[   55.950445] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   56.597895] wlan0: authenticate with AP 00:17:3f:9e:0a:3c
[   56.597927] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   56.607015] wlan0: authenticate with AP 00:17:3f:9e:0a:3c
[   56.607049] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   56.608891] wlan0: authenticated
[   56.608903] wlan0: associate with AP 00:17:3f:9e:0a:3c
[   56.608909] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[   56.630131] wlan0: authenticate with AP 00:17:3f:9e:0a:3c
[   56.632384] wlan0: authenticated
[   56.632396] wlan0: associate with AP 00:17:3f:9e:0a:3c
[   56.635077] wlan0: RX AssocResp from 00:17:3f:9e:0a:3c (capab=0x411 status=0 aid=1)

```

I see iwlagn and request for firmware iwlwifi-4965-2-lbm.ucode
I don't know if this is relevant at all.
I just thought I would post it.

---

### Post by pytheas22 on 2008-11-03
> I see iwlagn and request for firmware iwlwifi-4965-2-lbm.ucode
I don't know if this is relevant at all.
I just thought I would post it.

Yeah, so it's still trying to use iwlagn.  That may simply be because it defaults to iwlagn.  However, since you installed iwl4965 manually, that module should now exist on your system and you should be able manually to load it by typing:
```

sudo modprobe -r iwlagn iwl4965
sudo modprobe iwl4965
```

What happens if you type that?  Is your card brought up using iwl4965?  You can check the output of 'lshw -C Network' to see which module it's using.

---

### Post by goodrench on 2008-11-03
using the modprobe commands still loads the iwlagn driver

Here is the output from 'lshw -C Network'

```
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:46:79:cd
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.121 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

```


Now the wireless doesn't seem to be disconnecting like it was before.
here is the output from 'dmesg'
I belive the numbers at the beginning of each line have to do with time.
Before it would disconnect once every few minutes.

```
[ 1717.270198] mac80211-phy0: failed to remove key (0, 00:17:3f:9e:0a:3c) from hardware (-16)
[ 1717.276498] mac80211-phy0: failed to remove key (1, ff:ff:ff:ff:ff:ff) from hardware (-16)
[ 1721.743254] cfg80211: Using static regulatory domain info
[ 1721.743264] cfg80211: Regulatory domain: US
[ 1721.743268] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1721.743275] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
[ 1721.743281] 	(5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[ 1721.743287] 	(5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[ 1721.743293] 	(5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[ 1721.743299] 	(5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[ 1721.743305] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
[ 1721.743310] cfg80211: Calling CRDA for country: US
[ 1721.827973] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[ 1721.827986] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[ 1721.828093] iwlagn 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 1721.828107] iwlagn 0000:04:00.0: setting latency timer to 64
[ 1721.828139] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[ 1721.874934] iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
[ 1721.876976] phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 1721.878656] iwlagn 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 1721.878958] firmware: requesting iwlwifi-4965-2-lbm.ucode
[ 1722.105402] Registered led device: iwl-phy0:radio
[ 1722.105445] Registered led device: iwl-phy0:assoc
[ 1722.105478] Registered led device: iwl-phy0:RX
[ 1722.105509] Registered led device: iwl-phy0:TX
[ 1722.130165] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1725.312470] wlan0: authenticate with AP 00:17:3f:9e:0a:3c
[ 1725.314199] wlan0: authenticated
[ 1725.314208] wlan0: associate with AP 00:17:3f:9e:0a:3c
[ 1725.317713] wlan0: RX AssocResp from 00:17:3f:9e:0a:3c (capab=0x411 status=0 aid=1)
[ 1725.317721] wlan0: associated
[ 1725.342880] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1727.635691] iwlagn 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 1727.834769] Registered led device: iwl-phy0:radio
[ 1727.834809] Registered led device: iwl-phy0:assoc
[ 1727.834844] Registered led device: iwl-phy0:RX
[ 1727.834876] Registered led device: iwl-phy0:TX
[ 1727.860227] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1727.981028] wlan0: deauthenticating by local choice (reason=3)
[ 1730.120563] iwlagn 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 1730.324939] Registered led device: iwl-phy0:radio
[ 1730.324981] Registered led device: iwl-phy0:assoc
[ 1730.325014] Registered led device: iwl-phy0:RX
[ 1730.325045] Registered led device: iwl-phy0:TX
[ 1730.359909] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1731.474610] wlan0: authenticate with AP 00:17:3f:9e:0a:3c
[ 1731.474642] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 1731.476476] wlan0: authenticated
[ 1731.476488] wlan0: associate with AP 00:17:3f:9e:0a:3c
[ 1731.476493] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[ 1731.553058] wlan0: authenticate with AP 00:17:3f:9e:0a:3c
[ 1731.558800] wlan0: authenticate with AP 00:17:3f:9e:0a:3c
[ 1731.558822] wlan0: authenticated
[ 1731.558828] wlan0: associate with AP 00:17:3f:9e:0a:3c
[ 1731.563981] wlan0: RX AssocResp from 00:17:3f:9e:0a:3c (capab=0x411 status=0 aid=1)
[ 1731.563992] wlan0: associated
[ 1731.590921] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1742.112530] wlan0: no IPv6 routers present
[ 4224.730028] CE: hpet increasing min_delta_ns to 22500 nsec

```

This is definately much better than it was before.
I will test for monitor mode later.
The part about failing to remove key from hardware I have been getting since I tried an early beta of intrepid.
I suspect it is caused by the iwlang driver.
I was booting intrepid from a usb key but when I rebooted into hardy I still got the errors.
I hope this is not a serious issue.

---

### Post by pytheas22 on 2008-11-03
I'm not sure what the bit about the failure to remove key means, but it's not actually causing any problems that you're aware of, right?

If things are indeed working now, then it must have been because you rebuilt the iwlagn driver.  I guess you didn't need iwl4965 after all; you just needed a more recent version of iwlagn (built with the source code released a few days ago).  Please let us know if this continues to work for you.

---

### Post by goodrench on 2008-11-03
> **pytheas22 said:**
> I'm not sure what the bit about the failure to remove key means, but it's not actually causing any problems that you're aware of, right?

If things are indeed working now, then it must have been because you rebuilt the iwlagn driver.  I guess you didn't need iwl4965 after all; you just needed a more recent version of iwlagn (built with the source code released a few days ago).  Please let us know if this continues to work for you.

I think you are right. The key thing doesn't seem to be causing any problems that I know of. I will definitely post if I have any more issues.
Many thanks for all of your help.

---

### Post by coffecook on 2008-11-05
I had the same problem but did not want to spend too much time on it. I solved it by simply reinstalling the system. After that the wlan still didn't work. I then updated my system - and it worked.

---

### Post by goodrench on 2008-11-05
Well...
For the last couple of days, dmesg has not been flooded with the wireless errors that were there before but after doing some updates today (Nov. 5 2008) they are back.
Seems to be much of the same from before.

```
[  264.069899] wlan0: authenticate with AP 00:17:3f:9e:0a:3c
[  264.069931] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[  264.071765] wlan0: authenticated
[  264.071778] wlan0: associate with AP 00:17:3f:9e:0a:3c
[  264.071784] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[  264.096470] wlan0: authenticate with AP 00:17:3f:9e:0a:3c
[  264.103541] wlan0: authenticate with AP 00:17:3f:9e:0a:3c
[  264.103572] wlan0: authenticated
[  264.103578] wlan0: associate with AP 00:17:3f:9e:0a:3c
[  264.116909] wlan0: RX AssocResp from 00:17:3f:9e:0a:3c (capab=0x411 status=0 aid=1)
[  264.116921] wlan0: associated
[  264.138353] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  268.455253] [drm] Initialized drm 1.1.0 20060810
[  268.465218] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  268.465237] pci 0000:00:02.0: setting latency timer to 64
[  268.465508] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  268.679969] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
[  274.632517] wlan0: no IPv6 routers present
[  478.280800] iwlagn: Unaligned address = 10eab64e
[  478.281683] wlan0: deauthenticated (Reason: 6)
[  478.396935] wlan0: direct probe to AP 00:17:3f:9e:0a:3c try 1
[  478.399036] wlan0 direct probe responded
[  478.399047] wlan0: authenticate with AP 00:17:3f:9e:0a:3c
[  478.403203] wlan0: authenticated
[  478.403217] wlan0: associate with AP 00:17:3f:9e:0a:3c
[  478.405643] wlan0: RX ReassocResp from 00:17:3f:9e:0a:3c (capab=0x411 status=0 aid=1)
[  478.405652] wlan0: associated
[  678.285588] iwlagn: Unaligned address = 10eaac4e
[  678.286317] wlan0: deauthenticated (Reason: 6)
[  679.280154] wlan0: direct probe to AP 00:17:3f:9e:0a:3c try 1
[  679.282297] wlan0 direct probe responded
[  679.282310] wlan0: authenticate with AP 00:17:3f:9e:0a:3c
[  679.285222] wlan0: authenticated
[  679.285232] wlan0: associate with AP 00:17:3f:9e:0a:3c
[  679.287592] wlan0: RX ReassocResp from 00:17:3f:9e:0a:3c (capab=0x411 status=0 aid=1)
[  679.287601] wlan0: associated
[  769.506836] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[  878.160464] iwlagn: Unaligned address = 7559e4e
[  878.162797] wlan0: deauthenticated (Reason: 6)
[  879.160094] wlan0: direct probe to AP 00:17:3f:9e:0a:3c try 1
[  879.162269] wlan0 direct probe responded
[  879.162280] wlan0: authenticate with AP 00:17:3f:9e:0a:3c
[  879.165230] wlan0: authenticated
[  879.165240] wlan0: associate with AP 00:17:3f:9e:0a:3c
[  879.167572] wlan0: RX ReassocResp from 00:17:3f:9e:0a:3c (capab=0x411 status=0 aid=1)
[  879.167582] wlan0: associated
[ 1079.835189] iwlagn: Unaligned address = 7e3da4e
[ 1079.835907] wlan0: deauthenticated (Reason: 6)
[ 1080.830342] wlan0: direct probe to AP 00:17:3f:9e:0a:3c try 1
[ 1080.832471] wlan0 direct probe responded
[ 1080.832525] wlan0: authenticate with AP 00:17:3f:9e:0a:3c
[ 1080.835495] wlan0: authenticated
[ 1080.835509] wlan0: associate with AP 00:17:3f:9e:0a:3c
[ 1080.838938] wlan0: RX ReassocResp from 00:17:3f:9e:0a:3c (capab=0x411 status=0 aid=1)
[ 1080.838948] wlan0: associated
[ 1279.860240] iwlagn: Unaligned address = 282a804e
[ 1279.861089] wlan0: deauthenticated (Reason: 6)
[ 1280.860148] wlan0: direct probe to AP 00:17:3f:9e:0a:3c try 1
[ 1280.862268] wlan0 direct probe responded
[ 1280.862279] wlan0: authenticate with AP 00:17:3f:9e:0a:3c
[ 1280.865277] wlan0: authenticated
[ 1280.865287] wlan0: associate with AP 00:17:3f:9e:0a:3c
[ 1280.867616] wlan0: RX ReassocResp from 00:17:3f:9e:0a:3c (capab=0x411 status=0 aid=1)
[ 1280.867624] wlan0: associated
[ 1337.090689] mtrr: no MTRR for d0000000,10000000 found
[ 1340.415545] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
[ 1356.463694] CPU0 attaching NULL sched-domain.
[ 1356.463712] CPU1 attaching NULL sched-domain.
[ 1356.532599] CPU0 attaching sched-domain:
[ 1356.532610]  domain 0: span 0-1 level MC
[ 1356.532614]   groups: 0 1
[ 1356.532621] CPU1 attaching sched-domain:
[ 1356.532624]  domain 0: span 0-1 level MC
[ 1356.532627]   groups: 1 0

```

---

### Post by pytheas22 on 2008-11-05
> For the last couple of days, dmesg has not been flooded with the wireless errors that were there before but after doing some updates today (Nov. 5 200 they are back.

Chances are that it's because the updates that you installed gave you a new kernel image (I think the updates that I installed a few hours ago included a new kernel actually), which would have replaced your manually-installed version of iwlagn with the stock module from the repositories--which does not appear to work well for you.

So that means that you would have to recompile iwlagn again from source, using the instructions in post #27.  After doing that and rebooting, do things still not work?

---

### Post by goodrench on 2008-11-06
I will test it tonight and post my results

---

### Post by Lord Mauve on 2008-11-08
I also had problems with my Intel 4965 AG/AGN after the upgrade to Intrepid. I couldn't get it to associate with my encrypted network, but it could associate with the unencrypted one. I *think* I've now got it working. I did this by setting the fw_restart4965 option for the iwlagn module.

You can do this by adding

```
options iwlagn fw_restart4965=1
```

to /etc/modprobe.d/options and then 

```
modprobe -r iwlagn && modprobe iwlagn
```

---

### Post by goodrench on 2008-11-08
> **Lord Mauve said:**
> I also had problems with my Intel 4965 AG/AGN after the upgrade to Intrepid. I couldn't get it to associate with my encrypted network, but it could associate with the unencrypted one. I *think* I've now got it working. I did this by setting the fw_restart4965 option for the iwlagn module.

You can do this by adding

```
options iwlagn fw_restart4965=1
```

to /etc/modprobe.d/options and then 

```
modprobe -r iwlagn && modprobe iwlagn
```

If this does not go well, is there a way to revert back to the old settings?

---

### Post by binary.koala on 2008-11-08
thanks, fw_restart seems to work!

my symptoms were that after suspend or stand-by i _would be able_ to connect to any network but the connection would drop after a short while, and no iwlagn reload would help, only reboot. 
now it already stays on longer then before!

> **Lord Mauve said:**
> I also had problems with my Intel 4965 AG/AGN after the upgrade to Intrepid. I couldn't get it to associate with my encrypted network, but it could associate with the unencrypted one. I *think* I've now got it working. I did this by setting the fw_restart4965 option for the iwlagn module.

You can do this by adding

```
options iwlagn fw_restart4965=1
```

to /etc/modprobe.d/options and then 

```
modprobe -r iwlagn && modprobe iwlagn
```

---

### Post by pytheas22 on 2008-11-08
Thanks for pointing this out, Lord Mauve!  I don't have one of these cards myself so I was just going by what I was reading on the Internet and the little I know about these things...
```

If this does not go well, is there a way to revert back to the old settings? 
```

If you just remove the line 'options iwlagn fw_restart4965=1' from /etc/modprobe.d/options and reboot, it should set you back to the default settings, as far as I know.

---

### Post by joehill on 2008-11-11
I just did the routine, daily upgrades today (in Intrepid), and after the kernel updated, my wireless stopped functioning and hasn't worked since.  It doesn't detect any networks at all, even though I know lots are available in my building.  I've tried with the Intel 4965 card I have as well as a BCM4318 and neither can detect any networks.  I tried rebuilding the drivers as suggested above and then rebooting but nothing has changed.  I really wish I could use wireless in Intrepid!  This is a big step backwards to me and I'm considering reinstalling Hardy.

---

### Post by joehill on 2008-11-11
Oops, the problem is really with the Intel card--the external Broadcom had a different problem--I needed to reinstall the firmware cutter after upgrading to Intrepid.  So I'm back to the original problem--the internal Intel wireless chip.

---

### Post by pytheas22 on 2008-11-11
joehill: have you tried reloading the iwlagn driver with the 'fw_restart4965=1' option?  In other words, run these commands:
```

sudo rmmod iwlagn
sudo modprobe iwlagn fw_restart4965=1
```

Then wait a few seconds and see if your Intel card works.  If it does, run this command to make the fix permanent:
```

echo 'options iwlagn fw_restart4965=1' | sudo tee -a /etc/modprobe.d/options
```

If the wireless still doesn't work, what is the output of:
```

modinfo iwlagn
sudo iwlist scan
dmesg | grep -e iwl -e wlan
lshw -C Network
```

---

### Post by goodrench on 2008-11-11
> **joehill said:**
> I just did the routine, daily upgrades today (in Intrepid), and after the kernel updated, my wireless stopped functioning and hasn't worked since.  It doesn't detect any networks at all, even though I know lots are available in my building.  I've tried with the Intel 4965 card I have as well as a BCM4318 and neither can detect any networks.  I tried rebuilding the drivers as suggested above and then rebooting but nothing has changed.  I really wish I could use wireless in Intrepid!  This is a big step backwards to me and I'm considering reinstalling Hardy.

You say you did the upgrade?
I am concidering installing a fresh copy of intrepid to see if that takes care of the issues with the intel 4965.

---

### Post by goodrench on 2008-11-13
I did a fresh install two days ago and it seems to have solved my issues with iwlagn anD dmesg.
Dmesg in no longer flooded with errors and my wireless is no longer disconnecting.
It must have been an issue with the upgrade.
I think this will be the last time I do an upgrade.
From now on I will be doing fresh installs only.

---

### Post by pytheas22 on 2008-11-13
> I think this will be the last time I do an upgrade.
From now on I will be doing fresh installs only.

I came to that conclusion a year ago, after my own series of botched upgrade attempts.  If you [keep /home on its own partition]("http://www.psychocats.net/ubuntu/separatehome"), it's really easy to do fresh installs without having to reconfigure anything afterwards beyond apt-getting a few applications.

---

### Post by goodrench on 2008-11-14
> **pytheas22 said:**
> I came to that conclusion a year ago, after my own series of botched upgrade attempts.  If you [keep /home on its own partition]("http://www.psychocats.net/ubuntu/separatehome"), it's really easy to do fresh installs without having to reconfigure anything afterwards beyond apt-getting a few applications.

I agree about the home partition. This is the only way to install a system.
Especially if you do it like this

[http://mybrainrunslinux.com/node/2](http://mybrainrunslinux.com/node/2)

---

### Post by xnid on 2008-11-14
I have the same problem on my Dell Inspiron M1530 with a fresh install of 8.10. I also have the PRO/Wireless 4965 AG or AGN [Kedron] Network Connection. 

The problem only occurs on a open network, not at home where I have WPA connection. 

I tried [PHP]sudo rmmod iwlagn
sudo modprobe iwlagn fw_restart4965=1[/PHP] but it did not work for me :(

---

### Post by pytheas22 on 2008-11-14
xnid: have you tried connecting to multiple open networks?  If you can connect to your network at home without a problem but not to one particular open network, I'd suspect that there's an issue with the open network itself, not your wireless card.  Are you sure it's not filtering MAC addresses or using some other kind of security?  Can you connect with the same computer in Windows?

---

### Post by xnid on 2008-11-21
Thank you for your reply pytheas22.

It seems that there is some problem with the AP that I tried to connect to. It works fine now :)

---

