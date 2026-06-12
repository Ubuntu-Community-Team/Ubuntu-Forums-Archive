---
title: "[SOLVED] Sitecom WL-141 installation using NDISwrapper (Hardy Heron)"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by tijmz on 2008-07-31
I had difficulty connecting a Sitecom WL-141 wireless PCI card to my LAN, so I tried following [this guide](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/). Since I had this card working under Dapper a year ago or so, I know it should be able to connect. Back then I used the drivers found [here](http://download.fujitsu-siemens.com/Download/ShowDescription.asp?SoftwareGUID=3B928095-EEEE-4194-91A7-E0CBE2D28B56). The pciid of this card is the same as that of the WL-141 (i.e. 1260:3886).

Following aforementioned guide, I did the following (after I blacklisted the prism54pci in /etc/modprobe.d/blacklist)

```

cd /home/<username>/Desktop/<driver folder>
sudo ndiswrapper &#8211;i PRISMA00.inf
sudo ndiswrapper &#8211;m
gksu gedit /etc/modules
```

In the last file I entered ndiswrapper followed by a return, then I saved, exited and rebooted.

However, I still couldn't connect and what's more, the driver that Hardy used by default (named prism54pci) was still in use, even though I blacklisted it.

Does this mean the driver I load with NdisWrapper is the same as the one that was installed by default, or did I do something wrong and isn't the new driver installed yet? And if I did install the correct driver, but still it doesn't work, is there any other way to get the card working?

Small update: running ndiswrapper -l provides me with the following output:

```

prisma00: driver installed
     device (1260:3886) present (alternate driver: prism54)

```

so I would expect the device manager/network manager/lshw to show me prisma00 as the current driver, instead of prism54pci...

---

### Post by caljohnsmith on 2008-07-31
It looks like you used the wrong name to blacklist that module, maybe because the name has changed between when that guide was written. You should put "blacklist prism54" in your /etc/modprobe.d/blacklist--the module is now called prism54 and not prism54pci it looks like. Try that and reboot. :)

---

### Post by tijmz on 2008-08-01
Thanks for the reply.

The prism54 was blacklisted by default - I should've mentioned that. Right now the blacklist contains entries for both prism54pci and prism54.

If I check the details of my wireless card, prism54pci is still listed as the current driver, though (despite the output of ndiswrapper -l saying prisma00 is connected to the card).

---

### Post by caljohnsmith on 2008-08-01
> **tijmz said:**
> Thanks for the reply.

The prism54 was blacklisted by default - I should've mentioned that. Right now the blacklist contains entries for both prism54pci and prism54.

If I check the details of my wireless card, prism54pci is still listed as the current driver, though (despite the output of ndiswrapper -l saying prisma00 is connected to the card).
Your original output from ndiswrapper said:
> prisma00: driver installed
     device (1260:3886) present (alternate driver: [COLOR="Red"]prism54[/COLOR])
Which means the prism54 module is being used, not the prism54pci module nor the "prisma00" ndiswrapper driver.

I don't know why the blacklisting is not working, but to prevent that "prism54" module from loading for sure you can do the following:
```
sudo mv /lib/modules/`uname -r`/kernel/drivers/net/wireless/prism54/prism54.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/prism54/prism54.ko_backup
```

---

### Post by tijmz on 2008-08-01
I tried your suggestion, but it doesn't seem to make any difference. I rebooted the system, but even though the file is renamed, ndiswrapper -l gives the exact same result (listing prism54 as the alternate driver). Checking the wireless connection via the GUI also gives the same results as before:

[img]http://hangmat.etv.cx/images/wificonnection.png[/img]

I tried doing as you suggested, but using prism54pci instead of prism54 in the directory and filenames. However, there's no directory for this driver. To add to my confusion, the directory /lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless does list the file [COLOR="Red"]p54pci.ko[/COLOR] (and not something like prism54pci.ko).

:confused:

Edit: I'll try blacklisting this p54pci module and see what happens.

---

### Post by tijmz on 2008-08-01
That last attempt worked. I blacklisted p54pci and now the loaded driver is ndiswrapper. Wireless connection established.

Many thanks!

---

