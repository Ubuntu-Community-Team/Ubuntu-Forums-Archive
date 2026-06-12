---
title: "Ubuntu Wireless takes 10 min to work after boot on HP Laptop"
date: 2016-02-20
forum: Networking &amp; Wireless
---

### Post by nick245 on 2016-02-20
Hello Everyone! ):P

 I am brand new to your community and I look forward to learning much and contributing to the best of my current abilities. I have been using Linux for about 10 years so I do know a good amount already but there is always something new to learn. 

I took my HP laptop that came pre-loaded with Windows 7 and installed Ubuntu 14.04. It works great except for one detail. When I restart or boot up the computer it takes longer to boot than anything I have installed Linux on before. And that is including crappy old white-boxes. The main OS seems to load up fine. But once the computer is up and you can open and close files and apps, the wireless will take an additional 5-10 min to start working. I work in IT so I am pretty good with troubleshooting. Restarted, checked the wireless switch, tried checking all startup processes for anything weird, and I even took it apart and checked the hardware for any problems. I saw nothing that stuck out. I googled a little further and noticed this seems to be a normal thing with the combination of HP Laptops and Ubuntu. In many cases, the wireless does not work at all. The solutions are varied depending on the hardware. 

Below I shared the laptop/network info. If anyone sees anything I am missing, please let me know! It would be GREATLY appreciated.

Here are the commands I used: 

        cat /etc/lsb-release; uname -a  
         sudo lshw -C network
         lspci -nn | grep -e 0280 -e 0200
         iwconfig
         rfkill list all
         lsmod
         lspci
 

 Here is the information.
 

nooch@nooch-laptop:~$ cat /etc/lsb-release; uname -a 
```
DISTRIB_ID=Ubuntu 
 DISTRIB_RELEASE=14.04 
 DISTRIB_CODENAME=trusty 
 DISTRIB_DESCRIPTION="Ubuntu 14.04.4 LTS" 
 Linux nooch-laptop 3.13.0-77-generic #121-Ubuntu SMP Wed Jan 20 10:50:42 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux 
```
 

 

 nooch@nooch-laptop:~$ sudo lshw -C network 
```
*-network                
        description: Wireless interface 
        product: RTL8188EE Wireless Network Adapter 
        vendor: Realtek Semiconductor Co., Ltd. 
        physical id: 0 
        bus info: pci@0000:02:00.0 
        logical name: wlan0 
        version: 01 
        serial: 34:23:87:69:30:cf 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
        configuration: broadcast=yes driver=rtl8188ee driverversion=3.13.0-77-generic firmware=N/A ip=192.168.1.13 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn 
        resources: irq:16 ioport:3000(size=256) memory:f0200000-f0203fff 
   *-network 
        description: Ethernet interface 
        product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller 
        vendor: Realtek Semiconductor Co., Ltd. 
        physical id: 0 
        bus info: pci@0000:05:00.0 
        logical name: eth0 
        version: 07 
        serial: a0:d3:c1:62:41:4e 
        size: 10Mbit/s 
        capacity: 100Mbit/s 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s 
        resources: irq:47 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff memory:f0400000-f040ffff 
```
 

 

 

  nooch@nooch-laptop:~$ lspci -nn | grep -e 0280 -e 0200 
```
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01) 
 05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07) 
```
 



 nooch@nooch-laptop:~$ iwconfig 
```
eth0      no wireless extensions. 
  
 lo        no wireless extensions. 
  
 wlan0     IEEE 802.11bgn  ESSID:"H832B"   
           Mode:Managed  Frequency:2.437 GHz  Access Point: F8:E4:FB:56:5A:8F    
           Bit Rate=65 Mb/s   Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr=2347 B   Fragment thr:off 
           Power Management:off 
           Link Quality=70/70  Signal level=-32 dBm   
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
           Tx excessive retries:0  Invalid misc:6   Missed beacon:0 
```
  
 

 nooch@nooch-laptop:~$ rfkill list all 
```
0: phy0: Wireless LAN 
     Soft blocked: no 
     Hard blocked: no 
```
 


 

 nooch@nooch-laptop:~$ lsmod 
