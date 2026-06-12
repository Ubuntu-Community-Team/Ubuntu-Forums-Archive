---
title: "How to make a wireless modem connection w/ Lubuntu"
date: 2014-03-01
forum: Networking &amp; Wireless
---

### Post by ra7411 on 2014-03-01
How do I set this up?  I'm new to this o/s. 

The modem is an Actiontec c1000a.
The laptop is a Dell D400 and has previously had wireless hookups w/ this modem.

Thanks

---

### Post by ajgreeny on 2014-03-01
Can you show us the output of **lspci** in terminal, please or if it's a USB modem **lsusb**.  That should tell us the chipset of the adapter.

---

### Post by ra7411 on 2014-03-01
> **ra7411 said:**
> How do I set this up?  I'm new to this o/s. 

The modem is an Actiontec c1000a.
The laptop is a Dell D400 and has previously had wireless hookups w/ this modem [under xp].

Thanks


Here's the entire terminal output:

```
ra@ubuntuRA:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
01:01.0 CardBus bridge: Texas Instruments PCI7510 PC card Cardbus Controller (rev 01)
01:01.1 CardBus bridge: Texas Instruments PCI7510/7610 CardBus Bridge (rev 01)
01:01.2 FireWire (IEEE 1394): Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller
01:01.3 System peripheral: Texas Instruments PCI7410/7510/7610 PCI Firmware Loading Function
01:03.0 Network controller: Broadcom Corporation BCM4309 802.11abg Wireless Network Controller (rev 03)

xxxend
```

---

### Post by wildmanne39 on 2014-03-01
Please do:
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```
Reboot

---

### Post by wildmanne39 on 2014-03-01
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by ra7411 on 2014-03-01
> **Wild Man said:**
> Please do:
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```
Reboot


After   [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get purge bcmwl-kernel-source ran, I got:

[/FONT][/COLOR]TrueType core fonts for the Web EULA                                         
 &#9474;                                                                              
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                            
 &#9474;                                                                              
 &#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement          
 &#9474; ("EULA") is a legal agreement between you (either an individual or a         
 &#9474; single entity) and Microsoft Corporation for the Microsoft software          
 &#9474; accompanying this EULA, which includes computer software and may include     
 &#9474; associated media, printed materials, and "on-line" or electronic             
 &#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your         
 &#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be       
 &#9474; bound by the terms of this EULA. If you do not agree to the terms of         
 &#9474; this EULA, you may not use the SOFTWARE PRODUCT.

I've been seeing that alot lately. What is it about?

Then...

ra@ubuntuRA:~$ sudo apt-get install linux-firmware-nonfree
[sudo] password for ra: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ra@ubuntuRA:~$ 


I have no idea what's going with this thing.

---

### Post by wildmanne39 on 2014-03-01
This > rueType core fonts for the Web EULA
&#9474;
&#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE
&#9474;
&#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement
&#9474; ("EULA") is a legal agreement between you (either an individual or a
&#9474; single entity) and Microsoft Corporation for the Microsoft software
&#9474; accompanying this EULA, which includes computer software and may include
&#9474; associated media, printed materials, and "on-line" or electronic
&#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your
&#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be
&#9474; bound by the terms of this EULA. If you do not agree to the terms of
&#9474; this EULA, you may not use the SOFTWARE PRODUCT.
you should have only received that after trying to install microsoft fonts, not from the command you were ask to run.

To except the EULA you have to hit tab.
This:
```
ra@ubuntuRA:~$ sudo apt-get install linux-firmware-nonfree
[sudo] password for ra:
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ra@ubuntuRA:~$ 
```usually means you have software center and the terminal open at the same time.

Reboot your computer and run the commands again by copy and paste for accuracy.
Thanks

---

### Post by ra7411 on 2014-03-01
Thanks for info on getting rid of that EULA.
I did the  command line items again, all looked right.
Rebooted, and magically, a message about a wireless connection being available appeared.
Of course, I still can't get Chromium to recognize it and bring up webpages - do you know how to fill out the blanks on the wireless setup?

SSID: centurylink7969
mode: infrastructure (vs ad hoc)
bssid: <blank?>
device mac address: < I used the same as the one on the wired connection's address entry >
cloned mac address: blank

IPv4 settings
method: automatic (dhcp)
all else blank

IPv6 settings
method automatic
all else blank

wireless security
security wpa & wpa2 personal
pw from modem label, right?

The modem has:
security type:  wpa2-aes
key/passphrase: <alphanumerics>

Look right?
What else needs to be done?

Thanks

---

### Post by wildmanne39 on 2014-03-01
Set your settings to match the screenshots, network manager should have found your network automatically did it? In net work manager make sure security is set to wpa/wpa2. 

After you make the changes reboot and if you can not connect copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by ra7411 on 2014-03-01
[ATTACH]250811[/ATTACH]> **Wild Man said:**
> Set your settings to match the screenshots, network manager should have found your network automatically did it? In net work manager make sure security is set to wpa/wpa2. 

After you make the changes reboot and if you can not connect copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by wildmanne39 on 2014-03-02
According to the information you posted you have not changed your wireless settings in network manager to match the screenshots that I attached.

When it started showing networks available did you enter your password?
Thanks

---

### Post by ra7411 on 2014-03-02
I did post the [wireless-info.txt]("http://ubuntuforums.org/attachment.php?attachmentid=250811&d=1393725074") output file, but I have finally stumbled into getting the wireless connection to work.
1] I went into BIOS and changed "wireless control from f2 -----something, to "application" - I doubt this is what fixed it.
2]  I messed with the &#8220;fan&#8221; symbol in lower right next to time. Wireless conns. showed up: Centurylink7969 (that I set up), "CLCerise" and "Elizabeth", and somehow I activated my centurylink wireless connection. It works.

Question: is it likely to be able to use the wireless connects in hotels, coffee shops etc?

Thanks for the help.

---

### Post by wildmanne39 on 2014-03-02
You should be able to connect to other wifi hotspots but possibly not all.
Glad it is working!

---

### Post by ra7411 on 2014-03-03
Thanks for the help - much appreciated.

---

