---
title: "How to disable the on-board wi-fi in favor of wi-fi dongle?"
date: 2014-07-06
forum: Networking &amp; Wireless
---

### Post by smokingates on 2014-07-06
Is it possible to disable the wi-fi receiver/transmitter that came with my motherboard/network card (not sure which) on my "new" (6 months old) machine? The reason being is Ubuntu keeps switching me between the 2 and it's causing a lot of connection issues. Thanks in advance.

---

### Post by varunendra on 2014-07-06
There should be a setting in the BIOS setup to enable/disable the onboard wireless adapter.

Alternatively, you can block it from Ubuntu with -
```
rfkill block <wifi interface ID>
```
command.

---

### Post by smokingates on 2014-07-06
O.K so I had a look in the Bios but nothing for network adapter, even in devices >> advanced. how would I go about finding the "wifi interface ID" ? Thanks for the help so far :)

---

### Post by steeldriver on 2014-07-06
To find the interface ID, you can use rfkill with the list command

```

rfkill list

```

The number you need is something like

```

$ rfkill list
**[COLOR=#0000ff]1[/COLOR]**: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no

```

FYI a couple of other ways to disable a particular interface device are:

[LIST=1]
[*]add its MAC address (aka 'serial') to the list of unmanaged-devices in /etc/NetworkManager/NetworkManager.conf
[*](if it uses different drivers from the device you want to use) blacklist the internal device's driver
[/LIST]

---

### Post by Hadaka on 2014-07-06
Hi here is another way to get the info you need,,
please do..
```
cat /etc/udev/rules.d/70-persistent-net.rules
```
this is the out put of that command on my machine

```
hadaka@the-beach:~$ cat /etc/udev/rules.d/70-persistent-net.rule

# [COLOR=#ff0000]PCI[/COLOR] device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:00.0/ssb1:0 (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:22:33:44:55", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="[COLOR=#ff0000]eth0[/COLOR]"

# [COLOR=#ff0000]PCI[/COLOR] device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:03.0/ssb0:0 ([COLOR=#ff0000]b43[/COLOR]-pci-bridge) #[COLOR=#ff0000]wireless driver[/COLOR]
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:22:33:44:55", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="[COLOR=#ff0000]wlan0[/COLOR]"

# [COLOR=#ff0000]USB[/COLOR] device 0x148f:0x2573 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:22:33:44:55", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="[COLOR=#ff0000]wlan1[/COLOR]"

```

PCI - etho ethernet---intrnal card
PCI - wlan0 wireless -internal card  <-[COLOR=#ff0000]Turn off[/COLOR]...........     *Note my wireless is wlan 0 and 1 
USB -wlan1 wireless -external USB DONGLE...................          yours may be eth 1 and 2

Then useing steeldrivers suggestion...do..
*Example..your driver will be different
```
echo "b43" >> /etc/modprobe.d/blacklist-bcm43.conf
```
finally to find the driver for your internal wireless card  ,.,please do..
```
lspci -nnk | grep -iA2 Wireless
```

---

### Post by smokingates on 2014-07-07
Code:
rfkill list

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: phy3: Wireless LAN
    Soft blocked: no
    Hard blocked: no

cat /etc/udev/rules.d/70-persistent-net.rules
# PCI device 0x1969:0x1091 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="78:e3:b5:c7:8a:f1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="a4:db:30:87:6a:9b", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="44:94:fc:e2:e7:2c", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

/code

However when I use the "rfkill block phy0" command it seems to disable wireless entirely and I have to re-enable wireless from the signal strength drop down icon in the tray so I am a little wary about using "
echo "ath9k" >> /etc/modprobe.d/blacklist-phy0.conf"

Would there be a way to undo this if it somehow went wrong and disabled all wireless like the rfkill block command did?

Again, thank you for the help so far :) 
Also - how do I make code blocks like you guys are doing? Thanks in advance!

---

### Post by jeremy31 on 2014-07-07
Code tags are explained [http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)
try ```
rfkill block 0
```

---

### Post by coffeecat on 2014-07-07
@,smokingates, if you want an entirely GUI way of doing what you want, have a look at this post and the couple of posts following:

