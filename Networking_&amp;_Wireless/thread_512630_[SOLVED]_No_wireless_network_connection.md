---
title: "[SOLVED] No wireless network connection"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by fizikz on 2007-07-29
I'm having trouble getting my laptop's wireless to work under Ubuntu 6.06. My wireless device is Intel's 3945ABG, and as far as I can tell, the drivers were automatically installed when I installed Ubuntu. I also have wpasupplicant installed, as I use WPA. I've managed to install the Network Manager (gnome), but it just says "no network connection". If I comment out all the lines in /etc/network/interfaces except for 'lo' entries, network manager allows me to attempt connection to a network, or to try to create a new network, but even after I enter the SSID, encryption type, and password information, it just fails to connect after a long attempt. I've also tried installing ndiswrapper from the package manager out of desperation, but still nothing. 

I'm running out of ideas to try; help would be appreciated.

---

### Post by noob12 on 2007-07-29
It sounds like you got very close before you installed ndiswrapper.

DId you actually switch over to ndiswrapper with a windows driver or are you still on the linux ipw3945 driver?

The following things would help diagnosis.  Can you post the output of

```
lshw -C network
```

and

```
iwlist scan
```

If you control the access point, and your area is relatively safe, can you try first connecting with security disabled?  This will help separate various potential issues.

---

### Post by fizikz on 2007-07-29
I installed ndiswrapper from the package manager, but I didn't install the windows drivers. I suppose I could uninstall the ndiswrapper, as I think I should be able to get things working without it. The ipw3945 drivers are still there.

I tried the commands you suggested.

lshw -C network gives:
```
 *-network
       description: Ethernet interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 01
       serial: xx:xx:xx:xx:xx
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r1000 ip=192.168.2.10 multicast=yes
       resources: ioport:c800-c8ff iomemory:fe0ff000-fe0fffff irq:169
  *-network
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 02
       serial: xx:xx:xx:xx:xx:xx
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.0.5m firmware=13.0 1:0 () link=no multicast=yes wireless=unassociated
       resources: iomemory:fe1ff000-fe1fffff irq:185
  *-usb
       description: Bluetooth wireless interface
       vendor: ASUSTek Computer, Inc.
       physical id: 1
       bus info: usb@3:1
       version: 19.15
       serial: 0194E8-5B-0002
       capabilities: bluetooth usb-2.00
       configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s

```

iwlist scan gives:
```
lo        Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: xx:xx:xx:xx:xx:xx
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54
                    Quality=40/100  Signal level=-85 dBm  Noise level=-85 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 5512ms ago


```

I suppose I could try disabling the router's security temporarily and then try to connect, but I don't know if that should be necessary. The wireless works fine in Windows XP and also in OpenSuse 10.2 (using knetworkmanager).

---

### Post by noob12 on 2007-07-29
OK.  You are still using the ipw3945 driver according to the lshw.

The scan shows that the signal is a bit weak but you are getting to the access point and that it is set up to use WPA (version 1) and PSK authentication.

You say you are running NetworkManager, and you have commented out the lines pertaining to eth1 in /etc/network/interfaces (or equivalently set it to roaming in the network manager interface).

Left-clicking on the NetworkManager (nm-applet) icon in the panel should show you the SSID of the network.  You select it and then can you describe exactly what happens at that point?

Also:  do you have wpasupplicant installed?  and are you running the gnome keyring manager?

---

### Post by fizikz on 2007-07-29
It's strange that the signal was reported weak like that. I tried it again several times and got 94% signal strength. I'm right beside the router right now. Anyhow, I suppose that can happen. 

Initially, the Network Manager doesn't see my network's name, and I suppose that's because my router is setup not to broadcast its SSID. Anyways, I left click on the NM icon and select 'connect to other wireless network.' I enter the SSID, encryption type (WPA personal), and the key. The icon does its 'swirling' thing and then asks me for the key again. To my knowledge, I don't have 'keyring' setup, and I guess that's why it may be asking me again for my key. I assume 'keyring' is a password manager like 'wallet' in kde. Well, after waiting for a few minutes, the NM icon returns to its orange exlamation point. Resting my cursor over it reveals 'no network connection. If I left click on the icon, I see my SSID name, with an unckecked radio button, a shield icon, and a signal strenght indicator that looks empty. If I click on my SSID, nothing happens.

