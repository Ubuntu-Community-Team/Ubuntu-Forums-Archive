---
title: "BCM4312 driver install on Saucy Ubuntu completely offline."
date: 2014-02-24
forum: Networking &amp; Wireless
---

### Post by shain on 2014-02-24
I have been working on this 100 plus hours, 23 straight. I have been in several threads, and followed several guides. I give in. I can't get it alone. ugh.

I tried the open source, and those were able to see networks, but unable to connect (WPA2). I also tried compiling the proprietary drivers. I think I downloaded all the dependencies and installed them, but I was still getting a STOP error when I ran make clean and make. The wl driver never appeared anywhere. I did so much, that I figured some of what I had done may have conflicted with each other. Here is a fresh install.

Here is a bunch of Terminal dump. I don't know what will help you and what wont. If you need more let me know.



```
shain@lappy:~$ cat /etc/release

NAME="Ubuntu"
VERSION="13.10, Saucy Salamander"


shain@lappy:~$ lspci -nnk | grep -1A2 net
	Kernel driver in use: r852
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
	Subsystem: Dell Device [1028:0286]
	Kernel driver in use: tg3




0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
Kernel driver in use: b43-pci-bridge


shain@lappy:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:ae:28:1f:4c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10064 (10.0 KB)  TX bytes:10064 (10.0 KB)




shain@lappy:~$ nm-tool


NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:23:AE:28:1F:4C


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


shain@lappy:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


shain@lappy:~$ sudo lshw -short
H/W path        Device      Class       Description
===================================================
                            system      Inspiron 1318 ()
/0                          bus         0C236D
/0/0                        memory      64KiB BIOS
/0/400                      processor   Intel(R) Celeron(R) CPU          560  @ 
/0/400/700                  memory      32KiB L1 cache
/0/400/701                  memory      1MiB L2 cache
/0/1000                     memory      2GiB System Memory
/0/1000/0                   memory      1GiB DIMM DDR Synchronous 800 MHz (1.2 n
/0/1000/1                   memory      1GiB DIMM DDR Synchronous 800 MHz (1.2 n
/0/100                      bridge      Mobile PM965/GM965/GL960 Memory Controll
/0/100/2                    display     Mobile GM965/GL960 Integrated Graphics C
/0/100/2.1                  display     Mobile GM965/GL960 Integrated Graphics C
/0/100/1a                   bus         82801H (ICH8 Family) USB UHCI Controller
/0/100/1a.1                 bus         82801H (ICH8 Family) USB UHCI Controller
/0/100/1a.7                 bus         82801H (ICH8 Family) USB2 EHCI Controlle
/0/100/1b                   multimedia  82801H (ICH8 Family) HD Audio Controller
/0/100/1c                   bridge      82801H (ICH8 Family) PCI Express Port 1
/0/100/1c.1                 bridge      82801H (ICH8 Family) PCI Express Port 2
/0/100/1c.1/0               network     BCM4312 802.11b/g LP-PHY
/0/100/1c.3                 bridge      82801H (ICH8 Family) PCI Express Port 4
/0/100/1c.5                 bridge      82801H (ICH8 Family) PCI Express Port 6
/0/100/1c.5/0   eth0        network     NetLink BCM5906M Fast Ethernet PCI Expre
/0/100/1d                   bus         82801H (ICH8 Family) USB UHCI Controller
/0/100/1d.1                 bus         82801H (ICH8 Family) USB UHCI Controller
/0/100/1d.2                 bus         82801H (ICH8 Family) USB UHCI Controller
/0/100/1d.7                 bus         82801H (ICH8 Family) USB2 EHCI Controlle
/0/100/1e                   bridge      82801 Mobile PCI Bridge
/0/100/1e/1                 bus         R5C832 IEEE 1394 Controller
/0/100/1e/1.1               generic     R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
/0/100/1e/1.2               generic     R5C592 Memory Stick Bus Host Adapter
/0/100/1e/1.3               generic     xD-Picture Card Controller
/0/100/1f                   bridge      82801HM (ICH8M) LPC Interface Controller
/0/100/1f.1                 storage     82801HM/HEM (ICH8M/ICH8M-E) IDE Controll
/0/100/1f.2                 storage     82801HM/HEM (ICH8M/ICH8M-E) SATA Control
/0/100/1f.3                 bus         82801H (ICH8 Family) SMBus Controller
/0/1            scsi0       storage     
/0/1/0.0.0      /dev/cdrom  disk        DVD+-RW AD-7640A
/0/2            scsi2       storage     
/0/2/0.0.0      /dev/sda    disk        250GB SAMSUNG HM250HI
/0/2/0.0.0/1    /dev/sda1   volume      117MiB Windows NTFS volume
/0/2/0.0.0/2    /dev/sda2   volume      121GiB Windows NTFS volume
/0/2/0.0.0/3    /dev/sda3   volume      110GiB Extended partition
/0/2/0.0.0/3/5  /dev/sda5   volume      108GiB Linux filesystem partition
/0/2/0.0.0/3/6  /dev/sda6   volume      2037MiB Linux swap / Solaris partition
/0/2/0.0.0/4    /dev/sda4   volume      81MiB Linux swap / Solaris partition
/1                          power       DELL TT344




shain@lappy:~$ cat /etc/modprobe.d/* | egrep '80211|acx|at76|ath|b43|bcm|brcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rt1|rt2|rt3|rt6|rt7|wmi|witch|wl'
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


shain@lappy:~$ ls -lia /boot
total 27096
3276801 drwxr-xr-x  3 root root     4096 Feb 24 00:36 .
      2 drwxr-xr-x 23 root root     4096 Feb 24 00:34 ..
3276804 -rw-r--r--  1 root root  1005798 Oct  9 11:49 abi-3.11.0-12-generic
3276805 -rw-r--r--  1 root root   163251 Oct  9 11:49 config-3.11.0-12-generic
3276802 drwxr-xr-x  5 root root     4096 Feb 24 00:35 grub
3277164 -rw-r--r--  1 root root 17307898 Feb 24 00:36 initrd.img-3.11.0-12-generic
3276806 -rw-r--r--  1 root root   176500 Jun 17  2013 memtest86+.bin
3276807 -rw-r--r--  1 root root   178680 Jun 17  2013 memtest86+_multiboot.bin
3276803 -rw-------  1 root root  3285893 Oct  9 11:49 System.map-3.11.0-12-generic
3276920 -rw-r--r--  1 root root  5600032 Feb 24 00:32 vmlinuz-3.11.0-12-generic
```

