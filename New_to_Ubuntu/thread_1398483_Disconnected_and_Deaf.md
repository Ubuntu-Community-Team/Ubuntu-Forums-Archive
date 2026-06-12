---
title: "Disconnected and Deaf"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by 1401gazza on 2010-02-04
Hi
I'm a complete novice and was introduced to Ubuntu by a more experienced friend who installed it and also removed windows from my laptop completely. My friend has since moved hundreds of miles away and I'm stuck. I had a few teething problems with fsck freezing while booting, I managed to fix this but now my wireless card won't work, following the advice on the forum I looked for my card ID in the ndiswrapper database but it's not listed....What do I do now?

My card is a Belkin G plus MIMO F5D9010

I've also lost all sound! and I only use my laptop for the internet and my music collection...DOH!

---

### Post by tgalati4 on 2010-02-04
Open a terminal and page through this file:

dmesg | more      (spacebar to go forward, q to quit)

Look for disk/read errors.  It's possible your disk is failing.  If you lost your network and sound driver files then you won't have those functions.

I presume that your network and sound were working previously?

---

### Post by Bartender on 2010-02-04
Your "friend" made a poor choice in removing Windows completely.  Do you have recovery discs?

If so, I'd sure consider reinstalling Windows, then setting up Ubuntu as a dual-boot.  Going to Linux cold turkey isn't the best option.  Even if you were handy with Linux, there are still times when you need to use Windows.

---

### Post by 1401gazza on 2010-02-06
> **tgalati4 said:**
> Open a terminal and page through this file:

dmesg | more      (spacebar to go forward, q to quit)

Look for disk/read errors.  It's possible your disk is failing.  If you lost your network and sound driver files then you won't have those functions.

I presume that your network and sound were working previously?


Hi 
Yes network & audio were fine before.
I had a look through the dmesg terminal ( reminded me of the time I picked up a chinese newspaper ), I've copied anything that looked remotely negative below:-
[SIZE=2]
[/SIZE]    [SIZE=2][    1.825732] <6>8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)[/SIZE]
  [SIZE=2][    1.825799] 8139cp 0000:02:07.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too[/SIZE]
  [SIZE=2][    1.829370] 8139too Fast Ethernet driver 0.9.28[/SIZE]
  [SIZE=2] [    1.829484] 8139too 0000:02:07.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18[/SIZE]
  [SIZE=2][    1.831450] eth0: RealTek RTL8139 at 0xa000, 00:a0:d1:29:86:01, IRQ 18[/SIZE]
  [SIZE=2][    1.848451] [Firmware Bug]: ACPI(VGA0) defines _DOD but not _DOS[/SIZE]
  [SIZE=2] [/SIZE]
  [SIZE=2] [/SIZE]
  [SIZE=2][    1.819487] [drm] radeon default to kernel modesetting DISABLED.[/SIZE]
  [SIZE=2][    1.819653] pci 0000:01:05.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16[/SIZE]
  [SIZE=2] [/SIZE]
  [SIZE=2][    1.036966] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19[/SIZE]
  [SIZE=2] [/SIZE]
  [SIZE=2]
[/SIZE]
  [SIZE=2] [/SIZE]
  [SIZE=2][    0.267540] system 00:08: iomem range 0x0-0x9ffff could not be reserved[/SIZE]
  [SIZE=2][    0.267545] system 00:08: iomem range 0xec000-0xfffff could not be reserved[/SIZE]
  [SIZE=2][    0.267549] system 00:08: iomem range 0x100000-0x4bffffff could not be reserved[/SIZE]
  [SIZE=2] [/SIZE]
  [SIZE=2] [    0.233396] pci 0000:02:07.0: PME# disabled[/SIZE]

---

### Post by 1401gazza on 2010-02-06
> **Bartender said:**
> Your "friend" made a poor choice in removing Windows completely.  Do you have recovery discs?

If so, I'd sure consider reinstalling Windows, then setting up Ubuntu as a dual-boot.  Going to Linux cold turkey isn't the best option.  Even if you were handy with Linux, there are still times when you need to use Windows.


I don't think the complete removal of windows was intentional and no I don't have recovery discs. A local Computer shop quoted £45 to reload Windows XP but I thought I'd seek advice here first.

---

### Post by KIAaze on 2010-02-07
> **1401gazza said:**
> I had a few teething problems with fsck freezing while booting, I managed to fix this but now my wireless card won't work, following the advice on the forum I looked for my card ID in the ndiswrapper database but it's not listed....What do I do now?

My card is a Belkin G plus MIMO F5D9010

I've also lost all sound! and I only use my laptop for the internet and my music collection...DOH!

What did you do to fix the fsck freezing problem?

Also, do you have an Ubuntu Live-CD? (The standard Ubuntu installation disk is a Live-CD)
If not, you can download and burn one from here: [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)
Or Xubuntu in your case: [http://www.xubuntu.org/get](http://www.xubuntu.org/get)

Once you have one, you can boot from it.
It would be interesting to know if audio and wireless work by default or not first.
Also, if you have a separate home partition, an easy solution might be reinstalling.


Could you please post the output of the following command:
```
uname -a
```

Also run this:
```
sudo lspci -vvnn >~/lspci.log
```
And post the generated file ~/lspci.log

The driver for your wireless card appears to be [rt73usb]("http://ubuntuforums.org/showthread.php?t=493660"), so it might also be useful if you already have it installed or not.
To search for it run the following 2 commands:
```
sudo updatedb
locate rt73usb.ko

```

---

