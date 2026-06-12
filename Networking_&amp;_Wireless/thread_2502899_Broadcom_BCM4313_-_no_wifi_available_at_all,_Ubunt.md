---
title: "Broadcom BCM4313 - no wifi available at all, Ubuntu 24.04"
date: 2024-12-04
forum: Networking &amp; Wireless
---

### Post by Linux_newbie_no1 on 2024-12-04
I have spent most of today crawling through previous threads about this to no avail. Basically I decided to upgrade my old Lenovo G580 with a new SSD, which was fine. I then installed the latest version of Ubuntu Studio. At the beginning of the install where you get the option to join a wireless network it worked fine, however once the install had completed wifi had disappeared. I am now using ethernet. I tried following the sticky: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110) to no avail, plus numerous other possibilities, but whatever I've tried,  wifi remains 'disappeared'.

Output of lspci -nn -d 14e4:

02:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4313 802.11bgn Wireless Network Adapter [
14e4:4727] (rev 01)

Output of lspci -vvnn | grep -A 9 Network 

Subsystem: Broadcom Inc. and subsidiaries BCM4313 802.11bgn Wireless Network Adapter [14e4:051b]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 255
        Region 0: Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: bcma, wl


I have tried:
sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit
I have tried deselecting the Broadcom driver in Software Sources:


Is there anything else I can try? And please understand I am a complete Linux novice,  so any instructions will need step by step line by line detail,  thanks
sudo -iecho "blacklist b43" >>  /etc/modprobe.d/blacklist.confecho "blacklist ssb" >>  /etc/modprobe.d/blacklist.confexit

---

### Post by Linux_newbie_no1 on 2024-12-04
I should  have added, 

sudo lshw -C network:

*-network UNCLAIMED        
       description: Network controller
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0500000-f0503fff
  *-network
       description: Ethernet interface
       product: AR8162 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 10
       serial: 3c:97:0e:83:b2:27
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-
fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx driverversion=6.8.0-49-lowlatency duplex=ful
l ip=192.168.0.14 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:19 memory:f0400000-f043ffff ioport:2000(size=128)

---

### Post by Linux_newbie_no1 on 2024-12-04
I have also tried:

[COLOR=#000000]sudo apt remove broadcom-sta-dkms bcmwl-kernel-source

[/COLOR]
[COLOR=#000000]sudo apt install firmware-b43-installer[/COLOR]

---

### Post by jeremy31 on 2024-12-04
See the wireless script link in my signature and post results

---

### Post by Linux_newbie_no1 on 2024-12-04
Thanks, I'm in the UK, will tackle this tomorrow morning after a night's sleep

---

### Post by Linux_newbie_no1 on 2024-12-05
I've now run the script, as per attached.
[ATTACH]294605[/ATTACH]

Please let me know your thoughts

---

### Post by jeremy31 on 2024-12-05
Remove the blacklist on the drivers
```
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf
```
Reboot

---

### Post by Linux_newbie_no1 on 2024-12-05
That worked a treat! Thank you very much, I was just about to install a 22.04 ISO I had saved. Now just to work out how to reinstate all the additional touchpad config options which seem to have disappeared between 22 and 24 and all will be well!

---

### Post by varyag on 2024-12-06
Hi there, I'm also using the **BCM4313 14e4:4727 (rev 01)** driver and I followed the steps in [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)  to make my Wi-Fi work properly.

The wifi is able to connect but after some minutes it stops working and the 'no wifi adapter found' message is shown. I know that I need to use either the proprietary drivers or brcmsmac (linux-firmware is installed).

Pastebin of the wireless network script output: [https://termbin.com/cjun](https://termbin.com/cjun)

---

### Post by varyag on 2024-12-08
Just to let everyone know: I ran that command, rebooted and now my wifi works without an ethernet cable and it doesn't disconnect after some time. Thank you!

---

