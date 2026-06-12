---
title: "Dynex Dx-wgnbc"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by TrueJk7 on 2006-11-18
Problem: My Dynex (Best Buy brand) card will not work on Ubuntu Edgy Eft 6.10.

**Situation #1: **
I plug in the card and the power LED blinks once every two seconds, The hardware is listed in the lshw but does not show up in netowrk-admin. (gui)

**Situation #2:**
- I use ndiswrapper 1.8 (from Edgy Eft CD, through Synaptic) and I get the hardware listed and bound to driver "ndiswrapper" listed by lshw. 
- I also am able to run the command "iwlist scan" and wlan0 shows up with all the right results. 
- I go to network-admin gui and it shows. When I go to configure it will (after checking the "enable this connection" checkbox), nothing shows up as "Network Name (ESSID)".

   Tried blacklisting bcm43xx (but relized afterwards that was not needed, but left black listed anyways)

- The leds will flash independently, then after a while of doing that, flash at the same time. (hope that helps) 

   -> Tried the "sudo depmod -a" and "sudo rmmod ndiswrapper" then "sudo modprobe ndiswrapper" No luck
   -> Tried commenting everything (except lo) out of /etc/network/interfaces
   -> Tried restart
   -> Tried uninstalling and reinstalling the ndiswrapper completely, no resolution

