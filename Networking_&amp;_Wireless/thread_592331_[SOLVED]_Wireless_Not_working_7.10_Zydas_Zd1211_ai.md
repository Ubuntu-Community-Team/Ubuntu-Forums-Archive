---
title: "[SOLVED] Wireless Not working 7.10 Zydas Zd1211 airlink+usb"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by Magicalturkey on 2007-10-26
When i first upgraded to 7.10 my wireless connection was working, It no longer works and I cannot find any way in the network manager or WICD to get to any wireless settings.  I do have an Ethernet cable plugged in and set up under the wired profile for the time being.   I am starting to think that it stopped working after I installed DHCP3 security update 2 days ago, although I am not at all sure about this. 

When i plug the wireless USB adaptor in the dmesg output is: 

[ 5316.587318] usb 5-8: USB disconnect, address 4
[ 5318.757334] usb 5-5: new high speed USB device using ehci_hcd and address 5
[ 5318.814822] usb 5-5: configuration #1 chosen from 1 choice
[ 5318.866853] usb 5-5: reset high speed USB device using ehci_hcd and address 5
[ 5318.987133] usb 5-5: Could not load firmware file zd1211/zd1211_ub. Error number -2
[ 5318.987139] zd1211rw 5-5:1.0: couldn't load firmware. Error number -2
[ 5319.037872] usb 5-5: reset high speed USB device using ehci_hcd and address 5
[ 5319.095346] zd1211rw: probe of 5-5:1.0 failed with error -2

lsusb shows this:
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 005: ID 0ace:1211 ZyDAS 802.11b/g USB2 WiFi
Bus 005 Device 001: ID 0000:0000  

Iwconfig Shows:
lo        no wireless extensions.

eth0      no wireless extensions.

ifconfig shows:
eth0      Link encap:Ethernet  HWaddr 00:30:18:A6:3D:16  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:18ff:fea6:3d16/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18045 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15392 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19494231 (18.5 MB)  TX bytes:2400276 (2.2 MB)
          Interrupt:23 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:74 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 

also running sudo lsmod |grep usbcore shows this:
usbcore               163760  5 zd1211rw,usbhid,uhci_hcd,ehci_hcd

Any suggestions would be much appreciated. I swear I've read through every wireless post and bit of information I could find!!

Thanks

---

### Post by Magicalturkey on 2007-10-26
Bump!
if anyone has any experience in Interpreting this data a hint would help me a ton.  As ive got all this data but I cannot for the life of me figure out the next step to fix this problem. 

Thanks.

---

### Post by biau on 2007-10-29
try to install linux-ubuntu-modules

---

### Post by Magicalturkey on 2007-10-29
thanks for the response biau. 

I searched for linux-ubuntu-modules in sypnatic and it says I already have them installed is it one of those things that I need to uninstall and reinstall?

---

### Post by Magicalturkey on 2007-11-05
Finally, i was able to fix this problem by installing the Ubuntu-modules-rt (Realtime) package.  For some reason when I updated the system started using these new RT packages.  Once I installed the module I simply ran Iwconfig and the wireless usb card showed up.  From there I set up the network manager to look for the wireless card at that location, and Presto!! 

I hope this helps someone digging through the forums for a solution send me a message if I can help. 

Thanks, 
Mark

---

