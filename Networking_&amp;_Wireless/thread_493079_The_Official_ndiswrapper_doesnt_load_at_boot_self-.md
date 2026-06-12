---
title: "The Official ndiswrapper doesnt load at boot self-help thread!"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by #Reistlehr- on 2007-07-05
Personally, i really think we needed this. :D 

Now to start, this thread is directed to people who have added ndiswrapper to the /etc/modules file, and have to run modprobe ndiswrapper every time at boot.

Upon troubleshooting the problem, i decided to run this command:
```
dmesg |grep ndiswrapper
```
i received this in response:
```
[   46.728140] ndiswrapper version 1.47 loaded (smp=yes)
[   46.844870] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   46.846638] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   46.853080] ndiswrapper (NdisWriteErrorLogEntry:192): log: C000138D, count: 1, return_address: ffffffff88aaa80e
[   46.853084] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x110
[   46.853095] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[   46.853100] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[   46.853110] ndiswrapper (mp_halt:258): device ffff810073200500 is not initialized - not halting
[   46.853117] ndiswrapper: device eth%d removed
**[   46.853132] ndiswrapper: probe of 0000:03:00.0 failed with error -22**
[   46.856692] usbcore: registered new interface driver ndiswrapper
```

So i googled Error -22

[quote="ndiswrapper faq"]"If you get probe of XXXX:YY.ZZ.A failed with error -22, you may have IRQ problems or it might be a USB driver problem. If you have problems with IRQ assignment the kernel couldn't assign IRQ for the wireless card, you can find out which IRQ ndiswrapper is trying to use and release that IRQ find out which other device is using it with cat /proc/interrupts. You may want to use ACPI and configure BIOS to assign IRQs using ACPI. If it's a USB driver problem there are known issues with high speed USB and ndiswrapper, module under 2.6 is called ehci_hcd, try modprobe --remove ehci_hcd and then reload the ndiswrapper module, that's worked for some people."[/quote]

No i have an HP and i need to use the boot option of noapic. Everytime the system boots, i get an error in terminal, "disabling IRQ #7".. Now, those of you who know computers somewhat, know that IRQ 7 is designated for Parallel ports (printers). Since the laptops does not possess a device to run on IRQ7, so it's the operating system doing it's job handling the IRQ's with ACPI. Yet, when you check the IRQ's, it has assigned:
```
  7:      64228     839925    XT-PIC-XT        ehci_hcd:usb2

```

To see your interupts assigned by ubuntu, use:
```
cat /proc/interrupts 
```

Well, to get back ontopic, if you are like me, you probably tried to add depmod -a and modprobe ndiswrapper to rc.local, or create your own startup script, with no luck!

Well, one thing could be, from what i read, there is a bug in the 64-Bit kerenl that requires ndiswrapper to be loaded twice. is it true? who knows.

Another thing could be, that, your IRQ's are all messed up. But being on a laptop with a locked down BIOS, i have the inability to manually, through bios to assign IRQ's, so is there a way to manually assign ndiswrapper an IRQ?

Does something boot out of sequence?

If you're in the same ballpark, reply, and lets see if we can work it out.

**Everyone--**
If possible, i would like people to post the following outputs of the commands:
```
dmesg |grep ndiswrapper
```
```
cat /proc/interrupts
```
```
cat /proc/modules |grep ndiswrapper
```

Thank you.

---

### Post by S15_88 on 2007-07-05
I remember you had made a post in my thread regarding my problem with ndiswrapper and my wireless, it seems that this may be one of the problems that ndiswrapper is not loading correctly/succesfully unfortunitely i am at work right now and am using a company notebook but when i get home i'll be sure to post my output so we can resolve this problem and help others that encounter it!  

Thanks, Alain

---

