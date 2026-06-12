---
title: "Wireless network"
date: 2015-06-07
forum: Networking &amp; Wireless
---

### Post by hmiersch on 2015-06-07
Hi.
today I tried to get wifi going on my MacBook pro. Trouble is, I can't get it to work. 
I clicked on the network icon in the menu bar, then selected edit connections.
in he window I clicked add, then I selected wifi, and then create, and that's when the problems started.
SSID: this is where I enter the name of my network, right?
mode: set to infrastructure
BSSID: what am I supposed to enter here, and where do I find that info?
device mac address: which mac address goes here? The computer's or the router's?
cloned mac address: ???
MTU: set to automatic.

Problem: I can't get it to work. Can't connect to the wifi network, and this connection doesn't appear under the network icon in the menu bar. When I unplug the Ethernet cable, the network icon changes from 2 arrows pointing in opposite directions to a quarter-circle, and a box pops up telling me I'm disconnected.

what am I doing wrong?
also, if I want to use some other wifi, like at Starbucks, do I have to make a new configuration for every Starbucks I go to?

Ubuntu 14.04 on a MacBook pro

---

### Post by tristan16 on 2015-06-07
Click the network icon, and make sure the "Enable Wi-Fi" option is checked. Your computer should then pop up Wi-Fi networks in range. Click the one you want to connect to. If it needs a password, you will be asked to enter it. If all goes well, you should see the Wi-Fi icon stop blinking, and a notification telling you that the network is connected.

This is the automatic process. When you create a connection through "Edit Connections," you are manually creating a network. Here's what you should do:
SSID: Wi-Fi Network Name
Mode: Infrastructure
BSSID: You can leave this blank; this option isn't used for normal connections
Device MAC Address: Click the arrow next to this field and select your Wi-Fi adapter. It should be labeled as wlan0.
Cloned MAC Address: Again, you can leave this blank.
MTU: This can be left at Automatic. 

Enter your password information in the Wi-Fi Security tab, and save the connection.

---

### Post by hmiersch on 2015-06-07
You mean the network icon in the menu bar, in the top right corner of he screen? There is no "enable wifi" option. That menu shows the following lines:

Ethernet network (greyed out)
Ethernet
disconnect
vpn connections (which leads to a submenu)
Enable networking (checked)
Connection information
edit connection.

no enable wifi option.

And system settings doesn't help me either. The wifi connection doesn't appear there either, and when I click the plus button, the only interface it offers me is "VPN". If I click the options button in the lower right corner, it lets me edit the settings for my Ethernet connection which I don't wanna do because that connection works. It's just he wifi that I can't get to work.

Do you mean that when I click the arrow for device mac address, it should show me the mac address of my wifi hardware? It does not do that.

That, combined with the fact that there is no enable wifi option, tells me that something is wrong with my system. Do I need some kind of driver?

---

### Post by Bucky Ball on 2015-06-07
It sounds like you are trying to set up a static IP. If you're not, there should be no need to tweak with Network Manager. 

Please open a terminal and post the output of this command:

```
sudo lshw -C network
```

Please use [code] tags (see the last link in my signature).
___

*Thread moved to **Networking & Wireless**.*

***New to Ubuntu*** is for support requests for those new to Ubuntu, as the name suggests. You improve your chances by posting in an area related to your support issue. ;)

---

### Post by hmiersch on 2015-06-08
I ran that command yesterday. I'll post the output when I get a chance...

---

### Post by hmiersch on 2015-06-08
ok, here's the output from that command```


  *-network               
       description: Ethernet interface
       product: NetXtreme BCM57765 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: a8:20:66:3f:d9:ac
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 duplex=full firmware=57765-v1.37 ip=192.168.2.4 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:c1800000-c180ffff memory:c1810000-c181ffff
  *-network
       description: Network controller
       product: BCM4331 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:c1a00000-c1a03fff


```

---

### Post by tristan16 on 2015-06-08
> **hmiersch said:**
> ok, here's the output from that command```


  *-network               
       description: Ethernet interface
       product: NetXtreme BCM57765 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: a8:20:66:3f:d9:ac
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 duplex=full firmware=57765-v1.37 ip=192.168.2.4 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:c1800000-c180ffff memory:c1810000-c181ffff
  *-network
       description: Network controller
       product: BCM4331 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:c1a00000-c1a03fff


```

I found something from this discussion that might help: [http://askubuntu.com/questions/470153/no-wireless-when-install-14-04-on-macbook-pro](http://askubuntu.com/questions/470153/no-wireless-when-install-14-04-on-macbook-pro)

Specifically:
```

