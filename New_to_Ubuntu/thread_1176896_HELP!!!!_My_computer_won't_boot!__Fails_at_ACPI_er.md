---
title: "HELP!!!! My computer won't boot!  Fails at ACPI error"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by alexcckll on 2009-06-02
Folks, 

I need your help.  I am running a Thinkpad R61i, preinstalled with Ubuntu 8.04.2LTS.  I rebooted, and it failed to start with the error 

ACPI: Looking for DSDT in initramfs.. error file ./DSDT.aml not found.

I am typing this on an ancient Toshiba 230CX running an old version of SuSE.

HELP!

I have tried booting from a ShipIt CD... this failed.

---

### Post by mbsullivan on 2009-06-02
Try adding the following boot options for your kernel:

```
noapic nolapic
```


Assuming you're using GRUB as your bootloader, this entails editing /boot/grub/menu.lst.

If you're as lazy as me, the whole process should be accomplished through the following commands:

```
sudo sed -i.bak -e 's/\(^# kopt=.*$\)/\1 noapic nolapic/g' /boot/grub/menu.lst && sudo update-grub
```

Then reboot and see if it fixed the problem.

Mike

---

### Post by alexcckll on 2009-06-02
Before I make that change, why did it suddenly bork like that?  It was trying to detect something from the BIOS - and then failed to boot.

---

### Post by mbsullivan on 2009-06-02
Did you update the kernel recently? Newer kernels have changed the way they handle custom DSDT files.

My Thinkpad (x61) "borked" recently in a related manner, though the error was different. It would freeze after:

```
ACPI: Checking initramfs for custom DSDT 
```

The most robust solution turned out to be a firmware upgrade. Perhaps you could try the same.

The *noapic, nolapic* options, even if they work, may break other things (such as an internal wireless NIC, etc.). The change is completely reversable, though.

Mike

PS: If you can't get any kernel to boot, you may have to change your /boot/grub/menu.lst file from a LiveCD.

---

### Post by LewRockwell on 2009-06-02
> **alexcckll said:**
> Before I make that change, why did it suddenly bork like that?  It was trying to detect something from the BIOS - and then failed to boot.

Ok, so you've added additional information that belongs in the first post...

caught climbing up the drainpipe after midnight...

anywho...looks like you've changed the BIOS settings for your ACPI either intentionally or by accident.

you might try changing it back if you know what you did.

---

### Post by alexcckll on 2009-06-02
OK-  tried a GRUB update-it now fails with the line 

ACPI: setting ELCR to 0200 (from 0c00) 

What now?

---

### Post by alexcckll on 2009-06-02
> **LewRockwell said:**
> Ok, so you've added additional information that belongs in the first post...

caught climbing up the drainpipe after midnight...

anywho...looks like you've changed the BIOS settings for your ACPI either intentionally or by accident.

you might try changing it back if you know what you did.
I have absolutely no idea.

I have been using the machine as an appliance in effect.. but I had not rebooted for a while - but have now found the following.

The noapic nolapic clauses work to get the machine back - although I had to boot a number of times.

But what IS now interesting is that it'll boot if I have a cable connection on my wired Ethernet card.. but not if I don't.  Removing noapic nolapic puts me right back at my initial stage

---

### Post by alexcckll on 2009-06-02
> **mbsullivan said:**
> Did you update the kernel recently? Newer kernels have changed the way they handle custom DSDT files.

My Thinkpad (x61) "borked" recently in a related manner, though the error was different. It would freeze after:

```
ACPI: Checking initramfs for custom DSDT 
```

The most robust solution turned out to be a firmware upgrade. Perhaps you could try the same.

The *noapic, nolapic* options, even if they work, may break other things (such as an internal wireless NIC, etc.). The change is completely reversable, though.

Mike

PS: If you can't get any kernel to boot, you may have to change your /boot/grub/menu.lst file from a LiveCD.
I've never done a firmware update on my Thinkpad.  How do I go about it under Linux?

I have been accepting all updates as a matter of course.

---

### Post by woedend on 2009-06-03
Have you tried reinstalling/reconfiguring the kernel?  Neither of those are error messages that SHOULD keep the kernel from booting.  If still no luck i'd really look into the mobo firmware.

---

### Post by alexcckll on 2009-06-03
It often takes a second boot attempt - but the machine has overheated from time to time...

Could it be to do with a BIOS update being needed?

---

### Post by alexcckll on 2009-06-03
I tried booting LiveCD - and failed at the time.. I'm up and running now, courtesy of the noacpi nolapci stanza... 

I'm pretty new... 

What is now the case is that this machine booted.. but then after a few hours running - froze up apart from mouse movement.. i had to do a power-off shutdown to get the keyboard back.

I have no rescue media at all - and no easy way of getting it.

---

### Post by mbsullivan on 2009-06-03
> 
ACPI: setting ELCR to 0200 (from 0c00) 

When I was having similar problems with my x61, I would freeze on this line if and only if I had noapic BUT NOT nolapic in the kernel options.

It definitely looks like this is a Thinkpad specific issue, since I had a very similar experience.

> 
What is now the case is that this machine booted.. but then after a few hours running - froze up apart from mouse movement.. i had to do a power-off shutdown to get the keyboard back.


My guess is that this is an unrelated problem.

> I've never done a firmware update on my Thinkpad. How do I go about it under Linux?

If I were you, I'd try to update your firmware.

Lenovo offers an update ISO for Linux users. All you have to do is download it, burn it to a CD, and boot from the CD. I believe that the update for your laptop (double check me on this) is available [here]("http://www-307.ibm.com/pc/support/site.wss/MIGR-68178.html").

Mike

---

### Post by LewRockwell on 2009-06-03
> **alexcckll said:**
> I have absolutely no idea.

I have been using the machine as an appliance in effect.. but I had not rebooted for a while - but have now found the following.

The noapic nolapic clauses work to get the machine back - although I had to boot a number of times.

But what IS now interesting is that it'll boot if I have a cable connection on my wired Ethernet card.. but not if I don't.  Removing noapic nolapic puts me right back at my initial stage

Here again(and for the general benefit of all), this type of information is INVALUABLE content/context and belongs in your original thread post requesting assistance. At this point, anyone viewing this thread will wonder what will be revealed next?

I'd be alarmed if my computer wouldn't boot up without being connected to the LAN/WAN. It's not like you're doing a network boot.

My personal feeling is that you've taken on a firmware level rootkit that won't allow the boot to be successful unless the rootkit gets to "phone home" first.

You would not be the first one this has happened to(although it is rare, but becoming more common).

It is therefore imperative that you update ALL firmware relevant to your equipment in an attempt to rid your machine of this critter.

It should also be noted that there are cases where firmware rootkits are unremovable/undetectable except perhaps by the original OEM(not that that would ever be cost effective mind you)

---

