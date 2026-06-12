---
title: "iwconfig not accpeting configuration on Xubuntu"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by kaiwan on 2008-03-18
HI! 

I have laptop with Xubuntu on. Bought usb wireless adapter, Digitus, and tried it on my Ubuntu deskop. Used ndiswrapper, iwconfig, dhclient and ifup. And it worked. But the same procedure on Xubuntu doesnt work. Laptop is old so I cant connect it with cable.

So on Xubuntu laptop I managed to install driver using ndiswrapper.
But When I type:
sudo iwconfig wlan0 essid mynetname enc 123456789
and then I run iwconfig again to check if changes are stored
it shows me my wlan0 but under ESSIED says any/of and under ENC of ...
So it appears as it didnt save the changes I typed previously.  
Of course dhclient doesn't work.

---

### Post by vertago1 on 2008-05-03
I having the same probem in Xubuntu 8.04 with ndiswrapper and a airlink101 pci card (model 3028) using a realtek 8185 chipset.

I have tried both the windows xp and 2000 drivers with ndiswrapper and have the same problem with both. I know this card works with the 64bit kubuntu 8.04 using ndiswrapper.

The symptoms for me are as follows:
- Gnome network manager doesn't see any wireless interfaces.
- I used the network settings in Xfce to set the essid and wep key but it didn't seem to do anything, even though it successfully lists the wireless networks in the area.
- when I use dhclient it times out unless I have the wired hooked up.
- iwlist works correctly
- iconfig lists wlan0 as 
> IEEE 802.11g  ESSID:off/any  
Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated   
Bit Rate:54 Mb/s   Tx-Power:46 dBm   Sensitivity=0/3  
RTS thr:off   Fragment thr:off
Encryption key:6365-6369-6C   Security mode:restricted
Power Management:off
Link Quality:0  Signal level:0  Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0

- running:
sudo iwconfig wlan0 essid "<my network>" key s:"<my key>"
gives no output on the bash screen. Next, when I run dhclient it times out again, and running iwconfig lists wlan0 as unassociated.

dmesg gives the following lines concerning ndiswrapper:> [10237.189327] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[10237.249437] ndiswrapper: driver net8185 (Realtek,09/06/2007,5.1101.0906.2007) loaded
[10237.252264] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKB] -> GSI 3 (level, low) -> IRQ 3
[10237.530508] ndiswrapper: using IRQ 3
[10242.473856] wlan0: ethernet device 00:40:f4:f8:5a:88 using NDIS driver: net8185, version: 0x50449, NDIS version: 0x500, vendor: 'Realtek RTL8185 Wireless LAN (Mini-)PCI NIC                                     ', 10EC:8185.5.conf
[10242.478195] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[10242.552903] usbcore: registered new interface driver ndiswrapper
[10253.421038] wlan0: no IPv6 routers present


EDIT: I just removed all the ndiswrapper packages, removed the ndiswrapper kernel module, installed from source, reloaded the windows driver, added ndiswrapper via modprobe, and got the same results. If I can't figure it out tomorrow I will probably load kubuntu 8.04, but the machine is only a 800MHz.

so yeah, iwconfig is pretty much unresponsive for me in Xubuntu 8.04 with ndiswrapper

Maybe this extra info will help troubleshoot the problem

---

### Post by vertago1 on 2008-05-04
This is driving me crazy...

I popped in the kubuntu 8.04 instal dvd. Installed ndiswrapper and got the wireless card working using ndiswrapper. I installed kubuntu, and then installed ndiswrapper and got it to work. After I rebooted when I did the modprobe I started running into a very similar problem to what I was having while xubuntu was on the system. knetworkmanager recognizes the interface wlan0 however this time rather than being able to scan but not connecting it will neither scan or connect.

Ifdown wlan0 says that the interface is not configured. I am going to see if I can figure it out from there tomorrow.

---

### Post by sensae on 2008-06-24
I'm having exactly the same problem. Has anyone found a solution to this?

---

