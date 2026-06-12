---
title: "Ndiswrapper CNET USB CWD-854 version F"
date: 2006-10-17
forum: Networking &amp; Wireless
---

### Post by Ba|der on 2006-10-17
I need help to install my wireless USB-adapter.

Here is a list of most of my TS.

I first tried to just insert the adapter, but it did not appear in the network program. Then I tried the repository "deb [http://ubuntu.lupine.me.uk/](http://ubuntu.lupine.me.uk/) dapper main" and it probably failed to install properly so I think I got it removed again.

I've also been looking at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Some info from the TS;
>tail /var/log/messages
[...]
Oct 17 18:14:04 ibuddie kernel: [17180498.440000] usb 3-3: USB disconnect, address 6
Oct 17 18:14:14 ibuddie kernel: [17180508.760000] usb 3-3: new high speed USB device using ehci_hcd and address 7

At 18:14:04 I unplugged the cwd-854 ver. F, and at 18:14:14 I plugged it back in.

I used the rt2500usb.inf from the 2K directory on the CD that came with the product. I also tried the XP version.

>lspci and >lspci -n
(EDIT: Removed output of commands above)

It seems the device is not detected with lspci. I removed the adapter and reran lspci and it still gave the same output.

<EDIT:>
>lsusb:
Bus 003 Device 008: ID 148f:2573 Ralink Technology, Corp.
[...]
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)
This ID is on several adapterts on the list, but not together with the CWD-854. Should a driver from one of the other cards with same ID work?
</EDIT>
>sudo ndiswrapper -i rt2500usb.inf
Installing rt2500usb
>ndiswrapper -l
Installed ndis drivers:
rt2500usb               driver present

And it does not say hardware present. I also used the GUI Windows Wireless Drivers (ndisgtk). It also just installed the driver and says Hardware: NO.

I deinstalled the RT2500 and rt2500-source, but I wonder if there might be left an old driver that came then I compiled the rt2500 source. How can I check that and eventually keep it from loading if it does so?

From [http://www.ubuntuforums.org/showthread.php?t=151562](http://www.ubuntuforums.org/showthread.php?t=151562) it seems like Sood have the same problem.
Any other tips to get this working?

UPDATE:
I installed the rt73 driver instead (Had to install it on windows and to get the file)

> ndiswrapper -l
Installed ndis drivers:
rt73            driver present, hardware present

>sudo depmod -a
>  sudo modprobe ndiswrapper
Gave no output so I figure they ran OK.

ifconfig shows lo and eth0, but no wireless  device.

So I'm probably a bit closer to a solution althoug using the GUI network and ifconfig does not list my card...

---

### Post by Ba|der on 2006-10-17
Wee! :)

After some reboots, and deactivating the eth0 card, and changing from channel 13 to 6 on the router I got it to work!

---

