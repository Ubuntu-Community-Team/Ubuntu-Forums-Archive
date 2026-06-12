---
title: "Wireless Card Issues."
date: 2009-01-23
forum: New to Ubuntu
---

### Post by Josh_Lapointe on 2009-01-23
Hello Everyone.

I'm relatively new to the whole Linux Experience. So I downloaded the Kubuntu latest version off of the website, installed with no problem, and now finally got the chance to see if I can get this working. Simple and Sweet, I have a Broadcom Wireless Card in my Inspiron 1720. I did a bit of researching on my part and tried doing a ndiswrapper, but to no avail. It seems now when I'm trying to add the .inf driver to the ndiswrapper it seems to not be working. 

If anyone can point me in the proper direction, or even assist me with the installation of these drivers, it'd be great fully appreciated. Thanks in advance.

---

### Post by mrbiggbrain on 2009-01-23
linux-wlan-ng

youll likely need to compile it yourself, not sure how that will go on ubuntu, however you can compile the pci, notebook card, and usb drivers seperate (as youll likely only need one) or all of them (incase you ever need to use another type) 

its to my knowlege that alot of devices do work with this driver. if somone else could verify (also note my ubuntu install got my viao's wireless after install, and my other PC runs fedora 5 and it hasnt been my priority to compile it.)

---

### Post by Josh_Lapointe on 2009-01-24
So, your suggesting attempting to use that driver? 

Where, and how would I install that. (Once again, newbish question.)

---

### Post by zenial on 2009-01-24
9(ndiswrapper)

---

### Post by Josh_Lapointe on 2009-01-24
So I just go "9(ndiswrapper)" in terminal and that would compile the driver above?

Please aid.

---

### Post by Josh_Lapointe on 2009-01-24
Here's more information in case this would be able to help someone. 

lspci

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)                                                                  
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)                                                                   
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)                                                                  
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)                                                                  
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller(rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

Check Interface:

eth0      Link encap:Ethernet  HWaddr 00:1d:09:be:bd:e5
          inet addr:10.0.0.111  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:febe:bde5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25269 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23636 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:36001443 (36.0 MB)  TX bytes:1941437 (1.9 MB)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:920 (920.0 B)  TX bytes:920 (920.0 B)

Listing of Modules

Module                  Size  Used by
ipv6                  263972  10     
af_packet              25728  2      
binfmt_misc            16904  1      
rfcomm                 44432  2      
bridge                 56980  0      
stp                    10628  1 bridge
bnep                   20480  2       
sco                    18308  2       
l2cap                  30464  16 rfcomm,bnep
ppdev                  15620  0             
acpi_cpufreq           15500  1             
cpufreq_powersave       9856  0             
cpufreq_conservative    14600  0            
cpufreq_stats          13188  0             
cpufreq_userspace      11396  0             
cpufreq_ondemand       14988  1             
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
pci_slot               12552  0                                            
sbs                    19464  0                                            
sbshc                  13440  1 sbs                                        
container              11520  0                                            
iptable_filter         10752  0                                            
ip_tables              19600  1 iptable_filter                             
x_tables               22916  1 ip_tables                                  
sbp2                   29324  0                                            
parport_pc             39204  0                                            
lp                     17156  0                                            
parport                42604  3 ppdev,parport_pc,lp                        
joydev                 18368  0                                            
snd_hda_intel         381488  1                                            
snd_pcm_oss            46848  0                                            
snd_mixer_oss          22784  1 snd_pcm_oss                                
dcdbas                 15008  0                                            
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss                  
evdev                  17696  18                                           
snd_seq_dummy          10884  0                                            
uvcvideo               62728  0                                            
psmouse                45200  0                                            
snd_seq_oss            38528  0                                            
pcspkr                 10624  0                                            
serio_raw              13444  0                                            
snd_seq_midi           14336  0                                            
compat_ioctl32          9344  1 uvcvideo                                   
snd_rawmidi            29824  1 snd_seq_midi                               
btusb                  19736  3                                            
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi                   
bluetooth              61924  11 rfcomm,bnep,sco,l2cap,btusb               
videodev               41344  1 uvcvideo                                   
v4l1_compat            22404  2 uvcvideo,videodev                          
sdhci_pci              15360  0                                            
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event                                                                       
snd_timer              29960  2 snd_pcm,snd_seq                                 
iTCO_wdt               18596  0                                                 
wl                   1076372  0                                                 
ieee80211_crypt        13572  1 wl                                              
ricoh_mmc              11904  0                                                 
sdhci                  23940  1 sdhci_pci                                       
iTCO_vendor_support    11652  1 iTCO_wdt                                        
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq                                                                      
mmc_core               58268  1 sdhci                                           
video                  25104  0                                                 
output                 11008  1 video                                           
intel_agp              33724  0                                                 
wmi                    14504  0                                                 
battery                18436  0                                                 
ac                     12292  0                                                 
button                 14224  0                                                 
snd                    63268  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device                       
shpchp                 37908  0                                                 
pci_hotplug            35236  1 shpchp                                          
agpgart                42184  1 intel_agp                                       
soundcore              15328  1 snd                                             
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133256  1
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sd_mod                 42264  3
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0
cdrom                  43168  1 sr_mod
sg                     39732  0
usbhid                 35840  0
hid                    50560  1 usbhid
ata_piix               24580  2
pata_acpi              12160  0
b44                    35984  0
ata_generic            12932  0
libata                177312  3 ata_piix,pata_acpi,ata_generic
ohci1394               37936  0
scsi_mod              155212  5 sbp2,sd_mod,sr_mod,sg,libata
ieee1394               96324  2 sbp2,ohci1394
dock                   16656  1 libata
mii                    13440  1 b44
ehci_hcd               43276  0
ssb                    40580  1 b44
uhci_hcd               30736  0
usbcore               148848  6 uvcvideo,btusb,usbhid,ehci_hcd,uhci_hcd
thermal                23708  0
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0
fbcon                  47648  0
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  1


lshw -c network

  *-network
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:be:bd:e5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=10.0.0.111 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 52:99:b6:e8:9b:33
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


elder@pc:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.


elder@pc:~$ lsb_release -d
Description:    Ubuntu 8.10


elder@pc:~$ uname -mr
2.6.27-7-generic i686

---

### Post by diablo75 on 2009-01-24
Here's what I'd do.

Check System>Administration>Hardware Drivers to see if there are proprietary drivers for linux available that need to be activated.  Also be sure to update Ubuntu/Kubuntu with the update manager using a ethernet connection.  I would bet money there are drivers there for your Broadcom as it's a fairly common chipset.

If not, then move on to ndiswrapper.

To install ndiwrapper, click Applications>Add/Remove... and search for ndiswrapper (you might have to change the search filter from "Canonical supported" to "All Available").

Check it off, click apply and it'll be installed.

Next you'll click System>Administration>Windows Wireless Drivers (I think) to open the ndiwrapper gui.  You'll need to download drivers for your wireless adapter that were intended for Windows and find the *.inf file associated with the drivers.

---

### Post by Josh_Lapointe on 2009-01-24
Thank you. I am currently upgrading my Nvidia card, and don't see any Broadcom drivers, but I will update my computer, cause currently its saying that it has about 250 updates, so once those are all updated, I'll test that and hopefully it'll work without using ndiswrapper.

---

### Post by Josh_Lapointe on 2009-01-24
Well, good news and bad news. Good news is that after doing the upgrades I now see the Broadcom in the propritary drivers selection, which I turned on and installed. Bad news is that I think now I have two eth0 connections. Also, I tried installing the Ndiswrapper, and did, and installed the drivers, but it doesn't seem to show up the wireless card. 

Any other ideas?

Btw:

elder@pc:~$ ndiswrapper -l
b44win : driver installed
        device (14E4:170C) present (alternate driver: b44)

Now do I restart or ??

---

### Post by johngreaver on 2009-01-24
Josh Here is what i did to get my broadcom card working in under 5 minutes i have the airforce one 54g card and i tried nidiswrapper seceral times im a linux noob too i had no success with it the easiest way i found is if u can get to a wired connection plug in go to sofware sources actiavate all the third party reop's then open synoptic search b43-cutter install it it will ask u if u want it to fetch the firmware say yes then go up activate the driver crtl alt backspace log back in u should have wireless my card actually see's more networks and gets better signal than it ever did in wondows hope this helps

---

### Post by theozzlives on 2009-01-24
search for WLANBroadcom.tar.gz and use NDISWrapper with it

---

### Post by Josh_Lapointe on 2009-01-24
Hello

I think I finally got it configured. 
It seems to be working, I'm only getting 2 out of 4 bars, and I'm sitting in front of my wireless network. Any ideas beyond that guys? And gratefully appreciate all the help.

How I got my Inspiron 1720 connected Wireless:
- Install Kubuntu
- Update all sources.
- Go to hardware within System Configuration, and add the Broadcom driver.
If this gives you issues, go to Adapt and get the ndiswrapper, and install the GUI version, add the appropriate driver, and Vola! Reboot and should work.

Thanks a lot guys once again. But if anyone got suggestions for my wireless being low let me know.

---

### Post by Josh_Lapointe on 2009-01-24
Thanks everyone

---

