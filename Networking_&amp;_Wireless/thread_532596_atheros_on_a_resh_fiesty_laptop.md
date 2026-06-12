---
title: "atheros on a resh fiesty laptop"
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by lunaz on 2007-08-22
i tried to get it working last night by compiling some driver thing & ndiswraper.. it gave wierd errors all over so i reinstaled tonight. it's an acer aspire 3680, fresh as in just now feisty install..

here's some outputs; not real sure what to do to get it working. i'm wired right now.

```

luna@sux:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
luna@sux:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:24:34:61:39  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe34:6139/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1438 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1423 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1259670 (1.2 MiB)  TX bytes:132069 (128.9 KiB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)

luna@sux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
luna@sux:~$ lsmod
wlan                  204868  1 ath_pci
ath_hal               192592  1 ath_pci

```

---

### Post by hangthedj on 2007-08-22
[http://madwifi.org](http://madwifi.org)

you said you got some driver thing, if this was madwifi, remember you need to be root or use sudo, and you need the kernel headers for your kernel
and then sudo modprobe ath-pci

---

### Post by lunaz on 2007-08-24
last night i tried to compile the 0.9.3.2 madwifi drivers, and i got lots of errors, my friend told me to install libc-dev,lib6c-something, and 2 other pacages i forgot the names of. i did all that & there were no erors at the end, so i tried modprobe ath_pci, but i still can't get an interface.


i tried to use my belkin adapter with ndiswrapper too & the hardware isn't being recognized


i read the doc on madwifi, but dont know how to check if kernel is configured so i can try those instructions.


should i undo what i tried to do last night before i try another? how?

---

### Post by hangthedj on 2007-08-24
make sure you did 'make install' as well.

if that doesn't work,

```

sudo apt-get install build-essential linux-headers-$(uname -r)

```
then go to your madwifi directory
```

sudo make clean && sudo make && sudo  make install
sudo modprobe ath-pci

```
i also have a guide i wrote for my laptop, there are instructions on how to build the madwifi on it, at the bottom of the page in notes.
[http://www.geocities.com/sikofitt](http://www.geocities.com/sikofitt)

---

### Post by lunaz on 2007-08-24
cool, will try this when i get home.
is it 5 yet?

---

### Post by lunaz on 2007-08-24
i tried those commands, and i still can't get an interface. not sure what to do now.

---

### Post by lunaz on 2007-08-25
wow, it works with the belkin adapter in a different usb port!!!!!!!!! i'm posting from it right now.
the interface was called eth1...

---