**Situation #3: **
- Tried installing the newest version of madwifi (since it's an atheros chipset. ...Really, nothing worked. It appeared in netowrk-admin gui with same problem, (no essid). Then I so tried to do a "iwlist scan" with no results this time. "iwconfig" pulled up 0's for all the parameters of the device. (worse than before) 

**Current State**
So right now I'm using situation #2 (ndiswrapper) because that seems to be the closest resolution.
*State of current situation:*
[LIST]
[*]ndiswrapper installed through the synaptic package manager (1.8)
[*]using the driver that came with the cd net5211.inf (ndiswrapper installed with no issue and it says (driver present, hardware present) 
[*]Next I did check /etc/ndiswrapper/net5211/ to find that the sys file landed there too
[*]I ran "ndiswrapper -m" and it said the alias already existed.
[*]Ran "sudo depmod -a"
[*]Ran "sudo modprobe ndiswrapper"
[*]Added ndiswrapper (plus the return at theend of it all) to the /etc/modules list.
[*]Tried to go to the netowrk-admin gui and found that it lists the device as "wlan0"
[*]Tried to configure but no ESSID was given
[*]I ran "iwlist scan" and "wlan0" came up with all the networks in range with all the information needed. 
[*]"iwconfig" shows the device with 0's accros the board for it's values (see below)
[*]Now.... I'm lost
[/LIST]

SO what I would need at this point would be some outside help. The thing wont work. I checked on the ndiswrapper list before I started this whole thing and this guy said he got it working out of the freaking box. All he used was ndiswrapper. So apparently that's not the case in my situation. So please help. below is information on the output of my commands and the tail of the dmesg log concerning the drivers. 

Thanks

**Commands and their output**
dmesg (tail) 
```
[17180161.108000] ath_pci: driver unloaded
[17180234.952000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17180234.988000] ndiswrapper: driver net5211 (Dynex,05/05/2005,4.1.2.56) loaded
[17180234.988000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [C0C3] -> GSI 11 (level, low) -> IRQ 11
[17180235.472000] ndiswrapper: using irq 11
[17180235.980000] wlan0: vendor: ''
[17180235.980000] wlan0: ethernet device 00:14:a5:ca:eb:ac using serialized NDIS driver net5211, 168C:001A:17F9:0008.5.conf
[17180235.980000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17180269.116000] ndiswrapper: device wlan0 removed
[17180269.144000] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[17180276.908000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17180276.916000] ndiswrapper: driver net5211 (Dynex,05/05/2005,4.1.2.56) loaded
[17180276.916000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [C0C3] -> GSI 11 (level, low) -> IRQ 11
[17180277.400000] ndiswrapper: using irq 11
[17180277.904000] wlan0: vendor: ''
[17180277.904000] wlan0: ethernet device 00:14:a5:ca:eb:ac using serialized NDIS driver net5211, 168C:001A:17F9:0008.5.conf
[17180277.904000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

```

iwconfig
```
wlan0     IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:50:18:3D:9C:DE   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0/100  Signal level:-93 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lshw
```
     *-network DISABLED
          description: Wireless interface
          product: AR5005G 802.11abg NIC
          vendor: Atheros Communications, Inc.
          physical id: 0
          bus info: pci@03:00.0
          logical name: wlan0
          version: 01
          serial: 00:14:a5:ca:eb:ac
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=ndiswrapper multicast=yes wireless=IEEE 802.11b
          resources: iomemory:26000000-2600ffff irq:11

```

*Please let me know if more information is required.*

---

### Post by TrueJk7 on 2006-11-19
I would first like to say:
"I am good." :D 

Things with Linux get a little easier when you realize how it all works. So the problems were

Ndiswrapper did not "wrap" the driver correctly before. and network-admin just did not want to work. So I then came to realize I do not need that to get this working. In linux the GUIs are lightly-dependent on the actual commands. 
[B]
UNINSTALL ndiswrapper / INSTALL compiler[/B]
So first of all I went
System > Administration > Synaptic Package Manager
And completely removed ndiswrapper-1.8-utils and ndiswrapper-common. And I made sure g++ and gcc were installed.

**INSTALL ndiswrapper**
Then I went to Ndiswrapper's main page and downloaded the package 
[http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

From there I used the default package manager to extract the files to a directory. 

then I went in the directory and followed the directions on the ndiswrapper wiki. 
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

Basicly, In order the commands I ran were
Install the Kernel headers
```
sudo apt-get install linux-headers-`uname -r`
```

Make a link to the headers (now the #s are going to very depending on what build you have. You can find out your #s by inputing *ls /usr/src/* and hitting enter
```
sudo ln -s /usr/src/linux-2.6.17-10-386 /lib/modules/2.6.17-10-386/build
```

Then I relocated to where I extracted the ndiswrapper package.

Then while in there I ran the commands
```
make distclean
```

then
```
sudo make
```

then 
```
sudo make install
```

So now the newest version of NDISWRAPPER is installed!

**Blacklisting the current Driver. **
In terminal I ran 
```
lshw
```
Then located my wifi card and found it was bound to driver "ath_pci" So I then ran 

```
sudo nano /etc/modprobe.d/blacklist
```
and added to the end of everything "blacklist ath_pci" hit enter, the CTRL+X and saved the file

Then here So I wouldn't have to restart (like freakin windows) I rand the command to remove the module(driver)
```
sudo rmmod ath_pci
```

Now use the ndiswrapper driver
```
sudo modprobe ndiswrapper
```

**Connecting via command line**

Then from here I noticed with the command "iwlist scan" I can now find access points! So then I went to System > Administration > Network and found I can not configure the wifi card... So I was in trobule but I realized that I could run the correct commands I can connect with out the gui interface. :D And this my friends is what makes Linux so amazing!!

From here I looked online for a while and found ([http://72.14.203.104/linux?q=cache:ilLv2lvx6O0J:www.logicallysecure.com/resources/downloads/Linux%2520Wireless%2520Commands.doc+iwconfig+manually+connecting&hl=en&gl=us&ct=clnk&cd=4](http://72.14.203.104/linux?q=cache:ilLv2lvx6O0J:www.logicallysecure.com/resources/downloads/Linux%2520Wireless%2520Commands.doc+iwconfig+manually+connecting&hl=en&gl=us&ct=clnk&cd=4)) this doc which tells a little more on running commmands to access a wifi router. (since the link includes the IP address it may not be available later. (you can find the *.doc version [http://www.logicallysecure.com/resources/downloads/Linux%20Wireless%20Commands.doc](http://www.logicallysecure.com/resources/downloads/Linux%20Wireless%20Commands.doc))

So the commands I ran were:

Turn off the ethernet card
```
sudo ifdown eth0
```

This may never need to be run, just for my router
```
sudo iwconfig wlan0 rate 11MB
```

Then connect! (#'s are going to be your WEP key, and MyESSID is going to be what you find from running the command "iwlist scan"
```
sudo iwconfig wlan0 mode managed key ##########

sudo iwconfig wlan0 essid MyESSID

sudo dhclient wlan0
```

BAM! In business! Now to check and see if it works you can ping something

Try 
```
ping www.bbc.co.uk
```

if you get any results... your good! 
(by the way, if it keeps going and you want it to stop just hit "CTRL+C" It's like ALT+F4 for windows, kills the current program. 

Well... Let me know if anyone needs any more help I copied those commands directly from terminal so there were going to be no mistakes. I'm going to enjoy computing from the couch instead of the kitchen now. 

PEACE:D :D :D 
Jake

---

