---
title: "Wireless on Toshiba A505 S6980"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by milesfromnowhere121 on 2009-11-08
Well, I have a Toshiba a505 s6980 laptop with Windows 7 on it. I want to get Ubuntu 9.10 installed into a partition. 

My first problem is that the wireless isn't working. I don't really know anything about how wireless works. I just know that the network lists don't show up when I click on the little icon on the top bar of the desktop.

I got this computer at bestbuy, and I think it has a Realtek® 802.11b/g/n wireless LAN but it could have something made by intel. I'm not sure. 

Lastly, I had a Asus EEE PC for about two years with Linux (about one year with Ubuntu) so I'm not afraid of the command line and whatever else.

---

### Post by phillw on 2009-11-08
> **milesfromnowhere121 said:**
> Well, I have a Toshiba a505 s6980 laptop with Windows 7 on it. I want to get Ubuntu 9.10 installed into a partition. 

My first problem is that the wireless isn't working. I don't really know anything about how wireless works. I just know that the network lists don't show up when I click on the little icon on the top bar of the desktop.

I got this computer at bestbuy, and I think it has a Realtek® 802.11b/g/n wireless LAN but it could have something made by intel. I'm not sure. 

Lastly, I had a Asus EEE PC for about two years with Linux (about one year with Ubuntu) so I'm not afraid of the command line and whatever else.


Hmm, puzzled  [http://ubuntuforums.org/showthread.php?t=1290848](http://ubuntuforums.org/showthread.php?t=1290848)

Try you lappie with the ethernet cable un-connected as it boots from the LiveCD. It's reported as working system.

/edit, yeah, seems like a working rig -->>  [http://ubuntuforums.org/showthread.php?t=1246732](http://ubuntuforums.org/showthread.php?t=1246732)

Phill.

---

### Post by milesfromnowhere121 on 2009-11-08
Well, that's really odd. I didn't have the eithernet cable plugged in at all. Maybe its because I was using Ubuntu 9.10 rather than 9.04? 

I might give it a shot with my old Ubuntu 8.10 disk (because I don't have a copy of 9.04 right now). 

Am I just forgetting something really elementary? Just click on the little icon on the top bar and select the network, right?

---

### Post by LewRockwell on 2009-11-08
> **phillw said:**
> Hmm, puzzled  [http://ubuntuforums.org/showthread.php?t=1290848](http://ubuntuforums.org/showthread.php?t=1290848)

Try you lappie with the ethernet cable un-connected as it boots from the LiveCD. **It's reported as working system.**

Correction:

A particular assembly in the Toshiba A505 Series is reported to work

Each model in a series may contain different internal components

Your hardware may or may-not be supported without additional modules

You might check out:```
lspci
```

.

---

### Post by milesfromnowhere121 on 2009-11-08
Well, I ran ```
lspci
``` and I got 

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
04:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
04:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
04:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
miles@miles-laptop:~/Downloads$ ^C
miles@miles-laptop:~/Downloads$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
04:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
04:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
04:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)


I think that the important line is 

03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

or possibly 

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

Now what?

---

### Post by Lateralis on 2009-11-08
```

uname -r
sudo lshw -C network
lspci -v

```

With *lspsci -v* it will just be necessary to see the entries for the network cards.  The information you get out of these three commands may be useful in helping diagnose the problem.  Note: that doesn't mean I will definitely be able to help! :P

---

### Post by pablo.aguilar on 2009-11-16
Take a look at this page:
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/401126]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126")

The driver rtl8192se_linux_2.6.0010.1020.2009_64bit + Method 2 worked for me

---

### Post by milesfromnowhere121 on 2010-01-10
PROBLEM SOLVED! 

For future reference, here is what I did.

1. Connect to the internet via a wired connection 
2. Download the driver pack [http://launchpadlibrarian.net/33927923/rtl8192se_linux_2.6.0010.1012.2009.tar.gz](http://launchpadlibrarian.net/33927923/rtl8192se_linux_2.6.0010.1012.2009.tar.gz)
(I found it using the link in pablo.aguilar's post)
3. extract the driver pack (for consistency, lets use your desktop)
4. Open a terminal and run
```
 sudo apt-get install build-essential linux-source-2.6.31
```

5. In terminal, use the cd command to go to the folder where you saved the driver pack (I used something like cd /home/miles/Desktop/rtl...)
You can use tab to autocomplete the cd command. 

6. In terminal, enter 
```
sudo make
```
```
sudo su
```
```
make install
```

7. Now restart your system and unplug the wired connection. It should be fixed.

I combined the instructions found at [http://www.thinkwiki.org/wiki/ThinkPad_11b/g/n_Wireless_LAN_Mini-PCI_Express_Adapter_II](http://www.thinkwiki.org/wiki/ThinkPad_11b/g/n_Wireless_LAN_Mini-PCI_Express_Adapter_II) with the drivers and instructions found at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126)

Thanks so much everybody. This makes my computer seem a lot more valuable. LINUX RULES

---

### Post by c.pfarher on 2010-03-11
I posted a solution here:
[http://kikipblog.blogspot.com/2010/03/realtek-8172-de-toshiba-a505-s69803-en.html]("http://kikipblog.blogspot.com/2010/03/realtek-8172-de-toshiba-a505-s69803-en.html")
good luck!

---

### Post by Gman Link on 2010-03-19
I have the same laptop model, but after following your directions, I got a Kernel Panic. 
Or the interface didn't appear after the initial Ubuntu icon. 

Is there an alternative solution?

---

