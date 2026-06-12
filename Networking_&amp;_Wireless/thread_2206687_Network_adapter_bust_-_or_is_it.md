---
title: "Network adapter bust - or is it?"
date: 2014-02-20
forum: Networking &amp; Wireless
---

### Post by texpat on 2014-02-20
So I sat down at the PC (runs ubuntnu 12.04 LTS) and network was down. Just like that, from one day to the next. The machine was not shut down or reset. After checking the external hardware (ethernet cable, router) it seems that the problem is with the computer.

I've done the obvious (to me): check networking is enabled, restart, plus some things I found on this forum:

[FONT=Courier New]ifconfig [/FONT]turns up no IP
[FONT=Courier New]ping [/FONT]returns "network is unreachable"

Is there anything else I can to determine whether its the network adapter that's bust?

Thanks for reading. Any hints greatly appreciated :)

---

### Post by varunendra on 2014-02-20
Yes, please post the output of -
```
sudo lshw -numeric -C network
```

---

### Post by texpat on 2014-02-21
[FONT=Courier New]lshw -numeric -C network[/FONT]:
```
*-network
	description: Ethernet interface
	product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10EC:8136]
	vendor: Realtek Semiconductor Co., Ltd. [10EC]
	physical id: 0
	bus info: pci@0000:01:00.0
	logical name: eth0
	version: 02
	serial: 00:26:17:ba:e5:f0
	size: 10Mbit/s
	width: 64 bits
	clock: 33MHz
	capabilities: pm msi pciexpress msix vdp bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
	configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
	resources: irq:42 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdfe0000-fdfeffff memory:febf0000-febfffff
```

---

### Post by varunendra on 2014-02-21
> **texpat said:**
> [FONT=Courier New]lshw -numeric -C network[/FONT]:
```
	configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI **[B][COLOR="#FF0000"]duplex=half[/COLOR]**[/B] firmware=N/A latency=0 link=no multicast=yes port=MII **[COLOR="#FF0000"]speed=10Mbit/s[/COLOR]**
```

Please try -
```
sudo mii-tool -F 100baseTx-FD eth0
```

Report back if there are errors.

---

### Post by texpat on 2014-02-21
[FONT=Courier New]sudo mii-tool -F 100baseTx-FD eth0[/FONT]

Nothing happens. At least no feedback on the terminal. The only way to get the command to report anything was to use the [FONT=Courier New]-v -v[/FONT] option which returns
```
Using SIOCGMIIPHY=0x8947
```

---

### Post by varunendra on 2014-02-21
What does the command "sudo mii-tool" report, without any parameters?

Sounds like the command succeeded in doing what it was supposed to do, else it would have returned some error message.

---

### Post by texpat on 2014-02-21
@varunendra: thanks for your help so far. I won't have access to the machine in question till Monday, so please bear with me.

---

### Post by texpat on 2014-02-24
```
:~$ sudo mii-tool
 No MII transciever present!
```

---

### Post by varunendra on 2014-02-24
> **texpat said:**
> ```
:~$ sudo mii-tool
 No MII transciever present!
```

Interesting! I believe the "sudo mii-tool -F 100baseTx-FD eth0" command should have returned a clear error message stating that the interface eth0 does not support mii protocol (or something alike).

Anyway, can you connect the system to internet by other means? If yes, please install "ethtool" -
```
sudo apt-get install ethtool
```

If you can't connect to internet, try this one to get download URI(s) of the required package(s) -
```
apt-get install --print-uris ethtool
```
If your software cache has been updated even once, the above command should return the download links of the required packages at the bottom of the output. Use these links to download the packages on another computer and copy them back to this machine.

