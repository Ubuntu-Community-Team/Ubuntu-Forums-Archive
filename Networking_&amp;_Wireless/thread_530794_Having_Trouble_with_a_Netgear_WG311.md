---
title: "Having Trouble with a Netgear WG311"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by shopmanual on 2007-08-20
I got Ubuntu up and running last night and it works very well. Today I decided to get a wireless PCI card. So I checked the list of compatible cards, and saw the WG311. So I got it, but now am having some trouble installing it. I downloaded the DEB files for ndiswrapper, including the graphic tool, but I click install new driver, and then navigate to the .inf file and click ok, and nothing happens. I tried the terminal installation as well, and that doesn't work. I also tried madwifi and went through the tutorial, but that didn't work either. Please let me know what I should do.

PS It also says that madwifi is included in Ubuntu, and that any madwifi compatible cards should work out of the box, but I couldn't find madwifi on my computer so I tried the manual install.

---

### Post by NinjaDuck on 2007-08-23
What error does the terminal give?

---

### Post by psyburn on 2007-08-23
madwifi is part of the linux-restricited-modules-common package.

If you did a manual install you are likely to have farked the madwifi setup.
Reinstalling  linux-restricited-modules-common package should fix the manual install problem.
A manual install of madwifi is only neccessary if you want to use things like Kisimet (advanced wireless scanning program)

I have a D-Link DWL-G650 v.C2 which uses madwifi.
It had worked immediately with 6.06 (Dapper), 6.10 (Edgy) and 7.04 (Fiesty)
I had tried to install the madwifi-ng myself and messed up madwifi
Like I stated above, reinstalling  linux-restricited-modules-common package should "fix" the manual install problem.

---

### Post by J1m on 2007-10-20
Hi,

I believe a bug has been filed for Gutsy Gibbon and the wg311 wireless card.  Can't find it at the minute but I know I saw it.  I think the card gets detected but no ATH0 device is created.

Or something XD

---

### Post by brightspark on 2007-10-21
Hi 

I have exactly the same problem with the netgear pci card, worked through all the help, nothing.

I have the driver installed (inf) because when I try and install again it says the driver is installed.

The computer does not see the wireless at all;

Please let me know if you find the answer !!

---

### Post by wibble on 2007-10-21
I'm having the exact same issues.

I installed a Netgear WG311 wireless card into my machine, then did a fresh install of Gutsy Gibbon.  The wireless card was not picked up (well it wasn't usable.  I could see the wireless card under "System->Preferences->Hardware Information").

I tried reinstalling the linux-restricited-modules-common package, that had no effect.

I installed the "ndiswrapper-common", "ndiswrapper-utils-1.9" and "ndisgtk" packages and attempted to install the driver using the "Administration->Windows Wireless Drivers" GUI (I obtained the driver from "ftp://downloads.netgear.com/files/wg311v3_1_0.zip").

I tried the INF files under WinXP and Win 2000, in both cases after clicking install nothing appeared to happen.

I had a look in the bug tracker and the closest i could find was: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/21471](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/21471)

---

### Post by wibble on 2007-10-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/155291](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/155291) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have created a bug report for this issue: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/155291](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/155291)

---

### Post by tpscan on 2007-10-26
I also have a NetGear WG-311 _V3_ WiFi card that is recognized HW but **not enabled** in networking **because of an error** adding it to the device list.  

Below are some diagnostic steps that show which problem occurs during boot, when the device fails to be _"inserted into the iwlist because of symbol error"_. 

lspci shows --> 04:09.0 Ethernet controller **wmaster0**: 
--> Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
which is correct and is a supported chipset.

WiFi Networking IS working because a WG-111 USB dongle (**wlan0**) is plugged in, enables, connects and allows access.

a quick i**_fconfig_** report shows the **wlan0** USB working, PCI **wmaster0** is not:

**wlan0**  (the NG WG111)   Link encap:Ethernet  HWaddr 00:0F:B5:CC:3B:79  
          inet addr:192.168.0.9  Bcast:255.255.255.255  Mask:255.255.248.0
          inet6 addr: fe80::20f:b5ff:fecc:3b79/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:897 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1302826 (1.2 MB)  TX bytes:17987 (17.5 KB)

**wmaster0**  (the NG WG3111v3) Link encap:UNSPEC  HWaddr 00-0F-B5-CC-3B-79-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

The error during boot up shows the WG311_v3 card is recognized hardware, but is not entered into the networking list because of a "Symbol error".

From the boot log files we see:
...
[I]Oct 23 15:49:42 toms-linux kernel: [   52.954405] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
Oct 23 15:49:42 toms-linux kernel: [   53.135051] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 23
Oct 23 15:49:42 toms-linux kernel: [   53.135057] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [APCJ] -> GSI 23 (level, low) -> IRQ 23
Oct 23 15:49:42 toms-linux kernel: [   53.135240] PCI: Setting latency timer of device 0000:00:10.2 to 64
Oct 23 15:49:42 toms-linux kernel: [   53.307409] ieee80211_init: failed to initialize WME (err=-17)
Oct 23 15:49:42 toms-linux kernel: [   53.336654] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
Oct 23 15:49:42 toms-linux kernel: [   53.336693] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
Oct 23 15:49:42 toms-linux kernel: [   53.336727] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
Oct 23 15:49:42 toms-linux kernel: [   53.336781] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
Oct 23 15:49:42 toms-linux kernel: [   53.337291] wmaster0: Selected rate control algorithm 'simple'
Oct 23 15:49:42 toms-linux kernel: [   53.385181] phy0: hwaddr 00:0f:b5:cc:3b:79, rtl8187 V1 + rtl8225
Oct 23 15:49:42 toms-linux kernel: [   53.385202] usbcore: registered new interface driver rtl8187[/I]

log files and probe reports available if needed.

Hope this helps resolve the issue.

TomS

Update:
Hmm -- I should make it clear that I am using the 64-bit version of 7.10.
 I actually went to run NDISwrapper for the Marvell chips and discovered you need to insure you have the 64-bit driver files.
Still fiddling ...

---

