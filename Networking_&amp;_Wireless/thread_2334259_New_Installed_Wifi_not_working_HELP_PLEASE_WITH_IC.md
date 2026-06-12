---
title: "New Installed Wifi not working HELP PLEASE WITH ICE CREAM"
date: 2016-08-17
forum: Networking &amp; Wireless
---

### Post by azeem2 on 2016-08-17
So heres my problem i just installed ubuntu 14.04lts. But after installtion my only available connection is enthernet no wifi.  An i cant use ethernet cause all i have is wifi in my dorm. Can any one help also just a little more info am able to use my andriod to download anything if necessary and my adapter is a Broadcom BCM94311MC and am working with a acer extensa 4620z.

Thank A Mill in Advance

```
azeem@azeem-Extensa-4620:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011c]
	Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011c]
	Kernel driver in use: i915
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011c]
00:1a.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011c]
	Kernel driver in use: uhci_hcd
00:1a.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011c]
	Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011c]
	Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011c]
	Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
	Kernel driver in use: pcieport
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
	Kernel driver in use: pcieport
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
	Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011c]
	Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011c]
	Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011c]
	Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011c]
	Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011c]
	Kernel driver in use: lpc_ich
00:1f.1 IDE interface [0101]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011c]
	Kernel driver in use: ata_piix
00:1f.2 IDE interface [0101]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode] [8086:2828] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011c]
	Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011c]
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:011c]
	Kernel driver in use: tg3
04:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device [1468:0422]
	Kernel driver in use: b43-pci-bridge
0f:06.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
	Subsystem: Acer Incorporated [ALI] Device [1025:011c]
	Kernel driver in use: yenta_cardbus
0f:06.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
	Subsystem: Acer Incorporated [ALI] Device [1025:011c]
	Kernel driver in use: firewire_ohci
0f:06.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
	Subsystem: Acer Incorporated [ALI] Device [1025:011c]
	Kernel driver in use: tifm_7xx1
0f:06.3 SD Host controller [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]
	Subsystem: Acer Incorporated [ALI] Device [1025:011c]
	Kernel driver in use: sdhci-pci
azeem@azeem-Extensa-4620:~$ grep 0280 -A2
```

---

### Post by chili555 on 2016-08-17
Let's double-check the wireless; please edit your question to add the result of this terminal command:```
 lspci -nnk | grep 0280 -A2
```

---

### Post by azeem2 on 2016-08-17
Did i do it right an thanks for helping

---

### Post by chili555 on 2016-08-17
> Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)This answer explains how to get and install the required firmware. Post back if you get stuck.

[http://askubuntu.com/questions/813065/no-networking-lubuntu-14-04-on-imac-g5-powerpc/813090#813090](http://askubuntu.com/questions/813065/no-networking-lubuntu-14-04-on-imac-g5-powerpc/813090#813090)

---

### Post by azeem2 on 2016-08-17
So this what happen when i do that

```
azeem@azeem-Extensa-4620:~$ sudo mkdir /lib/firmware/b43sudo cp ~/Desktop/b43/* /libfirmware/b43
[sudo] password for azeem:
mkdir: cannot create directory ‘/lib/firmware/b43sudo’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/a0g0bsinitvals5.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/a0g0bsinitvals9.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/a0g0initvals5.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/a0g0initvals9.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/a0g1bsinitvals13.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/a0g1bsinitvals5.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/a0g1bsinitvals9.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/a0g1initvals13.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/a0g1initvals5.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/a0g1initvals9.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/b0g0bsinitvals13.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/b0g0bsinitvals5.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/b0g0bsinitvals9.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/b0g0initvals13.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/b0g0initvals5.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/b0g0initvals9.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/lp0bsinitvals13.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/lp0bsinitvals14.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/lp0bsinitvals15.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/lp0initvals13.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/lp0initvals14.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/lp0initvals15.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/n0absinitvals11.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/n0bsinitvals11.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/n0initvals11.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/pcm5.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/ucode11.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/ucode13.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/ucode14.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/ucode15.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/ucode5.fw’: File exists
mkdir: cannot create directory ‘/home/azeem/Desktop/b43/ucode9.fw’: File exists
mkdir: cannot create directory ‘/libfirmware/b43’: No such file or directory

```
An still nothing

---

### Post by chili555 on 2016-08-17
> azeem@azeem-Extensa-4620:~$ sudo mkdir /lib/firmware/b43sudo cp ~/Desktop/b43/* /libfirmware/b43
[sudo] password for azeem:
mkdir: cannot create directory ‘/lib/firmware/b43sudo’: File existsThis is not one command all jammed together; it is two different commands:```
 sudo mkdir /lib/firmware/b43
```Press Enter. Any errors or warnings? If not, now the next command:```
sudo cp ~/Desktop/b43/*  /lib/firmware/b43
```Press Enter. Any errors or warnings? If not, reboot.

---

### Post by azeem2 on 2016-08-17
Same error

azeem@azeem-Extensa-4620:~$ sudo mkdir /lib/firmware/b43
[sudo] password for azeem:
mkdir: cannot create directory &#8216;/lib/firmware/b43&#8217;: File exists
azeem@azeem-Extensa-4620:~$ sudo cp ~/desktop/b43/* /lib/firmware/b43
cp: cannot stat &#8216;/home/azeem/desktop/b43/*&#8217;: No such file or directory
azeem@azeem-Extensa-4620:~$

---

### Post by azeem2 on 2016-08-17
Or is it me thanks again

---

### Post by chili555 on 2016-08-17
It *is *you. I suggested: > sudo cp ~/Desktop/b43/*  /lib/firmware/b43But you typed:>  sudo cp ~/desktop/b43/* /lib/firmware/b43In Linux, there is a difference between Desktop and desktop. There is no such thing as, 'Oh, I know what you mean' in Linux.

Please retrace your steps. Type carefully and proofread twice. It must be exact.

---

### Post by azeem2 on 2016-08-17
Alright houston we have lift off thank :d

---

### Post by chili555 on 2016-08-17
Awesome! Please use thread tools at the top to mark Solved.

Have fun!

---

### Post by wildmanne39 on 2016-08-18
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

