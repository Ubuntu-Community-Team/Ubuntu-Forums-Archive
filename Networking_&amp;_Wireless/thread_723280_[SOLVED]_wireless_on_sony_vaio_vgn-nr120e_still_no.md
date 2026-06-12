---
title: "[SOLVED] wireless on sony vaio vgn-nr120e still not detected"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by gusanto on 2008-03-13
After trying to follow some suggestions in this forum, my wireless card on Sony Vaio VGN-NR120E is still not detected.
From "dmesg" output I have seen many lines telling about "ndiswrapper". Are those lines not indicating about the problem of the undetected wireless card? I can send those lines to this forum if needed.
If somebody is willing to guide me step by step from beginning again, it would be much appreciated (I don't know how to do it by myself as I'm only a normal computer user).
Thanks.

---

### Post by wieman01 on 2008-03-13
Please post:
> sudo iwlist scan
> sudo lshw -C network
> sudo cat /etc/network/interfaces

---

### Post by gusanto on 2008-03-13
sudo iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1a:80:1f:8b:1a
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A ip=192.168.1.102 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
```

sudo cat /etc/network/interfaces
```
auto lo
iface lo inet loopback
```

---

### Post by wieman01 on 2008-03-14
OK, your wireless device has either been switched off (physically?) or is not recognized (which would be odd since most Vaio's ought to work out of the box).

What wireless adapter have you got? Can you find out?

---

### Post by iFost on 2008-03-15
i have the same exact problem, the internet works fine with windows, but doesnt work on ubuntu.

---

### Post by gusanto on 2008-03-17
> **wieman01 said:**
> OK, your wireless device has either been switched off (physically?) or is not recognized (which would be odd since most Vaio's ought to work out of the box).

What wireless adapter have you got? Can you find out?

The device is physically turned on but no light comes on as it is when I'm running Windows Vista.
lspci gives me (part of it):
> 06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
        Subsystem: Foxconn International, Inc. Unknown device e000
        Flags: fast devsel, IRQ 18
        Memory at fa000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

---

### Post by wieman01 on 2008-03-18
> **gusanto said:**
> The device is physically turned on but no light comes on as it is when I'm running Windows Vista.
lspci gives me (part of it):
It appears your device has not been recognized. You may want to give 'ndiswrapper' a chance. Do you find your device on their list of know hardware?

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/")

Sorry I cannot advise more.

---

### Post by gusanto on 2008-03-18
> **wieman01 said:**
> It appears your device has not been recognized. You may want to give 'ndiswrapper' a chance. Do you find your device on their list of know hardware?

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/")

Sorry I cannot advise more.

The search gives me message:

> Search Keyword AR5006EG
Total 0 results found. Search for [ AR5006EG ]

It seems that I won't be able to connect internet from Ubuntu on my laptops.

---

### Post by wieman01 on 2008-03-18
Mmm... I found something here:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/")

Now search for "AR5006EG"...

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/")

Your card is definitely listed.

---

### Post by gusanto on 2008-03-18
> **wieman01 said:**
> Mmm... I found something here:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/")

Now search for "AR5006EG"...

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/")

Your card is definitely listed.

I downloaded the driver from the link you gave.  Please guide me the next steps so I won't miss any single step.
Thanks.

---

### Post by wieman01 on 2008-03-18
Last qestions though... Are you on 64-bit Ubuntu or 32-bit?

Please start following my tutorial (signature), I will support you.

---

### Post by gusanto on 2008-03-18
> **wieman01 said:**
> Last qestions though... Are you on 64-bit Ubuntu or 32-bit?

Please start following my tutorial (signature), I will support you.

>  getconf LONG_BIT gives me>  32

---

### Post by gusanto on 2008-03-18
Below are some outputs after following your steps in your signature:
1.  gedit /etc/modprobe.d/blacklist
> # This file lists those modules which we don't want to be loaded by
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
blacklist ath_pci

2. ndiswrapper -l
> net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)
netathr : driver installed
        device (168C:001C) present (alternate driver: ath_pci)

The second driver is the one that install the same driver from my Windows Vista (I followed a link to try so).

3. sudo gedit /etc/network/interfaces
> auto lo
iface lo inet loopback
auto wlan0
iface wlan0 inet dhcp
I added the last 2 lines as you wrote in your suggestion.

4. sudo iwlist scan
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Still the LED light of the wireless card does not come on.

---

### Post by diog3n3s on 2008-03-19
hello, i have the same problem here, with the same wireless adapter.  I have read around and found mention that it wont work if the ndiswrapper -l command shows ath_pci as an alternate driver, with people suggesting to blacklist it in modprobe.d, which i have done, as did other poster here.  And still ath_pci shows up as an alternate driver...is this the conflict that is keeping ndiswrapper from correctly loading the drivers?

---

### Post by ugm6hr on 2008-04-08
Try reading this, and look at the first link in this post - many people have found it useful.
[http://ubuntuforums.org/showpost.php?p=4259805&postcount=14](http://ubuntuforums.org/showpost.php?p=4259805&postcount=14)

---

### Post by chalewa on 2008-04-08
[http://ubuntuforums.org/showpost.php?p=3868406&postcount=48](http://ubuntuforums.org/showpost.php?p=3868406&postcount=48)

if you follow that tutorial, you should get it wireless


that is for the vgn-nr11oe, but it uses the same card.

---

### Post by gusanto on 2008-04-08
I have tried to follow the link suggested by ugm6hr,unfortunately I'm still unable to connect to internet from my wireless.  I think I'm close to that.  The wireless card now has been detected.  I tried to configure the wireless connection both from network-admin and wicd but had no luck.  Wicd even reported "No wireless networks found" which in fact I detected some wireless networks including mine.
Below are some outputs of some command (I appologize if these are not appropriate command as I'm only newbie):

 iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"DFI2000"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:15 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-98 dBm  Noise level=-98 dBm
          Rx invalid nwid:283  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

 sudo iwlist scan
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
[COLOR="Red"].... (ommitted) .....[/COLOR]

          Cell 02 - Address: 00:16:B6:47:AC:EB
                    ESSID:"DFI2000"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/70  Signal level=-40 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100 

[COLOR="Red"] ... (ommitted) ......[/COLOR]

I don't know why some of letters "o" have been replaced by icons.

sudo cat /etc/network/interfaces
> auto lo
iface lo inet loopback


iface eth0 inet dhcp





iface ath0 inet dhcp
wireless-essid DFI2000

Why do I have some empty lines on output above?

sudo cat /etc/network/interfaces
>   *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1a:80:1f:8b:1a
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A ip=192.168.1.102 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wifi0
       version: 01
       serial: 00:1d:d9:dd:a7:81
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (svn r2756) latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g















auto ath0

                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100


---

### Post by wieman01 on 2008-04-09
Looks much better now. If you now edited "/etc/network/interfaces" so that it reads:
> auto lo
iface lo inet loopback
I am sure Network Manager will pick it up after a reboot.

---

### Post by gusanto on 2008-04-09
Wireless Problem on Sony Vaio VGN-NR120E - S O L V E D

Finally I can connect to Internet through my wireless, the problem is solved.
What I have done to make it work was actually following this link [http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007](http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007) .  Thanks Ugm6hr for directing me to the link.  Here is the summary:
1. Download the madwifi from the link above

2. Install this tool to compile the source code:
 >  sudo apt-get install build-essential linux-headers-`uname -r`

3. Uninstall ndiswrapper or madwifi (if you have installed one of them before).  Go to the directory and then do:
   >  sudo make uninstall
    sudo make clean

4. Untar the downloaded madwifi file
>     sudo tar zxvf madwifi-ng-r2756+ar5007.tar.gz
    cd madwifi-ng-r2756+ar5007
    sudo make
    sudo make install
    blacklist the restricted driver by System>Administration>Restricted Drivers Manager
    sudo modprobe ath_pci (you may need to reboot you system if it gives you error)

5. Configure your wireless connection.  I use Wicd to do it (get it from synaptic).
    You may need to reboot the system after done.

That's all.  
Thanks to everybody who has spent time and given attention to this thread.

After succeeding with wireless, no my "Fn" key for controlling volume and brightness has no effect on them.  When I press it with F3 key to lower the volume, for example, it shows the volume meter moving down but has no effect on the volume.  This is not really a problem though, if somebody has a thought on it, it'd be much appeciated.

---

