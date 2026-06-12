---
title: "[SOLVED] Wifi detected, but unable to connect"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by thecoolcat on 2007-11-04
Hello,

I'm trying to connect to my wireless router using wireless USB adapter (using Gutsy), can someone please help me. Here are more details:

1) Adapter: D-Link DWL G122 (Rev D), Device ID is 07d1:3b01 

2) No linux drivers. So installed using ndiswrapper. (used WinXP version provided by the manufacturer). After installing the driver, I can now see the USB device

3) Output of  "iwlist wlan0 scan" command:
> 
          Cell 01 - Address: 00:14:6C:65:FD:28
                    ESSID:"NETGEAR_SafeHGU"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:48/100  Signal level:-65 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
[COLOR="Red"]          Cell 02 - Address: 00:17:9A:31:6B:4C
                    ESSID:"Archie"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:46/100  Signal level:-66 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0[/COLOR]


I'm trying to connect to "Archie".

4) My router was initially secured (128 bit WEP). I have now turned it off to simplify things.

5) Here's the contents of /etc/network/interfaces

> 
auto lo
iface lo inet loopback

[COLOR="Blue"]auto wlan0
iface wlan0 inet dhcp
##wireless-key xxxxxxxxxxxxxxxxxxxxxxxxxx
wireless-essid Archie[/COLOR]

iface wlan1 inet dhcp
##wireless-key xxxxxxxxxxxxxxxxxxxxxxxxxx
wireless-essid Archie
auto wlan1



I also tried to install another wireless usb adapter. After trying to configure the second usb adapter mu /etc/network/interfaces got modified and I see wlan1 for that adapter.

6) Here's some relevent info from dmesg command:

[COLOR="Red"][ 2184.921120] usb 1-8: USB disconnect, address 6
[ 2185.009548] ndiswrapper: device wlan1 removed
[ 2189.555334] usb 1-7: new high speed USB device using ehci_hcd and address 7
[ 2189.694944] usb 1-7: configuration #1 chosen from 1 choice
[ 2189.810803] usb 1-7: reset high speed USB device using ehci_hcd and address 7
[ 2190.007532] ndiswrapper: driver usb55n5x (D-Link,07/28/2005,2.1.0.4) loaded
[ 2192.177944] wlan0: ethernet device 00:15:e9:f3:d3:2d using NDIS driver: usb55n5x, version: 0x2000102, NDIS version: 0x501, vendor: 'Marvell 802.11 Driver for USB 2.0 Adapter', 07D1:3B01.F.conf
[ 2192.177973] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 2240.216990] NET: Registered protocol family 10
[ 2240.217358] lo: Disabled Privacy Extensions
[ 2240.217594] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2240.217942] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2278.404991] ADDRCONF(NETDEV_UP): wlan0: link is not ready[/COLOR]

7) It seems like I'm very close. Can someone help me?

Thanks in advance.

---

### Post by thecoolcat on 2007-11-04
When I do a "sudo dhclient wlan0", this is what I get:

[COLOR="red"]user@computer:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:12:17:35:17:10
Sending on   LPF/wlan0/00:12:17:35:17:10
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DSCPOFFERS received.
No working leases in persistent database - sleeping.[/COLOR]

I tried setting up default gateway using sudo route add default gw 192.168.1.1 and tried again.

Also, I tried the following:

[COLOR="Red"]sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>[/COLOR]

Still doesn't work. :( Can someone help me?

---

### Post by kevdog on 2007-11-04
Is the chipset of your device Marvell?

Marvell 802.11 Driver for USB 2.0 Adapter

Just make sure -- do a search on the internet if you dont know.

What channel is your router broadcasting on?

Have you tried booting with the USB stick in place?

---

### Post by thecoolcat on 2007-11-04
Thanks kevdog for your reply.

1) The chipset is indeed Marvell. I googled device ID and found out that it was a Marvell chipset.
2) >  What channel is your router broadcasting on?   How do I find this info? My router is a D-Link router.
Here's ipconfig from another machine that runs WinXP:
[COLOR="Red"]Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.0.100
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1[/COLOR]
3) Yes. I rebooted the machine with the USB in place. 

Thanks.

---

### Post by kevdog on 2007-11-04
i thin the default ip address of the dlink router is 192.168.0.1.  You will need another computer with a connection or an ethernet connection to access the router and look through the web interface at the settings of the router.

---

### Post by thecoolcat on 2007-11-04
Hah. OK. Its channel 6.

More details of my router:

Wireless 
MAC Address  00-17-9a-31-6b-4c  
SSID  Archie  
Channel 6  
ENCRYPTION  Disabled  

LAN 
MAC Address  00-17-9a-31-6b-4c  
IP Address  192.168.0.1  
Subnet Mask  255.255.255.0  
DHCP Server  Enabled  

WAN
...

---

### Post by thecoolcat on 2007-11-04
Hi kevdog,

I used one of your threads where you've mentioned about configuring through the command line. Rebooted. It works. Thanks. Let me fiddle around with it more. :)

---

### Post by thecoolcat on 2007-11-08
Marking this as solved.

Here's a summary:

1) About the adapter:
USB adapter is D-LINK DWL G122 (Rev D1)
lsusb gives this ID 07d1:3b01 
It has Marvell chipset.

2) Installed "ndiswrapper" package without working internet connection 

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 
sudo depmod -a
sudo modprobe ndiswrapper 
```

3)Add the module to "/etc/modules" to have it load automatically (use "kate" instead of "gedit" in Kubuntu):

```
sudo gedit /etc/modules 
```

Now add this to the end & save the file:

[COLOR="Red"]ndiswrapper [/COLOR]

4) Create alias directive
```
sudo ndiswrapper -m 
```

5) Edit [COLOR="Blue"]/etc/modprobe.d/blacklist [/COLOR]to add "[COLOR="red"]blacklist <your driver[/COLOR]" at the end of the file. (I just put all rt* drivers.)

6) Install your driver. I used WinXP version found in D-Link's website
```
sudo ndiswrapper -i <your_driver>.inf 
```
7) Verify:
```
ndiswrapper -l 
```

Output will tell you that the device is present, if the adapter is plugged in.

8a) Connect to your wireless now (unencrypted). Interface was [COLOR="blue"]wlan0[/COLOR] for me.
```
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```

8b) Connect to your wireless now (encrypted).
```
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> key HEX_KEY <<<-------- If using ASCII Equivalent, this is s:ASCII_KEY (please make note of the prefix s:)
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```
9) Reboot. (Make sure your adapter is in place when you reboot.)
10) Be happy if it works, if not, open a thread and ask for help. :)

---