EDIT: I just checked Synaptic Package Manager, and I have keyring manager installed. I just haven't dealt with it consciously or explicitly. Also, under Network Settings, the wireless icon says, 'not configured'. I'm guessing that's due to NM, since NM supports WPA whereas that Network Settings menu only has a WEP option. I've left things as is for the moment. Any suggestions are welcome.

---

### Post by noob12 on 2007-07-29
Have you got wpasupplicant installed?

```
aptitude show wpasupplicant
```

I'd recommend installing **gnome-keyring** eventually because this will simplify reauthentication each time and maintaining multiple keys if you use different nets at all.

---

### Post by fizikz on 2007-07-29
Yes, I do have wpasupplicant installed. 

```
Package: wpasupplicant
State: installed
Automatically installed: no
Version: 0.4.8-3ubuntu1.1
Priority: important
Section: net
Maintainer: Debian/Ubuntu wpasupplicant Maintainers <pkg-wpa-devel@lists.alioth.debian.org>
Uncompressed Size: 545k
Depends: libc6 (>= 2.3.4-1), libncurses5 (>= 5.4-5), libreadline5 (>= 5.1),
         libssl0.9.8 (>= 0.9.8a-1)
Suggests: libengine-pkcs11-openssl
Description: Client support for WPA and WPA2 (IEEE 802.11i)
 WPA and WPA2 are methods for securing wireless networks, the former using IEEE
 802.1X, and the latter using IEEE 802.11i. This software provides key
 negotiation with the WPA Authenticator, and controls association with IEEE
 802.11i networks.


```


As for gnome-keyring, I looked it up again in the Synaptic Package Manager and it turns out I had gnome-keyring installed, but not gnome-keyring manager. Now both are installed.

Still, whether the password is remembered or not, right now I'm not able to connect wirelessly at all. Any more suggestions?

EDIT: Ok, now I tried clicking on NM and choosing 'create a new wireless network'. After entering all the info, I get my SSID showing up with a selected radio button and a signal strength bar indicating a good connection. However, the NM icon still has the orange exclamation point. I tried repeating this procedure a few times and I get varied results; sometimes the signal strength indicator is empty, and other times my network simply isn't listed, even after I just entered all the info. This is getting really frustrating...

---

### Post by noob12 on 2007-07-29
On the chance that there is some issue with not receiving ESSID, can you enable the broadcast on your router for a bit and see if this improves things?  I haven't tried this specific combination before with the 3945-based wireless that I've used.

---

### Post by noob12 on 2007-07-29
One other thing, on the dialog where you enter the network key, make sure you are selecting **WPA Personal** and explicitly select **TKIP** rather than Automatic (Default) in the other pull-down.

---

### Post by fizikz on 2007-07-30
IT WORKED!!! Broadcasting the SSID from the router allowed the NM to identify and connect to the network without any problems. Actually, it is working fine even though I left the security option at Automatic (Default).

Thanks you so much for the help. I'm so very happy to finally have wireless with Ubuntu. Now I can move on to configuring everything else.

---

### Post by noob12 on 2007-07-30
Great.  Glad you got it working.  With the ESSID broadcast on, it should be able to figure everything out automatically.  

With the broadcast off, my understanding is that as long as iwlist scan still finds your AP, theoretically the manager should still be able to associate to the AP through the "Connect to Other Network ..." option, as long as you select all the details correctly.

On the Intel 2200-based laptop I have with me right now, I was able to do everything with the ESSID broadcast off using the "... Other Network ..." option even after removing all of my state information.  You might have been seeing a driver-specific issue or something else like your AP's beacon interval or the transmit power; I noticed on your iwlist scan a while ago that the last beacon had been received over 5 seconds ago at the time of the scan; that's very long.  A typical beacon transmission interval is 100ms.

Maybe once you've got everything else setup, you will feel rested and brave enough to experiment with switching the broadcast back off and seeing if you can still associate without changing any settings after a power down and reboot.  But trying this might lead to another fun(!) day of wireless diagnostics.

---

