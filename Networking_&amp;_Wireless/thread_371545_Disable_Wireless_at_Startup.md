---
title: "Disable Wireless at Startup"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by cb474 on 2007-02-27
I'm using network-manager to run an Atheros AR5212 on a ThinkPad T60. I'd like to configure network-manager to have wireless disabled at startup. Currently, if I right click on the network-manager applet, "enable wireless" is always checked after startup and will immediately attempt to connect to any present wireless access points. I'm often not using wireless and this wastes my battery.

Also, a side question, when "enable wireless" is unchecked, does this mean the wifi card is actually powered off or just that network manager is disabled for wireless? I want the card to power all the way off to save as much battery as possible.

Thanks for any ideas on how to do this.

---

### Post by racmar on 2007-03-13
The t60 series have a small wireless on/off switch located under the touchpad to the left.  To completely disable power to the wireless card, move the switch to the left ( off ).

To answer your question:  when network manager is set to disable networking, the wireless card still has power.

---

### Post by maser on 2007-03-22
Should that switch be working out of the box? I never tried to get it working, but it doesn't work on my T60 (Edgy). Is there any other way to disable the wireless card?

---

### Post by racmar on 2007-03-22
I'm also running Edgy, and the switch works fine for me.  I think the wireless card must be designed like a usb device, here is my output from dmesg after toggling the switch:
```
[17220216.408000] ipw3945: Radio Frequency Kill Switch is On:
[17220216.408000] Kill switch must be turned off for wireless networking to work.
[17220216.524000] usb 4-1: USB disconnect, address 2
[17220216.900000] usb 2-1: USB disconnect, address 3

```

Then, my wireless LEDs turn off ( both bluetooth and LAN ), and I can no longer access the Internet via the wireless connection.


When I change the switch back, I see the following dmesg output:
```
[17220249.080000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[17220249.296000] usb 4-1: new full speed USB device using uhci_hcd and address 4
[17220249.464000] usb 4-1: configuration #1 chosen from 1 choice
[17220249.892000] usb 2-1: new full speed USB device using uhci_hcd and address 4
[17220250.052000] usb 2-1: configuration #1 chosen from 1 choice

```
And my wireless starts working again.



NOTE:  I am using NetworkManager 0.6.3, not the standard ubuntu wireless manager.
```
sudo apt-get install network-manager-gnome network-manager
```

---

### Post by racmar on 2007-03-22
Oh, you could also remove the ipw3945 module from the kernel.  I think it is located in linux-restricted-modules:
```
sudo apt-get remove linux-restricted-modules-*
```

But that my disable more drivers ( eg. Nvidia and ATI )

It might make more sense to rename the ipw3945 kernel driver:
```
sudo mv /lib/modules/2.6.17-11-generic/kernel/drivers/net/wireless/ipw3945/ipw3945.ko /lib/modules/2.6.17-11-generic/kernel/drivers/net/wireless/ipw3945/ipw3945.ko.off

```

or blacklist the ipw3945 driver ( but I don't remember how to do that )

---

### Post by cb474 on 2007-03-28
I have network-manager-gnome and network-manager installed, in Edgy. It says it's version 0.6.3-2ubuntu6. Is that different from what you're using, racmar?

I'm also on a T60 and the wireless switch does not work for me. But I really wish it did!

---

### Post by racmar on 2007-03-28
```
dpkg -l | grep -i network | grep -i manager
ii  network-manager                            0.6.3-2ubuntu6                           network management framework daemon
ii  network-manager-gnome                      0.6.3-2ubuntu6                           network management framework (GNOME frontend)

```

As you can see, I have the same version.  Also, FN+F5 togles wireless on and off on my machine.  I would check the bios tfo see if there is some obvious reason why your wireless switch does not function.  Failing a solution, I would call Lenovo for tech support, possibly a warranty repair.

---

### Post by cb474 on 2007-04-05
racmar, Thanks for the response. I forgot about fn+f5. That does seem to work, for me, but the LED doesn't work, so it's a pain because you never know which state the wireless is in.

The switch continues not to work.

I'm pretty sure this is an issue with Ubuntu. The switch and everything works the way it should in Windows.

---

