---
title: "DWL-G520 network issues (Newbie)"
date: 2005-11-23
forum: Networking &amp; Wireless
---

### Post by Kuulwhip on 2005-11-23
I know there are multiple posts regarding issues but I am getting more confused reading through all of them as I am not sure where to start.

As the thread title indicates I have a DWL-G520 on my system, it is dual booted with XP Pro and XP works fine.

1.  Ubuntu sees the card as ath0, do I still need to use ndiswrapper and the windows driver?

2.  I am using a WRT54GX-v2 router with WEP 64 bit set up.  I will be changing that to 128 bit but I want to get this figured out first.

3.  I have went into properties of the NIC and it sees the wireless network, I have put the WEP key in place (even retyped it a couple of times to see if I was fatfingering it).  Whenever I go back into the network area my default gateway is blank again and I have to put ath0 back in.

I have no access to the network and my router shows no entry for my Linux box in the clients table.  I know the kind soul or souls who wish to help will want to see some command results from the terminal but I am not sure what so I will hold off on listing every command result I can think of.

In advance, thank you very much for your time as this is my only headache so far and I would hate to go hardwired ethernet, I do not relish the idea of running drops in the area where I have my Linux box.

---

### Post by anakrich on 2005-11-23
Hi,
I have a DWL G 630 PCMCIA wireless Rev C1. I have been using Suse 9.2 pro but switched to Ubuntu Breezy last night. This is what I did to get this card to work. This might not be the same card as you have but both of them have 2 chips one from TI and other from Atheros.
In Ubuntu it gets detected as ath0. True. But there are no native linux drivers for this card.
So use NDISwrapper (you could use ndisgtk but i prefer the command line) and simply follow the instructions in sound forge.net. (ndiswrapper -i *.inf, modprobe ndiswrapper, iwconfig commands details of which are in exhaustive detail on soundforge.net).
Then in the network icon on your panel, change the default gateway to ath0 and display connection status to ath0.
Restart your computer to check is ndiswrapper has been modprobed (this can be checked if your network connection says ok and your clock gets synchronized in startup). Once gnome is up, you should be able to browse the internet with wireless.

Hope this helps.

Ananth

---

### Post by Lambert on 2005-11-23
Usually ath0 is assigned to cards with an atheros chipset. I don't see a dwl-g520 having the following chipsets. And with the way you descrive 3. I would guess it won't use ath0.

802.11b 	DWL-520 		PCI 	Realtek 	rtl8180  	

802.11b 	DWL-520 Rev. E 		PCI 	Prism3 SSF 	

There could be more, this was just the list I looked at quickly. So just to double check run these commands.

```
sudo lshw -C network
and 
lspci -v
and 
lspci -n
```

Post that output here.

After we verify the chipset in the card we can take it from there to the exact driver needed or where to go from here.

When you run lshw -C network, you can find the device in the output and look for the line that begins configuration: if it doesn't have anything saying driver=xxx then you don't have a driver allocated to this device. You will probably need to use ndiswrapper. Click on the link in my signature about ndiswrapper. It should be pretty clear.

---

### Post by dodongo on 2005-11-23
I have a DWL-G520  (v.B2) that does run the Atheros drivers, and runs them (nearly) perfectly, at that.

Kuulwhip (welcome to Ubuntu, by the way!), if you've verified you have the correct settings put in for your WLAN, can you run:

```
sudo /etc/init.d/networking restart
```

once you've already booted?  See if that works for you.

My problem is not that the card doesn't work, but that it never works until the system has booted to GNOME and I reload the networking drivers using that command.

Anyone have any suggestions for *that* symptom?  Does that help you out at all?

---

### Post by Ford Prefect on 2005-11-23
I am using a D-link DWL G520 REV. B card.
However I need to use WPA passphrase authentication (No, I cannot use MAC filtering on my network.)

Does anyone have a link to a tutorial for ndiswrapper?  I mean a basic, step by step, explains everything twice, type tutorial?
I've Googled for over 2 months now trying to find one.

---

### Post by dodongo on 2005-11-23
I don't even know what ndiswrapper is :)

---

### Post by Lambert on 2005-11-23
[quote=Ford Prefect]I am using a D-link DWL G520 REV. B card.
However I need to use WPA passphrase authentication (No, I cannot use MAC filtering on my network.)

