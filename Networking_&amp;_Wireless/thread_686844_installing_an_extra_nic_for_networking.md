---
title: "installing an extra nic for networking"
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by luvinit on 2008-02-03
Hi,
I have added a nic card to my motherboard that also has an onboard NIC, with the aim of networking my comp as a server for a thin client. It turns out that both of these cards are the same, Realtek cards. Both these cards are identified under Hardware Information, but only the new card  (eth1)can be used for anything. I have to plug my cable modem into eth1 to get internet access. Firestarter doesn't recognise eth0 and says it isn't ready, no amount of messing in network tools can make it work. How do I get both of them to work?

Thanks

---

### Post by psyburn on 2008-02-03
Are they both realtek 8169 gigabit NIC's?

---

### Post by luvinit on 2008-02-03
hi,
 they are RT 8139 according to the Hardware Information. The card that I bought was just a plain unbranded one from Maplin. Is having the 2 of the same cards a problem?

---

### Post by psyburn on 2008-02-03
It can be and I've not had any luck with using 2 realtek 8169 NIC's together :mad:

When I went on my search for using dual 8169's, I found more info that doing this with 8139's is a world of pain. :(
Not that I've had any luck with 8169's in the same box. :confused:

If you could trade your 8139 PCI for a 8169 I would think you'd be in luck :)

---

### Post by luvinit on 2008-02-03
OK thanks, I guess it is logical to take it back and swap for another type, there seems to be plenty of choice, it was all just coincidence.The following command that I have learned from the magic of trawling the internet for hours on end has maybe shed some light on it. The same interrupt is shared by the 2 cards. Perhaps I can manually override the settings in the bios and it will magically work?

 desk@desktop:~$ cat /proc/interrupts
           CPU0       
  0:        136   IO-APIC-edge      timer
  1:       2984   IO-APIC-edge      i8042
  6:          5   IO-APIC-edge      floppy
  7:          0   IO-APIC-edge      parport0
  8:          3   IO-APIC-edge      rtc
  9:          0   IO-APIC-fasteoi   acpi
 12:     139921   IO-APIC-edge      i8042
 15:      50014   IO-APIC-edge      ide1
 16:      79116   IO-APIC-fasteoi   eth0, eth1
 17:      38182   IO-APIC-fasteoi   sata_via
 18:        407   IO-APIC-fasteoi   uhci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb4, ehci_hcd:usb5
 19:     175540   IO-APIC-fasteoi   nvidia
 20:       1335   IO-APIC-fasteoi   VIA8237
NMI:          0 
LOC:     402130 
ERR:          0
MIS:          0

---

### Post by psyburn on 2008-02-03
If you wanted to try that I would look up stuff on modprobe and ISA interrupts (for background)
Only hitch would be the fact that it would only work after you punched in the commands each time you rebooted. :(

Let me know how that goes...
If you figure it out I can check mine and we'll have a working solution you came up with.

---

### Post by luvinit on 2008-02-03
I will tell you about my attempts, I only aim to look in the bios and see what options are available. I have a feeling this whole network stuff is going to be a lot of hassle! :):lolflag:

---

### Post by luvinit on 2008-02-03
Ok that didn't work. You can manually assign an interrupt via the BIOS pnp/pci section, but BOTH realtek cards are on the same interrupt no matter what, you don't seem to be able to alter them individually.

---

### Post by psyburn on 2008-02-03
Well thats no good....:popcorn:
What are you thinking of doing?

EDIT: Don't get the wrong Idea that I'm telling you to use the Realtek 8169 NIC
I think they do a good job for their price but in your case anything ***but*** a 8139-based NIC will do

---

### Post by luvinit on 2008-02-04
Hi,
Now, I will probably make myself sound really stupid but is it necessary for you to have the computer that you want to network to connected and powered up during configuration? If it is, that is one possible of the problems that I am having. I don't have my thin client yet cus I wanted to check this stuff out before spending the money, and just assumed that I would be able to determine if the new network card works correctly by simply plugging my cable modem into it.
This isn't an Ubuntu specific problem because the exact same thing happens when I checked it in windows.
I changed my network card. It turns out that although the shop sells about half a dozen different cards, they are mostly the same card in different packaging. The only one I could find different was a realtek 8169. I have solved the irq conflict, but I think that happened because I put it in the very bottom PCI slot. However, the situation hasn't changed. The new  card is now called eth2, and Firestarter says that it is not ready if you configure it for internet connection sharing in the wizard. If I plug my cable modem into eth2 the connected LED lights and it appears to be connected, but as before I cannot connect to the internet if I try to load up a browser. This is different than before because with the other card I could only access the internet form the new card, eth0 wouldn't work.What do you think? Does this mean that the new card is working, but only as a LAN connection to the network, once something is connected, because it is normal for the system to only allow you internet/router/modem access via eth0?

---

### Post by kevdog on 2008-02-04
I thought the BIOS was responsible for assigning interrupts, not Linux per se.  Cant you go into the bios and manually assign the second card a different interrupt?  It may have it under the heading of "Legacy Devices", "PCI Configuration" or something else entirely but it should be there.

---

### Post by luvinit on 2008-02-04
Hi,
the whole interrupt thing is sorted now, but it makes no difference. It would be helpful if someone who actually knows something about networking could clarify whether what I am experiencing is normal.g. you should expect not to be able to get the modem to work in eth2 even if it is working correctly.

---

### Post by skysailor7 on 2008-02-05
You might want to check with your computer manufacturer.  Since eth0 is built-in, by installing another one via the pci slot, the one you installed might be disabling the onboard one.

---

