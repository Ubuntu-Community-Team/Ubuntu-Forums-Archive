---
title: "Netathw windows driver installed -- Cannot scan for networks"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by smooveg on 2008-06-29
It seems I was able to successfully install the ndiswrapper windows driver netathw, but Network Manager does not seem to be able to scan for networks. What do I seem to be missing??

Thanks in advance for the help!

PS - I'm running Hardy

Here's some output:

scott@scott-laptop:~$ ndiswrapper -l
netathw : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

----------

scott@scott-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

-----------

scott@scott-laptop:~$ iwlist ath0 scanning
ath0      No scan results

---

### Post by pytheas22 on 2008-06-29
It looks like you haven't blacklisted the native Atheros drivers, so they're still trying to control your card.  Otherwise the interface name should be wlan0, not ath0.  Open a terminal and type:

```
sudo gedit /etc/modprobe.d/blacklist
```

and add to the file that pops up these lines:
```

blacklist ath_pci
blacklist wlan
blacklist ath_hal
blacklist ath_rate_sample
```

then save the file, reboot and see if you have any luck.

By the way, are you positive that you need ndiswrapper for this card?  I know there are a few exceptions, but in general Atheros cards should work very well in Linux using native drivers.

---

### Post by smooveg on 2008-06-29
Worked great! I only had ath_pci blacklisted.

You are correct -- the usual recommendation is to use the Linux madwifi driver with Atheros chipsets, but I wanted to try something different (fresh install of Hardy).

The nice thing about using Ndiswrapper is that I didn't have to worry about downloading the driver from code, just used Synaptic (except for using ndiswrapper itself to install the Windows driver).

---

### Post by pytheas22 on 2008-06-29
With most Atheros chipsets, you shouldn't have to download any code.  You should be able to plug the card in and have it "just work."  You may need to check a box first saying that you don't mind using non-free software, since the Atheros drivers rely on closed-source firmware I think...unless you're Richard Stallman, you probably don't care that much.  But there are still some Atheros cards that require the latest release of the drivers, meaning you have to build madwifi from source.

Anyway, ndiswrapper is a fine solution too and I'm glad you're all set.

---