Does anyone have a link to a tutorial for ndiswrapper?  I mean a basic, step by step, explains everything twice, type tutorial?
I've Googled for over 2 months now trying to find one.[/quote]

not sure what you mean by tutorial for ndiswrapper but there's a wiki entry in my signature for ndiswrapper.

Or you can search around here.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

This is the link to the installation page but you can navigate around the ndiswrapper site from there.

---

### Post by SickTwist on 2005-11-23
[QUOTE=anakrich]Hi,
I have a DWL G 630 PCMCIA wireless Rev C1. I have been using Suse 9.2 pro but switched to Ubuntu Breezy last night. This is what I did to get this card to work. This might not be the same card as you have but both of them have 2 chips one from TI and other from Atheros.
In Ubuntu it gets detected as ath0. True. But there are no native linux drivers for this card.
So use NDISwrapper (you could use ndisgtk but i prefer the command line) and simply follow the instructions in sound forge.net. (ndiswrapper -i *.inf, modprobe ndiswrapper, iwconfig commands details of which are in exhaustive detail on soundforge.net).
Then in the network icon on your panel, change the default gateway to ath0 and display connection status to ath0.
Restart your computer to check is ndiswrapper has been modprobed (this can be checked if your network connection says ok and your clock gets synchronized in startup). Once gnome is up, you should be able to browse the internet with wireless.

Hope this helps.

Ananth[/QUOTE]

If the card has an atheros chipset, there is a native Linux driver called [madwifi]("http://madwifi.org"). Not only that, it is included in Ubuntu (it is part of the Linux restricted modules package). Run this command if it needs to be installed:

sudo apt-get install linux-restricted-modules-`uname -r`

---

### Post by Kuulwhip on 2005-11-25
Ok, sorry for the delay, Thanksgiving and all.  Thank you everyone for the quick responses, I am loving the Ubuntu community already.  Following is the original results for the commands requested.  On a side note, I sure would love to know how to keep the formatting from Linux txt files to Windows, I had to make it all nice as it came up as one long line in the document although the original seems to paste to this forum exactly as it appeared in Linux without any reformatting.

gene@LinuxKA:~$ sudo lshw -C network
  *-network:0
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: d
       bus info: pci@00:0d.0
       logical name: ath0
       version: 01
       serial: 00:11:95:e6:99:80
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0 (EXPERIMENTAL) multicast=yes wireless=IEEE 802.11g
       resources: iomemory:e2000000-e200ffff irq:17
  *-network:1 DISABLED
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 13
       bus info: pci@00:13.0
       logical name: eth0
       version: 10
       serial: 00:0d:61:af:bd:59
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=half link=no multicast=yes port=MII speed=10MB/s
       resources: ioport:e400-e4ff iomemory:e2011000-e20110ff irq:18
gene@LinuxKA:~$ lspci -v
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
        Subsystem: Giga-byte Technology GA-7VAX Mainboard
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: e0000000-e1ffffff
        Prefetchable memory behind bridge: d8000000-dfffffff
        Capabilities: <available only to root>

0000:00:0d.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: D-Link System Inc: Unknown device 3a13
        Flags: bus master, medium devsel, latency 168, IRQ 17
        Memory at e2000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root>

0000:00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: Giga-byte Technology GA-7VAX Mainboard
        Flags: bus master, medium devsel, latency 32, IRQ 20
        I/O ports at d000 [size=16]
        Capabilities: <available only to root>

0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology GA-7VAX Mainboard
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at d400 [size=32]
        Capabilities: <available only to root>

0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology GA-7VAX Mainboard
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at d800 [size=32]
        Capabilities: <available only to root>

0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology GA-7VAX Mainboard
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at dc00 [size=32]
        Capabilities: <available only to root>

0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology GA-7VAX Mainboard
        Flags: bus master, medium devsel, latency 32, IRQ 21
        Memory at e2010000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [K8T800 South]        Subsystem: Giga-byte Technology: Unknown device 5001
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Subsystem: Giga-byte Technology GA-7VAX Onboard Audio (Realtek ALC650)
        Flags: medium devsel, IRQ 22
        I/O ports at e000 [size=256]
        Capabilities: <available only to root>

0000:00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Giga-byte Technology GA-7VM400M Motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at e400 [size=256]
        Memory at e2011000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] (rev c1) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 11
        Memory at e0000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <available only to root>

