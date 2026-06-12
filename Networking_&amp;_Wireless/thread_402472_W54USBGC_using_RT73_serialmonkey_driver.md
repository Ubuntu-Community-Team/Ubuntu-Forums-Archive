---
title: "W54USBGC using RT73 serialmonkey driver"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by Markio on 2007-04-05
After spending 2 days trying to get this USB dongle working I thought I would post this in the hope that it will be useful.

The following steps should get the device (**13b1:0020** as shown by **lsusb**) up and running. I have tested this on Edgy and Feisty using No Encryption, WEP and WPA. The only thing is you can't use network manager to configure the device/connect to networks, you have to use the other files described in the driver readme as there is no utility as of yet (their words, not mine :shock: )

N.B. I assume kernel-headers are installed:
```
sudo apt-get install linux-headers-`uname -r`
```

1) download the latest serialmonkey RT73 archive:
```
wget http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz
```

2) untar the archive:
```
tar zxf rt73-cvs-daily.tar.gz
```

3) enter the module directory:
```
cd rt73-cvs-*/Module
```

4) build the driver
```
make
```

5) copy the driver across
```
sudo cp rt73.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/
```

6) load the module
```
sudo insmod /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt73.ko
```

7) copy the firmware across
```
sudo cp rt73.bin /lib/firmware/`uname -r`
```

8 ) Map module dependencies
```
sudo depmod -a
```

9) kill the old rt73usb driver
```
sudo modprobe -r rt73usb
echo 'blacklist rt73usb' | sudo tee -a /etc/modprobe.d/blacklist
```

10) update the modprobe config file
```
echo 'alias rausb0 rt73' | sudo tee -a /etc/modprobe.conf
```

11) update your **interfaces** file:
```
sudo gedit /etc/network/interfaces
```

12) Add a section for the device:
```
auto rausb0
iface rausb0 inet dhcp
```

13) make the rt73 config directory:
```
sudo mkdir -p /etc/Wireless/RT73STA
```

14) copy the default config across:
```
sudo cp rt73sta.dat /etc/Wireless/RT73STA
```

15) edit the **rt73sta.dat** file:
```
sudo gedit /etc/Wireless/RT73STA/rt73sta.dat
```

16) You need to change the SSID and if your network uses encryption that goes in here too...

- For no encryption:
```
AuthMode=OPEN
EncrypType=NONE
```

- For WEP encryption
```
AuthMode=SHARED
EncrypType=WEP
DefaultKeyID=1
Key1Type=0
Key1Str=<insert your hex key here>
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
```

- For WPA
```
AuthMode=WPAPSK
EncrypType=TKIP
WPAPSK=<insert your WPA key here>
```

**Example**:
```

[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
SSID=AP350
NetworkType=Infra
Channel=0
AuthMode=OPEN
EncrypType=NONE
DefaultKeyID=1
Key1Type=0
Key1Str=0123456789
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
WPAPSK=abcdefghijklmnopqrstuvwxyz
TxBurst=0
PktAggregate=0
TurboRate=0
WmmCapable=0
AckPolicy=0;0;0;0
BGProtection=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
PSMode=CAM
TxPreamble=0
AdhocOfdm=0
FastRoaming=0
RoamThreshold=70
```

17) I'm not sure if this is needed, but it is in the readme so anyway...create network-scripts dir:
```
sudo mkdir -p /etc/sysconfig/network-scripts
```

18 ) create the config script for the rausb0 device:
```
sudo gedit /etc/sysconfig/network-scripts/ifcfg-rausb0
```

19) paste the following into the file (remove the bootproto line if your using a static IP address):
```
DEVICE='rausb0'
ONBOOT='yes'
BOOTPROTO='dhcp'

```

20) make the module load at boot
```
echo 'rt73' | sudo tee -a /etc/modules
```

21) I think we're done? Plug in the usb dongle and do a:
```
sudo /etc/init.d/networking restart
```

**OR**

Restart the computer.

:popcorn: :KS

---

### Post by AleXit on 2007-04-06
> as there is no utility as of yet (their words, not mine  )Don't worry: A graphical utility is going to be released very soon (Rutilt 0.14, you can download and test it in the rt2x00 forum).

I use rt73 legacy driver as you have described..

Only a note:
I think rt73sta.dat is not the better way to configure it.
You can set the same parameters through iwpriv, and so for example setting the /etc/network/interfaces for wpa like this one:
```
auto rausb0
iface rausb0 inet static
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.1
        pre-up ifconfig rausb0 up
        pre-up iwconfig rausb0 essid "networkname"
        pre-up iwconfig rausb0 mode Managed
        pre-up iwconfig rausb0 channel 11
        pre-up iwpriv rausb0 set AuthMode=WPAPSK
        pre-up iwpriv rausb0 set EncrypType=TKIP
        pre-up iwpriv rausb0 set WPAPSK="wpapsk-key"
        pre-up iwpriv rausb0 set SSID="networkname" 
```

Another thing: in order to load the module on boot, you should add it in /etc/modules file:
```
echo 'rt73' | sudo tee -a /etc/modules
```

Bye!

---

### Post by Markio on 2007-04-06
Thanks for the tip, I'll give the app a try :D

I forgot about the modules file... goes to update post

---

### Post by roheres on 2007-04-12
Thanks a lot for this walk-through.

 It helped getting my wireless to work in feisty using rt73sta.dat .

---

