---
title: "Keep the same IP Address"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by greyblitz on 2008-10-14
Hi All,

Right now I have a WinXP laptop and Kubuntu desktop. The desktop has a printer hooked up to it which I also share with the laptop. Right now the laptop is associated with the printer via [http://192.168.1.101:631](http://192.168.1.101:631), but occasionally the IP of the desktop changes to 102 and I am unable to print.

How can I make the desktop keep the same IP? Or is there another way I can have the printer shared so that the laptop always knows where to connect?

Any assistance would be very much appreciated.

---

### Post by Iowan on 2008-10-14
Two relatively easy ways: First is to set up a static address, second is to set up your DHCP server to issue a static lease to your desktop (based on MAC address, and usually just outside the normal lease range. Kubuntu is one version I don't have, so I don't know the equivalent of Network Manager - although you could always manually edit **/etc/network/interfaces** file.

---

### Post by xENO_ on 2008-10-14
For what you're suggesting, you probably want to set the DHCP server (probably a device that is often incorrectly referred to as a "router") to assign a single IP address to a given system.  
Alternately, you can set a static IP in (K)Ubuntu.  I think KNetworkManager, and know that nm-applet (these are the network status icons in KUbuntu and Ubuntu) will allow this.  Note that it is necessary to set the static IP address to one that the DHCP server will not assign.  Based on the address you gave (192.168.1.101) that range is probably 192.168.1.100-192.168.1.150, so try 192.168.1.2 is probably a good choice.
If your network-manager applet does not allow you to set up a static IP, you can alter your "/etc/network/interfaces" file so that it resembles this:
```
######################################################################
# /etc/network/interfaces -- configuration file for ifup(8), ifdown(8)
# See the interfaces(5) manpage for information on what options are
# available.
######################################################################

#
# Automatically activate devices:
auto lo
auto eth0

#
# Static IP Configuration for Local Wired Network.
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
```

---

### Post by greyblitz on 2008-10-15
Thanks to both of you for a quick response. Unfortunately at first I didn't know my way around but now I've got it figured out. So it turned out to be quite easy, but now I've got another problem and it seems to be with the printer. 

Let me know if I should be starting a new thread.

I can send print jobs but it just sits there processing forever regardless if it is sent from the laptop or host desktop. The printer doesn't even turn on. However I noticed one thing: I had unplugged my computer for a day and then plugged it back in; before even starting up the desktop, the printer turned on. I'm guessing this has something to do with the USB connection. It is a Brother HL-2040. Any help would be really appreciated.

---

