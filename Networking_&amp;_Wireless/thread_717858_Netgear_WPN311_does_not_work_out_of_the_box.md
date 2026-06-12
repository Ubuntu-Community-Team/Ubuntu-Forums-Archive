---
title: "Netgear WPN311 does not work out of the box"
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by kmurray on 2008-03-07
I'm trying to get a Netgear WPN311 card working. I bought this card because the supported hardware wikipage says it works out of the box. I've searched the web and these forums for clues, but I'm stumped.

lspci says:
04:04.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

I've tried two versions of Ubuntu: 7.04 (Fiesty Fawn), and Hardy Heron (Alpha 5), without any success. My PC is a Dell XPS410N (came with Ubuntu pre-installed).

With Fiesty Fawn, the wireless interface doesn't show up in the Network Manager, and dmesg says:
[   17.703201] wlan: 0.8.4.2 (0.9.3.1)
[   17.720207] ath_pci: Unknown symbol _ath_hal_attach
[   17.720279] ath_pci: Unknown symbol ath_hal_process_noisefloor
[   17.720529] ath_pci: Unknown symbol ath_hal_computetxtime
[   17.720744] ath_pci: Unknown symbol ath_hal_mhz2ieee
[   17.720824] ath_pci: Unknown symbol ath_hal_detach
[   17.721185] ath_pci: Unknown symbol ath_hal_probe
[   17.721649] ath_pci: Unknown symbol ath_hal_init_channels
[   17.721820] ath_pci: Unknown symbol ath_hal_getwirelessmodes

Googling these messages shows up some bug reports, but many users say a kernel upgrade cured the problem, so I thought I'd try the latest and greatest Ubuntu.

After booting Hardy Heron, the wireless interface doesn't show up in the Network Manager either, and dmesg says:
[   30.794794] ath_hal: module license 'Proprietary' taints kernel.
[   30.809111] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   30.976478] wlan: 0.8.4.2 (0.9.3.3)
[   31.013431] ath_pci: 0.9.4.5 (0.9.3.3)
[   31.013519] PCI: Enabling device 0000:04:04.0 (0000 -> 0002)
[   31.013567] ACPI: PCI Interrupt 0000:04:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.017805] wifi%d: unable to attach hardware: 'Hardware didn't respond as expected' (HAL status 3)

Googling "HAL status 3" doesn't help. The only applicable bugreport on [www.madwifi.org](www.madwifi.org) has been closed, but the suggested resolution there does not fix my problem. There is a page on the madwifi.org site ([http://madwifi.org/wiki/UserDocs/Troubleshooting](http://madwifi.org/wiki/UserDocs/Troubleshooting)) which talks about problems with PCI bridges, but it doesn't seem to apply in my case.

So, maybe a free or semi-free driver for my card isn't going to work for me; let's try ndiswrapper. No probs, I apt-get ndiswrapper, and look on the Netgear CD for drivers. No luck. There's a 15Mb file labelled "setup.exe" in the drivers/bin subdirectory, but try as I might I can't get a driver out of it. I've tried cabextract, unshield, unzip without any success. I don't have access to a Windows box where I can run this CD, so it seems I am check-mated.

Fellow Ubuntites; my questions are:
1. How I can get a Netgear WPN311 working with free drivers?
2. How I can extract the driver from the setup.exe file?
3. Please recommend a wireless PCI card which will truly work "out of the box"

(thanks for reading this far)

---

### Post by kmurray on 2008-03-11
I'm currently trying to use ndiswrapper, but I haven't had any luck so far.
(I ended up installing wine so I could extract the windows drivers from the Netgear CD)

Typing
ndiswrapper -i wpn311.inf
gets me a complaint that wpn311 is already installed.

If I then type
ndiswrapper -l
I get the message that the driver is invalid.

I'm getting close to calling it quits on this. Can someone please suggest a wireless card that really does work out of the box? Please?

---

### Post by kmurray on 2008-03-26
For those who may google this thread; the resolution of my WPN311 problem was I returned it.

I couldn't get the madwifi or the ndiswrapper drivers to work, Google was no help, and I couldn't get anyone on this forum interested either.

---

### Post by michaelmoontaco on 2008-05-29
HOWTO-Configure WiFi With NetGear WPN311 on an Everex gPC in Ubuntu 8.04
Thu 29 May 2008 06:59:32 PDT 

This actually works, easily.

Hardware Installation:
Install the WPN311 wireless modem first (for Linux.  Install it last for Windows).
In the package manager search for "wifi"

Packages installation:
Install the packages for Windows Wireless Networking: Madwifi-tools (the ndiswrapper is here), ndisgtk, wifi-radar
Now you will have /System/Admin/Windows Wireless Drivers and Applications/Internet/WiFi Radar
Install Wine to run the Windows NetGear setup cd.
The Wine directories will be in the user directory as a hidden folder ".wine"

Wireless Interface Configuration:
Installation of the WPN311.inf driver:
Run the NetGear WPN311 cd, right-click on autosetup.exe and run it with Wine.
The installation will chug along then abort at the very end.  No worries.
Inspect:
/home/your username/.wine/drive_c/windows/inf/WPN311/WPN311.inf (You'll use this inf for windows network drivers applet)
(CAUTION: DO NOT USE /home/your username/.wine/drive_c/windows/inf/WPN311.inf in the parent directory.  IT WILL NOT BE VALID)

Wireless Modem Network Configuration:
Go to /System/Administration/Network application and configure "Wireless Connection" properties as follows:
	Disable roaming
	Enter Network Name ESSID your-network
	WPA Personal (WPA2 Personal is available, but I didn't use it)
	Enter the key
	Enable DHCP
	Click OK and let the configuration occur.
	
Go To /Systen/Administration/Network tools a ping around.  You should be able to ping 192.168.1.1 (Gateway) and other computers.

DONE!!!
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

I hope that this helps.

Best Regards, Mike

---

### Post by michaelmoontaco on 2008-05-29
Hi,

That didn't last long...  following a reboot, the WiFi was kaput.  This happened in both the Everex gPC and an ASUS A7NX-E PC.  Both were running Ubuntu 8.04.  It looks like the WiFi gods thought that I was a little to cheeky, just a little too smug for them.  

It looks like I'll have to pursue the WiFi sticky posts (and more).  

Maybe Ubuntu 8.10 will be the salvation.

To Be Continued...

Best Regards, Mike

[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

---

### Post by alillowr on 2008-06-26
> **michaelmoontaco said:**
> Hi,

That didn't last long...  following a reboot, the WiFi was kaput.  This happened in both the Everex gPC and an ASUS A7NX-E PC.  Both were running Ubuntu 8.04.  It looks like the WiFi gods thought that I was a little to cheeky, just a little too smug for them.  

It looks like I'll have to pursue the WiFi sticky posts (and more).  

Maybe Ubuntu 8.10 will be the salvation.

To Be Continued...

Best Regards, Mike

[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

I had recieved the same issue.  initially the instruction that were posted for the everex gpc worked.  but after a reset it is no longer working.  reset once and I just had to manually connect with the wifi application, no problem,  reset twice and I had to manually point "windows wirless drivers" app to the ini file, and ten manually connect.  reset a third time and now under the network app there are no more wirelles connectivity options.  just the wired or point to point.  So I can surely say that the "fix" did not fix

Now I am scouring the web for a solution.  trying ndiswrapper but no luck there either.

If anyone has a solution please post.

I am suprised that a hardware item that is supposed to natively be supported does not work, and how that there is not much support from others for something that fixes it.

---

