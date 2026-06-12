---
title: "NETGEAR N600 WNDA3100 Wireless configuration issue in Ubuntu 12.04 TLS"
date: 2014-02-27
forum: Networking &amp; Wireless
---

### Post by rajashekar3 on 2014-02-27
Hi All,

I am new to Ubuntu and trying to configure NETGEAR N600 WNDA3100 USB wireless adapter on Ubuntu machine. I have googled and tried so many solutions even though couldn't able to configure successfully. Could you please help me to solve this issue. Please see below for some details about my machine configuration.

 lsusb
```

Bus 001 Device 010: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 001 Device 011: ID 0951:1613 Kingston Technology DataTraveler DT101C Flash Drive
Bus 002 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 004 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 005 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

iwconfig
```

wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:ff   RTS thr:ff   Fragment thr:ff
          Encryption key:ff
          Power Management:ff
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.


```
lsmod
```

Module                  Size  Used by
nls_iso8859_1          12617  1 
usb_storage            48631  1 
snd_hda_codec_realtek    50304  1 
snd_hda_codec_hdmi     40852  1 
bnep                   19210  2 
rfcomm                 59026  0 
bluetooth             341971  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  17423  0 
snd_hda_intel          43326  5 
snd_hda_codec         169534  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
r8712u                164103  0 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                94597  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
radeon               1344679  3 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                55716  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28930  2 snd_pcm,snd_seq
joydev                 17329  0 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    61270  21 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    76692  1 radeon
drm_kms_helper         47306  1 radeon
sp5100_tco             13754  0 
soundcore              12600  1 snd
k10temp                12997  0 
drm                   247722  5 radeon,ttm,drm_kms_helper
i2c_piix4              17843  0 
mac_hid                13077  0 
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13316  1 radeon
video                  19046  0 
lp                     13359  0 
parport                40930  3 parport_pc,ppdev,lp
hid_generic            12492  0 
usbhid                 47620  0 
hid                    87771  2 hid_generic,usbhid
pata_acpi              12886  0 
r8169                  62856  0 
mii                    13693  1 r8169
ahci                   25703  2 
pata_atiixp            13058  0 
libahci                30834  1 ahci

```

sudo lshw -C network
```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: d4:3d:7e:0c:8d:aa
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:3
       logical name: wlan0
       serial: 6c:71:d9:1c:56:48
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u multicast=yes wireless=unassociated

```

iwlist scan
```

wlan0     No scan results


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


```

uname -r
```

3.11.0-15-generic


```

lspci -nn

```

