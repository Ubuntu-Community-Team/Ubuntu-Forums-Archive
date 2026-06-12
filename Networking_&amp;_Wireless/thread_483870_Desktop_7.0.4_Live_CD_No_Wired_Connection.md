---
title: "Desktop 7.0.4 Live CD: No Wired Connection"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by shreepads on 2007-06-25
Downloaded and created Desktop 7.0.4 Live CD and booted up in my dad's old (ancient!) PC which currently runs Windows 2000 professional.

The graphics, sound, keyboard, mouse, basic apps, USB pen drives are all working fine, but have a huge issue with the network.

The PC has an ethernet card and is connected to a D-Link ADSL 2+ modem/ router. While the 'LAN' light on the router is OK, the network connection icon at the top right shows 'No Network connection' on mouse-over.

Based on the help, opened the System - Administration - Networking control panel, but there I find that only 'Modem' is listed for configuration. While the help doc screenshot shows 'Wired' and 'Wireless' connections for configuration, [B]these options do not show up in the networking admin panel.
[/B]

From which I believe the system is unable to detect/ use the network card installed. What is the best way to get around this? Have been browsing the forum for some while but most discussions are around wireless card problems.

I'm not sure what other information I should give, so pls let me know. During the startup, I noticed the following errors (as close as I could get!):
- Driver fails 2000 test, ACPI = force
- Failed to restet NO_REBOOT flag
- FWH not detected

Also, the card is a **Realtek RTL 8139 PCI Fast Ethernet Adapter** (which, along with ADSL modem/ router, work fine with Win 2K)

Have checked on [https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek) and this card **is listed there with 'Auto-Detected' and 'Works' set as 'Yes'**

Need to sort this out before my dad will let me install Ubuntu!

---

