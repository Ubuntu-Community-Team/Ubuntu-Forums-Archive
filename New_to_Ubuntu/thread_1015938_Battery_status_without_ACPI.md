---
title: "Battery status without ACPI?"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by teranex on 2008-12-19
Hi,

Because of some problems (freezing x-server), i have disabled ACPI on my Travelmate 4001. Now i'm wondering if it is somehow possible to still see the battery status while ACPI is disabled? I guess not, but asking doesn't hurt i guess :)

thx!

---

### Post by mali2297 on 2008-12-19
> **teranex said:**
> Hi,

Because of some problems (freezing x-server), i have disabled ACPI on my Travelmate 4001. Now i'm wondering if it is somehow possible to still see the battery status while ACPI is disabled? I guess not, but asking doesn't hurt i guess :)

thx!

If you just have turned off the ACPI daemon but kept the kernel modules, then the battery status can still be read from the files /proc/acpi/battery/BAT0/info and /proc/acpi/battery/BAT0/state (at least on my system).

Check
```

cat /proc/acpi/battery/BAT0/info /proc/acpi/battery/BAT0/state

```

---

### Post by teranex on 2008-12-19
> **mali2297 said:**
> If you just have turned off the ACPI daemon but kept the kernel modules, then the battery status can still be read from the files /proc/acpi/battery/BAT0/info and /proc/acpi/battery/BAT0/state (at least on my system).

I turned ACPI of using a kernel param (acpi=off), so i have no /proc/acpi. I tried disabling acpid in Services and rebooting without the kernel param, but then my laptop freezes as happens most of the times when ACPI is enabled... i guess there is no way to check it when acpi is disabled with a kernel param?

---

### Post by sdennie on 2008-12-19
If you've booted with the acpi=off kernel option then no, I don't think you can see the battery status.

---

### Post by mali2297 on 2008-12-19
> **teranex said:**
> I turned ACPI of using a kernel param (acpi=off), so i have no /proc/acpi. I tried disabling acpid in Services and rebooting without the kernel param, but then my laptop freezes as happens most of the times when ACPI is enabled... i guess there is no way to check it when acpi is disabled with a kernel param?

Perhaps you can try [APM]("http://packages.ubuntu.com/intrepid/apmd") instead.

---

