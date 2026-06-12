---
title: "Atmel AT76C505, NDISWrapper"
date: 2014-06-29
forum: Networking &amp; Wireless
---

### Post by terry16 on 2014-06-29
I've been running Ubuntu 14.04 LTS on my desktop with no problems--except for one:  I have it connected via an ethernet connection.  I have an old usb wireless adapter--and I have the CD-ROM. There doesn't appear to be a linux-based driver for it, so I installed "Windows Wireless Drivers" NDISWrapper from the Ubuntu Software Center, but it does not appear anywhere else.  When I check back at the software center, it is listed as installed (complete with a green checkmark); when I look in the dash/home section, it is not listed as installed.  If I type in its name(s), nothing appears.  When I look in the system settings window, it is not listed.  In short, I appear to have successfully installed the program, but I cannot find a way to make it do anything.  I've searched this forum and elsewhere, but I cannot find a solution to this particular problem.  Any help would be greatly appreciated.

---

### Post by gordintoronto on 2014-06-29
Drivers work completely differently in Linux than in Windows.  Run this command: lsusb
and copy/paste the line which shows the wireless adapter. If you boot with the Ethernet cable disconnected, do you get a network icon on the top line, toward the right? (I have several wireless adapters, and they all "just work" without needing to install a driver.)

---

### Post by terry16 on 2014-06-29
Thanks for your reply.  When I reboot without the ethernet cable connected, it simply says that I am disconnected.
When I run lsusb, it recognizes that the device is attached to the usb port.
My REAL problem is that I cannot get the NDISWrapper program to launch and do its thing.

---

### Post by mörgæs on 2014-06-29
Remember to

> **gordintoronto said:**
> 
copy/paste the line which shows the wireless adapter.

---

### Post by terry16 on 2014-06-29
The line that shows the wireless adapter is this:  
Bus 002 Device 002: ID 1915:2233 Nordic Semiconductor ASA Linksys WUSB11 v2.8 802.11b Adapter [Atmel AT76C505]

Again,  my difficulty is that I cannot get ndiswrapper to launch (run) in order  to use the drivers I already have on CD-ROM.  I have a feeling that it  is something very easy that I am simply missing.  How do I get  ndiswrapper to launch?

---

### Post by Vladlenin5000 on 2014-06-29
> **terry16 said:**
> The line that shows the wireless adapter is this:  
Bus 002 Device 002: ID 1915:2233 Nordic Semiconductor ASA Linksys WUSB11 v2.8 802.11b Adapter [Atmel AT76C505]

Again,  my difficulty is that I cannot get ndiswrapper to launch (run) in order  to use the drivers I already have on CD-ROM.

<snip>that should be your LAST resource. Absolutely not recommended and chances are that that you don't need it.

This is for the experts: [https://wiki.debian.org/at76_usb#supported](https://wiki.debian.org/at76_usb#supported)
It seems it's natively supported since a long time (and many kernel versions) ago. It also seems it needs some firmware... That said I'll leave it to the experts to suggest the best procedure.

---

### Post by gordintoronto on 2014-06-29
According to this page: [https://wiki.debian.org/at76_usb](https://wiki.debian.org/at76_usb) 

your device has been supported within Linux for several years. Ndiswrapper is a hack to use Windows drivers, something you should do as a last resort.

If you insist: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by terry16 on 2014-06-29
Thank you for the responses.  I will certainly look into those options. Should I abandon even trying to run ndiswrapper?

I wonder why I could not find the linux-supported driver when I originally searched for it?  Thanks again; I'll let you know what happens.

---

### Post by Vladlenin5000 on 2014-06-29
What you should have done from the beginning is to describe your problem and ask for possible solutions.
What is your problem anyway? Can't see and/or connect to wireless networks?
If so first of all make sure the dongle still works... You know, that hardware belongs to a museum.

Now, assuming it works, there's a good chance it only needs some proprietary firmware because the driver should be there already. Hopefully you can manage to do a simple experiment: While keeping the USB connected also connect the Ethernet (LAN) cable. This should give you an internet connection. Wait a few seconds and then go to System settings > Software & Updates and open the "Additional drivers" tab, wait a few seconds again. Does it show something there? If so please select it, wit for download and installation process, reboot and... done. Obs.: Even if there's nothing in the aforementioned tab it may have downloaded what's needed and your wireless should be working now. Any other situation please post back.

---

### Post by chili555 on 2014-06-29
In recent Ubuntu versions, it is covered by the module at76c50x-usb. As has been stated, it requires firmware. I tried to install the firmware package and it wanted to remove a number of other items that I don't want removed. Maybe we can figure out a better method. Please load the module:```
sudo modprobe -r ndiswrapper
sudo modprobe at76c50x-usb
```Now check the log for clues as to what firmware it wants and we'll proceed.```
dmesg | grep at76
```

---

### Post by chili555 on 2014-06-29
> **Vladlenin5000 said:**
>  go to System settings > Software & Updates and open the "Additional drivers" tab, Does 'Additional Drivers' install any wireless drivers except Broadcom?

---

### Post by terry16 on 2014-06-29
Again: thank you for the response.  I thought I HAD described the  problem, and I thought I had articulated my need for the solution, but I  am not conversant in Ubuntu/linux lingo.

---

### Post by Vladlenin5000 on 2014-06-29
> **chili555 said:**
> Does 'Additional Drivers' install any wireless drivers except Broadcom?

Yes, I think so. I've seen Realtek and others (in the Debian based Venezuelan Canaima Linux), several Bluetooth and even DVB-T tuners (in Ubuntu). It was just an experiment anyway. Your method is the real deal and I'll leave to it hoping for the best outcome. You rock :guitar:

---