sudo apt-get update
sudo apt-get install linux-firmware-nonfree
```
[FONT=arial]

Just out of curiosity, do you know whether your Mac is a PowerPC or not? I remember reading something about PowerPCs needing a special version of Ubuntu, but I'm not in-the-loop for Macs, so I don't know if it's relevant here. [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)[/FONT][FONT=arial][/FONT]

---

### Post by chili555 on 2015-06-08
linux-firmware-nonfree is no longer correct. I suggest you consult the Broadcom sticky for instructions: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by hmiersch on 2015-06-08
Unfortunately that apt-get install stuff is not an option at the moment because my DSL is down, and at Starbucks I'd need the wifi which doesn't work. 

My mac has an i7 CPU.

---

### Post by chili555 on 2015-06-08
> **hmiersch said:**
> Unfortunately that apt-get install stuff is not an option at the moment because my DSL is down, and at Starbucks I'd need the wifi which doesn't work. 

My mac has an i7 CPU.After you confirmed your exact details from the sticky, what does it say you need?  We can probably work out a method if we knew.

---

### Post by hmiersch on 2015-06-08
That table tells me I need firmware-b43-installer.

---

### Post by Bucky Ball on 2015-06-08
Then with the cable plugged in, open the Software Centre, Synaptic or a terminal, search for and install it, else in a terminal type:

```
sudo apt-get install firmware-b43-installer
```

You may need to reboot after this, with the cable out, to get wireless going. First try pulling the cable out and see if wireless takes over once you've installed b43 though.

Update with a cable in prior to doing any of this and also check on chili's sticky to see if you need to blacklist anything if installing b43 doesn't work.

---

### Post by chili555 on 2015-06-08
Bucky, he has no ethernet available.

We suggest you follow the process at post #7 here to get the firmware without a connection: [http://ubuntuforums.org/showthread.php?t=2098717](http://ubuntuforums.org/showthread.php?t=2098717)

---

### Post by Bucky Ball on 2015-06-09
> **chili555 said:**
> Bucky, he has no ethernet available.



Doh! Of course. My mistake. Should have been in bed. It was about 5AM here. :)

(I read this: "When I unplug the Ethernet cable, the network icon changes from 2 arrows pointing in opposite directions to a quarter-circle, and a box pops up telling me I'm disconnected," from the first post and presumed ethernet was working when the cable was in ... Shouldn't presume ...)

---

### Post by hmiersch on 2015-06-10
Well, yes, the Ethernet works but that only gets me to my wifi router and from there to my DSL router.  The connection from there to the Internet is down, that's why I can't use anything that requires an Internet connection

---

### Post by chili555 on 2015-06-10
> The connection from there to the Internet is down, that's why I can't use anything that requires an Internet connectionI assume, by this, you mean that the internet is down because of the Internet Service Provider, or billing problems or changing service or some such. You do not mean that it ought to work but doesn't work for some unknown configuration problem, do you?

Did you get and install the b43 firmware as I linked?

---

### Post by hmiersch on 2015-06-10
I mean that my Internet connection is down due to problems at BT open reach. Equipment damage? Malfunction? Configuration issue? No idea. All I know is that the problem is not at my end. 
Anyway, I can't get that firmware because my Internet connection is down.

---

### Post by chili555 on 2015-06-10
You are answering this forum on some device that connects to the internet. Can you download it there and transfer it to your Ubuntu computer on a USB key or similar? Can you hand a USB key to a friend and ask them to help you out?

---

### Post by hmiersch on 2015-06-10
Looks like I have to go to starbucks again...

---

### Post by hmiersch on 2015-06-10
Went to Starbucks to download the installer (using OSX) but couldn't do anything with the file. Gotta go and plug in somewhere then use the software center or apt-get...

Unless of course someone can tell me where to find a good version of that installer. The useless one came from packages.ubuntu.com

---

### Post by tristan16 on 2015-06-10
> **hmiersch said:**
> Went to Starbucks to download the installer (using OSX) but couldn't do anything with the file. Gotta go and plug in somewhere then use the software center or apt-get...

Unless of course someone can tell me where to find a good version of that installer. The useless one came from packages.ubuntu.com

The post mentioned earlier said that you just need to copy the file over to Ubuntu. You should be able to do that with a USB drive.

---

### Post by hmiersch on 2015-06-10
> **tristan16 said:**
> The post mentioned earlier said that you just need to copy the file over to Ubuntu. You should be able to do that with a USB drive.

Tried that but as I said the file was useless. Software center complained about an internal error, the file is not executable and I couldn't unzip it either. So I deleted it.

---

### Post by chili555 on 2015-06-10
You want to download* b43.zip *as described in the link I gave you. Transfer the zipped file to your Ubuntu computer on a USB key or similar. Right-click it and select 'Extract Here,' namely, the desktop of the Ubuntu computer. You can't install it with Software Center or apt-get or anything else. The instructions are in the link.

Since you deleted it, I guess you are back to Starbucks tomorrow.

---

### Post by hmiersch on 2015-06-13
i managed to install that wifi driver using a friend's connection. now it works, and i can use the wifi at starbucks. :-)

---

### Post by Bucky Ball on 2015-06-13
Excellent news. Please see the second link in my signature. Thanks. ;)

---

