---
title: "yet another Tiscali/Sagem connectivity problem - please help!"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by xmalc on 2007-06-18
Hi, I'm having similar problems to a lot of other users - I can't get my Tiscali Sagem F@st 800 modem to connect to the internet.  I have run through the wiki page ([https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm](https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm)) and done the following:

1. downloaded the modem firmware
2. installed the firmware in /lib/firmware/ueagle-atm
3. created this file: /etc/ppp/peers/ueagle-atm and added my details
4. same for /etc/ppp/chap-secrets and /etc/ppp/pap-secrets 
5. run: pon ueagle-atm 

I'm running version 7.04 of Ubuntu.

I've noticed that both lights on the modem go on as soon as I plug it in, and they stay on solidly no matter what I do.

Here are some command outputs that might be useful...

> malcolm@malcolm-laptop:~$ lsmod|grep eagle
ueagle_atm             26792  0 
usbatm                 20224  1 ueagle_atm
usbcore               134280  8 ueagle_atm,usbatm,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd

> malcolm@malcolm-laptop:~$ dmesg|grep ueagle
[   27.872000] [ueagle-atm] driver ueagle 1.4 loaded
[   27.872000] usbcore: registered new interface driver ueagle-atm

> malcolm@malcolm-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3F:23:D1:FF  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6132 (5.9 KiB)  TX bytes:6132 (5.9 KiB)

I think there should be a ppp0 entry in that last command but it's not there...

and:

> malcolm@malcolm-laptop:~$ route
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

there's clearly something wrong here!!

I'm pretty new to this so any help will be gratefully received.

Thanks in advance

Malcolm

---

### Post by xmalc on 2007-06-27
Please don't all rush at once to help out....  I have bought a wireless router and hope to get ubuntu working through that instead.  If I have any problems I'll keep them to myself, you're all clearly very busy.

---

### Post by abejaruco on 2007-07-25
I'm having the same problem with a Huawei SmartAX MT882 in Ubuntu 7.04. It seems that the firmware is not loaded properly, but I still don't know why ...

Regards.

---