### Post by shreepads on 2007-06-25
Found a related bug on Launchpad along with some workarounds...
[https://bugs.launchpad.net/baltix/+source/network-manager/+bug/82927](https://bugs.launchpad.net/baltix/+source/network-manager/+bug/82927)

Seems that this problem isn't being fixed in 7.0.10 as well (at the bottom of the note). However the notes indicate that users do not face this bug in Drake/ Eft.

So I guess I will
 - Try the workarounds
 - Download and install Drake/ Eft and see if all is fine with them

---

### Post by shreepads on 2007-07-03
Downloaded and installed Drake.. Only improvement is that the scanner works, but face the same problem with the wired connection option not being available. Furthermore Drake is unable to read existing FAT32 partitions, which is one of the big plus that I have sold my dad on, so Drake is out... :(

So I moved back to trying to fix networking in Fawn.

I have attached the outputs from the following, before attempting to make any changes
 - /var/log/syslog (in two parts due to attachment size restrictions)
 - lspci -vvnn
 - ifconfig -a
 - /etc/network/interfaces

Tried running the same Live CD on a friend's PC (which is more recent and with the same networking configuration ie ADSL router connected via ethernet) that also has a Realtek 8139 network card and everything is working fine there
 - Getting IP from DHCP embedded in ADSL router
 - pppoeconf
 - Working Firefox
 - Working download of additional drivers for playing restricted media

---

### Post by shreepads on 2007-07-03
Next, I tried the following steps, based on the approach mentioned in the various posts.

[LIST]
[*]sudo dhclient: No reason why this should work, and it didn't. Output as follows:
```
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

No broadcast interfaces found - exiting.
```

[*]/etc/init.d/networking restart: Output is too large, so have attached the same. No change.

[*]sudo pppoeconf: This brought up a screen whose screenshot is attached, asking me to run modconf, but as that is not installed and networking is not working, can't go any further

[*]Attempted to download drivers from Realtek website and re-install. But the site ([http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=6&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=6&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)) says that the driver for 8139 is a part of the kernel and doesn't offer for download.
[/LIST]

Other options suggested that I don't want to try, unless I know something more:
[LIST]
[*]Download the Realtek driver code (location unknown) and recompile. This is simply too much work and creates a potentially unstable system as I don't know what I should do and I would need to get the compilers etc as well, which is difficult given that the network doesn't work.
[*]Insert some ACPI related pre-boot commands, which I don't know how to do and don't think I can, given that I am booting from a Live CD.
[*]'Shake up the PCI settings'. I don't know which PCI setting does what and cannot risk destabilising a working desktop, even if it is Win2K Professional.
[/LIST]

Any help will be very welcome. I have also attached a screenshot of the Networking Manager applet to give a clear idea of what I mean when I say 'No Wired Connection'

---

### Post by shreepads on 2007-07-03
Last post from my side, have run into a wall..

Checked the lspci output and find that my dad's computer has a Realtek RTL 8139D card while my friend's comp has a Realtek RTL-8139/8139C/8139C+ card. As per the Ubuntu wiki for supported hardware:
[LIST]
[*]My friend's card is supported ([https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek))
[*]But mine is not ([https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsDynamode](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsDynamode))
[/LIST]

Have looked at the Realtek specs for the 8139D card ([http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PNid=14&PFid=6&Level=5&Conn=4&ProdID=18](http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PNid=14&PFid=6&Level=5&Conn=4&ProdID=18)) and find that 8139D has ACPI features. As I mentioned in the first post my dad's PC is quite old (but the network card is a recent addition) and while booting from the Live CD I got the message "Driver fails 2000 test, ACPI = force" or something like that.

Is this a problem caused by the fact that the PC motherboard is quite old but the network card is very new and has features that the BIOS may not support? If so, how is Win2K Professional able to handle it?

I can see the <access denied> message in lspci for the network card. Do I need to refer to some additional parameters from the datasheet and set them up to make the card work? If so, pls provide some help on that.

---

### Post by kevdog on 2007-07-03
Is there any indication in the boot log?
dmesg | more

Look for anything about the card (I know there is a lot of info in this, however just keep looking)

---

### Post by shreepads on 2007-07-04
I have attached:
 - Output from sudo dmesg
 - Output from sudo lsmod
 - Output from sudo lspci -vvnnxxx

The ouput from lspci now contains the portions that were, in the earlier uploaded file, marked as <access denied> as this time I used sudo.

One thing that I can see immediately is that 3 devices share IRQ 3:
 - Pin A: Intel Corporation 82801AA SMBus, Intel Corporation 82801AA AC'97 Audio
 - Pin B: Hangzhou Silan Microelectronics Co., Ltd. RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor

Additionally ACPI has been disabled as the BIOS is older than year 2000. From the following links by MS and IBM, I got the idea that I need to change the IRQ for the network card to make things work as without ACPI the system will not be able to handle multiple devices on the same IRQ
 - MS: [http://support.microsoft.com/kb/252420](http://support.microsoft.com/kb/252420)
 - IBM: [http://www.ibm.com/developerworks/library/l-hw2.html](http://www.ibm.com/developerworks/library/l-hw2.html)

I tried the following, to no avail
 - Changing PnP option in BIOS to 'OS doesn't support PnP'
 - Changing power management BIOS setting, first to 'ACPI' and then to 'Disabled'
 - Trying to set the IRQ using setpci
```
sudo setpci -v -d 1904:8139 INTERRUPT_LINE=n
```

No bloody luck... :(

---

### Post by shreepads on 2007-07-04
Looked again at lspci and see that the description reads "Hangzhou Silan Microelectronics Co., Ltd. RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor [1904:8139]"

Did a search on Google etc and came up with the following:
 - SuseForums: [http://suseforums.net/lofiversion/index.php/t30046.html](http://suseforums.net/lofiversion/index.php/t30046.html)
 - [http://lists.samba.org/archive/linux/2006-August/015771.html](http://lists.samba.org/archive/linux/2006-August/015771.html)

Seems like this is a FAKE Realtek card, which is manufactured by Hangzhou Silan Microelectronics, but where the packaging and vendor/ device id is tailored to make one think it is a real chipset. To make things more interesting, the box comes with its own drivers for Win 2K etc.

The solution, as outlined in the following links, is to use NDISWrapper with the original Win drivers:
 - NDISWrapper (under 'List of card known to work'): [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/)
 - [http://www.geocities.com/rohitksethi/](http://www.geocities.com/rohitksethi/)

Though I think I will instead go to the dude who sold this and make him replace with the genuine article, else use Intel which is guaranteed to work, I guess.

Almost a week wasted on this... :(

---

### Post by reen254 on 2007-07-04
man i got the same ethernet card and a netgear router.. and i do have the same problem.. well the combination works fine with window xp.. but some setting has to be fixed in linux i guess.. man its my first day with linux.. but looking at your problem not getting solved and poor help available.. i guess i will just do away with ubuntu..

---

### Post by reen254 on 2007-07-04
just as i was gonna loose my interest in ubuntu..  its all been fixed.. in fact this reply is from ubuntu.. with the net running superb.. that shows its possible to run internet on that particular lan card.. how i did it,, i didnt.. a friend of mine who happens to be a linux freak..  configured it all out.. he typed a lot.. in a lot of boxes.. and it was boring but it took him 5 mins top.. so the only thing i offer you is that it WORKS.. GUD LUCK..

---

### Post by reen254 on 2007-07-06
this is wot i got.. i had two lan cards.. both were rtl8139 one onboard the other an add on{came along with broadband connection}.. on windows xp add on card was working fine.. when i loaded ubuntu.. it wasnt.. switching to the onboard card did the trick for ubuntu..

---

### Post by shreepads on 2007-07-13
Saw enough websites to convince me that the fake card won't work out-of-box..

Bought and installed a new DLink DFE 520 TX (VIA VT6105 chipset) and all is fine after a small scare when on inserting in one of the PCI slots the network simply didn't work
Plugged into another free slot and we're browsing from the Live CD!

Now the problem I have is that the network has stopped working in Windows 2000! Maybe this is a sign....

:lolflag:

---

