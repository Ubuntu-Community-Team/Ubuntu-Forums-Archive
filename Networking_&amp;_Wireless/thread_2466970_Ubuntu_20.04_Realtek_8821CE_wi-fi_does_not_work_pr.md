---
title: "Ubuntu 20.04 Realtek 8821CE wi-fi does not work properly"
date: 2021-09-11
forum: Networking &amp; Wireless
---

### Post by deepakdeshp on 2021-09-11
The power management for the wi-fi card is not disabled with following command.

```
[SIZE=3][COLOR=#2E8B57][FONT=Monaco]sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf [/FONT][/COLOR][/SIZE]  
```, Reboot.
 To set it off I had to run ```
 systemctl restart network-manager.service 
```
Setting the power management did not help as I ran the following script to check network failure.

```
#!/bin/bashsystemctl restart network-manager.service
while true; do
  ping -c 1 yahoo.com &>/dev/null || date  >>t1
  sleep 2
done


 
```

The network failure report

```
 cat t1Sun 12 Sep 2021 08:34:03 AM IST
Sun 12 Sep 2021 08:40:16 AM IST
Sun 12 Sep 2021 08:40:18 AM IST
Sun 12 Sep 2021 08:40:20 AM IST
Sun 12 Sep 2021 08:40:22 AM IST
Sun 12 Sep 2021 08:42:47 AM IST
Sun 12 Sep 2021 08:45:24 AM IST
Sun 12 Sep 2021 08:45:26 AM IST
Sun 12 Sep 2021 08:45:28 AM IST
Sun 12 Sep 2021 08:46:02 AM IST
Sun 12 Sep 2021 08:50:46 AM IST
Sun 12 Sep 2021 08:50:48 AM IST
Sun 12 Sep 2021 08:50:50 AM IST
Sun 12 Sep 2021 08:55:34 AM IST
Sun 12 Sep 2021 08:55:36 AM IST
Sun 12 Sep 2021 08:55:38 AM IST
Sun 12 Sep 2021 08:55:57 AM IST
Sun 12 Sep 2021 08:56:16 AM IST
Sun 12 Sep 2021 08:57:02 AM IST


 
```

```
  inxi -nzNetwork:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet driver: r8169 
           IF: eno1 state: down mac: <filter> 
           Device-2: Realtek RTL8821CE 802.11ac PCIe Wireless Network Adapter driver: rtw_8821ce 
           IF: wlo1 state: up mac: <filter>  
```

This is a dual boot with Windows 10. With Windows 10 there is no network problem.

 Any suggestions please?

---

### Post by deepakdeshp on 2021-09-11
I had installed the driver for 8821CE card from following instructions on Github. I am not sure if the later kernels have the driver for it now. How to unload the drivers installed following the Github instructions and use the kernel driver if it is available?

---

