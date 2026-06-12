---
title: "Wireless in 9.10 Dell not working"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by ardakshalkar on 2009-12-04
I have Dell vostro 1500 and I installed Ubuntu 9.10.
When I look at wireless connections at right top, it writes **disconnected** under wireless.
Also I couldn't connect manually.
When I try ubuntu in recovery mode it says you have to download broadcom b43.
What should I do, thank you!

I also have ubuntu 8.10 in which wifi radar doesn't work properly, and I connect to wifi manually.

---

### Post by ukripper on 2009-12-04
in terminal can you post output of the follwoing commands:
```
lspci
```

```
iwconfig
```

---

### Post by ardakshalkar on 2009-12-04
ardak@ardak-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
ardak@ardak-laptop:~$ ^C
ardak@ardak-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by ukripper on 2009-12-04
you have infamous Broadcom BCM43xx family.  follow this:

**_Method 1_** try this:

```
sudo apt-get install bcmwl-kernel-source
```

unplug any wired ethernet cable so you can use wireless.

Reboot and see if it comes up. If it doesn't follow method 2



**_Method2:_**
in terminal :

```
sudo apt-get install linux-backports-modules-karmic b43-fwcutter
```
3. Blacklist the ssb module.
```
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist-ssb.conf
```

4. Blacklist the wl module.

```
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist-wl.conf
```

5. Reboot and unplug any wired ethernet cable so you can use wireless.

Now after login see if your wireless comes up

---

### Post by ardakshalkar on 2009-12-04
What is the problem if it writes 
couldn't find package linux-backports-modules-karmic

---

### Post by ukripper on 2009-12-04
ok did the first one work after reboot?

Second method would require enabling backports

---

### Post by ukripper on 2009-12-04
to enable backports do this Open System->Administraion->Software Sources, click on the Updates tab, and check Unsupported upates (karmic-backports).

close it and then run in terminal:
```

sudo apt-get update
``` and then follow rest of the method 2

---

### Post by JBAlaska on 2009-12-04
**Do Method 1!** like so:

**First go to System, Administration, Software Sources and make sure "Proprietary drivers for devices (restricted) is checked.**

Then do this in a terminal:
```
sudo apt-get install bcmwl-kernel-source

```

**Reboot Ubuntu**

**Now go to System, Administration and "Hardware drivers" and check the use Broadcom sta wireless driver.**

**Reboot Ubuntu and you should have support for your wireless chipset.**

---

### Post by ardakshalkar on 2009-12-04
Thank you. all done.
Peace be upon you and your family!

---

### Post by lotharmat on 2009-12-04
Don't forget to mark the thread as SOLVED (thread tools above)

---

