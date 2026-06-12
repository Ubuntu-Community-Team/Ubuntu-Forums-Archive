---
title: "plz help with wireless device"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by Vic! on 2007-12-18
helpplease ........ im having trouble getting a laptop's wireless to work ..i posted this in another section but i have not recieved a reply yet :( .....with the new 7.10 update...if anyone can help me id greatly appreciate it.

heres some info.. my network settings dont even show a wifi connection / device thing i have a toshiba satellite....and

lspci output

mondoe@Mondoe-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
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
04:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


once again thank you everyone and happy holidays!!!

v

---

### Post by rustybronco on 2007-12-18
> **Vic! said:**
> 04:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

once again thank you everyone and happy holidays!!!
Your chipset is showing an ar5006eg, I would try this method.  [http://ubuntuforums.org/showpost.php?p=3912038&postcount=26](http://ubuntuforums.org/showpost.php?p=3912038&postcount=26)

---

### Post by Vic! on 2007-12-18
thanx sounds like im gettin closer there :) ... however im not quite understanding what i have to do here is there anyone that can break these instructions down for me ?? so far i know how to uninstall the ndiswrapper and madwifi but then as i get closer to the end im kina lost thanks alot :)


v

---

### Post by rustybronco on 2007-12-18
I can't give you a step by step at the moment (I'm at work) but when I get home if need be, I will.

---

### Post by Vic! on 2007-12-18
if u could id greatly appreciate it :) thanx .... meanwhile ill see if i can figure it out otherwise ill let you know ...thanx again!

---

### Post by Vic! on 2007-12-18
ok so here is where im at so far 

> mondoe@Mondoe-laptop:~$ ndiswrapper -l
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)
mondoe@Mondoe-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

mondoe@Mondoe-laptop:~$ 



and graphical


[IMG]http://farm3.static.flickr.com/2069/2121167600_685b117493.jpg?v=0[/IMG]



[IMG]http://farm3.static.flickr.com/2343/2120390163_dda0fc24a2.jpg?v=0[/IMG]

---

### Post by rustybronco on 2007-12-18
Step 16: reboot
Step 17: click on the network icon and click on "manual configuration". Wireless should now be one of the options...

did you reboot?

---

### Post by Vic! on 2007-12-18
yes i rebooted but the network settings still dont show wireless as a connection.   no idea y also my output for iwconfig is different..

---

### Post by rustybronco on 2007-12-18
I assume you installed ndiswrapper from source, not just through synaptic.
is this correct? 
You can also see kevdogs finest in my signature about trouble shooting and connecting from the command line.

---

### Post by Vic! on 2007-12-18
i tried it both ways right now i have ndiswrapper installed from source and i went through the instructions again and its not listed in my network devices yet... i noticed that when i  put typed iwconfig in terminal i was missing the last part in the terminal output  that the instructions showed

the following was missing:

> wlan0 IEEE 802.11g ESSID:"WirelessNetwork"
Mode:Managed Frequency:2.412 GHz Access Point: 00:1B:11:5F:BB:C1
Bit Rate=54 Mb/s
Power Managementff
Link Quality:100/100 Signal level:-32 dBm Noise level:-96 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


then i went to your kevdogs link and heres my output for the lshw -C network command

>  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0


acording to the guide it means the driver was incorrectly installed also there is no interface name for the device :S

---

### Post by rustybronco on 2007-12-18
Don't know how much I can help, but 
> mondoe@Mondoe-laptop:~$ ndiswrapper -l
net5211 : driver installed
device (168C:001C) present (alternate driver: ath_pci)
looks like your device is installed and present to me.

you did an upgrade from 7.04 to 7.10 that may have something to do with it.
see this post [http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154) paying attention to # 4,"To solve this (thanks to user elabranche!), check the contents of the file against the following. The file SHOULD read this way on a fresh CD install:"
 it can't hurt to try it.

---

### Post by Vic! on 2007-12-18
it wont let me alter it but its missing 

address127.0.0.1
netmask 255.0.0.0

 under the 

auto lo
iface lo inet loopback 

however my network settings dont even show a wireless device listed. 

wouldnt it be there atleast?

... what about using madwifi drivers?

---

### Post by rustybronco on 2007-12-18
> **Vic! said:**
> it wont let me alter it but its missing 

address127.0.0.1
netmask 255.0.0.0

 under the 

auto lo
iface lo inet loopback 


sudo gedit  /etc/network/interfaces      then save as...

***don't forget the rest of the stuff***

---

### Post by Vic! on 2007-12-18
hmm still not in the network manager.. i might try madwifi now but it seems the madwifi page is down since its not loading ... maybe ill call it a day and continue tommorow... thanks for your time and help!! :) +  happy holidays.

---

### Post by earache on 2007-12-19
> **Vic! said:**
> i might try madwifi now
Madwifi is enabled by default through a restricted module. It doesn't work either, though. This whole sh*t is getting on my nerves now. I'm starting to think I'll never get that AR5006EG card working on ubuntu.

---

### Post by Vic! on 2007-12-19
hmmm what if you use the latest madwifi?...

---

### Post by Vic! on 2007-12-20
OHHH i got it working ... sorta its not exactly pretty but im connected to wifi right now and its working :) ... [heres]("http://ubuntuforums.org/showthread.php?t=645010") the details hope this works for anyone that can use it

---

