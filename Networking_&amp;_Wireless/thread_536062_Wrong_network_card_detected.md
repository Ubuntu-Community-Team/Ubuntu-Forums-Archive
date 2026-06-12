---
title: "Wrong network card detected"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by ctmpbos on 2007-08-27
Ubuntu 7.04 detects a Realtec network card on my computer. But thats wrong and I have no network connection. How I can change my network from Realtec to Linksys?

THX

---

### Post by spd106 on 2007-08-27
Going by this page [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCards](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCards) and the Linksys subpage, you will need to use ndiswrapper to get the card working. 

There are several guides in this forum, but I'll just give you the link to more information on the wiki [http://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](http://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper).

---

### Post by ctmpbos on 2007-08-29
Why I should use ndiswrapper? The document page says: Did not autodetect during install , worked fine after install. I like to install the Linksys linux driver, but how to install it? I havent found instructions for Ubuntu, but for other linux versions. Unfortunately the directory structure of Ubuntu is different as described. I have this two files: Linksys.o and Linksys_drv.o.

---

### Post by spd106 on 2007-08-29
Sorry about the previous link, I made a mistake it should have been this one [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)

[QUOTE=ctmpbos]Why I should use ndiswrapper? The document page says: Did not autodetect during install , worked fine after install. [/QUOTE]

As you didn't mention which model or version of wireless card you have I took a guess, as most cards use ndiswrapper as a last resort I thought that would be enough, I'm sorry if that was wrong. Linksys use chipsets from many manufacturers, it appears as though your card has one made by Realtec (or is it Realtek?).

[QUOTE=ctmpbos]I like to install the Linksys linux driver, but how to install it? I havent found instructions for Ubuntu, but for other linux versions. Unfortunately the directory structure of Ubuntu is different as described. I have this two files: Linksys.o and Linksys_drv.o.[/QUOTE]

I have not seen this before, could you provide a link to the instructions.

---

### Post by ctmpbos on 2007-08-30
Here is the README.TXT from the Linksys driver files.

---

### Post by noob12 on 2007-08-30
So it appears you are talking about a wired ethernet card.  Even though linksys makes the card, the chipset on the card may be made by Realtek.  There may be a working driver shipped with Ubuntu.

Can you please post for us the output of these commands

```

lspci -nn

sudo lshw -C network

ifconfig -a

```

---

### Post by ctmpbos on 2007-08-30
Results see attachment.
After a new installation, the detected network card is now ADMtec. But all IP addresses are still 0.0.0.0 (wired network connection symbol on the panel) and still no network connection. I'm using a DSL router with DNS.

THX

---

### Post by noob12 on 2007-08-30
OK.  I see the ADMTek ethernet device.  The output  also shows the **tulip** driver has already claimed the device.  It is eth0.   You should not need to install an additional driver for this.

Let's take a look at the following 

```

sudo ethtool eth0

cat /etc/network/interfaces

grep dhclient /var/log/syslog

```

The first one will tell us what the ethernet link state is.  The second will show us how you have the interface setup.  The last one is to see if we are having problems acquiring an address using DHCP.

---

### Post by ctmpbos on 2007-08-31
I noticed, that I can change with the wired network button on the panel between 'Wired network (Unknown USB vendor...' and 'Wired network (ADMtec NC100...'. When I choose ADMtec all is working fine. But, when booting there is always the USB option active and perhaps by 5 reboots is only one, that shows the two options. In all other cases only the USB connection is shown. So I guessed, that the detection of the network card fails.
The results of your commands are in the attached document.

---

### Post by noob12 on 2007-08-31
I'm confused about your situation here.

As I understand you now, the ADMtek interface with the tulip driver is working but not on every boot.  Sometimes after booting you find that your USB ethernet device is active and your ADMtek device is not.  
Is that correct?

If so, in these cases where the ADMtek interface is not active, is the ADMtek ethernet device present at all (i.e. does eth0 show up in the listing **ifconfig -a**)?  I'm guessing it isn't showing up at all.

If you find after booting sometimes, it is not present in the **ifconfig -a** listing, we want to look at the output of **dmesg** for that boot.  Please post that if this is the case.

If it is present in **ifconfig -a** but is not shown as **UP** or has no address then we should look at other things.

---

### Post by ctmpbos on 2007-08-31
First, usb0 is always active after boot.
I have documented 3 cases:
Case 1: usb0 is active, eth0 is shown on panel button
Case 2: usb0 is active, eth0 is not shown on panel button
Case 3: case 1 and eth0 activated manually on panel button
In case 2 with 'ifconfig eth0 up' I become case 1 and can manually activate the network.

Question: What is the meaning of 'avah' in 'usb0:avah' in the ifconfig output (case 1 + 2)?

---

### Post by noob12 on 2007-08-31
OK.  And do you want both interfaces up normally at boot?  If so, try adding this stanza to your /etc/network/interfaces file (don't use NM to manage usb0).  See if that helps.

```

auto usb0
iface usb0 inet dhcp

```

---

### Post by ctmpbos on 2007-08-31
No, I need only the network card!. USB0 is a usb host to host bridge on the motherboard. The BIOS has no possibility to deactivate this. In Windows XP I have it deactivated with the device manager. Could I do that also in Ubuntu?

---

### Post by noob12 on 2007-08-31
OK.  I think just keeping the interface down is probably sufficient.  Replace any usb0 stanza in your /etc/network/interfaces file with the following single line:

```

iface usb0 inet manual

```

Do not use any auto line.  By default it should boot with the interface down.  This should also tell NM to leave it alone.

If that doesn't work you can try keeping the device unclaimed by blacklisting **usbnet**.  First try the above.

---

### Post by ctmpbos on 2007-09-02
Sorry, no success. After restart, the usb host to interface is now on usb1 instead on usb0 and still with the same problem. 
But I've found a solution in a other linux forum. There was a similar problem with a wireless card described. The solution was, to deactivate the Ubuntu network manager and this works fine on my system too. 
I suppose, there is a bug in the network manager, because this problems doesn't occurred on my system with Fedora or Mandriva, nor Knoppix.

Many THX for your help.

---

### Post by noob12 on 2007-09-02
Glad to hear you have resolved your issue. 

If you have a  stationary wired situation (which it sounds like to me) you probably don't need NM around and it probably will tend to get in the way.

If you did want to keep NM around, you can get the **usbnet ** device to consistently map to usb0 using /etc/iftab (see **man iftab**).

---

