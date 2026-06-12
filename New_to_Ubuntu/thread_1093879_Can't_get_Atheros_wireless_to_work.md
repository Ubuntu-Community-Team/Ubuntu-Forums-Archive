---
title: "Can't get Atheros wireless to work"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by ewitty on 2009-03-12
Please help! I have been trying for 3 days to get wireless working with Ubuntu (it works fine in Windows).

lshw -C network shows:

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:23:54:59:29:4a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.2.123 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ee:88:f0:11:70:1e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

iwconfig shows:

```

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

At one point iwconfig showed a wlan0 that was set to DISABLED (I think), but I've been messing around so much trying to find solutions on the web that now it's gone and I don't know how to make it come back. Wired internet works fine, as does pretty much everything else.

Any help very appreciated. Gonna have to go back to Vista (sigh) if I can't get this working.

---

### Post by martrn on 2009-03-12
Read the community documents first.  [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros")

Ensure you have the the linux-back-ports repository installed.  Either sudo gedit etc/apt/sources.lst  and check your back-ports repository is uncheked (eg no ## signs before the backports repository), or do this via the gnome menu.

then open a terminal and type :
```
 sudo apt-get install ath5k 
```
(eg install the ath5k module), located in the package linux-backports-modules-intrepid. Make sure it is activated on System/Administration/Hardware Drivers.

Then work through the steps 1..3 and 1..3 again from the [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros") page if that fails.

Remember if you go back to another operating system, you can always come back here and download a new copy of ubuntu or ask here from the wonderful vibrant members of the ubuntu community, if you need to install again, where you will find lots of very helpful friendly advice.  (Where can you get that in the windoze world).

---

### Post by ewitty on 2009-03-12
Thank you very much for the reply. I'm sure I installed the backports, but when I go to System/Administration/Hardware Drivers it is empty and says "no proprietary drivers were found."

also, sudo gedit etc/apt/sources.lst creates a blank text file, and I'm not sure how to use the gnome menu. How do I make sure backports are enabled?

---

### Post by martrn on 2009-03-12
> **ewitty said:**
> Thank you very much for the reply. I'm sure I installed the backports, but when I go to System/Administration/Hardware Drivers it is empty and says "no proprietary drivers were found."also, sudo gedit etc/apt/sources.lst creates a blank text file, and I'm not sure how to use the gnome menu. How do I make sure backports are enabled?

Goto System--->Administration--->Software_Sources

Goto the updates tab
and check the boxe(s)
Unsupported Updates (Intrepid Backports),

And that will ensure the back-ports repository is enabled.

It's probably 
```
sudo gedit /etc/apt/sources.list
``` for intrepid.

{ [ADDED] }
ensure you  '**sudo apt-get update && sudo apt-get upgrade**'  before the next bit.
------- { end [ADDED] }

Then open a terminal and type :

 ```
sudo apt-get install ath5k
```

(eg. to install the ath5k module), located in the package linux-backports-modules-intrepid. Make sure it is activated on System-->Administration-->Hardware_Drivers.

Then work through the steps 1..3 and 1..3 again from the [https://help.ubuntu.com/..../Atheros]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros") page if that fails.

---

### Post by bumanie on 2009-03-12
Follow [this guide]("http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html") from ubuntu geek. I used method 2 (I think).

---

### Post by ewitty on 2009-03-12
I followed the instructions, but Hardware Drivers is still empty. The list file works, but it only confirms backports are enabled (no # beside the backport lines)

'sudo apt-get install ath5k' shows:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ath5k

```

Any idea why?

---

### Post by martrn on 2009-03-12
> **ewitty said:**
> .....
E: Couldn't find package ath5k
[.....]
Any idea why?

