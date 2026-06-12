---
title: "USB Wi-Fi"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by skylerdray on 2008-05-19
Sorry if it has already been asked, but i am completly new to linux and i cant get my USB Belkin Wi-Fi wireless reciver to work in linux. It works fine in my Mirco$oft XP side, and my OSX86 side But not on my linux side. Any ideas?

---

### Post by chili555 on 2008-05-19
> **skylerdray said:**
> Sorry if it has already been asked, but i am completly new to linux and i cant get my USB Belkin Wi-Fi wireless reciver to work in linux. It works fine in my Mirco$oft XP side, and my OSX86 side But not on my linux side. Any ideas?It's been asked ten times a day!

In order to help, we need to know what kind of Belkin USB you have. This terminal command:```
sudo lshw -C network
sudo lsusb
```will help us find out what chipset your device uses. Then you can search for the chipset here and find dozens of people who have got it working successfully. Don't be shy to post back if you get stuck and please give us the URL of the tutorial you were following.

---

### Post by skylerdray on 2008-05-19
```
Bus 004 Device 002: ID 050d:705a Belkin Components 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 03f0:040c Hewlett-Packard 
Bus 003 Device 003: ID 0d7d:0240 Phison Electronics Corp. I/O-Magic/Transcend 6-in-1 Card Reader
Bus 003 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```
That's what it gave me.

---

### Post by james_vanb on 2008-05-19
Using Belkin Wireless g Network Adapter with the rt73 Driver. Have posted this solution in a couple of threads. Give it a shot - It worked for me.

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands (If not using Xubuntu, substitute commands as appropriate):

```
sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb
```

I'm not sure that this actually removes the drivers, but after 3 weeks of farting around with them it made me feel better.

Blacklist rt2500usb and rt73usb by opening text editor (mousepad for Xubuntu - gedit for Ubuntu) as follows:

```
sudo mousepad /etc/modprobe.d/blacklist
```

add rt2500usb and rt73usb to end of list, save and close.

REBOOT

This is where the guides I was following failed. Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin".
Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following :

```
sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf
```

Insert the wireless adapter.

Now issue the following commands:

```
sudo depmod -a
sudo modprobe ndiswrapper
```

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows:

```
sudo mousepad /etc/modules
```

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

```
sudo ndiswrapper -m
```

Reboot

You should now have a connection. Roaming mode works sporadically, so I manually configure. Left click on the network manager at the upper right corner and enter manual configuration. Open wifi properties. Untick "enable roaming". Next to Network name, you should be able to click on the arrow and a drop down will show available networks, click on yours. Set Password type to WPA personal. Set Configuration to Automatic configuration (DHCP). I don't use WEP yet, but if you do, you may have to enter your password in Network password.

Good Luck!!

---

### Post by chili555 on 2008-05-19
More! We need more! What did lshw tell you? Also check here: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/34902/comments/162](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/34902/comments/162) especially this: > Bus 004 Device 003: ID 050d:705a Belkin Components still not working....
This is a tough card, there are four known versions of this card.
802.11g F5D7050 v.1xxxx Prism54
802.11g F5D7050 v.2xxxx rt2x00
802.11g F5D7050 v.3xxxx man: 050d dev: 705a rt2x00
802.11g F5D7050 v. 4001 ?
 ?
802.11g F5D7050 v.4xxxx man: 050d dev: 705c ZD1211So try the lshw command as outlined above and look all over the card and tell us everything you can about its version.

---

