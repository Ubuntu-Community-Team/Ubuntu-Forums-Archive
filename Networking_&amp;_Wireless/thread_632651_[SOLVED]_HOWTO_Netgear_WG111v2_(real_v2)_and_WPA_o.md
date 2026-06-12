---
title: "[SOLVED] HOWTO: Netgear WG111v2 (real v2) and WPA on Xubuntu 6.06.1 LTS - my experien"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by slayer^_^ on 2007-12-05
Hi there, i'd like to share my experience, maybe it can be useful... let me tell you all the story, it's gonna be fun !!!

**_TROUBLE ZERO (OT)_** - I wanted to install Xubuntu Gutsy Gibbon on this old ARMADA V300 laptop, (64 mb RAM), but it turned to be impossible due to an initramfs gutsy bug that didn't allow me to use the ide=nodma option..

**_SOLUTION ZERO (OT)_** - then i turned to Xubuntu Dapper Drake 
6.06.1 LTS and i had been able to install it.

**_FIRST TROUBLE_** - Netgear WG111v2 recognized? not? surely not connecting... i already knew this usb dongle had troubles with pre-gutsy so i already knew a litl about it... i found the "final easy solution" in ubuntu forums, but it didn't work !!!

**_FIRST SOLUTION_** - 

**BLACKLIST the default drivers installed as part of Dapper**

```
sudo mousepad /etc/modprobe.d/blacklist
```

add to the bottom of the list

```
blacklist rtl818x
blacklist r818x
blacklist rtl8187
blacklist r8187
blacklist islsm_usb
blacklist islsm
```

this list is longer than the one i found in the most recent topics... the r-starting ones were not included... well i included them and i didn't have any troubles 'bout it

**install ndiswrapper**
Install the package ndiswrapper-utils (for example using the Synaptic Package Manager, don't worry if you've not a connection, this package should be on the Dapper Drake CD).

**find the Netgear WG111 driver**. now this was perhaps the most troubled part... in spite of what many forums said, WG111v2 DOESN'T (at least in my experience) WORK with WG111 drivers that you can find everywhere, that are said to work with v2 too. It's perhaps a misunderstanding due to the fact that many WG111v2 devices are labeled v2 but they mount a v1 hardware (the infamous fake v2). 

well i can't remember how to discover if your device is REALLY OR NOT a v2.. however you can try tiyping this command in the console

```
lsusb | grep NetGear
```

it is commonly reported that if the output is 0846:4240 your device is a real v2, though this is my output and i've got a v2

Bus 001 Device 003: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)

you can try the WG111 driver or the WG111v2 (WIN 98 !!!).

I used the WG111v2 (WIN 98 ). I got them from the bundle cd, but you can download them from [www.netgear.com](www.netgear.com) 

- the WG111 driver is in the ndis5 subfolder and is named netwg111.inf  (be sure not to copy only this file but all the parent folder)

- the WG111v2 driver is in the WIN98 subfolder and is net111v2.inf (again, copy the entire parent folder)

here's where to download drivers:

