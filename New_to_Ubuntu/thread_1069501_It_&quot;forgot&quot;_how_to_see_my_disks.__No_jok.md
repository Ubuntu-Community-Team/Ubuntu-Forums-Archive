---
title: "It &quot;forgot&quot; how to see my disks.  No joke."
date: 2009-02-14
forum: New to Ubuntu
---

### Post by DigiTan on 2009-02-14
I have two SATA disks that the BIOS and WinXP are able to recognize.  I boot off Live CD and normally I can find these disks in GParted, "Places," and the /dev/sda or /dev/sdb folder.  Now they're invisible.  (Good job, Ubuntu.  Good job)

I haven't installed anything and my disks are wired up exactly as they were before.  The only change between then and now is I add "acpi=off" to the boot menu options.  So it doesn't crash.

Also, Busybox has been telling this story during bootup, even in quiet mode...
```
ata200: failed to set xfermode (errmask=0x40)
```
It then waits 5 seconds between disk retries before giving up after what seems forever.  The first time I used Ubuntu, I didn't have to mount them.  If it could see these devices before, why would it pick now to forget how to use them?

---

### Post by DigiTan on 2009-02-14
While I'm still here...
[LIST]
[*]fdisk can't see it either
[*]CD/DVD ROM is still visible
[*]CD integrity check - Passed
[*]MemTest86 - Passed
[*]Fails to set xfermode whenever I set "acpi=off"
[*]"acpi_irq_balance" does nothing
[/LIST]

---

### Post by hellion0 on 2009-02-14
Try "acpi=force" and see what happens.

---

### Post by DigiTan on 2009-02-14
I'll try it next.

The boot syslog definitely identified both SATA disks.  I'm going to try changing the acpi settings in the BIOS to something Linux might actually be able to tolerate.  If unsuccessful, there's the open possibility that moving these devices to channels 3 and 4 will solve the problem.  It's worked for others on this forum.

---

### Post by DigiTan on 2009-02-14
Nope.  It's still sucking.

I tried acpi=force and both drives were visible again, but Ubuntu crashed before I had a chance to actually do anything about it.  I also tried setting different HDD suspend modes, then enabling RAID and Live CD couldn't even boot itself.

So basically Linux is unstable without acpi=off, and can't see drives with it on?  Just what my weekend needs.

---

### Post by DigiTan on 2009-02-14
I finally found a boot option combination that works.  If your system is unstable without the **acpi=off** or **noacpi** states, add **irqpoll** to your boot options.  Note, this does not work for everybody and like regular acpi problems, this is a bug that spans multiple chipsets and hardware configurations.

If irqpoll does not work for you, acpi_irq_balance works for some people in the kernel, but it did not for me.

Finally, if your'e desperate, try physically mounting your SATA disks to the highest channels your motherboard past.  In my case, this would have ment moving their plugs from sockets #1 and #2 to #3 and #4 respectively.  Luckily I did not have to go that far.

---

