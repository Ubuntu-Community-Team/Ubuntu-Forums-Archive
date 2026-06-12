---
title: "I can not connect to WLAN with Xubuntu 16.04"
date: 2016-07-15
forum: Networking &amp; Wireless
---

### Post by mariusfisher on 2016-07-15
Hi, 

i can not speak in english very well, but I'll gonna try it. So, I am sorry for grammatic mistakes. :)

My problem: 

I´v just installed Xubuntu 16.04. Before I already can not connect to the Internet while using the Live-Session, I took a cable, put it in my router. 
I have actually internet but not through WLAN, just with the cable. 

How can I fix it. I tried (already) everything.

- I checked and installed missing drivers with driver manager.
- I tried some option what I found on the Internet, but it did not work.

I wrote in th Terminal this
```
sudo lshw -C network
```

I got this

```
*-network               
       Beschreibung: Ethernet interface
       Produkt: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       Hersteller: Realtek Semiconductor Co., Ltd.
       Physische ID: 0
       Bus-Informationen: pci@0000:06:00.0
       Logischer Name: enp6s0
       Version: 01
       Seriennummer: 00:1d:60:6e:b3:b7
       Größe: 100Mbit/s
       Kapazität: 1Gbit/s
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       Konfiguration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.178.21 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       Ressourcen: irq:29 ioport:b800(Größe=256) memory:fe8ff000-fe8fffff memory:fe8e0000-fe8effff
  *-network
       Beschreibung: Kabellose Verbindung
       Produkt: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       Hersteller: Qualcomm Atheros
       Physische ID: 0
       Bus-Informationen: pci@0000:07:00.0
       Logischer Name: wlp7s0
       Version: 01
       Seriennummer: 00:15:af:38:e9:21
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       Konfiguration: broadcast=yes driver=ath5k driverversion=4.4.0-31-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       Ressourcen: irq:19 memory:fe9f0000-fe9fffff
```

Yes, I come from Germany so, something is in german there. :D

I click on the Network symbol, I choose my Wlan, I write my password, I click on Connect, and nothing happens. :( A message comes : Networks disconnected.

Could you pls help me, I would like to be very grateful.

Greetings

Marius

---

### Post by wildmanne39 on 2016-07-15
Please do:
```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```
if it does not connect after that run the wireless script in my signature.
Thanks

---

### Post by mariusfisher on 2016-07-16
[http://paste.ubuntu.com/19637142/](http://paste.ubuntu.com/19637142/)

I think, I may have problem with [COLOR=#0000FF]**ath5k driver.**[/COLOR]

---

### Post by wildmanne39 on 2016-07-16
Please change the settings in the router. WPA2-AES is preferred; not WPA and WPA2 mixed mode and absolutely not TKIP. Second, if your router is capable of N speeds, You should have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. Also set a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, change your country code it is showing the U.S. and you are in Europe if I am correct. Check yours:```
sudo iw reg get
```If you get 00 like I believe you will, they you need to change the setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set UK
```Of course, substitute your country code if not United Kingdom. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.
Change the last line to read:```
REGDOMAIN=UK
```Proofread carefully, save and close the text editor.

Go into network manager and set IPV6 to ignore then reboot computer.
Thanks

---

