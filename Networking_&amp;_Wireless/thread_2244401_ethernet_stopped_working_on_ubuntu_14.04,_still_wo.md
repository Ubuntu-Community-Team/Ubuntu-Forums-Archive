---
title: "ethernet stopped working on ubuntu 14.04, still works on windows or if I boot off CD"
date: 2014-09-16
forum: Networking &amp; Wireless
---

### Post by davidhodgesnz2 on 2014-09-16
[COLOR=#333333][FONT=UbuntuRegular]Everything was working fine on my Ubuntu 14.04 32 bit installation (on a Dell Vostro laptop) yesterday. I shut it down last night and since I powered it up this morning it is no longer handling the graphics correctly - it's very low resolution - and the ethernet connection does not work at all. When I reboot into Windows 7 or off I boot off a Linux Mint Live DVD, the ethernet and graphics work fine.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]The ethernet controller is detected but it's not using it ?![/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]lshw -C network reports:[/FONT][/COLOR]
*-network UNCLAIMED 
    description: Network controller 
    product: AR9285 Wireless Network Adapter (PCI-Express) 
    vendor: Qualcomm Atheros physical 
    id: 0 bus 
    info: pci@0000:0c:00.0 
    version: 01 
    width: 64 bits 
    clock: 33MHz 
    capabilities: pm msi pciexpress bus_master cap_list 
    configuration: latency=0 
    resources: memory:f69f0000-f69fffff *-network UNCLAIMED 
    description: Ethernet controller 
    product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
    vendor: Realtek Semiconductor Co., Ltd. physical 
    id: 0 bus 
    info: pci@0000:09:00.0 
    version: 03 
    width: 64 bits 
    clock: 33MHz 
    capabilities: pm msi pciexpress msix vpd bus_master cap_list 
    configuration: latency=0 
    resources: ioport:ce00(size=256) memory:f0204000-f0204fff memory:f0200000-f0203fff memory:f0220000-f023ffff
[COLOR=#333333][FONT=UbuntuRegular]The commands[/FONT][/COLOR]
/etc/init.d/networking restart
[COLOR=#333333][FONT=UbuntuRegular]and[/FONT][/COLOR]
/etc/init.d/networking force-reload
[COLOR=#333333][FONT=UbuntuRegular]produce no output and have no apparent effect.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]ifconfig shows only the loopback interface, no others.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]The only new software I recall installing yesterday was the aspectj package. And the ethernet still worked fine after I installed it, until I power cycled.

[/FONT][/COLOR]

---

### Post by praseodym on 2014-09-16
Download these 2 files and save them in "Downloads":

[http://media.cdn.ubuntu-de.org/forum/attachments/45/14/3005217-r8168-dkms-8.038.00.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/45/14/3005217-r8168-dkms-8.038.00.tar.gz)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb)

Installation:

```
cd ~/Downloads/
sudo dpkg -i *.deb
sudo tar xvf 3005217-r8168-dkms-8.038.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.038.00
sudo dkms build -m r8168-dkms -v 8.038.00
sudo dkms install -m r8168-dkms -v 8.038.00
sudo depmod -a
sudo update-initramfs -u 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.

---

### Post by davidhodgesnz2 on 2014-09-17
Brilliant! That worked perfectly thanks!

---

### Post by praseodym on 2014-09-17
Great! Please check if all compiling tools are fully installed:
```

sudo apt-get install --reinstall linux-headers-generic build-essential dkms
```
DKMS will build the driver whenever the kernel is updated.

---

### Post by davidhodgesnz2 on 2014-09-18
Excellent thanks. That makes my sound and video work again! So everything is working again, as far as I've noticed. :-)

---

### Post by davidhodgesnz2 on 2014-09-20
All worked fine until Ubuntu installed another update, which broke the ethernet again (this time it didn't break the video and sound). So I got it working again by following the steps in your first reply (I had to do a dkms remove for that module first) but how can I avoid having to do this every time Ubuntu does a software update (or at least an update that includes drivers or a new kernel), other than turning software updates off ?

Thanks very much.

---

### Post by praseodym on 2014-09-21
"Normally", DKMS builds the module automatically. You can try it via
```

sudo dkms autoinstall
```
if it occurs again.

---

### Post by davidhodgesnz2 on 2014-09-24
Yay! Ubuntu installed a kernel update today and it didn't break anything! So it seems to be all sorted now.

---

### Post by davidhodgesnz2 on 2014-09-27
Ubuntu's latest update broke the ethernet again (but not anything else). I tried 

sudo dkms autoinstall

and it produced no output and didn't solve the problem, even after I rebooted.

I also tried a dkms uninstall and install and that didn't solve it either.

I had to do a dkms uninstall, remove, add, build, install, reboot.

I'd like to file a bug report with ubuntu to get them to fix it as surely I can't be the only person wanting to run Ubuntu with this ethernet device, but ubuntu-bug wants me to specify a package and the r8168 driver doesn't seem to be an installed package (can't see it listed in dpkg --get-selections) ?

---

### Post by praseodym on 2014-09-28
Please run the wireless script from the sticky thread

---

### Post by davidhodgesnz2 on 2014-10-10
Did you want me to post the output here ?  Here it is, thanks.

---

### Post by praseodym on 2014-10-10
Please remove it again and try driver version 39 from here:

[http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#r8168-mittels-dkms](http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#r8168-mittels-dkms)

Link here:

[http://media.cdn.ubuntu-de.org/forum/attachments/24/39/3005217-r8168-dkms-8.039.00.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/24/39/3005217-r8168-dkms-8.039.00.tar.gz)

---

### Post by davidhodgesnz2 on 2014-10-10
Done, thanks. 

It said "Good news! Module version 8.039.00-NAPI for r8168.koexactly matches what is already found in kernel 3.13.0-37-generic.
DKMS will not replace this module."

I'll let you know if I have any more problems...

---

### Post by pegngary on 2014-10-21
This solution did not work for me.  Before I tried it echo on | sudo tee /sys/class/net/eth0/device/power/control would get it working until reboot.  Now that does not work.  I do not see any sticky thread.  Seems like it'a a bug.

---

### Post by pegngary on 2014-10-21
Well ran the code again, rebooted and it worked!  Rebooted again just to make sure and still works!  Thanks!

---

### Post by davidhodgesnz2 on 2014-12-02
It still breaks when the kernel is updated - I have to uninstall and reinstall the driver each time...

---

### Post by mark205 on 2015-03-13
I tried that download.  It did not work for me.   I have a Vostro 1500 Dell but have the same issue where it tells me its UNCLAIMED

---

### Post by blazinjay90210 on 2015-08-29
when you say reboot do you mean reboot the computer or the network manager

---