Put them in a new, empty directory (let's call it "packages") in your home and install with -
```
sudo dpkg -i packages/*.deb
```

Once ethtool is installed, try enforcing the same settings using ethtool this time -
```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```

Then please post back the output of -
```
sudo ethtool eth0
```

---

### Post by texpat on 2014-02-25
After:
```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```
Which seems to have run correctly
```
sudo ethtool eth0
```
reports
```
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  Not reported
	Advertised pause frame use: No
	Advertised auto-negotiation: No
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: off
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: no
```

---

### Post by varunendra on 2014-02-25
Is this a Gigabyte motherboard? Whether or not, is there a setting called IOMMU in the BIOS?

If there is, try changing its state to whatever it currently is. If there is no IOMMU there, try resetting the BIOS to defaults.

Depending on whether the system BIOS has the IOMMU feature, a few more options may be tried if the above doesn't work.

In the meanwhile, please also try the lower speed with full duplex (if changing IOMMU or resetting BIOS doesn't work) -
```
sudo ethtool -s eth0 speed **10** duplex full autoneg off
```

And.. please also check the dmesg log yourself (the **/var/log/dmesg** file). Are there any errors or otherwise interesting messages in it? If there are, please post those parts here. You may also check **/var/log/syslog** file which may sometimes contain useful messages that are not logged by dmesg.

---

### Post by texpat on 2014-02-27
Hi Varun and thanks for your patience :-)

Mainboard is ASUS, model P5KPL-AM SE

No IOMMU setting found in BIOS.

I found a setting [FONT=Courier New]**LAN Option ROM**[/FONT] which I enabled and then disabled again because it didn't have any apparent effect.

I also found a setting in the "Tools" section called "[FONT=Courier New]**AI NET 2**[/FONT]" with the option to "[FONT=Courier New]**Check Realtek LAN Cable**[/FONT]". When enabled it would report "[FONT=Courier New]**LAN cable not ready**[/FONT]" and send me back to BIOS setup. If I tried to go into the IA NET 2 menu again BIOS would hang forcing me to hard reset. I had to reinstate BIOS defaults to disable LAN Cable check.

BTW: I did, of course, plug the cable into another computer to make sure it works.

Reinstated BIOS defaults -> nothing changes, i.e. network still down

Reduced speed as per command you proposed -> no go

I looked at /var/log/dmesg which I find kind of cryptic ;-)
Searching for lines containing "eth0" I find, for example:

```
ADDRCONF(NETDEV_UP): eth0: Link is not ready

r8169 0000:01:00.0: eth0: link down
```

/var/log/syslog basically says the same but there is additional information that might be relevant:

```
Network Manager[762]: Ifupdown: get unmanaged devices count: 0
Network Manager[762]: SCPlugin-Ifupdown: (16300848) ... get_connections.
Network Manager[762]: SCPlugin-Ifupdown: (16300848) ... get_connections (managed=false): return empty list.
Network Manager[762]: keyfile: parsing Wired connection 1 ...
Network Manager[762]: keyfile:		read connection 'Wired connection 1'
Network Manager[762]: Ifupdown: get managed devices count: 0
Network Manager[762]: <info> modem manager is now available
Network Manager[762]: <info> monitoring kernel firmware directory 'lib/firmware'.
Network Manager[762]: <info> WiFi enabled by radio killswitch; enabled by statefile
Network Manager[762]: <info> WWAN enabled by radio killswitch; enabled by statefile
Network Manager[762]: <info> WiMAX enabled by radio killswitch; enabled by statefile
Network Manager[762]: <info> networking is enabled by statefile
Network Manager[762]: <warn> failed to allocate link cache: (-10) operation not supported
Network Manager[762]: <info> (eth0): carrier is OFF
Network Manager[762]: <info> (eth0): new Ethernet device (driver 'r8169' ifindex: 2)
Network Manager[762]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Network Manager[762]: <info> (eth0): now managed
Network Manager[762]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Network Manager[762]: <info> (eth0): bringing up device.
Network Manager[762]: <info> (eth0): preparing device.
Network Manager[762]: <info> (eth0): deactivating device (reasong 'managed') [2]
kernel: [   10.121108] r8169 0000:01:00.0: eth0: link down
kernel: [   10.121651] ADDRCONF(NETDEV_UP): eth0: Link is not ready
kernel: [   10.122120] ADDRCONF(NETDEV_UP): eth0: Link is not ready
```

I had to copy this by hand (no network and I forgot to bring my pendrive) from the borked compter's screen, so there may be typos.

---

### Post by varunendra on 2014-02-27
Pretty good copy for a hand typed log. :)

Not very sure but is the eth0 managed by the /etc/network/interfaces file? -
> **texpat said:**
> ```
Network Manager[762]: <info> (eth0): **deactivating device (reasong 'managed')** [2]
```

