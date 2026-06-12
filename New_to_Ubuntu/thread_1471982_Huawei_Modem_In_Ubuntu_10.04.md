---
title: "Huawei Modem In Ubuntu 10.04"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by Sudumahaththaya on 2010-05-04
I'm try to create a mobile broadband connection using my Huawei E 1550 medem. but in Network manager there is not way to select my modem in the first step ( device selection step ) the drop down menu is locked. what to do ?? :sad:

how to configure my modem with ubuntu ??

---

### Post by Megaptera on 2010-05-04
Hi,
Right now I'm using a Huawei E220 modem in Ubuntu 10.04. I just plugged it in USB port, waited a few minutes for it to "load" then clicked on the network icon and had the option there to create new...
That gave me a simple pop-up menu with 4 or 5 stages and it works fine. I'm on 3 mobile broadband in the UK btw.
I know it's a different model but hope this helps?

---

### Post by chemtut on 2010-05-04
Hi
I use Vodafone PAYG in the UK and it also works with 10.04.
Have you tried plugging it in before boot?
Good luck

---

### Post by qorron on 2010-05-05
exactly the same issue here.

the led turns blue, blinking which means that the modem has logged into a 3G network and is waiting for a commend to establish a connection.

dmesg:
```

[261648.191392] usb 2-1: new high speed USB device using ehci_hcd and address 2
[261648.351761] usb 2-1: configuration #1 chosen from 1 choice
[261648.356088] scsi15 : SCSI emulation for USB Mass Storage devices
[261648.356376] usb-storage: device found at 2
[261648.356381] usb-storage: waiting for device to settle before scanning
[261648.356456] scsi16 : SCSI emulation for USB Mass Storage devices
[261648.356662] usb-storage: device found at 2
[261648.356666] usb-storage: waiting for device to settle before scanning
[261653.351651] usb-storage: device scan complete
[261653.353490] usb-storage: device scan complete
[261653.353565] scsi 15:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[261653.356001] scsi 16:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
[261653.377176] sr2: scsi-1 drive
[261653.377450] sr 15:0:0:0: Attached scsi CD-ROM sr2
[261653.377630] sr 15:0:0:0: Attached scsi generic sg9 type 5
[261653.378057] sd 16:0:0:0: Attached scsi generic sg10 type 0
[261653.388291] sd 16:0:0:0: [sdh] Attached SCSI removable disk
[261666.164735] ISO 9660 Extensions: Microsoft Joliet Level 1
[261666.167734] ISOFS: changing to secondary root

```

it did work in 9.10
but now, it is broken.

to fix it:
```

apt-get install usb-modeswitch

```
replug it and off you go.

here is the bugreport:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546728](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546728)


PS: I can not believe it.
they had a very simple and working solution one month prior to the release date. and they did not use it.
linux gets worse with every release... or is it just ubuntu?
because our servers run just fine with lenny.

---