```
Module                  Size  Used by 
 ctr                    13049  2  
 ccm                    17773  2  
 bnep                   19624  2  
 rfcomm                 69160  0  
 bluetooth             391136  10 bnep,rfcomm 
 uvcvideo               80885  0  
 videobuf2_vmalloc      13216  1 uvcvideo 
 videobuf2_memops       13362  1 videobuf2_vmalloc 
 videobuf2_core         40664  1 uvcvideo 
 videodev              134688  2 uvcvideo,videobuf2_core 
 arc4                   12608  2  
 radeon               1522941  3  
 kvm                   455843  0  
 crct10dif_pclmul       14289  0  
 rtl8188ee              89677  0  
 crc32_pclmul           13113  0  
 hp_wmi                 14062  0  
 sparse_keymap          13948  1 hp_wmi 
 rtl_pci                26690  1 rtl8188ee 
 snd_hda_codec_realtek    65904  1  
 rtlwifi                63475  2 rtl_pci,rtl8188ee 
 snd_hda_codec_hdmi     46368  1  
 mac80211              630728  3 rtl_pci,rtlwifi,rtl8188ee 
 snd_hda_intel          56531  5  
 snd_hda_codec         193017  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel 
 cfg80211              484040  2 mac80211,rtlwifi 
 ttm                    93424  1 radeon 
 drm_kms_helper         55071  1 radeon 
 snd_hwdep              13602  1 snd_hda_codec 
 aesni_intel            55624  4  
 snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel 
 aes_x86_64             17131  1 aesni_intel 
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel 
 snd_seq_midi           13324  0  
 lrw                    13286  1 aesni_intel 
 snd_seq_midi_event     14899  1 snd_seq_midi 
 gf128mul               14951  1 lrw 
 nls_iso8859_1          12713  1  
 glue_helper            13990  1 aesni_intel 
 snd_rawmidi            30144  1 snd_seq_midi 
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi 
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi 
 ablk_helper            13597  1 aesni_intel 
 joydev                 17381  0  
 rtsx_pci_ms            18151  0  
 cryptd                 20359  2 aesni_intel,ablk_helper 
 serio_raw              13462  0  
 k10temp                13126  0  
 memstick               16966  1 rtsx_pci_ms 
 snd_timer              29482  2 snd_pcm,snd_seq 
 drm                   303102  5 ttm,drm_kms_helper,radeon 
 hp_accel               26012  0  
 snd                    69322  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi 
 lis3lv02d              20156  1 hp_accel 
 soundcore              12680  1 snd 
 input_polldev          13896  1 lis3lv02d 
 i2c_algo_bit           13413  1 radeon 
 i2c_piix4              22155  0  
 shpchp                 37032  0  
 wmi                    19177  1 hp_wmi 
 video                  19476  0  
 hp_wireless            12637  0  
 mac_hid                13205  0  
 parport_pc             32701  0  
 ppdev                  17671  0  
 lp                     17759  0  
 parport                42348  3 lp,ppdev,parport_pc 
 rtsx_pci_sdmmc         23274  0  
 r8169                  71677  0  
 psmouse               106692  0  
 mii                    13934  1 r8169 
 rtsx_pci               46245  2 rtsx_pci_ms,rtsx_pci_sdmmc 
 ahci                   34091  3  
 libahci                32716  1 ahci 
```
 



 nooch@nooch-laptop:~$ lspci 
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Complex 
 00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Richland [Radeon HD 8650G] 
 00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller 
 00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port 
 00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 09) 
 00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] 
 00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11) 
 00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11) 
 00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11) 
 00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11) 
 00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 16) 
 00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01) 
 00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11) 
 00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40) 
 00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 0) 
 00:15.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 1) 
 00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 0 
 00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 1 
 00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 2 
 00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 3 
 00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 4 
 00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 5 
 02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter (rev 01) 
 04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01) 
 05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 07) 
```
[IMG]https://ssl.gstatic.com/ui/v1/icons/mail/images/cleardot.gif[/IMG]

---

### Post by deadflowr on 2016-02-20
Moved to *Networking and Wireless*

---

### Post by chili555 on 2016-02-20
>  I work in IT so I am pretty good with troubleshooting.Excellent. May I assume you needn't a step-by-step?

I suggest you try rtlwifi_new and a reboot. [http://askubuntu.com/questions/730430/wifi-connection-keeps-dropping-in-ubuntu-15-10-rtl8821ae/731247#731247](http://askubuntu.com/questions/730430/wifi-connection-keeps-dropping-in-ubuntu-15-10-rtl8821ae/731247#731247)

Please see Pilot6's answer. Although the subject question is for a different Realtek device, the rtlwifi_new package covers yours and several others.> this seems to be a normal thing with the combination of HP Laptops and Ubuntu....which are running some Realtek devices.

---

