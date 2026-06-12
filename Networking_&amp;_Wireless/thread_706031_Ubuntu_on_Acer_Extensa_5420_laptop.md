---
title: "Ubuntu on Acer Extensa 5420 laptop"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by jason_fresher on 2008-02-24
i installed Ubuntu on my Acer Extensa 5420 laptop using the Wubi installer, and for some reason, neither the wireless nor the wired net work... could someone help me out ? or could someone let me know if they have had similar problems with this laptop ? the device manager shows the wireless card as a Dell wireless card, while windows shows it as a broadcom wireless adapter.

the Ethernet adapter is a Marvell Yukon 88E8071 PCI-E Gigabit Ethernet Controller

and the wireless adapter is a BROADCOM.NTx86.6.0:BCM43XG_NT6


any help will be appreciated, since i really want to get this laptop configured to Ubuntu so i can get moving.

---

### Post by Mad_Gouki on 2008-02-24
I have this same laptop.
the wifi does not work from a fresh install, however, for me, the ethernet did.  I ran a Gutsy livecd and installed from that.  I don't know if wubi installs the same version that the livecd does, but if it does, your ethernet should be working.

to get the wifi working, plug your laptop up through ethernet and then at the top click system>administration>restricted drivers manager
it should list an ati video card and a bcm43xx card there.  click the enabled box by the bcm43xx card in the list, and it should download 2 or 3 files and install them.  After that, the wifi card should work.
we could have different hardware in our acer extensa 5420's, but I think acer numbers the computers individually based on the specific hardware inside.

If you don't have working ethernet, you will have to download the drivers with another computer and transfer them to the laptop (via usb, disk, something like that) and then install them from there.

if you are using Ubuntu Gutsy, this link should guide you through getting the wifi driver with online or offline capabilities.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

It would be helpful to know which version of Ubuntu you have installed.

---

### Post by jason_fresher on 2008-02-24
i just checked it, its Ubuntu 7.04, Feisty Fawn..

when i open restricted device manager, all i get is the ATI raedon. the Wifi card is not listed.

---

