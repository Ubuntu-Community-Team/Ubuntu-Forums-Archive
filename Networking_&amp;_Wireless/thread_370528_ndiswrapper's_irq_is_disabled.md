---
title: "ndiswrapper's irq is disabled"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by halfmanhalfbug on 2007-02-25
Hey ubuntus
Has anyone had a problem with ndiswrapper's IRQ being disabled?
Details: HP L2000 (AMD Turion, Broadcom 4318) 64 bit Edgy 2.6.17-11-generic kernel, ndiswrapper 1.37.
 I compiled and installed ndiswrapper from source (version 1.37) and installed the 64 bit firmware. ndiswrapper - l yields
```
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
```
The bcm43xx driver is blacklisted and wlan0 is present. No problem there but when I scan for networks none can ever be found. Then I checked dmesg and found:
```
Feb 20 20:14:28 crash kernel: [   39.039643] ndiswrapper version 1.37 loaded (preempt=no,smp=yes)
Feb 20 20:14:28 crash kernel: [   39.136401] ndiswrapper (link_pe_images:577): fixing KI_USER_SHARED_DATA address in the driver
Feb 20 20:14:28 crash kernel: [   39.137777] ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) loaded
Feb 20 20:14:28 crash kernel: [   39.138038] GSI 21 sharing vector 0xB1 and IRQ 21
Feb 20 20:14:28 crash kernel: [   39.138043] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 20 (level, low) -> IRQ 177
Feb 20 20:14:28 crash kernel: [   39.146399] ndiswrapper: using IRQ 177
Feb 20 20:14:28 crash kernel: [   39.395925] NET: Registered protocol family 17
Feb 20 20:14:28 crash kernel: [   39.844717] wlan0: ethernet device 00:90:4b:f8:d4:e2 using NDIS driver: bcmwl5, version: 0x364400a, NDIS version: 0x501, vendor: '', 14E4:4318.5.conf
Feb 20 20:14:28 crash kernel: [   39.844905] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Feb 20 20:14:28 crash kernel: [   39.857539] usbcore: registered new driver ndiswrapper
```

So far so good, but then:
```
Feb 20 20:14:28 crash kernel: [   40.079722] irq 177: nobody cared (try booting with the "irqpoll" option)
Feb 20 20:14:28 crash kernel: [   40.079728] 
Feb 20 20:14:28 crash kernel: [   40.079729] Call Trace: <IRQ> <ffffffff802b6875>{__report_bad_irq+53}
Feb 20 20:14:28 crash kernel: [   40.079755]        <ffffffff802b6af0>{note_interrupt+544} <ffffffff802a131b>{__rcu_process_callbacks+251}
Feb 20 20:14:28 crash kernel: [   40.079772]        <ffffffff802b6160>{__do_IRQ+224} <ffffffff802737a2>{do_IRQ+66}
Feb 20 20:14:28 crash kernel: [   40.079784]        <ffffffff80265cd0>{ret_from_intr+0} <EOI>
Feb 20 20:14:28 crash kernel: [   40.079802] handlers:
Feb 20 20:14:28 crash kernel: [   40.079804] [_end+130818464/2130452480] (ndis_isr+0x0/0xc0 [ndiswrapper])
Feb 20 20:14:28 crash kernel: [   40.079875] Disabling IRQ #177
```

So ndiswrapper and the Broadcom card are assigned IRQ 177 but then IRQ 177 is immediately disabled by the kernel!! If I add "irqpoll" to the boot options:
```
title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro quiet splash pci=assign-busses irqpoll
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot
```
 then everything works. I can find wireless networks and connect. However I now get the following error:
```
Feb 20 21:24:51 crash kernel: [  366.686201] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
```
Has anyone experienced the same problem? Is there a better way to fix it? Does the new kernel (2.6.20 now, I think) have the same problem?
Thanks for helping,
hmhb

---

### Post by chili555 on 2007-02-25
Sometimes IRQ problems can trace back to the setting in your BIOS that defines if you are using a plug-n-play operating system, like Windows. Try looking in your BIOS and set this to the opposite of how its set now.  Let us know the outcome, so we can all learn.

YMMV

---

### Post by halfmanhalfbug on 2007-02-26
Thanks for the reply chili555
How do I edit the BIOS? I remember reading somewhere that there is a magic key to press during startup. True?
I'm not sure it's an issue with the BIOS since previously ndiswrapper and Fedora Core 5 worked fine on this computer, but with enough coffee I'm willing to have a go at it.
hmhb

---

### Post by chili555 on 2007-02-26
It usually tells you in the first second or three of your machine booting: "Press DEL to enter setup" or "F1 to enter BIOS setup utility" or similar.

---

### Post by halfmanhalfbug on 2007-02-26
I found some  info that makes me suspect a kernel bug. This [post]("http://ubuntuforums.org/showthread.php?t=342558&page=2") had the exact same problem with a Dell 1500 wireless. And this [thread]("http://lkml.org/lkml/2006/4/30/76") shows the mess that is IRQ assignment in kernel 2.6.17, especially for IRQ 177. I found that if I pass the kernel parameter "pci-routeirq" and remove "irqpoll" then ndiswrapper is assigned IRQ 217 and is fine but firewire is given the fatal IRQ 177 and is disabled. I can live without firewire but I'll file a kernel bug and maybe try compiling 2.6.20 and giving it a shot.

---

### Post by chili555 on 2007-02-26
You can install 2.6.20 via synaptic painlessly like this: > 1. backup /etc/apt/sources.list
2. replace temporary (!) all edgy with feisty in sources.list
3. apt-get update
4. apt-get install linux-headers-2.6.20-5 linux-headers-2.6.20-5-generic linux-image-2.6.20-5-generic
5. check /boot/grub/menu.lst, mine was set to hd(0,6) and /dev/sda7 and were wrong. It must be hd(0,1) and /dev/sda2
6. restore your /etc/apt/sources.list from step 1
7. reboot

I am not sure about the part here:> check /boot/grub/menu.lst, mine was set to hd(0,6) and /dev/sda7 and were wrong. It must be hd(0,1) and /dev/sda2
I think you just need to duplicate what the settings are for your 2.6.17.x kernels.

I installed 2.6.20 on this laptop in about 15 minutes. Since the 2.6.17 et al kernels are still here, and I can boot into one any time, this seems like a painless way to try it.

I plagiarized much of this from other posts here.

Good luck.

---

### Post by halfmanhalfbug on 2007-02-27
Thank you Chili555!
I installed Feisty kernel 2.6.20-5-generic just as you described and now there are no disabled IRQ's. I need to go to a WiFi cafe tonight to test  out the scanning but it looks like all devices are running great!
When I was filing a kernel bug I found that one already exists (oops). Look at this link: [https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57355]("https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57355") to see what's going on. It looks like it's specific to 2.6.17. I would say to everyone who's experiencing flaky or non-functional bus devices in kernel 2.6.17 check the following:
```
dmesg | grep "Disabling IRQ"
```
and upgrade your kernel to 2.6.20.
Thanks again,
hmhb

---