gene@LinuxKA:~$ lspci -n
0000:00:00.0 0600: 1106:3189 (rev 80)
0000:00:01.0 0604: 1106:b198
0000:00:0d.0 0200: 168c:0013 (rev 01)
0000:00:0f.0 0101: 1106:0571 (rev 06)
0000:00:10.0 0c03: 1106:3038 (rev 81)
0000:00:10.1 0c03: 1106:3038 (rev 81)
0000:00:10.2 0c03: 1106:3038 (rev 81)
0000:00:10.4 0c03: 1106:3104 (rev 86)
0000:00:11.0 0601: 1106:3227
0000:00:11.5 0401: 1106:3059 (rev 60)
0000:00:13.0 0200: 10ec:8139 (rev 10)
0000:01:00.0 0300: 10de:0185 (rev c1)
gene@LinuxKA:~$

---

### Post by Lambert on 2005-11-25
The card does have an atheros chipset so you don't need ndiswrapper. Madwifi is loaded and allocated to the card correctly.

You should be able to just go into system>admin>network, highlight the device, click properties, enter your network properties, ok then activate.

If you can try to connect via open signal first and after success then add wep back into the equation.

There seems to be mixed success with wep but I would suggest using open setting instead of shared.

If you can't get connected this way come back and post the output of iwconfig and ifconfig

You can always click on the troubleshooting guide in my signature to see if you can solve your connection.

---

### Post by Kuulwhip on 2005-11-25
Ok, removed WEP and it worked, woohoo.

Now, for WEP.  Is this something I may never get working?  The keys generated by my router:  Are they plain text or HEX?  I was entering them as plain (ASCII) text in the Linux Network Properties dialogue for the card.  I would really hate to leave it wide open like that although I could just turn it off when I want to use Linux for a while and then regenerate the keys and turn it back on when I am done (can anyone hear the sarcasm while I am describing that option?).

Thanks for the assistance thusfar, now onto WEP.

---

### Post by Kuulwhip on 2005-11-26
So does anyone have any answers on WEP for this chipset?  It sees the network but I have no access, the router doesn't acknowledge it as a DHCP client, etc when WEP was in place.  I used various keys were generated, no luck.  Is there something I am doing as far as the dropdown in networking the is ASCII or HEX for the key?

---

### Post by dodongo on 2005-11-26
[QUOTE=Kuulwhip]So does anyone have any answers on WEP for this chipset?  It sees the network but I have no access, the router doesn't acknowledge it as a DHCP client, etc when WEP was in place.  I used various keys were generated, no luck.  Is there something I am doing as far as the dropdown in networking the is ASCII or HEX for the key?[/QUOTE]

Your router doesn't give you any clues as to whether or not the WEP key is ASCII or HEX?  One way to take a stab at it is to look at the invidual characters.  Are they all 0-9 or A-F?  If so, chances are it's a HEX key.

---

### Post by Kuulwhip on 2005-11-26
Ok, much as I hate doing this, I will own up to the fact that I made a complete brain fart on this.  After changing to the DWL-G520 from the previous wireless card I had left everything on ASCII in Ubuntu for WEP from when I had been troubleshooting the last card.  So.....  Changed it back to HEX like the last kind soul had suggested and we are off and running.  Thank you everyone for thier time on this.  I will stop banging my head on my keyboard in a few minutes.

---

### Post by dodongo on 2005-11-26
This is fun :)  Good luck with your now-working Ubuntu system!

---

### Post by Unverzagt05 on 2005-12-15
Bumping this issue

i too have the DWL-G520 card REV B. Im on ubuntu right now, but i don't feel comfortable leaving my router open like it is right now. I can't use WEP nor Shared, is their a way that this can be fixed, or am i SOL ?

---

### Post by dodongo on 2005-12-15
[QUOTE=Unverzagt05]Bumping this issue

i too have the DWL-G520 card REV B. Im on ubuntu right now, but i don't feel comfortable leaving my router open like it is right now. I can't use WEP nor Shared, is their a way that this can be fixed, or am i SOL ?[/QUOTE]

And you're sure you have the key set to either HEX or ASCII in *both* locations -- on the router AND on the computer?

For the router, it should tell you this on the page where you type in your key.

In Ubuntu, head to the System menu, then Networking, then select your network adapter (wireless) and do Properties.  There's a box there that'll tell you.  Make sure they match, and that they have the same key.

---