And do the classic ifconfig commands do anything? -
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```

If not, I think I have tried all I could think of. The only thing left is to try the proprietary driver, assuming it is a driver bug (a serious one if it is).

Accordingly, please download the r8168 driver from here : [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

Assuming you copied this driver package (r8101-1.024.00.tar.bz2) into your Home directory, extract and install it with -
```
tar xf r8101-1.024.00.tar.bz2
cd r8101-1.024.00
sudo ./autorun.sh
```
It will automatically remove (and backup) the current driver, compile and install the proprietary one and load it. If that doesn't make the ethernet active either, we are probably beating a dead horse.

---

### Post by Bashing-om on 2014-02-27
texpat; Hi !

I have recently recovered in a similar situation; My steps:
Hardwire procedure:
1. network card detected ?
    sudo lspci | grep Ethernet
2. IP address assigned ?
    ipconfig eth0 (or whichever the network is,eth1)
 -no address returned ?
3. Check /etc/network/interfaces
  13.10 should be:
    # The primary network interface
##changed eth0 to eth1 26feb2014##
auto eth1
iface eth1 inet dhcp
4. Disable the firewall (be prepared to know how to set it up again !)
    iptables -F
///
What I found:
a) Bent pin on my original inet card -> changed out the cable
b) No response when pinging my router -> recloned the router mac addresses
c) inappropriate setting in the control file /etc/network/interfaces -> set the correct device name
///
With the above done, I had my internet connectivity established (4 days trouble shooting !)
If you have to go to step 4 heed the warning and do your homework !

just my little bit
[INDENT][INDENT]to try and help
[/INDENT][/INDENT]

---

### Post by texpat on 2014-02-28
@Varun: installed proprietary driver but still no fun :-(

Just for the heck of it I restared the machine to boot a live Linux (Parted Magic) from CD. Since I didn't get a network there either, I'm assuming I have a hardware problem.

I checked for obvious damage, but I'm way out of my depth when it comes to hardware issues.

@Bashing-om: thanks for chipping in.

I ran through the first 3 points quickly:

Network card is detected.
No IP-address is assigned.
etc/network/interfaces reads (just in case its important: the computer runs 12.04 LTS)
```
auto lo
iface lo inet loopback
```

I've decided to take the machine to the repair shop.

Here's thanking you again for reading and contributing. Even though this time we couldn't solve the problem (possibly because it just couldn't be solved here), I've learnt a great deal again.

---

### Post by varunendra on 2014-02-28
> **texpat said:**
> Just for the heck of it I restared the machine to boot a live Linux (Parted Magic) from CD. Since I didn't get a network there either, I'm assuming I have a hardware problem.

I happen to concur with you. If you haven't been removing the older kernels, try booting into one of them from the grub menu. If you don't get the grub menu by default at startup, tap the 'Shift' (or 'Esc' in some systems) key during the purple splash screen to get it.

If the symptoms are same with the older kernel(s) also, then I'm fully convinced that it is a hardware fault.

---

### Post by Bashing-om on 2014-02-28
texpat; Well.

Taking the machine to the shop may well be the fastest solution, Overall, perhaps not the best. I am more than willing to do whatever I can to get ya up and running. As the card is recognized, the most likely cause is in configuration.
Your /etc/network/interfaces file is correct for version 12.04 -> are you connecting through a router ? Is your wired connection through a cable modem to your ISP ? Does the output of "ifconfig" show that the loopback interface is good ? ( TX and RX number are all the same ?) Then we can assume that the card is good.

Try RE-setting your router and modem ( do you get a blinking response on the link LED indicator on your modem ? ) - Maybe even the link is down between your hardware and the ISP ? ( maybe ask your provider to reset the cable modem for you ?)

It would be a shame to spend good money only to find it is a config problem.

[INDENT][INDENT]where there are solutions there is no problem[/INDENT][/INDENT]

---

### Post by texpat on 2014-02-28
I agree it may not be the best move to make, but the machine belongs to a small business I work for and, although not vital, is important enough to warrant throwing some money at it to get the problem solved in a more or less timely fashion.

The problem is in the computer itself. I'm quite confident about that. Resetting the router was one of the first things I did. I checked the cable on another PC and it works perfectly well. I plugged another PC's ethernet cable (which I knew worked) into this computer and it remained mute. Other computers on the network can access Internet without problems.

The problem is most likely a hardware problem. Although I didn't go through with Varun's proposal to boot an old kernel (by the time this was suggested the machine was already at the repair shop), I think Its safe to say its a hardware issue since the Parted Magic live CD also got no network, exhibiting the same symptoms as the native Ubuntu install (i.e. card checks out, but no IP and no traffic between computer and router, "network not accessible")

I'm quite sure that there are many things you have in mind that may still prove me wrong, but unfortunately I don't have the time test them out.

Nevertheless, thank you both and, by extension, the whole forum community. It isn't to be expected that we can solve all each other's problems here, but we'll sure give it our best shot!

---

### Post by Bashing-om on 2014-02-28
texpat; Hey,

OK, All then, as all is done presently we can do. We will await what the shop finds.

Please to keep us informed -> and what else we can do.

[INDENT][INDENT]expediency is a 
[INDENT][INDENT]harsh master
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by texpat on 2014-03-07
So the machine is up and running again. The problem was the network adapter.

Repair shop installed a new one and BINGO!

Marking this solved and hope that anyone with similar issues may benefit.

---

### Post by varunendra on 2014-03-07
Thanks for the feedback! Confirmations are always the sweetest and probably most important part of a problem thread. :)

I hope I'd be able to use this experience to offer better help next time I see a similar case.

---

