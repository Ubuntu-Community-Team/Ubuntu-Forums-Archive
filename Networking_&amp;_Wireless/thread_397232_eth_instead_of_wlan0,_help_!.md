---
title: "eth instead of wlan0, help !"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by Ephemeral on 2007-03-30
Hello !
I am running Ubuntu 6.10 and have installed a driver with ndiswrapper to run a Inventel UR054g (R01) dongle, so that I can access my Wanadoo Livebox with wifi.
Anyways, I am having problems :

Everything is installed, all the stuff like :

sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
(...)

(altho, if state some in case I forgot theme ^___^ )

But, when I type : iwconfig 
I get : 
lo (no wireless extensions)
eth0 same
eth1 IEEE 802.11b (etc, but invalid access and nothing working)
and another

But no wlan0 !
I have edited /etc/iftab and commented out eth0 and eth1.
I have edited /etc/network/interfaces, it now displays :

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

 auto eth1
 iface eth1 inet dhcp

 auto eth2
 iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid Wanadoo_xxxx
```

this command :
```
cat /etc/modprobe.d/ndiswrapper
```
gives me :
```
alias wlan0 ndiswrapper
```
And nothing else

I can post anything you'll need, but PLEASE help me !!!

---

### Post by Ephemeral on 2007-03-30
yo !!!

---

### Post by spd106 on 2007-03-30
Can you please post the output of the following command?
```
sudo lshw -class network
```

This will tell you the interface name currently in use by the device and the driver you are using. If says it's using bcm43xx, then you will have to remove this before ndiswrapper can be loaded.

---

### Post by Ephemeral on 2007-03-30
```
eternal@eternal-desktop:~$ sudo lshw -class network
Password:
  *-network DISABLED      
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@02:05.0
       logical name: eth1
       version: 10
       serial: 00:0f:ea:d3:c2:94
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=half link=no multicast=yes port=MII speed=10MB/s
       resources: ioport:a000-a0ff iomemory:ea004000-ea0040ff irq:217
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: eth0
       serial: 00:3d:b4:00:00:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b
```

This is what I get, any help ?

---

### Post by dbott67 on 2007-03-30
Deleted and moved after my 2nd post for clarity.

---

### Post by dbott67 on 2007-03-30
It appears as though your wireless is **eth0** *(according the the output of lshw -C network)* and your wired is **eth1**.   I also noticed that the MAC address for eth0 (your wireless) looks strange (00:3d:b4:00:00:00) --- this could be part of the trouble if the MAC is not being read properly.

It appears as though you have followed many of the same steps I did.  The only thing I would recommend is uncommenting your iftab file back to it's original form and make sure that your **/etc/network/interfaces** file is specifying the correct logical interface ([COLOR=Red]**eth1=wired**[/COLOR], **[COLOR=Red]eth0=wireless[/COLOR]**).  If this works, then we can proceed to change the name as it appears in the iftab file so that **[COLOR=Red]eth0=wired[/COLOR]** and[COLOR=Red]** wlan0=wireless**[COLOR=Black] (which is outlined in my reference post at the bottom).[/COLOR][COLOR=Black]

To start, we need to edit your **/etc/network/interfaces** to look something like this:
[/COLOR][/COLOR][COLOR=Red][COLOR=Black]```

auto lo
iface lo inet loopback

[COLOR=Blue] # Wireless Interface[/COLOR]
[COLOR=Red] auto eth0[/COLOR]
iface eth0 inet dhcp
[COLOR=Red] wireless-essid Wanadoo_xxxx[/COLOR]

[COLOR=Blue] # Wired Interface[/COLOR]
auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```Next, we need to undo any changes you made to your **/etc/iftab** file so that it looks something like this:

[/COLOR][/COLOR]```

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:3d:b4:00:00:00 arp 1 [COLOR=Red]#Wireless[/COLOR]
[COLOR=Black][COLOR=DarkOliveGreen]eth1[/COLOR] [/COLOR]mac 00:0f:ea:d3:c2:94 arp 1 [COLOR=Red]#Wired[/COLOR]

```Just be sure that the entries in your iftab correspond  to the correct MAC address for each network card.

#####################################################################

For reference, I documented my troubles & corresponding solutions in getting wireless working on my laptop in [this thread]("http://www.ubuntuforums.org/showthread.php?t=274915"), but I'll post the relevant part here:
> **dbott67]
**_Broadcom 4311 Wireless:_**

I was able to get the wireless card working, however, I needed to blacklist the existing bcm43xx module and use ndiswrapper:

1. Install **build-essential** from Synaptic (for compiling ndiswrapper)

2. Download latest stable version of **ndiswrapper** from [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

3. Compile **ndiswrapper** according to [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

4.  Blacklist the bcm43xx module:
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```5. In order to get 'iwlist scanning' to display results, I needed to edit my /etc/network/interfaces file to contain the appropriate settings for my AP:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
[COLOR=Red]wireless-essid MYSSID
wireless-key s:mysecretwepkey
[/COLOR]
auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```I'm not sure why my wireless card is now using eth1 (it used to be wlan0 in Dapper), but hey, it's working! :)

```
dbott@edgy:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:40:05:B2:AF:45
                    ESSID:"bott"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:92/100  Signal level:-37 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s said:**
> Note: any kernel updates will require that ndiswrapper be recompiled[/COLOR]

**_February 24, 2007 - Wireless Update_**

