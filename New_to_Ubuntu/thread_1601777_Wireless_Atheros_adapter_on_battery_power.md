---
title: "Wireless Atheros adapter on battery power"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by A_P on 2010-10-20
Hey,

How can I make my wireless connexion work when I'm on battery? Each time when I login on my laptop when not plugged to the power source I can't connect to my router, it says wireless network disconnected, I can't see any access point. Even if I plug it after doesn't work without a restart. I thought is something related to the power saver protocol and tried to modify /usr/lib/pm-utils/power.d/laptop-mode, the laptop_mode_battery line  to do the same thing as laptop_mode_ac with no results. There is more to modify or something else to workaround?

It's a toshiba A210 laptop with atheros 5001 adapter and the OS is ubuntu 10.10.

---

### Post by Hippytaff on 2010-10-20
Does it work when your laptop is plugged it?

---

### Post by A_P on 2010-10-20
Yes it does without any problems. Have this issue only when I use the battery and login. If I login when it's plugged will connect, I can unplug it after that and will stay connected. But if I manually disconnect it or logout and login back will not connect any more unless I restart it and have it plugged.

---

### Post by P4man on 2010-10-20
Is the wireless connected via USB (could be internally)? If in doubt, check the output of

```
lsusb
```

If your wireless is in there, you could try adding

```
usbcore autosuspend=-1
```

to your kernel options, or put it in a file in /etc/modprobe.d/
You can do that per device too, save some battery, but Im not entirely sure how, so try this first and see if it actually helps.

---

### Post by A_P on 2010-10-20
no is in pci
```
lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc M76 [Radeon Mobility HD 2600 Series]
01:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
14:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
1a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
```

---

### Post by P4man on 2010-10-20
okay, this may sound trivial, but .. have you made sure wireless networking is actually enabled (when you booted on battery) ? Right click network manager and check if its enabled. Or is that option not even there?

Also, does the laptop have a hardware wifi button?

Last question: what happens when you turn it on while on power, and disconnect the powercord just when the bios post has finished and grub / ubuntu begins booting? If the problem doesnt persist then, then it looks like a bios issue. If you still have no wireless then, then its more likely an ubuntu setting.

---

### Post by A_P on 2010-10-20
Yes I have looked before and it is enabled, I even unchecked and checked back and nothing. It has a key slider to enable/disable wifi and i keep it on enable. Also I tried to disable it and enable it back from key, still nothing.

As I said it happens also when I logoff ( not restart ) and disconnect the powercord, when I login back it shows me that is looking to connect but right after it goes offline because it doesn't find any access point. So it doesn't seems to be a bios issue.

---

### Post by P4man on 2010-10-21
With the wifi not working, can you post the output of

```
rfkill list
```

and

```
iwconfig
```

---

### Post by A_P on 2010-10-21
The commands were given after a startup on battery ( no wifi connexion )

```
rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
``````
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:eek:ff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:ff
          
vmnet1    no wireless extensions.

vmnet8    no wireless extensions.
```

---

### Post by P4man on 2010-10-21
Thats odd.. that all looks fine?  What does

```
iwlist scanning
```

produce?

---

### Post by A_P on 2010-10-21
This

```
iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

vmnet1    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.
```

---

### Post by P4man on 2010-10-21
can you try again with sudo?

```
sudo iwlist scanning
```

Thought it wasnt needed but I was doing it in root prompt.

---

### Post by A_P on 2010-10-21
It gave me exactly the same thing, but seems that it takes a bit more time to show the results for wlan0

---

### Post by P4man on 2010-10-21
It should take a second or so.. as its scanning all channels. 

Okay, a wild guess.

```
gksudo gedit  /etc/modprobe.d/blacklist-ath_pci.conf 
```

Add this line:
```
blacklist acer-wmi
```

Reboot. Cross fingers. If it doesnt help, Id remove it again

---

### Post by A_P on 2010-10-21
Still doesn't work but something has changed. Now at least is trying to connect, it asks me for my password 3 times in a raw, but I already have it memorised, fails to connect and notifies me Wireless disconnected-you are offline something like that.

Now sudo iwconfig scanning for wlan0 says - wlan0     Interface doesn't support scanning : Device or resource busy - but the gnome network icon from panel doesn't show is busy with anything.
With iwconfig scanning has the same result as before, but now I can see my access point under the same gnome network icon from panel.

