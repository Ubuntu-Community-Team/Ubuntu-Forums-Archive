---
title: "Need Help Installing Belkin ExpressCard"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by Kapitalizt on 2007-07-18
When I plug in my N1 Wireless ExpressCard, Ubuntu doesn't see it at all.

---

### Post by Kapitalizt on 2007-07-20
Okay I installed my Belkin card (f5d8071) via ndiswrapper.

ndiswrapper -l:

```
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)
net5416 : driver installed
        device (168C:0024) present (alternate driver: ath_pci)
```

I can't connect to my Belkin N Router with this card but I can connect to other routers with the same card. I turned the security completely off and still no avail. I can connect to this router on my onboard Broadcom however. I also tried my card on Windows and was able to connect at N (300 Mbps) speed on my router as well.

EDIT: I was able to get my card to connect using WPA2 authentication with TKIP encryption technique. Weird thing is I can't connect to my router with the card if there is no security. The only problem now is that the connection information on NetworkManager is saying that I am running at 54Mbps when I should be running at N speeds.

---

### Post by ferrett1968 on 2007-08-02
Hello, I'm a new user of Kubuntu and I have the same problem with the same express card.
dmesg doesn't reveal the presence of a new hardware when i connect it to my notebook.

Kernel 2.6.16
Sony Vaio vgn-c2z/b

Thanks!

---

### Post by Drizzt321 on 2007-08-05
> **ferrett1968 said:**
> Hello, I'm a new user of Kubuntu and I have the same problem with the same express card.
dmesg doesn't reveal the presence of a new hardware when i connect it to my notebook.

Kernel 2.6.16
Sony Vaio vgn-c2z/b

Thanks!

Are you plugging the card into your system with it already up and running? If so, try loading the pciehp driver first. If that doesn't work, try the acpiphp driver. If that one doesn't work, you'll have to boot your system with the card in. 

Why you might have to do that you ask? Simple. The first method is the correct way of doing PCI-Express hotplug. The second way is similar to the way XP does it, and the last is a garaunteed way to get the card to be recognized by the kernel. Many venders don't implement the correct way of hotplugging PCI-Express, and I haven't been able to get the 2nd way to even load on my system, so I am stuck with the 3rd way.

--Araon

---

### Post by abrichr on 2007-10-01
I'm using a Compal HEL80 laptop, with Feisty x86 installed.  I'm trying to enable hotplugging for my eSata ExpressCard in order to use my external hard drive.  So far it only works if I boot with the device plugged in.

I tried "sudo modprobe pciehp pciehp_force=1", which doesn't output anything, or detect the device.  

I also tried "sudo modprobe acpiphp", which outputs:

```
FATAL: Error inserting acpiphp (/lib/modules/2.6.20-16-generic/kernel/drivers/pci/hotplug/acpiphp.ko): No such device

```

I've tried contacting Compal, but they have little to no customer service.  What can I do?

---

### Post by teaker1s on 2008-02-18
if your n card is a F5D8071 plug in prior to booting
```
lspci
``` should show up as atheros unknown 024, if it does see my reply [here]("http://ubuntuforums.org/showthread.php?p=4353839#post4353839")

---

