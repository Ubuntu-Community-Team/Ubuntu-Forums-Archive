---
title: "Cannot make WOL (Wake on LAN) work with r8169 (Gigabyte A P35-DSP3 Motherboard)"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by bollee23 on 2007-11-04
I Cannot make WOL (Wake on LAN) work with r8169 driver (Gigabyte A P35-DSP3 Motherboard under Gutsy AMD64).
Since I'am slightly game addicted I have a second partition  with Windows XP and I can tell that after shutting down from XP WOL is working OK (WOL from my DD-WRT router).
After shutting down from Gutsy there is no way to wake up my PC.
I have tried many things as suggested in many forums :
- adding startup scripts to enable WOL through the "ethtool -s eth0 wol g" command (command is executed without any error and 'ethtool eth0' returns consistent WOL flags)
- removing '-i' option on the 'halt' command from the /etc/init.d/halt script
- using the Realtek official driver ( r8168 ) in place of the Gutsy provided r8169
- forcing network shutdown (ifdown -a --force) before 'halt' command in /etc/init.d/halt script

If anyone have the same issue I would feel less alone and if some guru have a clue ... :)

In advance thank you.



[B]
ethtool output :[/B]

Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes

**lspci -nn output : **

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)

---

### Post by t0m on 2007-11-05
I think I have quite a similar problem, or maybe the same. I have a different motherboard, though.
[http://ubuntuforums.org/showthread.php?p=3710570](http://ubuntuforums.org/showthread.php?p=3710570)

Tried the same "solutions" (besides using an alternative driver),  but unfortunately it still doesn't wake...

So are there people out there using Wake-on-Lan successfully on Gutsy? Please help!

---

### Post by bollee23 on 2007-11-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/160413](https://bugs.launchpad.net/ubuntu/+bug/160413) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Thank you t0m, I feel less alone !

So maybe it's not a specific driver related issue.

I have just reported the problem on Launchpad.

---

### Post by njparton on 2007-11-06
It works with my gutsy both with the onboard realtek nic and my new Intel pro card. In fact I've even managed to get it to work with a multicast or broadcast wake with my intel card.

I'm not gloating, just confirming that it is possible so hang in there.

I was going to ask that you've got your BIOS set up correctly, but if you can wake from a windows shutdown then that should be ok.

When you shutdown with ubnutu, do the lights on the nic at the back of your PC stay on? If not then either the dirver or the network module(s?) are being unloaded at shutdown and the PC therefore can't be woken as the the nic is dead until you restart.

Check your ACPI settings/config files.

I've got this problem with S3 suspend but not with shutdown. Not worked out a solution yet...

---

### Post by bollee23 on 2007-11-06
Concerning NIC LEDs they are both OFF either after shuting down from Gutsy or XP : so in my case LEDs are not significant of a good or bad configuration.

Concerning ACPI I have some doubts about my conf :

I have installed acpitool. and I don't see the pci id of my NIC (04:00.0) when doing acpitool -w and everything seems disabled :

   Device       S-state   Status   Sysfs node
  ---------------------------------------
  1. PCI0         S5     disabled  no-bus:pci0000:00
  2. PEX0         S5     disabled  pci:0000:00:1c.0
  3. PEX1         S5     disabled  
  4. PEX2         S5     disabled  
  5. PEX3         S5     disabled  
  6. PEX4         S5     disabled  pci:0000:00:1c.4
  7. PEX5         S5     disabled  pci:0000:00:1c.5
  8. HUB0         S5     disabled  pci:0000:00:1e.0
  9. UAR1         S3     disabled  pnp:00:06
  10. IGBE        S4     disabled  
  11. USB0        S3     disabled  pci:0000:00:1d.0
  12. USB1        S3     disabled  pci:0000:00:1d.1
  13. USB2        S3     disabled  pci:0000:00:1d.2
  14. USB3        S3     disabled  
  15. US31        S3     disabled  pci:0000:00:1a.0
  16. USB4        S3     disabled  pci:0000:00:1a.1
  17. USB5        S3     disabled  pci:0000:00:1a.2
  18. USBE        S3     disabled  pci:0000:00:1d.7
  19. USE2        S3     disabled  pci:0000:00:1a.7
  20. AZAL        S5     disabled  pci:0000:00:1b.0

So maybe you pointed out a pb in my configuration : but I don't know much about acpi : what would do or check in order to adapt the acpi configuration ?

In advance thank you

---

### Post by njparton on 2007-11-06
You've gone way over my head there so I can't help any further I'm afraid.

Interesting point about your LEDs - mine need to be lit continuously (not out or flashing) for WOL to work.

---

### Post by LosWochos on 2008-02-18
I have exactly the same Problem. Wakeup from S1 in Windows XP works without any problems...

- Motherboard: Shuttle FV25 with VIA PN133T Chipset
- 2x NICs: Realtek 8139c (onboard), Realtek 8169 --> Both with WOL support (tested in windows)
- Debian Etch and Ubuntu 7.10

# ethtool (onboard NIC):

```

	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 32
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000007 (7)
	Link detected: yes

```


# acpitool -w

- enabling PCI0 doesn't have any effect

```

Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. SLPB	  S5	*enabled   
  2. PCI0	  S5	 disabled  no-bus:pci0000:00      <-- this could be the problem!
  3. USB0	  S3	 disabled  pci:0000:00:07.2
  4. USB1	  S3	 disabled  pci:0000:00:07.3
  5. MODM	  S4	 disabled  
  6. UAR1	  S5	 disabled  pnp:00:08


```


Are there any solutions?


LosWochos

---

### Post by andrej_domzale on 2008-03-01
Hi
Here it is how I overcome this problem in ubuntu gutsy and realtek  RTL8111/8168B :

Download driver from realtek and install as written in readme (inside bz2 file):
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)
File is: Linux driver for kernel 2.6.x and 2.4.x (Support x86 and x64), version 8.005.00