### Post by Joe_Linux on 2021-09-12
[https://www.youtube.com/watch?v=GO68UhEEARU](https://www.youtube.com/watch?v=GO68UhEEARU)

---

### Post by deepakdeshp on 2021-09-15
> **Joe_Linux said:**
> [https://www.youtube.com/watch?v=GO68UhEEARU](https://www.youtube.com/watch?v=GO68UhEEARU)
Thank you but it is a 20.04 server and there is no GUI

---

### Post by deepakdeshp on 2021-09-17
I am running kernel ```
 5.13.0-14-generic

  
```. But the wi-fi performance is not proper. Is there are any place I can submit kernel bugs for ubuntu?

---

### Post by chili555 on 2021-09-17
Did you try the steps in my post here? [https://ubuntuforums.org/showthread.php?t=2465375&highlight=dropping](https://ubuntuforums.org/showthread.php?t=2465375&highlight=dropping)

---

### Post by deepakdeshp on 2021-09-19
> **chili555 said:**
> Did you try the steps in my post here? [https://ubuntuforums.org/showthread.php?t=2465375&highlight=dropping](https://ubuntuforums.org/showthread.php?t=2465375&highlight=dropping)

Thank you Dr Sheldon,
I made the change in  [COLOR=#000000][FONT=&amp]/etc/default/crda and made the last line as [/FONT][/COLOR][COLOR=#000000][FONT=&amp]REGDOMAIN=IN .I am from India, Rebooted. But there is no joy . The wi-fi network isnt steady.[/FONT][/COLOR][COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]My machine is 
ls[I]b_release -a
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:    20.04


Codename:    focalBus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0bda:b00a Realtek Semiconductor Corp. 
Bus 003 Device 003: ID 30c9:0013  
Bus 003 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
(base) uma@uma ~ $ lspci -nnk | grep -iA3 network
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter [10ec:c821]
    DeviceName: WLAN
    Subsystem: Hewlett-Packard Company RTL8821CE 802.11ac PCIe Wireless Network Adapter [103c:831a]
    Kernel driver in use: rtw_8821ce
    Kernel modules: rtw88_8821ce
04:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Picasso [1002:15d8] (rev c2)

```[/I]
In the router Band is 2.4 GHZ (B+G+N)
Mode is AP

---

### Post by deepakdeshp on 2021-09-19
```
 iwconfiglo        no wireless extensions.


eno1      no wireless extensions.


wlo1      IEEE 802.11  ESSID:"DIGISOL"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: C4:70:0B:B8:5F:5B   
          Bit Rate=39 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  **Invalid misc:2517 **  Missed beacon:0


vmnet1    no wireless extensions.


vmnet8    no wireless extensions.


  
```

---

### Post by deepakdeshp on 2021-09-19
This is a triple boot machine and wifi with Windows 10 works without any problems.

---

### Post by chili555 on 2021-09-19
> **deepakdeshp said:**
> This is a triple boot machine and wifi with Windows 10 works without any problems.That's often the case. The network management mechanism in Windows pretty accurately tracks changes in the router state and stays connected. So far, at least, Ubuntu does not.

Did you undertake the changes to the router settings that I recommended?

---

### Post by deepakdeshp on 2021-09-21
I couldn't find the router settings that you mentioned. The network configuration is ipv4, pppoe,enable Nat, enable vlan

---

### Post by deepakdeshp on 2021-09-21
I can't see the router settings you mentioned. It looks an uphill task to make the wi fi work.

---

### Post by chili555 on 2021-09-21
The seetings I referred to are in the administration pages of the wireless router to which you are attached. Most routers are sold with factory defaults like WPA and WPA2 mixed mode, auto channel select and auto band (2.4 gHz or 5 gHz) switching. These all need to be set to fixed, not auto select.

---

### Post by deepakdeshp on 2021-09-23
From all the various pages this is the once I found most useful I am attaching it here.

---

### Post by deepakdeshp on 2021-09-25
The router is Digisol dg gr-1321.
It's a Fibre optic router.

---

### Post by kurt18947 on 2021-09-25
> **chili555 said:**
> The seetings I referred to are in the administration pages of the wireless router to which you are attached. Most routers are sold with factory defaults like WPA and WPA2 mixed mode, auto channel select and auto band (2.4 gHz or 5 gHz) switching. These all need to be set to fixed, not auto select.

Hi Chili

The device that deepakdeshp has looks a little bit different than what we're used to. I did a quick search, this looks like that product's web page.

[https://www.digisol.com/products/ftth-solutions/xpon/digisol-gepon-gpon-onu-dg-gr1321-300mbps-wifi-router-with-1-pon-1-ge-1-fe-port-1-fxs-port/](https://www.digisol.com/products/ftth-solutions/xpon/digisol-gepon-gpon-onu-dg-gr1321-300mbps-wifi-router-with-1-pon-1-ge-1-fe-port-1-fxs-port/)

I looked in the support pages but did not see that model number. The other thought I had was to get a USB wifi adapter known to work with Ubuntu.

---

### Post by chili555 on 2021-09-26
> **deepakdeshp said:**
> From all the various pages this is the once I found most useful I am attaching it here.What are the available settings under the Security tab?

---

### Post by deepakdeshp on 2021-09-27
The other tabs of security have got value disabled. The security tab with values is attached. IMO there is no use of this tab.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289201&stc=1[/IMG]

---

### Post by deepakdeshp on 2021-09-28
What are some of the Ubuntu compatible wi fi USB dongles? Any idea?
What about this TP-Link USB WiFi Adapter for PC(TL-WN725N), N150 Wireless Network Adapter for Desktop - Nano Size WiFi Dongle Compatible with Windows 10/7/8/8.1/XP/ Mac OS 10.9-10.15 Linux Kernel 2.6.18-4.4.3 [https://www.amazon.in/dp/B008IFXQFU/ref=cm_sw_r_apan_glt_fabc_KBFH2C8R39M2MJY2YWMA?_encoding=UTF8&psc=1](https://www.amazon.in/dp/B008IFXQFU/ref=cm_sw_r_apan_glt_fabc_KBFH2C8R39M2MJY2YWMA?_encoding=UTF8&psc=1)

I think it should work with kernel 5.11 or 5.13?

---

### Post by chili555 on 2021-09-28
Please consult the sticky: [https://ubuntuforums.org/showthread.php?t=2397914](https://ubuntuforums.org/showthread.php?t=2397914)

---

### Post by deepakdeshp on 2021-09-30
Thank you Dr. That is an invaluable information for people buying wi fi adapters.

---

### Post by deepakdeshp on 2021-10-06
I have a wi-fi adapter which I was using for my Raspberry pi . Initially it wasnt working with the Pi , I opened a thread at Raspberry forum and the driver for it was built. [https://forums.raspberrypi.com/viewtopic.php?f=28&t=241185](https://forums.raspberrypi.com/viewtopic.php?f=28&t=241185) .Mostly the Pi isnt in use so I decided to use this dongle for my Ubuntu machine. I followed the same steps as on the Pi  and the driver is working with Ubuntu too.

Now I want to configure the adapter so that it can connect to the wi-fi network automatically. How do I do that?

---

### Post by DisturbedDragon on 2021-10-09
I have the same NIC in a Lenovo laptop. Used the DKMS from github for two years but after a kernel upgrade to 5.11 series, wifi was no longer available. I remove the manually installed diver and rebooted, wifi was back and performing well. Looks like it was included in the kernel starting in the 5.11 series. Currently using 5.14.0-1004-oem with no additional driver installed.

---