---

### Post by Bucky Ball on 2014-02-24
Very odd. That card should work out of the box, but sometimes it doesn't. You might find some joy in one of these links, if you haven't tried them already. Probably the easiest thing to try first is to do and update via an ethernet cable and then check 'Additional Drivers'. What do you have there?

For BCM4312:
[http://www.ubuntuask.com/q/answers-no-wireless-connection-detected-hp-pavilion-dv6-1220-with-a-broadcom-bcm-4312-101104.html](http://www.ubuntuask.com/q/answers-no-wireless-connection-detected-hp-pavilion-dv6-1220-with-a-broadcom-bcm-4312-101104.html)

For BCM43**:
[http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx](http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx)

Install STA or b43, not both.  
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access)

Also correct about things conflicting, especially if you been using ndiswrapper for this. Don't go there, it is not needed for this card and hasn't been for quite some time now. It should be working fine and the quest is to find out why it is not.

---

### Post by shain on 2014-02-26
Thank you. I was able to get going. I posted in two forums at once, and another gentlemen on a different forum immediately replied, seeming to already know how to fix this issue without an internet connection. All but one solution you posted required an internet connection to work. I had already tried the other, offline solution, and it may have worked, but I had already installed a conflicting driver. I appreciate your timely reply.

If future googlers are having this same issues, I followed the steps outlined here.

[http://linuxforums.org.uk/index.php?topic=11496.0](http://linuxforums.org.uk/index.php?topic=11496.0)

---

### Post by varunendra on 2014-02-26
Next time you have the same issue with the same card (BCM4312), a much simpler solution is to download the "linux-firmware-nonfree" package from here : [http://packages.ubuntu.com/saucy/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/saucy/all/linux-firmware-nonfree/download)

Copy the downloaded file onto your Desktop, then install it with command -
```
sudo dpkg -i Desktop/linux-firmware*.deb
```
Reboot and done!

Make sure NOT to install the conflicting driver "wl" (package name - bcmwl-kernel-source). It gets automatically installed during OS installation if you were connected to internet and had enabled "Install Updates" option. So if it was installed and wasn't working (as usually happens), or if you are not sure, add this command above the first one above to be extra sure -
```
sudo apt-get purge bcmwl-kernel-source
```
This one simply purges the "wl" driver, so that the native "b43" can load and work without conflicts.

Please mark the thread as [SOLVED] now that it is, thanks. :)

---