NETGEAR WG111
[ftp://downloads.netgear.com/files/wg111_2_1.zip](ftp://downloads.netgear.com/files/wg111_2_1.zip)

NETGEAR WG111v2
[ftp://downloads.netgear.com/files/wg111v2_1_3_0.zip](ftp://downloads.netgear.com/files/wg111v2_1_3_0.zip)

**configure ndiswrapper**

```
cd /DRIVER/DIRECTORY/
sudo ndiswrapper -i net111v2.inf
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```

obviously netwg111.inf if you plan to install the WG111 driver

**configure modules**

```
sudo mousepad /etc/modules/
```

''...add to bottom of the listing...''
ndiswrapper

now **reboot** and type in the console

```
ndiswrapper -l
```

to be sure the installation has gone properly, the output should be something like:

Installed drivers:
net111v2 driver installed, hardware present

**_SECOND  TROUBLE_** : Xubuntu 6.0.6.1 LTS network interface DOESN'T allow you to choose a WPA encrypted wireless connection.

**_SECOND SOLUTION_** : You can use wpa_supplicant

**link MAC to wlan0**  You can find the MAC address of the device written on the side. It should be something like 000FB5XXXXXX, you just need to place the colon after each 2 characters/numbers.

```
sudo mousepad /etc/iftab/
```

''...add to bottom of the listing...''

```
wlan0 mac 00:00:00:00:00:00
```

replacing it with your mac address (it should be written on your wireless adapter)

**put the WG111v2 USB device in** I performed a re-boot at this point.

**Install wpa_supplicant**

```
sudo apt-get install wpasupplicant
```

probably it's already installed

**configure wpa supplicant**

probably there's no wpa_supplicant.conf file, however edit it (if it's not present it will be created) :

```
sudo mousepad /etc/wpa_supplicant.conf
```

add these strings:

```
 network={
 ssid="YOURNETWORKNAME"
 psk="YOURALPHANUMERICKEY"
 key_mgmt= WPA-PSK
 proto=WPA
 pairwise=CCMP TKIP
 }
```

for example ssid="Pingu" and psk="pazzwoord"

save and exit

**configure network interface**:

```
sudo mousepad etc/network/interfaces
```

add these strings:

```
iface wlan0 inet dhcp
wireless-essid Nomerete
wireless-mode managed
wireless channel 11 (your wireless channel here!!!)
wpa-driver ndiswrapper 
wpa-conf /etc/wpa_supplicant.conf
auto wlan0
```

obviously it may be not wlan0 but, for example, wlan1 or eth1 instead. it depends on your hardware configuration. moreover obtain your wireless channel from the configuration file of your router/modem. 
the most important passage here is "wpa-driver ndiswrapper", every wpa_supplicant guide, obviously, reported "wpa-driver wext" that meant to use linux native driver (but we blacklisted it, didn't we?)

**save and active network interface** with:
```
sudo ifconfig wlan0 up
```

**reboot your networking with**

```
sudo /etc/init.d/networking restart
```

at this point everything worked... i sometimes experienced network absence after reboot, but with the command 
```
sudo /etc/init.d/networking restart
``` 
everything began to work again

**you might want to use a static ip address**

```
sudo mousepad /etc/network/interfaces
```

and use this configuration instead:

```
iface wlan0 inet static
address 192.168.1.2 (your static ip address)
netmask 255.255.255.0
gateway 192.168.1.1
network 192.168.0.0
wireless-essid YOURNETWORKNAME
wireless-mode managed
wireless channel 6 (your wireless channel)
wpa-driver ndiswrapper
wpa-conf /etc/wpa_supplicant.conf
auto wlan0
```

obtain your wireless channel from your router settings.

and now **reboot**...

at this point, if network doesn't work (don't look at the applet networking, try opening a browser), try **rebooting the network **devices

```
sudo /etc/init.d/networking restart
```

if again network is dead, try **uninstalling your netgear driver and installing a different version**... for example, to switch from wg111v2 to wg111 driver:

```
sudo -e net111v2.inf
cd /DRIVER/DIRECTORY/ndis5
sudo ndiswrapper -i netwg111.inf
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```
  
i hope to have solved your troubles... post your experience with this weird dongle here..

---

### Post by JuiceyBananas on 2008-04-02
This fixed my problem wonderfully. Thank you very much!

I have the WG111v2 and it was coming up with the same information you mentioned in the terminal. I would be able to find wireless networks and connect to my WEP network but the connection would only last five minutes at the most. I'd have to re-boot just to get the connection back for another 5 minutes.

Unfortunately I didn't have my Ubuntu CD, I had burned the ISO to a RW and used the disk for something else. So after entering in my WEP numerous times and attempting to re-connect over and over again I finally got a long enough window to hit "apply" on the package manager and download ndiswrapper.

Followed your directions up to the WPA part and everything is wonderful. I include my story here in case other people are searching these forums for answers.

I love you.

---

### Post by slayer^_^ on 2008-04-25
thank you for posting your experience ;)

---

