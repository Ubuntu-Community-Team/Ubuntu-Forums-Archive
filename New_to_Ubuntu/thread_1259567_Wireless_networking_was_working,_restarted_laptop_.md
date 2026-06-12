---
title: "Wireless networking was working, restarted laptop and then it wasn't?"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by gismo93 on 2009-09-06
So just installed ubuntu 9.04 today and I'm really enjoying it.

One problem was that when I first booted up, my wireless network wasn't being detected.
So I went to System>Administration>Hardware drivers and found the driver for my wirless card was disabled, naturally I enabled it and everything was working fine then.

The update manager kept annoying me, asking me to update so I thought, might as well get this out of the way, and I proceeded with the updates.

When it was finished downloading and installing It asked me to restart my PC, so I did.
When it booted up again, I straight away went into firefox and server was not found.

I thought, well I'll just click the network Icon and connect to my network and make sure it connects automatically everytime, but when I went in there I didn't see a wireless connection.

I checked to make sure the driver was enabled and it was.

I really don't know what to do, so any help explained it simple terms because, well I'm a n00b to ubuntu.

Thanks in advance!

---

### Post by swoody on 2009-09-06
Well, hello and welcome to the forums gismo93 :)

Can you help us out with a few more details about your system by posting the output of:

```
ifconfig
```
and
```
lspci
```

This should help us get on the right track with your hardware. Thanks :)

Edit: Also, could you include the output of:
```
sudo iwlist scan
```

---

### Post by uylug on 2009-09-06
Open up a terminal by going into Applications -> Accessories -> Terminal

And type the following commands:

```
lshw -C network
```
```
lsmod
```
```
ifconfig
```

---

### Post by gismo93 on 2009-09-06
output of ifconfig is

```
eth0      Link encap:Ethernet  HWaddr 00:1a:80:f9:15:d2  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:80ff:fef9:15d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5394 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3671 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3662049 (3.6 MB)  TX bytes:653549 (653.5 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3368 (3.3 KB)  TX bytes:3368 (3.3 KB)
```and output of lspci is

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 15)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
```

EDIT: output of sudo iwlist scan just says interface doesn't support scanning

---

### Post by swoody on 2009-09-06
Well, that's good. Your computer still recognizes your wireless adapter, but it's just not loading at bootup. What I would reccomend to start off would be to uninstall your current driver through System>Admin>Hardware Drivers, then restart your computer when it tells you to. Then after your system reboots with no drivers loaded, go ahead and select the driver again, install it, and reboot again. If this doesn't work out for you, you may want to do a bit of reading on the Atheros Wiki page for Ubuntu [HERE]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros")

I'm going to keep searching for a better solution to this problem, but try these out, and see if it doesn't get you back up and running in the meantime :)

---

### Post by gismo93 on 2009-09-06
how exactly do i uninstall the driver?

i went to hardware drivers and theres only an option to disable the drivers and then activate it again.

thanks for all the answers, hopefully i can get it all working again!

---

### Post by swoody on 2009-09-06
Sorry about that. Yes, I meant 'Disable' the driver, and then restart your computer :)

---

### Post by gismo93 on 2009-09-06
thanks swoody, got it working thanks to the link you provided!

the driver was being blacklisted i think, anyway all i know is that its working now!
thanx guys!

---

### Post by swoody on 2009-09-06
Great, that's good to hear :D

Just as you saw with this case, there's a plethora of documentation for Ubuntu. If you ever have any issues in the future, you may want to try Googling, or searching the wiki pages. I'm not suggesting not to post in the forums, there's always people happy to help you out, but you may be able to find what you're looking for without having to wait on a response :)

---

