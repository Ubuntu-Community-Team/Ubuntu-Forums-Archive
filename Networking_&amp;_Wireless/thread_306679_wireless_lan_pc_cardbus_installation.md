---
title: "wireless lan pc cardbus installation"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by MySweetTedy on 2006-11-25
hi,

I am new to ubuntu and i am trying to install my wireless cardbus adapter on my ubuntu 6.10. the model of my card is surecom 108M wireless lan pc cardbus adapter EP-9428-gp.
i have no idea which program or packet and how exactly to use them, so if u link me to some tutorial or some howto i will be greatful, cause i dont really know what to do

thx in advance

---

### Post by spd106 on 2006-11-25
A quick search suggests that it has an Atheros chipset, so you may be in luck. Check this by entering **lspci** at a terminal. You should see something close to this
```
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

```
You should also see an entry for ath0 in **iwconfig**.

If not try **lsmod | grep ath** and it should look something like this.
```
:~$ lsmod | grep ath
ath_pci               100000  0 
ath_rate_sample        16512  1 ath_pci
wlan                  207580  5 wlan_wep,wlan_scan_sta,ath_pci,ath_rate_sample
ath_hal               192976  3 ath_pci,ath_rate_sample

```
If not check that the "linux-restricted-modules" package has been installed in synaptic.

If there is nothing like any of these, then could you post the output from lspci.

---

### Post by MySweetTedy on 2006-11-25
hi again, im afraid it doesnt work, that&#347; all i see:

tedi@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
07:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
tedi@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"Sitecom"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          
tedi@ubuntu:~$ lsmod | grep ath
tedi@ubuntu:~$

---

### Post by MySweetTedy on 2006-11-25
p.s. im simultaniously trying to run it with a wireless usb-stick from Sitecom, that came along with the router..that&#347; why i see the wlan0 and wmaster0 etc..
thx a lot again

---

### Post by spd106 on 2006-11-25
What about the linux-restricted-modules package? It should be installed. Try **sudo aptitude install linux-restricted-modules-'uname -r'** or open up System -> Admin -> Synaptic and search for it there.

---

### Post by spd106 on 2006-11-25
[quote=MySweetTedy]p.s. im simultaniously trying to run it with a wireless usb-stick from Sitecom, that came along with the router[/quote]

Do you want to provide the output from **lsusb** as well then?

---

### Post by MySweetTedy on 2006-11-25
here is what i see : 
tedi@ubuntu:~$ sudo aptitude install linux-restricted-modules-'uname -r'
Password:
E: Malformed line 3 in source list /etc/apt/sources.list.d/edgy-multiverse.list (dist parse)
E: Malformed line 3 in source list /etc/apt/sources.list.d/edgy-multiverse.list (dist parse)
E: The list of sources could not be read.
tedi@ubuntu:~$ 


about ur second question : 
 	
Quote:
Originally Posted by MySweetTedy
p.s. im simultaniously trying to run it with a wireless usb-stick from Sitecom, that came along with the router
Do you want to provide the output from lsusb as well then?   
i have no idea how to answer that, no idea what it means :(
i dont care on which wireless adapters it works, either one would be ok, and i dont need both of them

---

### Post by spd106 on 2006-11-25
You don't need the multiverse repos for this, so open Synaptic and untick the multiverse option in the repositories dialog. Then click on reload, you should be able to install packages now.

 [quote=MySweetTedy]i have no idea how to answer that, no idea what it means [/quote]
Sorry about that, I meant enter **lsusb** at a terminal, same as you did before with lspci. Could you post the complete output from **lsmod** while your at it. This should tell you which kernel drivers are currently loaded.

To get the atheros based pcmcia card to work you will have to load the ath_hal driver which is in the linux-restricted-modules package. Once this is installed it should be enough to eject the card and re-insert it. Then you can enter the details in the System -> Admin -> Networking gui.

---