Regarding the eth1 issue, I believe it was related to an entry in my iftab file that contained the following line:
```
eth1 mac 00:16:ce:31:88:XX arp 1 
```I changed the file to read:
```
dbott@edgy:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:15:c5:0c:ad:XX arp 1
[COLOR=Red]wlan0[/COLOR] mac 00:16:ce:31:88:XX arp 1

```And then I installed **network-manager-gnome** and it seems to have cured all my problems.  The card is now recognized as **wlan0** and the network manager handles all the settings (WEP, scanning, etc.).


---

### Post by Ephemeral on 2007-03-31
Okay, so I reinstalled ndiswrapper.
I installed the driver, BUT :
When I type :
ndiswrapper -l

I get this :

```
'ARNING: etc/modprobe.d/blacklist line 4 : ignoring bad line starting with '
'ARNING: etc/modprobe.d/blacklist line 7 : ignoring bad line starting with '
'ARNING: etc/modprobe.d/blacklist line 11 : ignoring bad line starting with '
'ARNING: etc/modprobe.d/blacklist line 14 : ignoring bad line starting with '
'ARNING: etc/modprobe.d/blacklist line 20 : ignoring bad line starting with '
'ARNING: etc/modprobe.d/blacklist line 24 : ignoring bad line starting with '
'ARNING: etc/modprobe.d/blacklist line 27 : ignoring bad line starting with '

```
and then it show that prisma 02 is installed, but that the driver has an alternatve, which is islsm_pci, which I have blacklisted
Any ideas ? (if you could hsot the blacklist file, I could then overwrite mine)

---

### Post by Ephemeral on 2007-03-31
yo ....

---

### Post by Ephemeral on 2007-03-31
heeeelllllooooooooooooo

---

### Post by dbott67 on 2007-03-31
This is mine:
```
dbott@edgy:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
blacklist bcm43xx [COLOR=Red]*# <-- I added this one to blacklist my Broadcom wireless*[/COLOR]

```Can you post yours?

-Dave

---

### Post by Ephemeral on 2007-04-01
```
eternal@eternal-desktop:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we dont want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesnt seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# allow wifi
blacklist prism54
blacklist islsm_usb
blacklist islsm_pci
blacklist islsm_device
blacklist islsm_pci
blacklist islsm_pci
eternal@eternal-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:off/any  
          Mode:Auto  Channel=0  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth3      no wireless extensions.

sit0      no wireless extensions.

eternal@eternal-desktop:~$ ndiswrapper -l
'ARNING: /etc/modprobe.d/blacklist line 4: ignoring bad line starting with '
'ARNING: /etc/modprobe.d/blacklist line 7: ignoring bad line starting with '
'ARNING: /etc/modprobe.d/blacklist line 11: ignoring bad line starting with '
'ARNING: /etc/modprobe.d/blacklist line 14: ignoring bad line starting with '
'ARNING: /etc/modprobe.d/blacklist line 17: ignoring bad line starting with '
'ARNING: /etc/modprobe.d/blacklist line 20: ignoring bad line starting with '
'ARNING: /etc/modprobe.d/blacklist line 24: ignoring bad line starting with '
'ARNING: /etc/modprobe.d/blacklist line 27: ignoring bad line starting with '
prisma02 : driver installed
        device (1435:0427) present (alternate driver: islsm_usb)
eternal@eternal-desktop:~$ sudo gedit /etc/modprobe.d/blacklist
Password:
eternal@eternal-desktop:~$ ndiswrapper -l
prisma02 : driver installed
        device (1435:0427) present (alternate driver: islsm_usb)
eternal@eternal-desktop:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we dont want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.
# evbug is a debug tool that should be loaded explicitly
blacklist evbug
# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd
# replaced by e100
blacklist eepro100
# replaced by tulip
blacklist de4x5
# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394
# snd_intel8x0m can interfere with snd_intel8x0, doesnt seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m
# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
# allow wifi
blacklist prism54
blacklist islsm_usb
blacklist islsm_pci
blacklist islsm_device
blacklist islsm_pci
blacklist islsm_pci
eternal@eternal-desktop:~$

```

```
Then I reboot
```

```
eternal@eternal-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

eth3      IEEE 802.11b  ESSID:off/any  
          Mode:Auto  Channel=0  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

eternal@eternal-desktop:~$ ndiswrapper -l
prisma02 : driver installed
        device (1435:0427) present (alternate driver: islsm_usb)
eternal@eternal-desktop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth3      No scan results
sit0      Interface doesn't support scanning.

eternal@eternal-desktop:~$ 

```

I edited the file using Windows, maybe that's what added the 's
So now it's eth3 instead of eth1
Any ideas ?
Should I use :
```
sudo ndiswrapper -a 435:0427 prisma02
```
?

---

### Post by Ephemeral on 2007-04-01
bump...

---

### Post by Ephemeral on 2007-04-01
hellllllloooooooooo...

---

### Post by Ephemeral on 2007-04-01
*cries*

---

### Post by dbott67 on 2007-04-01
The only thing I can suggest is that you go through this thread very carefully:
[http://www.ubuntuforums.org/showthread.php?t=280239&highlight=UR054g](http://www.ubuntuforums.org/showthread.php?t=280239&highlight=UR054g)

Read the whole thread through to the end first, as the first drivers tried did not work.  Post #66 contains drivers that worked for the OP.

You might also want to post some of your questions/problems/results to that thread, as they were able to resolve the problem.

-Dave

---

