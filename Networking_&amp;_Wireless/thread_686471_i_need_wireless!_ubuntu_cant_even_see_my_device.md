---
title: "i need wireless! ubuntu cant even see my device"
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by Cew27 on 2008-02-03
i have an atheros network card in my laptop and ubuntu cant see it , how can i set it up, its rather annoying having to use ethernet with a laptop
please help

---

### Post by lswest on 2008-02-03
can you post the output of ```
lspci
``` should tell us if the card is recognized, if it is, then all we need is the right driver for it.

---

### Post by Cew27 on 2008-02-03
thanks you for your reply i have posted a few threads about this that have remained untouched, im really getting annoyed with this wireless issue

cew27@cew27-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
0a:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0a:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
0a:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0a:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
cew27@cew27-laptop:~$

---

### Post by lswest on 2008-02-03
no problem, always happy to help out^^
well, as i look at that output, i don't see anything that looks like it could be your card, do you by any chance know exactly what model it is?

---

### Post by Cew27 on 2008-02-03
Atheros
WLAN 	wlanwim2120vst.exe
2.0.0.12

---

### Post by kevdog on 2008-02-03
Is this a usb or pci device?

---

### Post by Cew27 on 2008-02-03
pci it is inside the laptop

---

### Post by Cew27 on 2008-02-03
is it possible to get it working?

---

### Post by jank on 2008-02-03
i also had a roblem with my atheros card so maybe my post will help you. But remember that you have a different model so you might have to change something. [http://ubuntuforums.org/showthread.php?t=662014](http://ubuntuforums.org/showthread.php?t=662014)

---

### Post by Cew27 on 2008-02-03
thanks, althaugh your wireless card was detected i cant detect mine

---

### Post by Cew27 on 2008-02-03
bump

---

### Post by jank on 2008-02-03
im not really sure if this will help, but I think you can use madwifi,
First open the terminal
```
sudo apt-get install build-essential
```
if you have not done it already
then download this file: [http://sourceforge.net/project/downloading.php?group_id=82936&use_mirror=mesh&filename=madwifi-0.9.3.3.tar.gz&20778782](http://sourceforge.net/project/downloading.php?group_id=82936&use_mirror=mesh&filename=madwifi-0.9.3.3.tar.gz&20778782)
and extract it to the directory you choose. Then open the terminal
```
cd "the directory you extracted it to"
```
then
```
make
```
then
```
sudo make install
```
if you get no errors reboot and see if it helps.

Sorry I couldn't make a complete terminal guide. Im still quite new and don't know it very well.

---

### Post by Cew27 on 2008-02-03
i have done that but still cant see the wireless

---

### Post by kevdog on 2008-02-03
If lspci doesnt detect the card, check either dmesg or the boot log for errors.  If nothing is listed to guide you to a solution, then Im sorry to say you are probably SH** out of luck for the internal device working with ubuntu.

---

### Post by Cew27 on 2008-02-04
never mind, i will get a newwireless card thats compatible with ubuntu althaugh this is a let down

---

### Post by kevdog on 2008-02-04
I understand your frustration -- I would be extremely disappointed also.  Just as a side note however, I would get an Atheros based chipset that is compatible with the madwifi drivers.  You will definitely be disappointed.

---

### Post by oldsmobile_mike on 2008-02-17
As others have mentioned, sometimes it's best to just try a different wireless card instead of pulling your hair out trying to get one to work.  A quick search on ebay turned up 177 matches for "mini pci wifi" just now.  Most of them in the sub-$20 range.  Personally I bought two before I found one that worked well.  The first one was an Intel 2200-based something-or-other, that while I was eventually able to get "working" after installing a bunch of ipw library stuff, it had compatibility issues with my Sager motherboard, that every two or three times I rebooted it would report a bus conflict.  My second attempt was more successful, a Lucent Orinoco-based model that was detected by the OS "right out of the box", and which I was able to get working perfectly with both the built-in Network Manager app, and WICD (after a little tweaking of the software).  For reference, this is the exact same card I bought, here:

[http://cgi.ebay.com/Orinoco-Wireless-Mini-PCI-802-11b-card-WIFI-GOLD-equiv_W0QQitemZ110224479898QQihZ001QQcategoryZ45003QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/Orinoco-Wireless-Mini-PCI-802-11b-card-WIFI-GOLD-equiv_W0QQitemZ110224479898QQihZ001QQcategoryZ45003QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

Note that I am not affiliated with the seller in any way, just wanted to confirm that even though it's only a b-model, the card works great under Linux.  :-)

As a side note, anybody need an Intel 802.11b/g wifi card?  Sell it to you real cheap.  ;-)

---

### Post by Cew27 on 2008-02-17
much appretiated 
dont suppose you could find me on in the uk that world work with my medion laptop, and with ubuntu/mint

---

### Post by oldsmobile_mike on 2008-02-17
> **Cew27 said:**
> much appretiated 
dont suppose you could find me on in the uk that world work with my medion laptop, and with ubuntu/mint

Um...  Well, [www.ebay.co.uk](www.ebay.co.uk) lists 37 different auctions right now:

[http://search.ebay.co.uk/search/search.dll?from=R40&_trksid=m37&satitle=mini+pci+wifi](http://search.ebay.co.uk/search/search.dll?from=R40&_trksid=m37&satitle=mini+pci+wifi)

I saw cards listed ranging from Intel, Atheros, Broadcom, Dell, etc.  I've heard that Broadcom are particularly difficult to set up, but you might reference the list of auctions to this list of cards reported to be compatible with Ubuntu:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Hope this helps!

---

### Post by Cew27 on 2008-02-17
your damn right it did thanks!

---

