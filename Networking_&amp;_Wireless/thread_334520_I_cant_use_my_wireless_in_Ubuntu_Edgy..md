---
title: "I cant use my wireless in Ubuntu Edgy."
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by ragnaphobia on 2007-01-09
Hi, I'm new to Linux. This is my first time using a new operating system so please dont make fun of me for asking such a easy question(if it is) :confused: 

I read alot of guides online on how to make wireless work. I'm using broadcom wireless chipset.

Before i installed ndiswrapper, i went to system>Administration>networking, there is no Wlan. I have installed wireless-tools already. 

I tried installing ndiswrapper but when i check the version information, i got this instead.

root@ubuntuEDGY:~# ndiswrapper -v
utils Error: no version specified!
driver version:        1.28
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1


when ahead of installation of windows drivers but i got invalid driver instead.

Im using a Hp Compaq presario V3135TU with Broadcom wireless chipset.  
Kernel of Ubuntu Edgey   --->  /lib/modules/2.6.17-10-generic . 

Please help me solve this problem. I'hv been doing this for the past week and right now i dont know what to do anymore.](*,)  Thanks

---

### Post by teaker1s on 2007-01-09
okay well you will need to copy and paste this command in terminal

[COLOR="Red"]sudo apt-get install ndiswrapper-utils[/COLOR]

[COLOR="Red"]sudo apt-get install network-manager-gnome[/COLOR]

then

[COLOR="Red"]sudo modprode ndiswrapper[/COLOR]
[COLOR="Red"] sudo ndiswrapper -l[/COLOR]

if it says your hardware is install and driver great- reboot,if not paste output here

also do these and post outputs

[COLOR="Red"]sudo lspci[/COLOR]

[COLOR="Red"]sudo lsusb[/COLOR]

---

### Post by ragnaphobia on 2007-01-09
hi, thanks for the help. i redid everything and everything is fine but i cant see any wireless thing
i type iwconfig and it didnt show my wlan
i followed [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")

root@ubuntuEDGY:~/bcm4311# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D3:15:92:97  
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe15:9297/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14672 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10767 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17501979 (16.6 MiB)  TX bytes:799987 (781.2 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:274 errors:0 dropped:0 overruns:0 frame:0
          TX packets:274 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21220 (20.7 KiB)  TX bytes:21220 (20.7 KiB)

---------------------------------------------
Thank you.

---

### Post by teaker1s on 2007-01-09
have you tried [COLOR="Red"]network-manager-gnome[/COLOR] also please post output of commands I asked you to do and paste previously;)

---

### Post by ragnaphobia on 2007-01-09
hi, i restarted my computer and i ran the set of codes again except for re-installation because i already install both ndiswrapper and network manager.

here are the outputs:

---------------------------------------------------------------------

**root@ubuntuEDGY:~# ndiswrapper -l**
installed drivers:
bcmwl5          driver installed, hardware (14E4:4324) present (alternate driver: bcm43xx)

-----------------------------------------------------------------------

**root@ubuntuEDGY:~# sudo lspci**
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
08:08.0 Ethernet controller: Intel Corporation Intel(R) PRO/100 VE Network Connection (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
08:09.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)


---------------------------------------------------------------------

**root@ubuntuEDGY:~# iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---------------------------------------------------------------------

Here's a screenshot showing that wireless shows up after restart
[IMG]http://www.geocities.com/bartragnaphobia/networksettings.png[/IMG]

Everything seems to be fine but i would like to know what if i got alot of wireless connections. How do i manage them? I have not tried connecting to any access points at this point of time.

---

### Post by teaker1s on 2007-01-09
okay your soooo close,remove the tick in the wired network shown in your screen shot.
 remove the ethernet cable and it appears you have two network-manager-applets by the volume icon on panel.

Rebooting you should now be able to left click the network-manager-gnome applet next to volume icon and see available networks click an available network and you'll be able to put in passphrass or network key

---

### Post by ragnaphobia on 2007-01-09
AT LAST!!! i got it to work. geesh i owe u one man. Thanks alot for your help :eek: Now i can continue to explore ubuntu properly. haha

---

### Post by teaker1s on 2007-01-09
your wellcome, 
be aware that if you plug any ethernet cable in ubuntu will now choose ethernet over wireless

now you can enjoy a relaxing wirefree ubuntu edgy:mrgreen:

---

