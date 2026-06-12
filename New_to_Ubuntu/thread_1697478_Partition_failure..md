---
title: "Partition failure."
date: 2011-02-28
forum: New to Ubuntu
---

### Post by mjhadley on 2011-02-28
Hello, I'm using a ASUS 1005HAB netbook that had Ubuntu 10.10 and Windows XP on it. The Ubuntu filesystem failed and couldn't make it identify the partition so I used Windows XP to delete the partitions that Ubuntu was on so I could just reinstall but now when I turn on my computer it says Error No Partition and have Grub rescue> options. I have attempted to boot from a live USB image of Ubuntu, Windows XP also I tried plugging in an external DVD drive with Ubuntu disc and a Windows XP disc. All of the past options haven't boot. I can't even access the BIOS to adjust have boots when. I really hope that i haven't ruined my computer and I don't have the money to go to Staples of somewhere to have them fix it. I'm using a room mates computer currently til I can get my netbook running.
Thank you in advance for all of your help. This community is awesome and really hope that I can get this figured out.

---

### Post by Hedgehog1 on 2011-02-28
Hi there.

Here is what happened - one of the partitions you deleted was also the boot partition.

You can fix this using the XP install CD - boot off of it, and get to the command line prompt.

Once there, type:

```
FIXMBR
```

Then remove the CD and reboot - right into XP.

***The Hedge***

:KS

---

### Post by mjhadley on 2011-02-28
I have attempted to boot using an Windows XP disc via the external DVD drive and it doesn't pop up. I don't believe that DVD drive isn't getting enough power for it to spin the disc, so that won't work. Any other options? Do you think an external DVD drive with a power source would work?

---

### Post by Hedgehog1 on 2011-02-28
Ahh..  If anyone has a USB CD/DVD drive that has it's own power supply you could borrow for a few minutes, that would work.

:KS

---

### Post by Mark Phelps on 2011-03-01
> **mjhadley said:**
> I don't believe that DVD drive isn't getting enough power for it to spin the disc, so that won't work. 
Presuming you have the DVD drive connected to a USB port, if that is a v1.1 USB port, it's probably not generating enough power.  Some external USB devices come with cables that have two USB connectors on one end.  If you have one of those, you need two USB ports on your PC -- as one port handles the data, and the other port supplies the power.

> Do you think an external DVD drive with a power source would work?

Maybe ... but it's possible that your PC doesn't have the ability to boot from USB (which is a BIOS option), and it that is the case, plugging in an external drive will do you no good.

---