[http://ubuntuforums.org/showthread.php?t=1682546&p=10432612&viewfull=1#post10432612](http://ubuntuforums.org/showthread.php?t=1682546&p=10432612&viewfull=1#post10432612)

I've not tried it since that test with Ubuntu 10.10, but I see no reason why network manager should not oblige with the latest 14.04. A quick look tells me that Wireless tab is now called "Wi-Fi" but apart from that it should be the same.

**Edit**: if your machine has already connected with both devices, you will probably find that if you go to Edit Connections from the network manager menu, there will be two names under Wi-Fi, which will be the configurations for each device. Use the edit button to inspect both and simply untick the "automatically connect" box under the General Tab for the device you don't want to connect. The MAC for the device will be in the Wi-Fi tab and you can edit the connection name if you want to make it easier for yourself to see at a glance which connection configuration is for which device.

---

### Post by Hadaka on 2014-07-07
Hi, I apologize, I gave you an incorrect command
not to worry, it will do nothing and didnt change anything.
here is the correct command to blacklist ath9k driver.
please COPY and paste.
```
echo "blacklist ath9k" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

When you disabeled phy0 with the rfkill command, that would be like turning the power
off in your home from the breaker panel, not the light switch. The above command only
blacklists driver ath9k for wlan0 nothing else, its like correctly useing the light switch

thanks

---

### Post by varunendra on 2014-07-07
> **jeremy31 said:**
> try ```
rfkill block 0
```

+1

Both "rfkill block 0" and blacklisting 'ath9k' will do the job, without fail, without confusion.

To enable the internal wifi again, either use "rfkill unblock 0" command, or "sudo modprobe -v ath9k" command (if you blacklisted it) as applicable. Enabling an interface from the NM drop-down menu does the same thing as the "rfkill unblock" command.

- Methods to temporarily disable the internal wifi are :

1) Manually using the "rfkill block 0" command each time
2) Manually removing the driver each time with "sudo modprobe -rv ath9k" command.


- Methods to permanently disable the internal wifi are :

1) Adding the "rfkill block 0" command to '/etc/rc.local' file
2) Blacklisting the 'ath9k' module


- In case of permanently disabling the interface '0', it can be temporarily enabled (for only the running session) with -

1) "rfkill unblock 0" command, or,
2) "sudo modprobe -v ath9k" command.


What coffeecat explained (explicitly defining the MAC id of the interface you want to use) is also an alternative way to achieve what you want. The only possible problem I can think of *may be* that IF you forgot to plug in the USB adapter while turning Ubuntu off, and the internal wifi has not been disabled, Network Manager *may* automatically create a new connection to connect to the SSID you bound with the USB adapter's MAC ID. But I'm not sure about that, maybe it is as solid a workaround as the above ones.

---

### Post by coffeecat on 2014-07-07
> **varunendra said:**
> 
What coffeecat explained (explicitly defining the MAC id of the interface you want to use) is also an alternative way to achieve what you want. The only possible problem I can think of *may be* that IF you forgot to plug in the USB adapter while turning Ubuntu off, and the internal wifi has not been disabled, Network Manager *may* automatically create a new connection to connect to the SSID you bound with the USB adapter's MAC ID. But I'm not sure about that, maybe it is as solid a workaround as the above ones.

It's solid. Each NM connection is bound to a specific MAC. If the connection bound to the internal wifi has "automatically connect" unticked, then NM will just sit there connecting to nothing if the USB device is not plugged in. If, however, the user clicks on the SSID in the NM menu, then NM will connect using the configurations saved in the connection. Frankly, I think this is the easiest way to achieve what the OP wants.

---

### Post by varunendra on 2014-07-07
> **coffeecat said:**
> It's solid. Each NM connection is bound to a specific MAC. If the connection bound to the internal wifi has "automatically connect" unticked, then NM will just sit there connecting to nothing if the USB device is not plugged in. If, however, the user clicks on the SSID in the NM menu, then NM will connect using the configurations saved in the connection. Frankly, I think this is the easiest way to achieve what the OP wants.

Just woke up from sleep, so yeah, it's making more sense now.. :p

---

### Post by smokingates on 2014-07-07
Hmm well "rfkill block 0" appears to do the same as 
rfkill block <wifi interface ID>

... at least in terms of being able to see and connect to networks with my wi-fi dongle (and indeed at all), also I just realised that Ubuntu is seeing my dongle as "Realtek NETGEAR WNA3100M" in the NM drop down menu which it isn't... it's from a company called "on networks" and the model is "N300MA" according to the installation guide that came with it in the box.

Also I felt confident enough to try "sudo modprobe -rv ath9k" and it worked! my on board network list has vanished so will test with the permanent method mentioned then mark as solved if all is still good after a reboot.

Anyone in future reading this neads to be aware that "sudo modprobe -rv ath9k" is appropriate only for my machine where ath9k was found by using one of the previous commands in this thread.

A big thank you to all that made made the effort :D

---