After driver is installed, I got two drivers when I use lsmod | grep r81
Old driver is r8169, new one is r8168. We must rid of r8169 driver. I do like this:
( see: [http://ubuntuforums.org/archive/index.php/t-671614.html](http://ubuntuforums.org/archive/index.php/t-671614.html) )

First, you need to rename the r8169 driver, because it won't work with this one.

> mv /lib/modules/`uname -r`/kernel/drivers/net/r8169.ko /lib/modules/`uname -r`/kernel/drivers/net/r8169.ko.old
> depmod -a

To save the current ramdiscimage and make a new one:
> mv /boot/initrd.img-`uname -r` /boot/initrd.img-`uname -r`.old
> mkinitramfs -o /boot/initrd.img-`uname -r`

Now you have to reboot. After this, it worked for me. To see weather the right module is loaded, you can use this:
> lsmod | grep r81*

There it showed me the right module, r8168.



Now come final step, edit /etc/network/interfaces
My lokes like this:



iface eth0 inet dhcp
up ethtool -s eth0 wol g
address 192.168.2.117
netmask 255.255.255.0
gateway 192.168.2.1

auto lo
iface lo inet loopback

auto eth0






After this WOL works fine.

BR
Andrej

---

### Post by CanMan23 on 2008-03-10
Hi all,
just wanted to post an easier solution, just in case someone is interested. Had exactly the same issue on the same MB, when Mythbuntu was installed.

**Solution:**
[LIST=1]
[*]Run ethtool to active wol via magic packet (e.g. ethtool -s eth0 wol g) - required only once, if no dual boot is used, otherwise it might need to be run everytime Linux is started
[*]Edit /etc/init.d/halt and remove the -i parameter from the "halt" command
[*]Edit /etc/init.d/reboot and remove the -i parameter from the "reboot" command
[/LIST]

That's it -- working for me. Sending a WOL magic packet start the machine.

---

