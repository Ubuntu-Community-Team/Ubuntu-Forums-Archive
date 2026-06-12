---
title: "Problems Booting After Latest Linux Kernal"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by Chrissd on 2010-12-27
Hi

I have just updated my wife's laptop to 10.10 and it installed the latest Linux kernal, 2.6.35-24, which just sits with a flashing cursor.

Now she has to change the option in Grub2 to select 2.6.32-27. On Google the only fix related to Nvidia graphics issue, but she has ATI.

Many thanks in advance for any assistance.

Chriss

---

### Post by drs305 on 2010-12-27
> **Chrissd said:**
> Hi

I have just updated my wife's laptop to 10.10 and it installed the latest Linux kernal, 2.6.35-24, which just sits with a flashing cursor.

Now she has to change the option in Grub2 to select 2.6.32-27. On Google the only fix related to Nvidia graphics issue, but she has ATI.

Many thanks in advance for any assistance.

Chriss

The flashing cursor may mean you have to reinstall the video drivers. From the Grub2 menu (if you don't see it, hold down the SHIFT key during the boot), highlight the first entry. Press "e" to edit it. Cursor to the end of the "linux" line and replace "quiet splash" with "nomodeset". 

Press CTRL-x to boot. If it boots to the Desktop, select System, Administration, Additional Drivers/Hardware Drivers and reinstall your video driver.

---

### Post by Chrissd on 2010-12-27
Hi,

Thanks for the reply, it doesn't go to the Desktop, it's hanging on the line:
```

[0.666619] NET: Registered protocol family 1

```
with a flashing cursor below it.

Apprechiate the assistance.

---

### Post by sandyd on 2010-12-27
> **Chrissd said:**
> Hi,

Thanks for the reply, it doesn't go to the Desktop, it's hanging on the line:
```

[0.666619] NET: Registered protocol family 1

```with a flashing cursor below it.

Apprechiate the assistance.
add
```

acpi=off

```
as well.

---

### Post by Chrissd on 2010-12-27
After nomodeset?

---

### Post by sandyd on 2010-12-27
> **Chrissd said:**
> After nomodeset?
ya

---

### Post by Chrissd on 2010-12-27
That got it booting. How do I go about fixing this permanently?

---

### Post by sandyd on 2010-12-27
```

sudo nano /etc/default/grub
```
add it to the kernel arguments.

---

### Post by Chrissd on 2010-12-28
This has strange side effects, unfortunately, and seems to me like a bit of bodge to solve.

Side effects include no power manager and laptop not turning itself off after being shut down.

Is there a way to find out what's causing the issue, and then fix that?

Thanks again. :D

---

### Post by sandyd on 2010-12-28
> **Chrissd said:**
> This has strange side effects, unfortunately, and seems to me like a bit of bodge to solve.

Side effects include no power manager and laptop not turning itself off after being shut down.

Is there a way to find out what's causing the issue, and then fix that?

Thanks again. :D
Then lets isolate the problem with acpi

try these (one at a time after removing acpi=off)
```

acpi=force
#If you have a processor with HT (Hyper-Threading)
acpi=ht
#no irq routing + no pci scanning
pci=noacpi
#no irq
pci=noirq
#disables acpi for linux PnP
pnpacpi=off
#noioapic
noapic
#disables local apic
nolapic

```If none of them work, try combinations (the commands above make up acpi=off)

---