00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Complex [1022:1510]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6320] [1002:9806]
00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler HDMI Audio [1002:1314]
00:04.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Port [1022:1512]
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller [1002:4385] (rev 42)
00:14.1 IDE interface [0101]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c] (rev 40)
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
00:15.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) [1002:43a0]
00:16.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:16.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0 [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1 [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2 [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3 [1022:1703]
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4 [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6 [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5 [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7 [1022:1719]
root@appsupport-B02311:/# sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndis.txt, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/cut, it will be ignored in a future release.

```

ndiswrapper -l
```

bcmwlhigh6 : driver installed

```

---

### Post by wildmanne39 on 2014-02-27
*Thread moved to **Networking & Wireless**.*

---

### Post by wildmanne39 on 2014-02-27
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by varunendra on 2014-03-01
Welcome to the forums rajashekar3 !

Unless I missed it in the lsmod, it doesn't look like ndiswrapper was loaded. Please try -
```
sudo modprobe -v ndiswrapper
```
Does the usb adapter work after this?

Which version of windows driver are you using with ndiswrapper? 32 bit or 64 bit?

Please post the outputs of -
```
lsb_release -cd
uname -mr
cat /etc/modules
cat /etc/rc.local
```

And like Wild Man asked, please use 'Code' tags for posting the outputs. If you need to see an example with screenshots on HowTo, please follow the "Using Code Tags" link in my signature below.

---

### Post by rajashekar3 on 2014-03-03
Hi Varun,

Thanks for your reply...
At last i managed to configure WNDA 3100 wireless USB adapter in Ubuntu 12.04. But still i have issues.
The wireless network connection showing as connected to wlan1, but i can not open any web page not even google page. And i tried to run this command sudo apt-get update, noticed that unable to download the files.

Please see below output for sudo apt-get update: Could you please suggest me how to fix this ?
```

Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                                                              
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                                                        
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages/DiffIndex                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages/DiffIndex                            
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                                                    
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                                                       
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages/DiffIndex                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources/DiffIndex    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex 
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                 
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources           
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources             
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources           
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

```

syslog output:

```

Mar  3 11:58:57 appsupport-B02311 wpa_supplicant[966]: Authentication with 64:d9:89:99:37:32 timed out.
Mar  3 11:58:57 appsupport-B02311 NetworkManager[896]: <info> (wlan1): supplicant interface state: associating -> scanning
Mar  3 11:59:02 appsupport-B02311 wpa_supplicant[966]: Trying to associate with 64:d9:89:90:73:62 (SSID='office_net' freq=2452 MHz)
Mar  3 11:59:02 appsupport-B02311 NetworkManager[896]: <info> (wlan1): supplicant interface state: scanning -> associating
Mar  3 11:59:22 appsupport-B02311 wpa_supplicant[966]: Authentication with 64:d9:89:90:73:62 timed out.
Mar  3 11:59:22 appsupport-B02311 NetworkManager[896]: <info> (wlan1): supplicant interface state: associating -> scanning
Mar  3 11:59:27 appsupport-B02311 wpa_supplicant[966]: Trying to associate with 5c:50:15:4d:8b:12 (SSID='office_net' freq=2432 MHz)
Mar  3 11:59:27 appsupport-B02311 NetworkManager[896]: <info> (wlan1): supplicant interface state: scanning -> associating
Mar  3 11:59:47 appsupport-B02311 wpa_supplicant[966]: Authentication with 5c:50:15:4d:8b:12 timed out.
Mar  3 11:59:47 appsupport-B02311 NetworkManager[896]: <info> (wlan1): supplicant interface state: associating -> scanning
Mar  3 11:59:53 appsupport-B02311 wpa_supplicant[966]: Trying to associate with 00:27:0d:09:c0:72 (SSID='office_net' freq=2452 MHz)
Mar  3 11:59:53 appsupport-B02311 NetworkManager[896]: <info> (wlan1): supplicant interface state: scanning -> associating
Mar  3 11:59:54 appsupport-B02311 NetworkManager[896]: <info> (wlan1): roamed from BSSID 64:D9:89:99:37:32 (office_net) to 64:D9:89:90:73:62 (office_net)
Mar  3 12:00:13 appsupport-B02311 wpa_supplicant[966]: Authentication with 00:27:0d:09:c0:72 timed out.
Mar  3 12:00:13 appsupport-B02311 NetworkManager[896]: <info> (wlan1): supplicant interface state: associating -> scanning
Mar  3 12:00:18 appsupport-B02311 wpa_supplicant[966]: Trying to associate with 64:d9:89:98:42:a2 (SSID='office_net' freq=2432 MHz)
Mar  3 12:00:18 appsupport-B02311 NetworkManager[896]: <info> (wlan1): supplicant interface state: scanning -> associating
Mar  3 12:00:24 appsupport-B02311 NetworkManager[896]: <info> (wlan1): roamed from BSSID 64:D9:89:90:73:62 (office_net) to 64:D9:89:99:37:32 (office_net)
Mar  3 12:00:38 appsupport-B02311 wpa_supplicant[966]: Authentication with 64:d9:89:98:42:a2 timed out.
Mar  3 12:00:38 appsupport-B02311 NetworkManager[896]: <info> (wlan1): supplicant interface state: associating -> scanning
Mar  3 12:00:43 appsupport-B02311 wpa_supplicant[966]: Trying to associate with 64:d9:89:99:36:e2 (SSID='office_net' freq=2417 MHz)
Mar  3 12:00:43 appsupport-B02311 NetworkManager[896]: <info> (wlan1): supplicant interface state: scanning -> associating
Mar  3 12:01:03 appsupport-B02311 wpa_supplicant[966]: Authentication with 64:d9:89:99:36:e2 timed out.
Mar  3 12:01:03 appsupport-B02311 NetworkManager[896]: <info> (wlan1): supplicant interface state: associating -> scanning
Mar  3 12:01:08 appsupport-B02311 wpa_supplicant[966]: Trying to associate with 64:d9:89:90:73:62 (SSID='office_net' freq=2452 MHz)
Mar  3 12:01:08 appsupport-B02311 NetworkManager[896]: <info> (wlan1): supplicant interface state: scanning -> associating
Mar  3 12:01:28 appsupport-B02311 wpa_supplicant[966]: Authentication with 64:d9:89:90:73:62 timed out.
Mar  3 12:01:28 appsupport-B02311 NetworkManager[896]: <info> (wlan1): supplicant interface state: associating -> scanning

```

Thanks,

---

### Post by Kent_Kush on 2014-03-16
I wasted considerable time in finding out the right installation method for WNDA3100 Netgear N USB Network adapter. In the end it was actually quite simple. First, understand the reason why this Network adapter does not work.  1. As your output above shows, it uses Braoadconn chipset. Unfortunately, Ubuntu and other Linux OSs have not developed a generic for this chipset mainly because only Netgear seem to be using on very few of its products.
2. Netgear only has Windows drivers.  3. Obviously windows drivers do not work under any linux system. 
Solution: To make the driver work under Ubuntu/Linux you will need TWO programs: 1. WINE (to install the driver) 2. NDISWrapper - a program that grabs these drivers and make them work under linux.  So you will have to download and install Wine and the NDISwrapper.
(The best way to install both Wine and Ndiswrapper is through synaptic software option. Be sure to check mark Ndis GTK if not already checked) The snynaptic automatically installs everything without you have to input any commands in the terminal)
GETTING THE WINDA3100v2 drivers:  You can download these drivers directly into your download. CAUTION: Netgear may not have Windows XP driver clearly marked. Because WINE only works Windows XP you will have to find the right Win XP drivers and download. 
Because you cannot delete the extracted driver files it is best to create a folder (I created mine inside downloads) and leave them there. Ubuntu's archive manager will extract them. But make sure the extracted files are put back in the same folder)
Start Wine and install the driver.  Wine will install it in "C" drive. Let it stay there.
Start Ndiswrapper. Browse to the folder where you put the extracted driver file. Ndiswrapper will grab it and install it for you.
You may have to restart. At this point most like Ubuntu will automatically grab the USB adapter.  If not just click on the wireless icon in the upper right hand corner and then add the network connection. You should not have any problems after this install if you leave everything intact and not delete any driver or other directories/folders.

---

