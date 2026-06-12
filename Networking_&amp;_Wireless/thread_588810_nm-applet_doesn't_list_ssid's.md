---
title: "nm-applet doesn't list ssid's"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by GriZzm0 on 2007-10-23
I've just managed to get my wlan working with ndiswrapper. I can connect to networks as long as I know the SSID. But for some weird reason I don't see any networks when I left-click the nm-applet icon unless I've connected to it once manually. Before I've connected to a network manually "iwlist wlan0 scan" won't show anything but once I've connected to a network it will show 6 diffrent networks.
How do I get all the nearby broadcasting SSID's to appear in the nm-applet list? And how can I list all SSID's with "iwconfig wlan0 scan"** _before_** I've connected to a network manually?

---

### Post by MegaJim on 2007-10-23
This is the same problem I had after updating to Gutsy from Feisty.

Its quite annoying as I have a 25 digit alphanumeric key and nm-applet will not remember the key when networks are entered manually.

For the moment, I would recommend uninstalling the network manager suite and instead using Wicd Manager (select WEXT driver).  It can be installed with a package manager after adding the repository listed on their download page ([http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)).

The Wicd applet can be configured to load on start and autoconnect to networks in range - works for me!  Let me know how you get on.

---

### Post by GriZzm0 on 2007-10-23
Thanks. It works, I guess. Not 100% sure if it finds the SSID's before I connect to one of them manually. I'll have to test that some more. ;) The tray icon ain't working thoo. :/

**Edit:**
Tried using tray-edgy.py instead of tray.py and it worked. However, it says "Not connected" when I use a wired connection. Works like a charm if I use a wireless connection. Thats perhaps how it's supposed to work?

---

### Post by GriZzm0 on 2007-10-24
Ok, tried it some now. And it's the same problem. It won't show any SSID's unless I connect to one of them manually first. It seams like I have to use one of the SSID's first to "activate" the wlan card.

---

### Post by Lambert on 2007-10-24
> **GriZzm0 said:**
> Ok, tried it some now. And it's the same problem. It won't show any SSID's unless I connect to one of them manually first. It seams like I have to use one of the SSID's first to "activate" the wlan card.

Your problem sounds more like a driver function problem. Check your syslog file for any output.

Also what chipset / windows driver are you using and are you using ndiswrapper from repos or compiled latest version?

---

### Post by GriZzm0 on 2007-10-24
The wlan drivers is called "WLAN miniCard D2301 & USB D1705" and was downloaded from [http://support.fujitsu-siemens.com/com/support/linkapplication.html?LNG=EN&ProductID=3733](http://support.fujitsu-siemens.com/com/support/linkapplication.html?LNG=EN&ProductID=3733) then chose "Windows XP media center". The .inf file is called "sis163u.inf". And yes, I downloaded ndiswrapper from the repo.

---

### Post by Lambert on 2007-10-24
> **GriZzm0 said:**
> The wlan drivers is called "WLAN miniCard D2301 & USB D1705" and was downloaded from [http://support.fujitsu-siemens.com/com/support/linkapplication.html?LNG=EN&ProductID=3733](http://support.fujitsu-siemens.com/com/support/linkapplication.html?LNG=EN&ProductID=3733) then chose "Windows XP media center". The .inf file is called "sis163u.inf". And yes, I downloaded ndiswrapper from the repo.

I'm going to quote from the [ndiswrapper site]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/").

> 
Important: Not all Windows drivers are tested / stable. If the Windows driver that you use is problematic, try alternate Windows drivers that others have tested, especially those in List. Always, try Windows XP drivers and if Windows XP drivers are not available, try Windows 2000/2003 drivers. Windows Vista drivers are not supported (yet) - using Windows Vista driver will result in many &#8216;unknown symbol&#8217; error messages when loading ndiswrapper. 

To identify the driver that you need from List, first identify the card you have with lspci and note the first column such as 0000:00:0c.0 and then find out the PCI ID of the card by running lspci -n and locating the entry corresponding to the first column of lspci output. The PCI ID is third column or fourth in some distributions and of the form 104c:8400. Now you need to get the Windows driver for this chipset. In the List, find out an entry for the same PCI ID, and download the driver corresponding to it. Unpack the Windows driver with unzip/cabextract/unshield tools, and find the INF file (.INF or .inf extension) and the SYS file (.SYS or .sys extension). If there are multiple INF/SYS files, you may look in the List if there are any hints about which of them should be used. Make sure the INF file, SYS file and any BIN files (For example, TI drivers use BIN firmware) files are all in one directory.


[The page showing the list of devices and drivers.]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/")

I suggest trying a different driver as it seems the current one you're using is the problem.

---

### Post by GriZzm0 on 2007-10-24
I don't think theres anything wrong with the driver as the network works. The only problem is that it doesn't list the nearby netwrosks unless I connect to one of them first. Once I've connected to one of them I can see all of them.

**Edit:** Trying to connect to a random network (it doesn't even have to exists) allows me to run iwlist wlan0 scan. Weird stuff.

---

