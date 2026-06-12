---
title: "Using USB-USB bridge cable on Ubuntu"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by drtvasudevan on 2008-11-25
Hello. I have this old USB bridge cable from LPT.com that was originally designed to work with Windows. It says on the cable body: BAFO NET-LinQ USB to USB Network Bridge Cable and dmesg on my Kubuntu Hardy system shows this upon connecting this device to two systems running Ubuntu:

[ 1300.500080] usb 1-2: new full speed USB device using uhci_hcd and address 5
[ 1300.671060] usb 1-2: configuration #1 chosen from 1 choice
[ 1300.675363] usb0: register 'plusb' at usb-0000:00:1d.0-2, Prolific PL-2301/PL-2302, 82:8c:c2:6d:f1:b9

On Windows it was supposed to be plugged into two systems' USB ports and the appropriate proprietary program (which came with the cable on a floppy) was loaded on both machines. You could view the files and media of either system from either. You drag-drop to transfer files, during which transfer one of the two systems is locked to be a server and the other a client. The lock is released upon completion.

My question: Is there a way to use this old cable on Ubuntu?

Thanks in advance.

---

### Post by beyboo on 2008-12-06
Ok, heres what I did, since I also have one of those Bafo Direct Linq cables. Looks very similar to the white one shown here. 
[http://www.linux-usb.org/usbnet/#t-host](http://www.linux-usb.org/usbnet/#t-host)

The cable dint work for me on Hardy, but its detected and configured on Intrepid as usb0.

To connect and transfer data, here is what I did. 


[SIZE="4"]**Setting up both computers on a common "LAN"**[/SIZE]

On my primary machine with Intrepid, I configured USB0 using 
ifconfig usb0 192.168.1.1

On the other machine also with Intrepid, I configured usb0 using 
ifconfig usb0 192.168.1.2

Heres the output of my USB0 from the primary machine

> usb0      Link encap:Ethernet  HWaddr 66:d9:21:a8:a8:02  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::64d9:21ff:fea8:a802/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:921888 errors:0 dropped:0 overruns:0 frame:0
          TX packets:466825 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1376253833 (1.3 GB)  TX bytes:35119141 (35.1 MB)



Intrepid also allows the configuration of usb0 through its spanking new nm-applet which is the default tool to configure a network. 

Select edit connections  > Auto usb0 and set a manual IP on both computers, using the same IP as default gateway as well.


[SIZE="4"]Transferring files[/SIZE]
[LIST=1]
[*]Ensure that the Firewall is switched off and you can ping each other
[*]If you can ping, setup an ftp server wu-ftp daemon on any one or both the machines.
[*]Install Filezilla FTP client on both computers
[*]Thats it !! (Really)
[*]start wu-ftp daemon using "sudo wu-ftp" on one machine
[*]use filezilla on the other machine to quickconnect. Use the User ID and password of the host machine you are connecting to.
[*]browse & transfer files :)
[/LIST]

[SIZE="4"]Comments[/SIZE]
The transfer speed sucks !! :(

---

### Post by drtvasudevan on 2009-04-25
thanks for the reply!

---

### Post by larytet on 2009-04-30
Is there a USB-to-USB bridge which turn one of the PCs into a storage device for the second PC ?

I thought to connect my EeePC to the USB on my DVR and view photos right off the disk without moving the files to the flash disk first.


thanks

---