Searching [http://packages.ubuntu.com/search?suite=all&arch=i386&searchon=all&keywords=atheros]("http://packages.ubuntu.com/search?suite=all&arch=i386&searchon=all&keywords=atheros") is giving me : madwifi-tools so
```
sudo apt-get install madwifi-tools
```
is I guess the equivalent.

I don't know the package name or why / if they changed it from as its listed in the community documents ?

You can search the packages ([URL="http://packages.ubuntu.com/"]
http://packages.ubuntu.com/[/URL]) until you find the package you need.

---

### Post by martrn on 2009-03-12
If you go upto the above guide, by bumanie and

```
sudo apt-get install linux-backports-modules-intrepid
```

Then goto  System-->Administration-->Hardware_Drivers make sure Atheros driver is activated.

Then that should do the same thing.
You might need to  blacklist the old modules, and reboot your system.

Failing that you need to manually install the drivers.
See:
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros")
Don't let the change in name of a package put you off following this through.

---

### Post by Ratscallion on 2009-03-12
Hi there. I also have an Atheros Wireless Card which was bundled with my HP laptop. I managed to get around this problem by doing the following:

If you have a computer with Internet access, on either a different partition on the same computer, or a different computer altogether:
Go to [The ubuntu package search (click)]("http://packages.ubuntu.com") and search for ndiswrapper. Download all of the available packages (there should be four available).
Copy/access these debian based packages on the ubuntu partition of the PC, and install them. Google around for the XP Driver for your specific Atheros card, which should come in a zip file. 
Extract the zip file, and either browse or drag and drop the .inf file into ndiswrapper which SHOULD if you installed it correctly, be in 
System->Administration->Windows Wireless Drivers.
Then, disable the HardWare support for the Atheros Card in System->Administration->Hardware Drivers.
Reboot your system, check ndiswrapper still has the driver installed, and that your Atheros card is no longer active in Hardware Drivers. If all this is good, click on the network icon in the system tray, and you SHOULD be able to see available networks.
If the system tray doesn't work, try 
```
sudo iwlist wlan0 scan
``` with wlan0 being your wireless card, which it usually is.
Hope this helps, ask questions if needed.

---

### Post by ewitty on 2009-03-12
This is really difficult. I followed the instructions in every post here, and still nothing.

When I type sudo apt-get install linux-backports-modules-intrepid, I get:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-backports-modules-intrepid is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

That makes me think it's already installed. But when I go to Hardware Drivers, it's empty. 

Anything I should try next? Why on earth is this so difficult?

---

### Post by nothingspecial on 2009-03-12
Different computer I know but try the instructions [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/AspireOne")

I`m not sure if it`ll work with your particular card because it`s different but it always works with my atheros card.

Oh and if you have edited /etc/modules before put a # infront of ath5k.

And disable anything in system>administration>hardwaredrivers.

Like I said, I have no idea if this will work for your card ........ at your own risk:D

---

### Post by ewitty on 2009-03-12
> **nothingspecial said:**
> Different computer I know but try the instructions [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/AspireOne")

I`m not sure if it`ll work with your particular card because it`s different but it always works with my atheros card.

Oh and if you have edited /etc/modules before put a # infront of ath5k.

And disable anything in system>administration>hardwaredrivers.

Like I said, I have no idea if this will work for your card ........ at your own risk:D

Thanks for the reply, but it didn't work. I think I will give up and go back to Windows. I really want to like ubuntu, but this is ridiculous. It should not take 4 days to get a wireless card running.

---

### Post by fly-by-night on 2009-03-12
Just another something.  After every change/bit of advice you try out, remember to Disable Networking and re-enable it afterwards. 
Assuming you have a network icon in the taskbar right click it and Disable/Enable it.

Please note I have not read much of the replies above - just a bit of advice from me.
Also with wireless I had to configure my DNS servers manually. Reached my router but not the internet.

---

### Post by stchman on 2009-03-12
> **martrn said:**
> Read the community documents first.  [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros")

Ensure you have the the linux-back-ports repository installed.  Either sudo gedit etc/apt/sources.lst  and check your back-ports repository is uncheked (eg no ## signs before the backports repository), or do this via the gnome menu.

then open a terminal and type :
```
 sudo apt-get install ath5k 
```
(eg install the ath5k module), located in the package linux-backports-modules-intrepid. Make sure it is activated on System/Administration/Hardware Drivers.

Then work through the steps 1..3 and 1..3 again from the [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros") page if that fails.

Remember if you go back to another operating system, you can always come back here and download a new copy of ubuntu or ask here from the wonderful vibrant members of the ubuntu community, if you need to install again, where you will find lots of very helpful friendly advice.  (Where can you get that in the windoze world).

There is no ath5k package in the repositories.

---

### Post by stchman on 2009-03-12
What kind of wireless card do you have?

Please post an lspci and lsusb here in this thread.

If it is indeed an Atheros card I have a script to install the madwifi drivers.

[http://www.stchman.com/aspire_one_intrepid.html](http://www.stchman.com/aspire_one_intrepid.html)

Comment out the stuff on wireless LEDs as those are an Aspire One thing.

---

### Post by ewitty on 2009-03-12
iwconfig shows:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

This is after I used fdisk and reinstalled ubuntu. I can not find any wireless access points however, and y Hardware Drivers is ALWAYS empty.

Interestingly, if I boot ubuntu from the CD, wireless is recognized and I can get online. This is SO frustrating.

---

### Post by ewitty on 2009-03-12
lspci:

```

03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```

lsusb:

```

Bus 008 Device 002: ID 1d74:0003  
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0b05:1751 ASUSTek Computer, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Please let me know what to try next. Thanks!

---

### Post by joshua.solidum on 2009-03-12
will madwifi driver works?I have installed ubuntu hardy heron in a compaq
c700 laptop using VMware enabling ubuntu to run inside windows vista
yet the only way for the ubuntu to work is via roaming NAT connection!?
wifi still doesnt work,adapter is atheros a b g adapter..also I have problems connecting usb adapters and memory card to be recognized in ubuntu..

---

### Post by martrn on 2009-03-12
> **ewitty said:**
> iwconfig shows:

```

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

This is after I used fdisk and reinstalled ubuntu. I can not find any wireless access points however, and y Hardware Drivers is ALWAYS empty.

Interestingly, if I boot ubuntu from the CD, wireless is recognized and I can get online. This is SO frustrating.

That shows it is working.
Your ESSID (your network name) is BLANK.

Your card is working you need to play around with configuring the card to work with your desktop (gnome).  The drivers (kernel modules) are now installed.

```
sudo iwconfig wlan0 ESSID MYCOMPUTER
iwlist wlan0 scan
```

---

### Post by ewitty on 2009-03-12
> **martrn said:**
> That shows it is working.
Your ESSID (your network name) is BLANK.

Your card is working you need to play around with configuring the card to work with your desktop (gnome).  The drivers (kernel modules) are now installed.

```
sudo iwconfig wlan0 ESSID MYCOMPUTER
iwlist wlan0 scan
```

I'm not sure how to configure the card. How do I start gnome?

Nothing happens when I enter the code above. I get a response:

```

wlan0     No scan results

```

Thanks again!

---

### Post by martrn on 2009-03-12
To start gnome :

```
sudo /etc/init.d/gdm start
//  -- or --
startx
```

See :  [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo")

you need to (run) '**sudo network-admin**' (from a terminal) or select System-->Administration-->Networking Here you should type the ESSID that you have assigned to your router into the box that says "Network Name (ESSID), and you should set up the WEP (encryption) as mentioned in your router manual of leave it blank if you have not set up WEP (encrytion) for your wireless connection.

Also check the above URL for connection via the terminal if you wish to do that.

---

### Post by Ratscallion on 2009-03-14
> **ewitty said:**
> I'm not sure how to configure the card. How do I start gnome?

Nothing happens when I enter the code above. I get a response:

```

wlan0     No scan results

```Thanks again!
You don't need to start GNOME, it automatically starts when you load your Graphical Desktop, as that is Default in Ubuntu.
Try checking your HardWare Drivers (check previous post) and, if and only if, there is support for your card, disable it. Reboot, then right click on the Networking icon in the system tray, and Check the item "Enable Wireless". After it's checked, try doing the following in a Terminal (Applications -> Accessories -> Terminal).
```
 sudo iwlist wlan0 scan
```
This assumes that wlan0 is the name of your wireless network thingy, change it appropriately, post the new results here.

---

