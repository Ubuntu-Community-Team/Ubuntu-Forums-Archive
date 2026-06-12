---
title: "Can my computer boot from a USB stick?"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by sylvainrb on 2009-08-01
On my BIOS for the boot order, one of the option is "onboard or USB CD-ROM" so I was wondering if I'd make a bootable USB stick, the computer would actually boot from it or the bootable option on the BIOS has to be just "USB".

Thanks!

---

### Post by LookTJ on 2009-08-01
The name varies a bit. For me, the name is USB removable device.

But you can try it out :)

---

### Post by -=hazard=- on 2009-08-01
> **sylvainrb said:**
> On my BIOS for the boot order, one of the option is "onboard or USB CD-ROM" so I was wondering if I'd make a bootable USB stick, the computer would actually boot from it or the bootable option on the BIOS has to be just "USB".

Thanks!

Yes it should work.

---

### Post by Dark Aspect on 2009-08-01
> **sylvainrb said:**
> On my BIOS for the boot order, one of the option is "onboard or USB CD-ROM" so I was wondering if I'd make a bootable USB stick, the computer would actually boot from it or the bootable option on the BIOS has to be just "USB".

Thanks!

Yes, Linux boots from USB without modification and Windows can with some modifications that break Microsoft's license agreement. Just bare in mind that any OS you boot from USB will be slightly slower and you should always disable the swap\page file to avoid them wearing out your USB flash drive.

---

### Post by -=hazard=- on 2009-08-01
> **Dark Aspect said:**
> Yes, Linux boots from USB without modification and Windows can with some modifications that break Microsoft's license agreement. Just bare in mind that any OS you boot from USB will be slightly slower and you should always disable the swap\page file to avoid them wearing out your USB flash drive.

I think he was wondering if his motherboard is capable booting from an USB.

---

### Post by Dark Aspect on 2009-08-01
> **-=hazard=- said:**
> I think he was wondering if his motherboard is capable booting from an USB.

Oh......

Well thats kinda of pointless to know really. I have booted off motherboards that didn't support USB boot. You can just create a live cd that will boot USB from that.

---

### Post by sylvainrb on 2009-08-01
> **-=hazard=- said:**
> I think he was wondering if his motherboard is capable booting from an USB.

Yes I think hazard got the point. I want the computer to boot from the USB stick to install another OS on the machine.

The file's too big to be on a CD and I don't have a DVD Burner.

@Dark Aspect: I'm not sure I'm getting the process of using a LiveCD to boot from the USB to install another OS. If you could explain a little more? Thanks

---

### Post by -=hazard=- on 2009-08-01
__sylvainbr you can try it right now man, it doesn't cost you nothing creating a bootable usb.
I think it will work :)

---

### Post by Dark Aspect on 2009-08-01
> **sylvainrb said:**
> @Dark Aspect: I'm not sure I'm getting the process of using a LiveCD to boot from the USB to install another OS. If you could explain a little more? Thanks

[How to make a Grub floppy/CD that boots all systems in a PC ]("http://www.justlinux.com/forum/showthread.php?t=142409")

Than you can boot any drive in any computer from grub, USB or other wise. though you'll have to know where your USB drive is (/dev/sd*) to load it with command line or modify the howto to your needs. take a look at /boot/grub/device.map and it begins to make a little sense. hd0,0 is drive one, partition one; hd1,0 is drive two, partition one and so on. Find which one is your USB drive and your pretty much done, heck if you don't mind walking around with cd+flash drive you don't even need a bootable USB drive.

---

### Post by -=hazard=- on 2009-08-01
> **Dark Aspect said:**
> Oh......

Well thats kinda of pointless to know really. I have booted off motherboards that didn't support USB boot. You can just create a live cd that will boot USB from that.

The idea is to boot on linux from an usb on all machines, lets say on a win machine you cant boot from a linux bootalbe usb if the motherboard doesnt support that, then if you create a linux live cd to use it on a win machine and after to boot from the usb where is the sense of using a bootable usb?

---