Also there was something else blacklisted in that file
```
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci
```should I remove it? let only the line I add it? or both?

---

### Post by P4man on 2010-10-21
You should add it, blacklist both.


> Also there was something else blacklisted in that file
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci
blacklist acer-wmi


 Then after a reboot, check in jockey (system > administrion > hardware drivers) if it offers another driver or not, or if its using one already.

---

### Post by A_P on 2010-10-21
Under Administration have Additional Drivers and there is only a driver for graphic card.

---

### Post by P4man on 2010-10-21
OKay. But blacklisting acer-wmi did result in network manager actually finding the card and AP, but now you have trouble connecting to it, correct? I assume this problem also happens when you boot with the powercable connected?

---

### Post by A_P on 2010-10-21
No, I added the line you said and saved the file, shut it down, unpluged, opened and happened what I described above, shut it down, plugged and opened again. On login connexion is working and still have both blacklisted lines in that file.

---

### Post by P4man on 2010-10-21
Its almost like its using a different driver. Actually, maybe it is. 
Lets check that. Can you post the output of 

```
sudo lshw -C network
```

For both cases where it works and doesnt work?

---

### Post by A_P on 2010-10-21
Now its acting as before... is not trying to connect to anything, guess after it's first failed try its saving the settings or something.

This is what I get:

Connexion working
```
sudo lshw -C network
[sudo]
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:04:1b:da
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:44 ioport:a000(size=256) memory:cf8ff000-cf8fffff memory:84400000-8441ffff
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:9e:b0:f5:46
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic firmware=N/A ip=192.168.2.100 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:cfcf0000-cfcfffff
```

Connexion not working when on battery
```
sudo lshw -C network
[sudo]
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:04:1b:da
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=no multicast=yes port=MII speed=100MB/s
       resources: irq:44 ioport:a000(size=256) memory:cf8ff000-cf8fffff memory:84400000-8441ffff
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:9e:b0:f5:46
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:cfcf0000-cfcfffff
```

---

### Post by P4man on 2010-10-21
Same driver. Im almost out of ideas. You could try WiCD instead of networkmanager, but I doubt it will change anything. And you could  try ndiswrapper as a workaround, but I would report this on launchpad. I have no idea whats different in either boot.

---

### Post by Hippytaff on 2010-10-21
A shot in the dark, but might it be something to do with not enough (or no) power being assigned to the usb when on battery? might it have something to do with autosuspend?
 
try editing /etc/laptop-mode/conf.d/usb-autosuspend.conf
 
with 
 
```

CONTROL_USB_AUTOSUSPEND=0

```
 
but you might want to read the man page first
 
```

man laptop-mode.conf

```

---

### Post by P4man on 2010-10-21
AFterhought.. compare the output of dmesg of a battery and a wired boot, and see if anything relevant is different?

---

### Post by A_P on 2010-10-21
Well I tried ndiswrapper just before you post it and installed a xp driver for it. It seems I messed up because it doesn't see it at all anymore. rfkill list shows only bluetooth. I'm running the live cd now to post this. Have already removed ndiswrapper together with xp driver and it still can see it.

how can I manually add it?

---

### Post by P4man on 2010-10-21
TBH, what do you think of a 6.25 pound solution like this:

[http://cgi.ebay.co.uk/Intel-4965-4965AGN-wireless-WiFi-PCI-E-card-802-11N-AGN-/190458642563?pt=LH_DefaultDomain_0&hash=item2c58384083](http://cgi.ebay.co.uk/Intel-4965-4965AGN-wireless-WiFi-PCI-E-card-802-11N-AGN-/190458642563?pt=LH_DefaultDomain_0&hash=item2c58384083)

Added bonus you get 802.11 N speeds if you have a router that supports it.

---

### Post by P4man on 2010-10-24
The same issue has been reported here:
[http://ubuntuforums.org/showthread.php?t=1603232](http://ubuntuforums.org/showthread.php?t=1603232)

Thing is, that is with a very different network card, so it looks like its not a wifi driver issue (and I retract my recommendation of buying another one, as possibly it wont fix anything). It looks perhaps like a PCI-E powersaving issue.

Im also continuing to look in to the issue in that thread, perhaps you can subscribe to it and also post your results there?

---

