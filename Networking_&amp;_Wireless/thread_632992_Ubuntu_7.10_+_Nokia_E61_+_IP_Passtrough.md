---
title: "Ubuntu 7.10 + Nokia E61 + IP Passtrough"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by ramadhian on 2007-12-06
How to make Internet Connection in Nokia E61 using IP Passtrough with Ubuntu ?

as I can see when I plug the DKU USB to my Ubuntu Box ,, 

dmesg show this :

dmesg | grep rndis

[ 1336.742228] eth1: register 'rndis_host' at usb-0000:00:1d.2-2, RNDIS device, 00:14:a7:ae:ee:51
[ 1336.743933] usbcore: registered new interface driver rndis_host

lsmod | grep rndis

rndis_host       7808  0 
cdc_ether         7168  1 rndis_host
usbnet            19976  2 rndis_host,cdc_ether
usbcore       138632  6 rndis_host,cdc_ether,
                                          usbnet,ehci_hcd,uhci_hcd

In Windows XP Mode ,, Nokia with IP Passtrough need Nokia Network Bridge and Bridging connection with Nokia RNDIS Network Card with Ethernet LAN Card.

I just carious to know how to manage this in Ubuntu

rama@rama:~$ ifconfig
 
eth0 Link encap:Ethernet  HWaddr 00:0E:A6:68:73:AC  
         inet addr:192.168.0.73  Bcast:192.168.0.255
         Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68353 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:69968419 (66.7 MB)  TX bytes:4958104 (4.7 MB)
          Interrupt:20 

eth1 Link encap:Ethernet  HWaddr 00:14:A7:AE:EE:51  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:1974 (1.9 KB)

eth1:avah Link encap:Ethernet  HWaddr 00:14:A7:AE:EE:51  
          inet addr:169.254.8.186  Bcast:169.254.255.255
          Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo      Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1400 (1.3 KB)  TX bytes:1400 (1.3 KB)


I dont have any idea about the Next Step How to make this IP Passtrough work ,,?

Any Hints about this ??

---

### Post by K.Mandla on 2007-12-20
Moved to Networking and Wireless.

---

