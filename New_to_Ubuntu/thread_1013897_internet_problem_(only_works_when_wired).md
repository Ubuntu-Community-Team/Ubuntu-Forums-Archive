---
title: "internet problem (only works when wired)"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by brighteyes6311 on 2008-12-17
I got sick of Window's BS and finally decided to UPGRADE to Ubuntu after countless times of watching MS blue screen and crash even after Geek Squad said that they had fixed the problem. Anyways, so my real problem now is that I really know nothing about Ubuntu and can only get the internet to work when it is connected straight to the wireless router. It connects when wired quick and efficiently, but I am a college student and I NEED wireless capability. 
I am running a toshiba satellite a305D-s6848. My machine does have a wireless card built into it though I don't know much about it, sorry. The chipset is an ATI RS690M. If you need anymore information about the computer check here: 
[http://reviews.cnet.com/laptops/toshiba-satellite-a305d-s6848/4505-3121_7-33088925.html](http://reviews.cnet.com/laptops/toshiba-satellite-a305d-s6848/4505-3121_7-33088925.html)
last but not least, please when explaining anything remember that I am extremely new to this (Before yesterday I didn't know what the terminal was), but eager and willing to learn.
                                  Thanks a million.

---

### Post by S_e_P_p on 2008-12-17
Hello,

You should post the following information.

Open a terminal and type:

```

lspci -nn
lshw -C network

```

Paste the output here.

Greets,
SePp

---

### Post by kdreimiller on 2008-12-17
i have a toshiba satelitte l305d-s5868 and had to set up my wireless as well.  i followed the instructions in the following link and it worked perfectly.

[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

check it out, see if it helps you out.  i suspect we might have similar computers so it might work for you.

---

### Post by brighteyes6311 on 2008-12-17
> **S_e_P_p said:**
> Hello,

You should post the following information.

Open a terminal and type:

```

lspci -nn
lshw -C network

```

Paste the output here.

Greets,
SePp

I typed in your code and this is what it told me:

gavin@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
00:04.0 PCI bridge [0604]: ATI Technologies Inc Device [1002:7914]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) [1002:7915]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) [1002:7916]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
05:06.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
05:06.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
05:06.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
05:06.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
05:06.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)

---

### Post by brighteyes6311 on 2008-12-17
> **kdreimiller said:**
> i have a toshiba satelitte l305d-s5868 and had to set up my wireless as well.  i followed the instructions in the following link and it worked perfectly.

[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

check it out, see if it helps you out.  i suspect we might have similar computers so it might work for you.

I tried following the steps on this site and it ended up not working. Thank you for your time. I am going to look through the posts on the site to see if anyone had the same problem that I did. thanks.

---

### Post by S_e_P_p on 2008-12-18
Hi,

You should disable all previous installed drivers and install
ndiswrapper. This allows you use the windows driver.

Type:

```
sudo apt-get install ndiswrapper-utils-1.9
```

download the latest XP driver.
extract the XP driver

open a terminal
```
 sudo ndisgtk 
```

select the net5211.inf file.

Your wlan should work now.

Greets,
SePp

---

### Post by nothingspecial on 2008-12-18
Copy and paste these lines into your terminal

Download the latest madwifi snapshot.

```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz	

```

Unzip it

```
tar -xvf madwifi-hal-0.10.5.6-r3875-20081105.tar.gz
```	



navigate to the extracted 

```

cd madwifi-hal-0.10.5.6-r3875-20081105
```

If you`ve not got the tools necessary for compiling get them


```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

Then compile it
```

sudo make
```


```
sudo make install
```

load the module (driver)

Code:
```

sudo modprobe ath_pci
```

make it load every time you boot

Code:
```

gksudo gedit /etc/modules
```

then copy and paste this to the bottom of that file
Code:
```

ath_pci
```

save
exit
reboot

---

### Post by enigmik on 2009-01-11
I *had* the same issue on the same laptop. See:[http://wireless.kernel.org/en/users/Download]("http://wireless.kernel.org/en/users/Download")

Make sure you disable the restricted driver BEFORE you attempt to install compat-wireless.

---

