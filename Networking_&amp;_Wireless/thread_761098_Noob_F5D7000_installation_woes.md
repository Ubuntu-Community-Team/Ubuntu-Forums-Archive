---
title: "Noob F5D7000 installation woes"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by adamtheestimator on 2008-04-20
I'm an absolute NOOB to Ubuntu/Linux, but I have installed Xubuntu on my daughters' 450mhz machine.
Now I am trying to install my Belkin F5D7000 wireless card, and I seem to be stuck.
No freezing, no error messages...just no connection.
The Act light is on but nobody is home. (Link is not on...)
I've run the following commands according to what I've seen asked of many-a-noob by the wise Uber-Ubuntu-ers.
Here's what I've got so far:

**lspci -n**

00:00.0 0600: 1106:0598 (rev 04)
00:01.0 0604: 1106:8598
00:07.0 0601: 1106:0686 (rev 15)
00:07.1 0101: 1106:0571 (rev 06)
00:07.2 0c03: 1106:3038 (rev 06)
00:07.4 0600: 1106:3057 (rev 10)
00:08.0 0300: 1002:4755 (rev 9a)
00:0a.0 0280: 1814:0301


**iwconfig**

lo        no wireless extentions

wmaster0  no wireless extentions

wlan0     IEEE 802.11g ESSID:""
          Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
          Retry min limit:7  RTS trh:off  Fragment thr=2346 B
          Link Quality:0 Signal Level:0 Noise Level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0  Missed beacon:0


**ndiswrapper -l**

rt61 : driver installed
        device (1814:0301) present (alternate driver: rt61pci)


**lshw -C network**

*-network
	description: Wireless interface
	product: RT2561/RT61 802.11g PCI
	vendor: RaLink
	physical id: a
	bus info: pci@0000:00:0a.0
	logical name: wmaster0
	version: 00
	serial: 00:11:50:db:ee:f7
	width: 32 bits
	clock: 33MHz
	capabilities: pm bus_master cap_list logical ethernet physical wireless
	configuration: broadcast=yes driver=rt61pci latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11g


I've followed the instructions that KEVDOG provided (thanks for tryin', KEVDOG!), but I am lost.
What am I doing wrong?
What have I missed?
Thanks in advance for your help!
Oh yeah!  I'm running Xubuntu Gutsy Gibbon 7.10...

---

### Post by Paris Heng on 2008-04-21
Why u install the NDSW? The Belkin driver is already in there (inside the Kernel) >>  zd1211.

---

### Post by adamtheestimator on 2008-04-21
Thanks for the quick response, Paris!

The reason I did *any* of this is because I (like a lot of Ubuntu users) am a recent convert (almost) to Ubuntu.  In a Windows machine, when you put a new card in the back of your desktop, Windows recognizes that and tries to install the drivers for you (basically, all you have to do is click next a couple of times).  

I first tried to install the F5D8000, because I have a Belkin pre-N router and it would be smokin' fast, but when I read up on how to install, it seemed Terminal and a manual install was the way, and that the pre-N card was fraught with problems.  So trying to stay in the Belkin family, I also found that this card (F5D7000) was supposed to install pretty much out of the box.  It didn't.  'Install out of the box' to me is the Windows install.  

I guess I need to go back to square one and try it again, and not in Terminal.  Huh?

---

### Post by adamtheestimator on 2008-05-14
:redface: Is there any special magical lines of Terminal commands that I need to enter to get rid of what I have already set up whilst using the "how-to" that KevDog provided? :-k

---

### Post by ubume2 on 2008-06-14
I don't know what kind of hardware the F5D7000 is. I have a Belkin wireless usb adapter. It is a F5D7050 driver. As it turns out I did not have to install the driver.

Primarily, I followed Kevdog's HowTo with a few changes. I uninstalled the driver's installed by ndiswrapper, and uninstalled ndiswrapper.  I found out I could get wireless on Live CD. Here is my post in Kevdog's thread.

[http://ubuntuforums.org/showthread.php?t=571188&page=51](http://ubuntuforums.org/showthread.php?t=571188&page=51)

Basically, I found that if you had problems with network manager you will have problems with WICD. So manual configuration was the way to go for me.

I think besides making changes in /etc/rc.local, I made a couple of changes in /etc/network/interfaces.

Wieman01 had a howto on setting up WPA encryption. I don't use WPA encryption, but between the content of Wieman01's how to and kevdog's, I came to my solution.

---

