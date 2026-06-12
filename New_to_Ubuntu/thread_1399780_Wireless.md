---
title: "Wireless"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by JakeFrederix on 2010-02-06
Another issue with wireless internet;
general problem layout;
1) I connect to my network
2) after some time (the time lapse varies) I get disconnected
3) a box appears asking me to enter the password for the network, which I do
4) the box appears another couple of times, I keep filling in the password
5) the box stops appearing, no wireless networks can be found because I am disconnected

I set up the network, and I know the password. (so that is not an issue)
Another laptop is perfectly able to connect to the network, even when I am not. (so again, the router, or internet configuration is not a problem)
When I restart my laptop, I am again able to get internet, but the problem will invariantly occur again.

Many thanks in advance,
Jake

---

### Post by Enigmapond on 2010-02-06
I had the same problem. I ended up installing wicd which is another network manger and it's run constant for over two weeks now without a glitch and actually the icon is better as well. If you install, it will uninstall the current network manager so I would get that into the cache just in case you have any problems but it works very well for me.

---

### Post by JiuJitsu500 on 2010-02-06
I suggest the same, but if it's a hardware issue or something else... obviously another manager won't help :) but, it's worth a try for sure... I did it too

---

### Post by 3rdalbum on 2010-02-06
Sometimes it will ask for the password because the card was unable to connect, and Network Manager thinks that the only reason why it can't connect is because of an incorrect password.

Rather than reboot, you could try using "modprobe" to remove the kernel module for your wireless card, and then reinsert it. For instance, my wireless card uses the "rtl8187" module:

```
sudo modprobe -r rtl8187
sudo modprobe rtl8187
```

I suggest checking Launchpad for any bug reports and workarounds for this problem, which will be particular to your card.

---

### Post by JakeFrederix on 2010-02-06
I tried installing the other networkmanager, and it gives me the same bogus vague remarks. Oh, but instead, this one suddenly stops recognising any wireless networks.

```
>lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Acer Incorporated [ALI] Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
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
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc Device 9712
01:05.1 Audio device: ATI Technologies Inc Device 970f
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev ff)
```I've also perused other messages in this forum with similar problems, and have already installed the drivers needed for broadcom using

```
>sudo apt-get install b43-fwcutter
```

Honestly, I'm at the end of my sanity. I'm already downloading a beta of Windows 7. That should tell you how messed up this situation is.

Jake

---

### Post by bkratz on 2010-02-06
Your wireless card is a

Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev ff)

It does not use b43, that is for Broadcoms


Here is a series of links for you to look at:

[http://ubuntuforums.org/showthread.php?t=1309605&highlight=AR928X](http://ubuntuforums.org/showthread.php?t=1309605&highlight=AR928X)
[http://ubuntuforums.org/showthread.php?t=1137780](http://ubuntuforums.org/showthread.php?t=1137780)
[http://ubuntuforums.org/showthread.php?t=1379148](http://ubuntuforums.org/showthread.php?t=1379148)

---

### Post by lotharmat on 2010-02-06
Please tell me you followed the advice and didn't purge your apt cache.

Theoretically you should be able to get network manager back if this is the case

---

### Post by JakeFrederix on 2010-02-06
uninstalled the driver for broadcom.
Installed both backport modules.
I'm posting this using the wireless network :D.
Still waiting for the 'disconnected' to come though.
I do notice the change however, the signal-strength is maximal (which is expected since I'm sitting two feet away from the router). The strength used to be 2 bars, instead of 4.

*yaaays slightly*

Jake

---

### Post by bkratz on 2010-02-06
> **JakeFrederix said:**
> uninstalled the driver for broadcom.
Installed both backport modules.
I'm posting this using the wireless network :D.
Still waiting for the 'disconnected' to come though.
I do notice the change however, the signal-strength is maximal (which is expected since I'm sitting two feet away from the router). The strength used to be 2 bars, instead of 4.

*yaaays slightly*

Jake

In the threads mentioned that strong signal is not a fluke! Congratulations and enjoy your wireless.


Sorry, I should have added please mark the thread solved with the thread tools above to help others find it.

---

