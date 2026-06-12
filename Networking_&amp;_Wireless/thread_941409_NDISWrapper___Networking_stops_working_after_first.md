---
title: "NDISWrapper :  Networking stops working after first reboot"
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by FuriousGeorge on 2008-10-08
I've made a bug report about this in [LaunchPad]("https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/264340"), and I've posted about it on some unofficial [kubuntuforums.net]("http://kubuntuforums.net/forums/index.php?topic=3097289.0"), but no responses thus far.

Steps to reproduce bug:
1.  Install kubuntu on Asus P5B-VM based system w/ TEW-423PI wNIC (r8185 chipset)
2.  install ndiswrapper
3.  install the [appropriate windows XP driver]("http://www.trendnet.com/asp/download_manager/brokenlink.asp?action=report&iFile=9222")
(networking functional)
4.  Reboot computer.
(no longer able to scan for networks)

Reproducible:
Always

Workarounds:
In order to 'get it working again' I need to uninstall the driver, reboot the computer, and reinstall the driver.  It will then 'work' until the subsequent reboot.

Additional Info:

```

administrator@Station4:~$ sudo ndiswrapper -l
net8185 : driver installed
        device (10EC:8185) present

05:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (8000ns min, 16000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: I/O ports at b800 [size=256]
        Region 1: Memory at ff7ff400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

$ ifconfig wlan0
wlan0 Link encap:Ethernet HWaddr 00:14:d1:51:1e:11
          inet6 addr: fe80::214:d1ff:fe51:1e11/64 Scope:Link
          UP BROADCAST MULTICAST MTU:1500 Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
          Interrupt:17 Memory:ff7ff400-ff7ff425
$ sudo iwlist scan
[sudo] password for administrator:
lo Interface doesn't support scanning.
eth0 Interface doesn't support scanning.
wlan0 No scan results
(there are plenty of networks that it should see)
~$ tail -fn 10 /var/log/messages
Sep 3 09:09:23 station02 kernel: [ 1570.604374] ndiswrapper (mp_reset:62): wlan0 is being reset
Sep 3 09:11:35 station02 kernel: [ 1702.494132] ndiswrapper (mp_reset:62): wlan0 is being reset
Sep 3 09:20:17 station02 kernel: [ 2224.066157] ndiswrapper (mp_reset:62): wlan0 is being reset
Sep 3 09:22:29 station02 kernel: [ 2355.955973] ndiswrapper 

$ lsmod |grep ndis
ndiswrapper 192920 0
usbcore 146028 5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd

$ ls -la /etc/ndiswrapper/net8185/
total 348
drwxr-xr-x 2 root root 4096 2008-09-03 08:35 .
drwxr-xr-x 3 root root 4096 2008-09-03 08:35 ..
-rw-r--r-- 1 root root 452 2008-09-03 08:35 10EC:8185:13F2:10BD.5.conf
-rw-r--r-- 1 root root 452 2008-09-03 08:35 10EC:8185:14F2:10BD.5.conf
-rw-r--r-- 1 root root 452 2008-09-03 08:35 10EC:8185.5.conf
-rw-r--r-- 1 root root 452 2008-09-03 08:35 10EC:8185:6165:18E8.5.conf
-rw-r--r-- 1 root root 452 2008-09-03 08:35 10EC:8185:8185:10EC.5.conf
-rw-r--r-- 1 root root 10715 2008-09-03 08:35 net8185.inf
-rw-r--r-- 1 root root 308096 2008-09-03 08:35 rtl8185.sys

```

Compiling the latest ndiswrapper from source does not help, nor does changing the PCI bay for the NIC.

I understand this may be fixed in kernel 2.6.25.  Can anyone verify that?  If so, should I try my own kernel on a production system?  I've done it a hundred times on gentoo, but i'm new to debian based distros like *buntu, and I think I heard someone tell me it wasn't recommended for some reason.

Otherwise I think I could probably teach myself to shell script a solution, with a little guidance.  I kinda envision it as a simple script to replicate whatever ndiswrapper does when i uninstall the driver, which I would call when I reboot.

Then, when I boot up I would need another script to reinstall the driver and connect to the network.

If someone could help me out with the shutting down part, I'm sure I could come up with the second half.

Any help is much appreciated.

---

### Post by Ayuthia on 2008-10-08
Now, does the ndiswrapper module get loaded when you reboot?  If it does, can you remove the module and reload it to make it work:
```
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```

---

### Post by FuriousGeorge on 2008-10-08
Unfortunately, I forgot to mention that I had already tried that.  If only it were that simple :)


# sudo modprobe -r ndiswrapper
Segmentation Fault

//happens whether or not the windows driber is loaded in ndisgtk

---

### Post by FuriousGeorge on 2008-10-09
Solved

There is support in the 2.6.27 kernel.

I found an ornery fellow on freenode in #linux-kernel who was channeling 'Comic Book Guy' and pointed me to some .debs that even saved me the trouble of compiling and fixing grub, etc

---