### Post by HiImTye on 2009-08-01
> **-=hazard=- said:**
> The idea is to boot on linux from an usb on all machines, lets say on a win machine you cant boot from a linux bootalbe usb if the motherboard doesnt support that, then if you create a linux live cd to use it on a win machine and after to boot from the usb where is the sense of using a bootable usb?

size

---

### Post by sylvainrb on 2009-08-01
I guess I just had to try to boot from the USB. On the first try, I selected the "onboard or USB CD-ROM" but it didn't work. I went back into the BIOS and like magic the option boot from a USB device appeared. Rebooted the machine and now I have it as a choice for booting. Tried it and it worked!

Thanks guys for the input!

---

### Post by Dark Aspect on 2009-08-01
> **-=hazard=- said:**
> The idea is to boot on linux from an usb on all machines, lets say on a win machine you cant boot from a linux bootalbe usb if the motherboard doesnt support that, then if you create a linux live cd to use it on a win machine and after to boot from the usb where is the sense of using a bootable usb?

To illegally gain access to a computer for one........

And two boot from a external hard drive if the main hard drive is too small for dual boot.

---

### Post by -=hazard=- on 2009-08-01
> **Dark Aspect said:**
> To illegally gain access to a computer for one........

And two boot from a external hard drive if the main hard drive is too small for dual boot.

> HiImTye

sizeYou still don't get the point, I mean what sense does, to boot from a damn usb after you already have booted to another system with a damn live cd? -.-

---

### Post by HiImTye on 2009-08-01
> **-=hazard=- said:**
> You still don't get the point, I mean what sense does, to boot from a damn usb after you already have booted to another system with a damn live cd? -.-
well the CD would really only be needed for motherboards that don't boot from the USB natively. just for a simple bootloader, I assume. could be the size of a credit card (if you cut it before you formatted the CD, that is). would be a pretty handy catch-all boot setup, if you think about it. just a GRUB CD and a USB stick, otherwise just a USB stick. keep it in your wallet and your keychain lol

---

### Post by Dark Aspect on 2009-08-01
> **HiImTye said:**
> well the CD would really only be needed for motherboards that don't boot from the USB natively. just for a simple bootloader, I assume. could be the size of a credit card (if you cut it before you formatted the CD, that is). would be a pretty handy catch-all boot setup, if you think about it. just a GRUB CD and a USB stick, otherwise just a USB stick. keep it in your wallet and your keychain lol

Thank you for actually thinking, **THAT** was what I was **TRYING** to say. It helps gain access to motherboards that don't support or lock USB boot options in the bios. I've used this method at my college since logging in as a student user is extremely slow due to all of the user's accounts being over a server and IT's epic fail. I would still boot off USB if the motherboard supported it and I had access simply cause its easier.

The point is not to boot directly from USB but rather have portable access to all computers. It doesn't matter how you boot off USB, or how many grub loaders you go through.

---

### Post by -=hazard=- on 2009-08-02
> **HiImTye said:**
> well the CD would really only be needed for motherboards that don't boot from the USB natively. just for a simple bootloader, I assume. could be the size of a credit card (if you cut it before you formatted the CD, that is). would be a pretty handy catch-all boot setup, if you think about it. just a GRUB CD and a USB stick, otherwise just a USB stick. keep it in your wallet and your keychain lol

Yes I understand that, you just explained yourself wrong before, because booting from cd and then from the booted cd boot on an usb it's just pointless :)

Ps: F***ing a windows system with a linux bootable cd or usb is the greatest feeling lol

---

### Post by -=hazard=- on 2009-08-02
> **Dark Aspect said:**
> Thank you for actually thinking, **THAT** was what I was **TRYING** to say. It helps gain access to motherboards that don't support or lock USB boot options in the bios. I've used this method at my college since logging in as a student user is extremely slow due to all of the user's accounts being over a server and IT's epic fail. I would still boot off USB if the motherboard supported it and I had access simply cause its easier.

The point is not to boot directly from USB but rather have portable access to all computers. It doesn't matter how you boot off USB, or how many grub loaders you go through.

If the motherboard doesn't support booting from usb then you have to use a bootable cd, you cant do nothing for that. But anyway all the recent motherboards support usb booting.

---

