---
title: "Changing drivers for card"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by darkpaladin79 on 2007-03-15
I've got an edimax ew7128 (i'll check that for sure later, dont think thats the right model name), and it has been autodetected as using the rt61 driver.  Actually, it uses the rt2500 driver.  How can i simply switch which driver it uses? I'm fairly new to ubuntu.


Thanks,
Ivan

---

### Post by chili555 on 2007-03-15
Check here: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax) It shows three different versions of the 7128, one with the rt61 chipset, one with the rt2500 and one with AR5212!

Generally, if a card tells you it's a rt61, I'd tend to believe it. But, if you really want to do this, simply sudo rmmod -f rt61, sudo gedit /etc/modprobe.d/blacklist and add rt61. Then sudo modprobe rt2500. It may not stick, unless you sudo gedit /etc/modules to add alias eth1 rt2500. Use your relevent wireless interface in place of eth1 here. You will probably want to reboot.

Post back and let us know.

---

### Post by darkpaladin79 on 2007-03-15
Well, I got this card working before on fedora core 4, on (i think =/) the rt2500.  I really hope that was the one, since now there's reasonable doubt that it wasn't rt2500.

Anyway, under device manager the card is identified as:

Vendor: RaLink
Device: Unknown (0x0301)

Status: Status
Bus Type: PCI

Device Type: Unknown
Capabilities: Unknown

I do have lights flashing on the outside of the card, which is a good sign.  Sometimes, ifup ra0 gives me some sort of error on the essid which i can't copy down, its an error in /etc/ifup.pre.d or something.

edit:
Here's the error:
 /etc/network/if-pre-up.d/wireless-tools: line 103:   4818 Segmentation fault
 $IWCONFIG "$IFACE" essid "$IF_WIRELESS_ESSID"


Another quick q in case I missed something: Are there any special formattings I need for interfaces under ubuntu? Like putting essid in quotes or putting the wep password in hex or something.  Maybe this is causing an error.



Progress is progress. . .


-Ivan

---

### Post by chili555 on 2007-03-16
Here is my Acme Little Giant WEP tutorial. See if it helps. [http://www.ubuntuforums.org/showthread.php?t=172810&page=2&highlight=wep](http://www.ubuntuforums.org/showthread.php?t=172810&page=2&highlight=wep)

---

### Post by darkpaladin79 on 2007-03-16
Well I haven't gotten much farther.  Check this out:
sudo iwlist ra0 c
ra0        13 channels in total; available frequencies : 
            channel 01: 1 mhz
            channel 02: 2 Mhz
. . .up to
            channel 54: 54 Mhz
            current channel=6

Isn't that supposed to give me channels 1 to 11? I have the channel set to 6 on router and in /etc/network/interfaces. . .Weird.  Gives me the feeling that I do need rt2500 instead.

---

### Post by darkpaladin79 on 2007-03-16
Well after no success for a week or so, I think I'm just going to go back to fedora, where it worked fine.  Thanks for help anyway guys.

---

