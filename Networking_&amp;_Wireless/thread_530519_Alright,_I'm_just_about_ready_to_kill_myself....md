---
title: "Alright, I'm just about ready to kill myself..."
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by Dinchamion on 2007-08-20
This is bloody impossible!! :mad: I recently bought a wireless router and two adapters so we can make a home network. It worked flawlessly in Windows, however the license won't permit me to work with it, so I decided to fire up good ol' Ubuntu again.

I spent the whole damn day with trying to figure out how to make wireless work in Feisty. I managed to set up ndiswrapper, load the drivers with it (the ones I got on a CD with the adapters), and it is NOT WORKING! :( ndiswrapper -l comes back with the message that the driver is loaded and the hardware is present, but no wlan connection in the network manager, and the system says that the wlan0 interface doesn't exist. However, I didn't get a single error message during installation or boot, I just can't use the adapter.

It's an MSI US60SE adapter, and a fresh Feisty install. I'm pretty much stuck, because my computer is the only one that uses SATA, so I can't even get out my hd to update somewhere else or at least put stuff on it, and without internet connection... well, I can't live without internet connection.

My eyes are popping out from staring at my PDA all day to search for howtos, but I couldn't find a single solution yet.

Somebody please, help me!

---

### Post by jakev383 on 2007-08-20
Did you also install ndiswrapper-utils?
I've never heard of your wireless adapter, but if it uses the Broadcom chipset you may need to set a blacklist:
```

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

```
Lastly, try these commands:
```

sudo depmod -a
sudo modprobe ndiswrapper


```

---

### Post by bmartin on 2007-08-20
I did some Google searching and it appears to be an Atheros chipset. First, run **sudo update-pciids**, then try using **lspci** and look for output that refers to an Atheros chipset or your WiFi device.

---

### Post by l33t_3lv3n_g33k on 2007-08-20
Your card isn't listed on the NDISwrapper page under the [List of cards known to work]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/"), but that doesn't mean it won't.  

It's a good sign that ndiswrapper -l shows the driver as installed and hardware present.  

The wireless adapter isn't always installed at wlan0.  I've seen them at eth1 and ra0.  Run iwconfig in the command line and it should tell you which network interface is your wireless adapter.
```
iwconfig
```

---

### Post by Dinchamion on 2007-08-20
It is a USB adapter, so lspci doesn't help much... anyway, lsusb comes back with the following:

```
Bus 002 Device 002: I'D 0cf3:0002 Atheros Communications Inc.
```

dmesg | grep ndis:

```
[   16.273667] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   16.703371] ndiswrapper: driver athfmwdl (,12/05/2003,1.00.001) loaded
[   16.703698] ndiswrapper (miniport_init:265): assuming WDM (non-NDIS) driver
[   16.703720] usbcore: registered new interface driver ndiswrapper
```

lsmod | grep ndis:

```
 ndiswrapper     194608  0
usbcore     134280   6 ndiswrapper,xpad,usbhid,ehci_hcd,ohci_hcd
```

iwconfig:

```
lo      no wireless extensions
```

sudo ndiswrapper -l

```
athfmwdl : driver installed
            device (0CF3:0002) present
```

sudo ndiswrapper -m

```
module configuration already contains alias directive
```

These are my outputs... did I forget to include something?

---

### Post by bmartin on 2007-08-20
I've done a little forum searching. There should be a .bin file included with your drivers, perhaps ar5523.bin. Whatever the name is, it needs to be in your ndiswrapper driver's directory. There used to be a program to do this for you, but it's now considered obsolete.

For example, if you driver's name is **athfmwdl** and your bin file is ar5523.bin, you'd want to put the bin file at:
/etc/ndiswrapper/athfmwdl/ar5523.bin

---

### Post by dasunst3r on 2007-08-20
As far as I know, Atheros chipsets should use the *madwifi* driver.  With a wired connection, try issuing this command in the terminal: *sudo apt-get install hostapd madwifi-tools*

More info: [https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi](https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi)

---

### Post by Dinchamion on 2007-08-20
I tried copying the .bin file to the directory, but no effect. In fact, I did the whole thing with the other driver I have as well, same results. I can see the led flashing on the adapter, as if it's working, but it doesn't show up anywhere, and obviously unusable.

I'll try the madwifi now... if it were to work, it'd be pretty ironic seeing as I'm pretty damn mad by now... :P

---

### Post by Dinchamion on 2007-08-21
No change so far... :( Still trying to get it work, now it's a day to go mad about madwifi.

... but if I cannot get this done, I'm pretty much screwed. Can't work, have no money to buy another license for Windows (or to buy another adapter or card for that matter)... Meh. :mad:

---

### Post by wieman01 on 2007-08-21
Does scanning yield any results? That's usually a good indicator whether wireless works or not:
> iwlist scan
And also post the contents of:
> sudo gedit /etc/network/interfaces

---

### Post by s3a on 2007-08-21
> **Dinchamion said:**
> No change so far... :( Still trying to get it work, now it's a day to go mad about madwifi.

... but if I cannot get this done, I'm pretty much screwed. Can't work, have no money to buy another license for Windows (or to buy another adapter or card for that matter)... Meh. :mad:
If nothing works, use your local craiglist to sell your items and buy some that you know will work for sure. Check the Ubuntu Wiki or NDISwrapper's list of functional devices. That way, you'll lose only a bit of money in exchange for functionality. I recommend you go for those that run out of the box as they will give you no headaches.

---

### Post by wieman01 on 2007-08-21
> **s3a said:**
> If nothing works, use your local craiglist to sell your items and buy some that you know will work for sure. Check the Ubuntu Wiki or NDISwrapper's list of functional devices. That way, you'll lose only a bit of money in exchange for functionality. I recommend you go for those that run out of the box as they will give you no headaches.
Very true actually. Don't waste your time.

---

### Post by Dinchamion on 2007-08-21
I went back to ndiswrapper, since 1) madwifi just doesn't work, or if it does, it bloody well hides it :P;2) ndiswrapper actually sees my adapter, just something isn't right.

When I do sudo ndiswrapper -v, I get:

```
utils Error: no version specified
```

I downloaded the ndiswrapper package from a mirror and installed on my computer. I cannot compile the source, because I don't have the ability to transfer that much files (kernel headers, libc6, etc) to my computer without a wired connection (which I can't use on my computer, because the dls modem and the wifi router is a storey below my room)... I have to use a 1,44 floppy, so only small files play.

Anyway, I downloaded a bunch of packages and tried them out. Same result: ndiswrapper installs without a problem, windows driver both through the gui and the command line installs fine, the feedback is what you'd expect: driver installed, hardware present.

However, the adapter doesn't show up anywhere else. sudo lshw -C network comes back empty (not a character whatsoever), lsusb shows my adapter and it's device ID... I'm suspecting something is wrong with my ndiswrapper installation, but I can't figure out what. I know it should return with the version number, but it doesn't.

I tried search for this error, but no luck, in terms of working solution for me. Again, I can't compile it myself because I'm unable to install the needed packages.

---

### Post by Dinchamion on 2007-08-21
Well, I got the thing working! :D Thank God, i was near my limits really... had to compile ndiswrapper manually (managed to do it... heh), and from that point on it worked like a charm.

However, if you guys could point me in the right direction, the network manager applet only allows me to use WEP (hex) or WEP (ascii), but my network is configured to use WPA-PSK. For now, I was able to connect, but wouldn't want to reconfigure it every time I reboot or even worse, reinstall every time. How could I make these network settings permanent and automatically loaded/used?

As I said, I'm using WPA-PSK (was using WPA2, but my PDA doesn't like it, so went back to WPA), with TKIP, static IP addresses and SSID broadcasting.

---

### Post by wieman01 on 2007-08-21
> **Dinchamion said:**
> Well, I got the thing working! :D Thank God, i was near my limits really... had to compile ndiswrapper manually (managed to do it... heh), and from that point on it worked like a charm.

However, if you guys could point me in the right direction, the network manager applet only allows me to use WEP (hex) or WEP (ascii), but my network is configured to use WPA-PSK. For now, I was able to connect, but wouldn't want to reconfigure it every time I reboot or even worse, reinstall every time. How could I make these network settings permanent and automatically loaded/used?

As I said, I'm using WPA-PSK (was using WPA2, but my PDA doesn't like it, so went back to WPA), with TKIP, static IP addresses and SSID broadcasting.
If the Windows driver and your card support WPA, you should see the option in Network Manager now... If you don't, you can always check out my tutorial (signature).

---

