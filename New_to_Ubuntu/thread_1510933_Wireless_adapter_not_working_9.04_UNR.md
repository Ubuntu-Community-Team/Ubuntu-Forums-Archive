---
title: "Wireless adapter not working 9.04 UNR"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by bharuchas on 2010-06-16
Hi I have Karmic Koala 9.04 installed, on my benq joybook Lite U 101B.
I have been using this for the past month and things were fine since installation. Today however my wireless adapter is just not switching on. I tried rebooting many times, i tried, Updating through synaptic manager, I tried uninstalling and reinstalling the network adapter, i looked through so many forum posts and tried them all to no avail.
When i boot up and right click on the network icon it shows wifi enabled, but when i left click it shows wireless is disabled.
Once I click on disable networking and again enable networking the wifi switch shows disabled thereafter till reboot.
lspci
sohrab@sohrab-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
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
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

sohrab@sohrab-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:8b:a6:78:93  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:fea6:7893/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42731 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:57416161 (57.4 MB)  TX bytes:2669086 (2.6 MB)
          Interrupt:26 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5524 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5524 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:276280 (276.2 KB)  TX bytes:276280 (276.2 KB)

sohrab@sohrab-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

The network works fine with ethernet cable, the wifi onoff switch is coupled with the bluetooth switch as Fn F10, the bluetooth enables and disables but the wifi is killing me.

Could someone please guide me without a reinstall as i had not partitioned the hard disk while installing UNR and now have more than 100gb of data on it.

Thanking you all for such an amazing product and such fantastic help forums.
Sohrab

---

### Post by lkraemer on 2010-06-16
Please open a Terminal Window and (copy & paste) these
commands one at a time.  Then post the output.
```

lspci
lspci -nn
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf

```

lk

---

### Post by bharuchas on 2010-06-17
> **lkraemer said:**
> Please open a Terminal Window and (copy & paste) these
commands one at a time.  Then post the output.
```

lspci
lspci -nn
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf

```

lk

Thanks LK, I just rebooted 8-10 times more and it started now.
But it could happen again, should i still post the output?

---

### Post by patrickportland on 2010-06-22
I'm not entirely sure if it's related, but I came across your post and the following one when trying to debug a similar issue I'm having: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/536998](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/536998)

---

### Post by bharuchas on 2010-06-23
Thanks but does not seem applicable here.

---

### Post by fresnofred on 2010-06-23
dumb maybe but does your sysyem have an fn- wireless buttons.  maybe u mistakenly shut off wifi with your keyboard

---

